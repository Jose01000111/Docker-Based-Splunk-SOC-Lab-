# Phase 6 — 🐳 Docker-Based Splunk SOC Lab (Windows 11 Pro x64)

In this phase, I’m running Splunk Enterprise in Docker on my Windows 11 Pro machine. The goal is to understand how Splunk interacts with Windows, containers, endpoints, and VMs in a SOC lab. It was a little frustrating at first because Docker setup and permissions got in the way, but by the end, everything worked and I could finally start learning Splunk properly.

---

## ⚙️ Docker & System Setup

Before touching Splunk, I had to make sure my Windows version and CPU were compatible. I also learned how Docker containers behave on Windows and how WSL2 interacts with the host OS.  

<img width="458" height="456" alt="3MGgXqE" src="https://github.com/user-attachments/assets/e01a1bd2-8960-429e-9c7d-210a1657c642" />

---

<img width="699" height="489" alt="JiQ89Tn" src="https://github.com/user-attachments/assets/8f1994c0-65f6-42c1-b1dc-471ea0d4d2ef" />

---

<img width="686" height="765" alt="HS18rl0" src="https://github.com/user-attachments/assets/f3b7a0a6-7a7c-4d26-b29f-e1ab95ab3671" />

>- Windows 11 Pro, Version 22H2, x64-based  
>- Docker Desktop for AMD64 with WSL2 backend  
>- Host OS interacts with containers for port mapping and file sharing   

---

## 🐳 Pulling and Running the Splunk Container

I pulled the Splunk image and ran it in a container. It felt amazing getting some movement & just seeing the container spin up was super satisfying. Containers are really lightweight compared to spinning up full VMs for each tool. 

<img width="788" height="285" alt="bTPwD9C" src="https://github.com/user-attachments/assets/26d6bf43-b9d4-463a-8254-3aaf0662212e" />

---

<img width="619" height="107" alt="NQlziii" src="https://github.com/user-attachments/assets/db399939-8f7d-464c-9612-a47da73cb9dd" />

>- Splunk Enterprise container image  
>- Container ports mapped to host (8000 for Web, 9997 for Forwarder)  
>- License acceptance handled through environment variables  

---

## 📂 Creating a Sample Log

<img width="599" height="127" alt="OIGb5bc" src="https://github.com/user-attachments/assets/c4dc088b-d7b8-4089-99ac-41a3051aa5c5" />

I created a sample log on my Windows endpoint to simulate real logs. This helped me practice ingestion and understand how endpoints feed data into Splunk.  

>- Windows endpoint Documents folder  
>- Sample log file with multiple test lines  
 

---

## 📊 Creating a Splunk Index

I created a new index in Splunk Web called `os_logs`. I kept extra options disabled so I could focus on learning ingestion and searches.  

<img width="970" height="268" alt="RRN2an0" src="https://github.com/user-attachments/assets/f2a81085-6ba6-458e-acbb-87d05581210a" />

---

<img width="945" height="174" alt="joFA4KD" src="https://github.com/user-attachments/assets/1a4fade0-ea0f-419f-a703-6b5f58a4e964" />

---

<img width="447" height="194" alt="o2XY6ey" src="https://github.com/user-attachments/assets/ca1540da-bfd9-4885-b07f-5cd0db3a5914" />



>- Index: os_logs  
>- Event-based data type  
>- Max size: 500 GB, Buckets: auto   

---

## ⬆️ Uploading Logs

Uploading the sample log made me feel like I was bridging my Windows endpoint with Splunk running in Docker. Seeing the logs appear in searches was really satisfying.  




>- File uploaded from Windows host  
>- Source type: syslog (or auto-detect)  
>- Index: os_logs  

---

## 🔍 Searching Logs

Running searches verified that everything worked. All test lines appeared, confirming the container-host integration and ingestion pipeline are solid.  

<img width="1228" height="492" alt="1IHbWVe" src="https://github.com/user-attachments/assets/300619a6-a956-4aee-b833-d5769096b7ee" />

>- Search bar queries: index=os_logs sourcetype=syslog  
>- Built confidence in the ingestion → search workflow  

---

## 🔄 Container Control

I stopped and restarted the container to simulate real-world operations. Splunk preserved the data, which is reassuring for SOC lab practice.  

<img width="504" height="59" alt="BuOITmM" src="https://github.com/user-attachments/assets/7900e342-7aec-4d58-9367-9f2d35bccc01" />

>- Docker stop/start commands for container lifecycle  

---

## ✍️ Observations

Running Splunk in Docker on Windows 11 Pro gave me hands-on insight into SOC labs without needing multiple VMs. I can ingest logs from endpoints, experiment with dashboards, and practice searches. Troubleshooting Docker permissions, leftover containers, and file paths was frustrating but super educational.  

>- Windows host + Docker container integration  
>- Endpoint log ingestion  
>- Splunk Web exploration and dashboards  
>- Hands-on SOC lab experience in a lightweight containerized setup

