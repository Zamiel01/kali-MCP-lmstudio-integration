# How I Connected Kali MCP Server to LM Studio to Run AI Models

![Home](./images/Home.png)  
![Kali](./images/kali.png)

---

## Step 1: Install the MCP Kali Server  

First, open your terminal and install the **Kali MCP server** package:

```bash
sudo apt install mcp-kali-server
```
![Open LM Studio](./images/install.png)
---

## Step 2: Clone the MCP Server Repository  

Next, go to your home directory and clone the official GitHub repository to get `mcp_server.py`:

```bash
cd ~
git clone https://github.com/Wh0am123/MCP-Kali-Server
```

This will download the repository containing `mcp_server.py`.

---

## Step 3: Install LM Studio  

Go to the official [LM Studio](https://lmstudio.ai) website and download the latest version.  
Once downloaded, make it executable and run it:

```bash
chmod +x ./LM-studio-<version>-x64.AppImage
./LM-studio-<version>-x64.AppImage
```

![Open LM Studio](./images/open-lmstudio.png)

---

## Step 4: Download a Model  

Once LM Studio is running, go to the **Program** tab (top‑left corner).  
Click **Install** and choose a model – I recommend using the **GPT‑OSS** model.

---

## Step 5: Start the Kali MCP Server  

Open a new terminal window and start the server:

```bash
kali-server-mcp
```

You should see the server running at:

```
http://127.0.0.1:5000
```

This is your Kali MCP server.

---

## Step 6: Configure LM Studio to Use the MCP Server  

In LM Studio, open the `mcp.json` file.  
Replace its content with the following, making sure to update the path to `mcp_server.py`:

```json
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

```
![Open LM Studio](./images/entering-mcp.json-script.png.png)
```
```

**Important:** Replace `/absolute/path/to/mcp_server.py` with the actual path where you cloned the GitHub repository.  
Save the file.

---

## Step 7: Restart LM Studio  

Close LM Studio and open it again.  
Your setup should now be fully functional, allowing you to run AI models from your Kali MCP server through LM Studio.


---

✅ **Conclusion**  
By connecting LM Studio to my Kali MCP server, I can now run AI models locally on Kali with full integration. This setup opens up new possibilities for testing and deploying models in a secure Linux environment.