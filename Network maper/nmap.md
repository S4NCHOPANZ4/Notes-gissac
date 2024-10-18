# NMAP

Namp standing for network maper is a powerful open-source scanning tool used for network discovery and securty. 

## Used for 

* Discover hosts and services
* Scan for open ports 
* Indentify operating systems 
* Perform vulnerability snanning 

## General scan

```bash
nmap -p- --open -sS --min-rate 5000 -vvv  -Pn {ip_target} -oG allPorts 
```

* ```-p-``` Scans **all 65,535 ports**.

* ```--open``` Shows only **open ports**, filtering out closed or filtered ones.

* ```-sS``` **TCP SYN scan**, a stealthy and fast port scan technique.

* ```--min-rate 5000```  Ensures the scan sends at least **5000 packets per second**, making it faster.

* ```--vvv``` **Very verbose output**, showing detailed scan progress.

* ```-Pn``` **No ping**, treats the target as online without ping checks (useful when ICMP is blocked).

* ```{ip_target}``` Replace with the **IP address** of the target.

* ```-og allPorts``` **Outputs the results in grepable format and saves them to a file named allPorts** for easier parsing.


## Nmap Scan Techniques


| nmap { switch } 192.168.1.1  | DESCRIPTION
|--------------|--------------|
|  -sS | TCP SYN port scan (Default)  | 
|  -sT  | TCP connect port scan (Default without root privilege) | 
|  -sU  | UDP port scan | 
|  -sA  | TCP ACK port scan | 
|  -sW  | TCP Window port scan | 
|  -sM  | TCP Maimon port scan | 


## Host Discovery


| Switch | Example                                  | Description                                   |
|--------|------------------------------------------|-----------------------------------------------|
| -sL    | nmap 192.168.1.1-3 -sL                   | No Scan. List targets only                    |
| -sn    | nmap 192.168.1.1/24 -sn                  | Disable port scanning. Host discovery only    |
| -Pn    | nmap 192.168.1.1-5 -Pn                   | Disable host discovery. Port scan only        |
| -PS    | nmap 192.168.1.1-5 -PS22-25,80           | TCP SYN discovery on port x. Port 80 by default|
| -PA    | nmap 192.168.1.1-5 -PA22-25,80           | TCP ACK discovery on port x. Port 80 by default|
| -PU    | nmap 192.168.1.1-5 -PU53                 | UDP discovery on port x. Port 40125 by default |
| -PR    | nmap 192.168.1.1-1/24 -PR                | ARP discovery on local network                |
| -n     | nmap 192.168.1.1 -n                      | Never do DNS resolution                       |

## Port Specification


| Switch      | Example                                      | Description                                                |
|-------------|----------------------------------------------|------------------------------------------------------------|
| -p          | nmap 192.168.1.1 -p 21                       | Port scan for port x                                        |
| -p          | nmap 192.168.1.1 -p 21-100                   | Port range                                                  |
| -p          | nmap 192.168.1.1 -p U:53,T:21-25,80          | Port scan multiple TCP and UDP ports                        |
| -p          | nmap 192.168.1.1 -p-                         | Port scan all ports                                         |
| -p          | nmap 192.168.1.1 -p http,https               | Port scan from service name                                 |
| -F          | nmap 192.168.1.1 -F                          | Fast port scan (100 ports)                                  |
| --top-ports | nmap 192.168.1.1 --top-ports 2000             | Port scan the top x ports                                   |
| -p-65535    | nmap 192.168.1.1 -p-65535                    | Leaving off initial port in range makes scan start at port 1 |
| -p0-        | nmap 192.168.1.1 -p0-                        | Leaving off end port in range makes scan go to port 65535    |
