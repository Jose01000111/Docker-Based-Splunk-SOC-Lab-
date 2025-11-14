# Phase 6 — 🐳 Docker-Based Splunk SOC Lab (Windows 11 Pro x64)

In this phase, I’m diving into running Splunk Enterprise in Docker on my Windows 11 Pro machine. My goal is to understand how Splunk interacts with Windows, containers, endpoints, and VMs in a SOC lab. It was frustrating at first because Docker setup and permissions kept tripping me up, but by the end, everything is running and I can really start learning Splunk.

---

## ⚙️ Docker & System Setup

Before touching Splunk, I had to make sure my Windows version and CPU were compatible. I also learned how Docker containers behave on Windows and how WSL2 interacts with the host OS.  

- Windows 11 Pro, Version 22H2, x64-based  
- Docker Desktop for AMD64 with WSL2 backend  
- Host OS interacts with containers for port mapping and file sharing  
- Understanding leftover containers and cleanup helps prevent conflicts

Tech Stack / Index:

- Windows 11 Pro x64  
- Docker Desktop (AMD64)  
- WSL2  
- PowerShell (for managing files and Docker commands)

---

## 🐳 Pulling and Running the Splunk Container

I pulled the Splunk image and ran it in a container. The GUI opened in my browser, which made me realize how containers can host SOC tools without spinning up full VMs for everything. I ran into license acceptance errors and leftover container issues, which taught me how to troubleshoot in a Docker environment.  

- Container runs Splunk Web (port 8000) and Forwarder (port 9997)  
- Mapping container ports to Windows host is key for access  
- License acceptance and container cleanup are part of Docker workflow  

Tech Stack / Index:

- Splunk Enterprise (Docker image)  
- Container ports mapped to host  
- Docker run parameters for environment variables  

---

## 🌐 Splunk Web Exploration

Opening Splunk Web for the first time was satisfying. Dashboards, menus, and system settings are intuitive. I explored Search & Reporting and default dashboards to understand where data will appear once I start ingesting logs.  

- Search & Reporting app is my main workspace  
- Default dashboards give quick insights  
- Settings menu manages users, roles, indexes, and apps  
- Using a browser on Windows host interacts directly with containerized Splunk  

Tech Stack / Index:

- Splunk Web UI  
- Windows host browser  
- Dashboards & Reporting app  

---

## 📂 Creating a Sample Log

I created a sample log on my Windows endpoint to simulate logs from a real server or endpoint. This helped me practice ingesting data without needing a full VM or forwarder.  

- Documents folder on Windows host contains `sample2.log`  
- Test logs simulate Windows endpoint events  
- Copied log into the container for ingestion  

Tech Stack / Index:

- Windows endpoint file system  
- PowerShell for file creation  
- Docker copy command to move logs into container  

---

## 📊 Creating a Splunk Index

I created a new index called `os_logs` in Splunk Web. Keeping extra options disabled allowed me to focus on ingestion and searching rather than complex index settings.  

- Index holds all Windows sample logs  
- Paths mostly default to container-managed storage  
- Disabled tsidx reduction and integrity checks to simplify lab  

Tech Stack / Index:

- Splunk Indexes: os_logs  
- Event-based indexing  
- Splunk GUI for index management  

---

## ⬆️ Uploading Logs

Uploading `sample2.log` made me feel like I was bridging my Windows endpoint with Splunk running in Docker. Seeing logs appear in searches confirmed the container-host integration works.  

- File uploaded from Windows host to Splunk container  
- Source type set to syslog (or auto-detect)  
- Index set to `os_logs`  

Tech Stack / Index:

- Windows endpoint log file  
- Splunk Web Add Data function  
- syslog source type  
- os_logs index  

---

## 🔍 Searching Logs

After uploading, I ran searches to verify everything worked. All test lines appeared. This step helped me practice the most essential Splunk skill: finding the data I need quickly.  

- Confirmed logs from Windows endpoint appear  
- Validated ingestion pipeline from host → container → Splunk  
- Practiced using basic Splunk queries  

Tech Stack / Index:

- Splunk search bar  
- index=os_logs  
- sourcetype=syslog  

---

## 🔄 Container Control

I stopped and restarted the container to simulate real operations. Splunk preserved the data, proving containerized setups can be stable for SOC labs.  

- Stop/start container preserves logs  
- Access container logs via Docker for troubleshooting  
- Useful for testing resilience without full VM resets  

Tech Stack / Index:

- Docker container lifecycle commands  
- Persistent Splunk container storage  

---

## ✍️ Observations

Running Splunk in Docker on Windows 11 Pro gave me hands-on insight into how SOC tools can run on lightweight containers. I can ingest logs from Windows endpoints, experiment with dashboards, and practice searches without needing multiple VMs. Troubleshooting Docker permissions, leftover containers, and file paths was frustrating but valuable.  

I feel more confident that I can run Splunk locally, bridge Windows endpoints or servers, and start building real SOC workflows in a lab environment.

Tech Stack / Index:

- Windows host  
- Windows endpoint logs  
- Docker + Splunk container  
- Splunk Web UI  
- Search & Reporting app  
