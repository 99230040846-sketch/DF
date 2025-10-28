# Experiment-3: Password Capturing Using Wireshark

**Course / Lab:** Digital Forensics Lab  
**Experiment No.:** 3  
**Title:** Password Capturing Using Wireshark  

---

## Aim
To capture and analyze network packets using Wireshark.

---

## Requirements
- Wireshark  
- Windows  
- Active internet connection or local network traffic  

---

## Description
Wireshark is a popular open-source network protocol analyzer.  
It allows forensic investigators and security analysts to:  
- Capture live network traffic  
- Inspect packet contents (headers & payloads)  
- Filter and search packets (e.g., HTTP, DNS, TCP, ICMP, ARP)  
- Detect suspicious or malicious activity  
- Reconstruct sessions (e.g., HTTP requests, TCP streams)  

---

## Procedure — Steps to Capture and Analyze Passwords

**Step-1:** Open Wireshark. You will see different network interfaces. Select the network that is connected (e.g., Wi-Fi).  

![](exp3/Screenshot%202025-09-01%20234225.png)

**Step-2:** On the top left corner, click the blue shark fin button. Wireshark begins capturing live traffic and packets appear in real-time.  

![](exp3/Screenshot%202025-09-01%20234307.png)

**Step-3:** After starting packet capture, go to a website and log in with credentials.  

![](exp3/Screenshot%202025-09-01%20235058.png)

**Step-4:** Return to Wireshark and apply filters like **HTTP** to find HTTP packets on the network.  

![](exp3/Screenshot%202025-09-01%20234701.png)

**Step-5:** Some HTTP packets will be captured. We specifically look for **form data** that the user submitted to the website.  
- We have two main methods used for submitting form data from web pages like login forms to the server: **GET** & **POST**  

![](exp3/Screenshot%202025-09-01%20234727.png)

**Step-6:** To check credentials in requests sent via the **GET method**, apply this filter:  
- http.request.method == "GET"  

![](exp3/Screenshot%202025-09-01%20234807.png)

**Step-7:** If credentials are not found with GET, apply the **POST method filter**:  
- http.request.method == "POST"  

As you analyze the HTML form in POST requests, you can view user credentials (e.g., username and password).  
Example:  
- Form item: "uname" = "naganand"  
- Form item: "pass" = "12345"
