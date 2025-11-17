# How I Connected Kali MCP Server to LM Studio to Run AI Models

![Home](./images/Home.png)
<br><br>
![Kali](./images/kali.png)

I recently discovered a way to connect my Kali MCP server to LM Studio, enabling me to run AI models directly from Kali. Here’s a step-by-step guide on how I did it.

---

## Step 1: Install the MCP Kali Server

First, open your terminal and install the Kali MCP server package:

```bash
sudo apt install mcp-kali-server
<br>
Step 2: Clone the MCP Server Repository
Next, go to your home directory and clone the official GitHub repository to get mcp_server.py:

bash
Copy code
cd ~
git clone https://github.com/Wh0am123/MCP-Kali-Server
This will download the repository containing mcp_server.py.

<br>
Step 3: Install LM Studio
Go to the official LM Studio website and download the latest version.
Once downloaded, make it executable and run it:

bash
Copy code
chmod +x ./LM-studio-<version>-x64.AppImage
./LM-studio-<version>-x64.AppImage
<br>
Step 4: Download a Model
Once LM Studio is running:

Go to the Program tab (top-left corner)

Click Install to choose a model

I recommend using the GPT-OSS model

<br>
Step 5: Start the Kali MCP Server
Open a new terminal window and start the server:

bash
Copy code
kali-server-mcp
You should see the server running at:

cpp
Copy code
http://127.0.0.1:5000
This is your Kali MCP server.

<br>
Step 6: Configure LM Studio to Use the MCP Server
In LM Studio, open the mcp.json file.

Replace its content with the following (update the path to your mcp_server.py):

json
Copy code
{
  "mcpServers": {
    "kali_mcp": {
      "command": "python3",
      "args": [
        "/absolute/path/to/mcp_server.py",
        "--server",
        "http://127.0.0.1:5000/"
      ]
    }
  }
}
🔹 Important: Replace /absolute/path/to/mcp_server.py with your actual path.

Save the file.

<br>
Step 7: Restart LM Studio
Close LM Studio and open it again.
Your setup should now be fully functional — LM Studio will connect to your Kali MCP server and run models through it.

✅ Conclusion
By connecting LM Studio to my Kali MCP server, I can now run AI models locally on Kali with full integration. This setup opens up new possibilities for testing and deploying models in a secure Linux environment.