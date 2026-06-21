# Integrative-Project-Deliverables
Integrative Project: Deliverables by Andres Pesantez, Ariel Yumbillo and Israel Farfan
# Part 3 — Stand up and Attack the Black Hat Bash Lab
**Course:** Introduction to UNIX — SIN-B  
**Reference:** Chapter 3, Black Hat Bash

---

# Part 3.A — Lab Deployment and Verification

## Environment

### Operating System

```text
Debian GNU/Linux 13 (Trixie)
```

### Docker Version

```text
Docker version 26.1.5+dfsg1
```

### Docker Compose Version

```text
Docker Compose version 2.26.1-4
```

---

## Repository Cloning

The Black Hat Bash repository was cloned and the lab directory was accessed.

```bash
git clone https://github.com/dolevf/Black-Hat-Bash.git
cd Black-Hat-Bash/lab
```

---

## Lab Deployment

The laboratory environment was deployed using:

```bash
sudo make deploy
```

Deployment completed successfully.

### Evidence

```text
OK: all containers appear to be running.
OK: Lab is up and provisioned.
```

---

## Lab Verification

The deployment was validated using:

```bash
sudo make test
```

### Output

```text
Lab is up.
```

---

## Running Containers

Command:

```bash
sudo docker ps --format "{{.Names}}"
```

### Output

```text
p-web-02
c-backup-01
p-web-01
c-redis-01
p-ftp-01
c-db-02
p-jumpbox-01
c-db-01
```

A total of **8 containers** were running successfully.

---

## Network Validation

Command:

```bash
ip addr | grep "br_"
```

### Output

```text
br_corporate 10.1.0.1/24
br_public 172.16.10.1/24
```

The two required networks were successfully created.

| Network | Gateway |
|----------|----------|
| Public | 172.16.10.1/24 |
| Corporate | 10.1.0.1/24 |

---

## Container Access Verification

Command:

```bash
sudo docker exec -it p-web-01 bash
```

Hostname verification:

```bash
hostname
```

### Output

```text
p-web-01.acme-infinity-servers.com
```

Successful shell access confirms that the container is operational.

---

# Lab Architecture

| Machine | Hostname |
|----------|----------|
| p-web-01 | p-web-01.acme-infinity-servers.com |
| p-web-02 | p-web-02 |
| p-ftp-01 | p-ftp-01 |
| p-jumpbox-01 | p-jumpbox-01 |
| c-db-01 | c-db-01 |
| c-db-02 | c-db-02 |
| c-redis-01 | c-redis-01 |
| c-backup-01 | c-backup-01 |

---

# Network Diagram

```text
                PUBLIC NETWORK
                 172.16.10.0/24
                        |
                  br_public
                        |
      -----------------------------------
      |          |           |          |
   p-web-01   p-web-02   p-ftp-01   p-jumpbox-01


              CORPORATE NETWORK
                  10.1.0.0/24
                        |
                 br_corporate
                        |
      -----------------------------------
      |          |           |          |
    c-db-01   c-db-02   c-redis-01   c-backup-01
```

---

# Part 3.B — Port Scanning Technique Using Nmap

## Objective

Perform a basic reconnaissance scan against the target host:

```text
172.16.10.10
```

---

## Command Used

```bash
nmap -sV 172.16.10.10
```

---

## Results

```text
PORT     STATE SERVICE VERSION
8081/tcp open  http  Werkzeug httpd 3.0.1 (Python 3.12.3)
```

---

## What Does This Technique Do?

Nmap is a network reconnaissance tool used to identify open ports, active services, and software versions running on remote systems.

The `-sV` option enables service and version detection.

---

## Why Does It Work?

Network services listen on specific TCP or UDP ports. By connecting to those ports and analyzing responses, Nmap can determine whether a service is running and identify the software behind it.

---

## Information Obtained

The scan identified:

- One open TCP port.
- An HTTP service running on port 8081.
- Werkzeug HTTP Server version 3.0.1.
- Python version 3.12.3.

---

## Interpretation

The target machine hosts a web application accessible through TCP port 8081.

The server appears to be developed using Python and served through Werkzeug, a common WSGI web server used by Flask applications.

This information is valuable because it allows a security analyst to:

- Identify the web technology stack.
- Search for known vulnerabilities.
- Plan additional enumeration and testing activities.
- Understand the attack surface exposed by the target.

---

## Conclusion

The Black Hat Bash laboratory was successfully deployed using Docker on Debian 13. All eight containers were operational, both required networks were created correctly, and access to a target machine was verified. A reconnaissance scan using Nmap successfully identified an active web service and its underlying technologies, demonstrating the effectiveness of basic network enumeration techniques.


