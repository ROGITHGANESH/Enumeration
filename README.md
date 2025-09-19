# Name:ROGITH GANESH.R
# Register no:212223100046

# Explore Google hacking and enumeration 

# AIM:

To use Google for gathering information and perform enumeration of targets

## STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various Google hacking keywords and enumeration tools as follows:


### Step 3:
Open terminal and try execute some kali linux commands

## Pen Test Tools Categories:  

| Operator    | Description                        | Example Usage           |
| ----------- | ---------------------------------- | ----------------------- |
| `site:`     | Search within a specific domain    | `site:example.com`      |
| `inurl:`    | Search in URL                      | `inurl:admin`           |
| `intitle:`  | Search in page title               | `intitle:"index of"`    |
| `filetype:` | Search by file type                | `filetype:pdf`          |
| `intext:`   | Search inside page text            | `intext:"confidential"` |
| `link:`     | Pages that link to a specific site | `link:example.com`      |
| `cache:`    | View cached version of a site      | `cache:example.com`     |
| `ext:`      | Same as filetype                   | `ext:xls`               |

 ## Architecture 
 ```
+----------------------+
|   Attacker / Hacker  |
|   (Browser & Google) |
+----------+-----------+
           |
           | Google Dork Queries
           v
+---------------------------+
|       Google Search       |
+---------------------------+
           |
           | Indexed Public Content
           v
+---------------------------+
|   Target Websites / Data  |
| - Leaked files            |
| - Open directories        |
| - Sensitive info          |
+---------------------------+

```

# Output:


# DNS Enumeration


## DNS Recon

| Record Type | Meaning                        | Example Output                   |
| ----------- | ------------------------------ | -------------------------------- |
| A           | Host to IPv4 address           | `example.com -> 93.184.216.34`   |
| AAAA        | Host to IPv6 address           | `example.com -> ::1`             |
| MX          | Mail server info               | `mail.example.com`               |
| NS          | Name servers                   | `ns1.example.com`                |
| TXT         | Misc data (SPF, verifications) | `v=spf1 include:_spf.google.com` |
| CNAME       | Canonical names (aliases)      | `www -> example.com`             |

## Common Tools Used (Kali Linux)

| Tool           | Description                                | Usage Example                           |
| -------------- | ------------------------------------------ | --------------------------------------- |
| `nslookup`     | DNS lookup tool (simple queries)           | `nslookup example.com`                  |
| `dig`          | DNS lookup utility (detailed)              | `dig example.com any`                   |
| `host`         | Simple DNS querying tool                   | `host example.com`                      |
| `dnsenum`      | Perl script to enumerate DNS info          | `dnsenum example.com`                   |
| `fierce`       | DNS scanner to locate non-contiguous IPs   | `fierce -dns example.com`               |
| `dnsrecon`     | Powerful DNS enumeration script            | `dnsrecon -d example.com -a`            |
| `theHarvester` | Subdomain enumeration using search engines | `theHarvester -d example.com -b google` |


## OUTPUT:

## Architecture Diagram 
```
+-------------------+        +------------------+       +------------------+
|                   |        |                  |       |                  |
|   Attacker (You)  +------->|   Target Server   +<----->+    DNS Server    |
| Kali Linux / Parrot|       | (Mail / DNS Host) |       |  (Authoritative) |
+---------+---------+        +---------+--------+       +---------+--------+
          |                            ^                          ^
          |                            |                          |
          |                            |                          |
          |           +-----------------------------+            |
          |           |      Information Tools      |            |
          |           |-----------------------------|            |
          |           | smtp-user-enum              |            |
          |           | nmap --script smtp-enum-*   |            |
          |           | dnsenum                     |<-----------+
          |           +-----------------------------+
          |
          v
+-----------------------------+
|   Output/Report             |
|  - Usernames Found          |
|  - MX Records / Zones       |
|  - Subdomains / IPs         |
+-----------------------------+

```

## dnsenum
**Purpose:** A multithreaded Perl script to enumerate information from DNS servers.

**Use case:** Performs DNS zone transfers, brute force subdomains, and gather host IPs.

```
dnsenum youtube.com
```


## Output:
<img width="1287" height="892" alt="image" src="https://github.com/user-attachments/assets/751e90f0-4942-4bb4-88bc-50049cefd661" />
<img width="1612" height="987" alt="image" src="https://github.com/user-attachments/assets/68967fd8-fc7f-4e4b-b36a-f937a00a0c98" />

## SITE:
<img width="1919" height="1026" alt="485464521-daa10ffb-f7ac-48d1-a687-f74b6e62a04f" src="https://github.com/user-attachments/assets/8a00cbaf-2b30-4214-8046-b0a1edad2136" />
## FILETYPE:
<img width="1919" height="869" alt="485465269-e455db6c-efe1-42b7-828a-325b7a6680e8" src="https://github.com/user-attachments/assets/7b8cb3ac-6772-4742-b4e4-5945932d5b65" />
## LINK:
<img width="1918" height="875" alt="485465923-27b906ee-1b12-4201-80c1-2c49c765f24e" src="https://github.com/user-attachments/assets/8149cb37-63ef-41c9-9af0-68cbabae4fdc" />
## CACHE:
<img width="1919" height="877" alt="485466071-2d925b92-eb81-47d2-88e0-fd537c42bfb0" src="https://github.com/user-attachments/assets/11ba2c6b-81a4-4f88-815f-0fed9fe772cf" />


# DNS:
```
dns recon -d youtube.com
```
# output:
<img width="1656" height="914" alt="image" src="https://github.com/user-attachments/assets/14c15ffe-eaf1-4b67-8d51-46f31963478c" />
<img width="1656" height="914" alt="image" src="https://github.com/user-attachments/assets/80e86a43-2921-49df-9d73-7ea72dc7927b" />

# Fierce:
```
fierce domain youtube.com
```
# Output:
<img width="1660" height="933" alt="Screenshot 2025-09-07 122422" src="https://github.com/user-attachments/assets/16634d8e-97b0-4ae8-b088-642d896d1ea0" />

## The harvester:

# output
<img width="854" height="411" alt="image" src="https://github.com/user-attachments/assets/6059ea80-b492-4d7a-87e5-0cc39e2af2c9" />


## smtp-user-enum
**Purpose:** Standalone tool used to enumerate valid users by using the VRFY, EXPN, or RCPT TO commands.

**Use case:** Brute-forces SMTP to find users.

```
smtp-user-enum -M VRFY -U users.txt -t <target-ip>
```
  
 ## Output
  <img width="854" height="411" alt="image" src="https://github.com/user-attachments/assets/6993266d-2133-41ae-8932-c6829a466861" />



## nmap –script smtp-enum-users.nse <hostname>

**Purpose:** Uses smtp-enum-users NSE script to enumerate valid users on an SMTP server.

**Use case:** Helps identify email accounts on mail servers.

```
nmap -p 25 --script smtp-enum-users.nse <target-ip>
```
## OUTPUT:
<img width="688" height="97" alt="image" src="https://github.com/user-attachments/assets/6b514723-a36c-4853-bf74-3d21abef581a" />



## RESULT:
The Google hacking keywords and enumeration tools were identified and executed successfully
