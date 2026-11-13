# PENETRATION TESTING REPORT

## Footprinting & Network Scanning Phases
### W2-PM-FINAL | CYBERSECURITY | NETWORKWALKS

| Field | Detail |
| :--- | :--- |
| Pentester Name (Cybersecurity Professional) | Olasumbo Olanubi |
| Program/Batch | B084-Networkwalks |
| Date | 12 November 2026 |
| Modules completed | W2-PM1 (Multiple Kali Tools), W2-PM2 (GHDB), W2-PM4 (theHarvester), W2-PM5 (Zenmap) |
| Client/Target | 1. Networkwalks (secured written permission already) <br> 2. My own local LAN Network |
| Permission secured from client? | Yes |
| Phases covered | Phase 1: Reconnaissance & Footprinting <br> Phase 2: Scanning & Network Discovery <br> Phase 3: Scanning in Progress |

## 1. Liability Disclaimer
I have performed these activities only on the systems & devices where I had secured written permission from the client / owner of those devices/systems that I own myself. All these materials are for education and research purpose only. Do not use this knowledge to break the law.

## 2. Introduction
This report covers footprinting the networkwalks.com domain using multiple Kali Linux tools (W2-PM1), Google Hacking Database (W2-PM2), theHarvester (W2-PM4) and network scanning with Zenmap (W2-PM5) as part of my ongoing internship program at Networkwalks.

All commands were run in Kali Linux. Each section below includes the exact command used, the result I observed, a screenshot as evidence, and a short note on finding matters from an attacker's point of view.

## 3. Tools Used
| Tool | Purpose |
| :--- | :--- |
| Kali Linux & Windows | Operating systems used for reconnaissance activities |
| WHOIS | Find domain registration details (owner, dates, name servers) |
| WhatWeb | Fingerprint web technologies (server, CMS, plugins, IP) |
| Nslookup | Resolve the domain name to its IP address using DNS |
| Curl | Read the HTTP response headers of the website |
| Wafw00f | Detect whether a Web Application Firewall protects the site |
| DNSRecon | Enumerate all DNS records (NS, MX, SPF, TXT, SRV) |
| GHDB / Google Dorks | Find exposed cameras, login portals and open directories |
| theHarvester | Gather emails, hosts and IPs about a domain from public sources |
| Zenmap (Nmap GUI) | Scan the local subnet to find live hosts, IPs and MAC addresses |
| Ipconfig | Identify my local IP address and subnet |

## 4. Activities Performed

### 4.1 Footprinting & Reconnaissance
I performed reconnaissance against the networkwalks.com domain using six Kali Linux tools: WHOIS, WhatWeb, Nslookup, Curl, Wafw00f and DNSRecon. Each tool was used to collect a different type of information about the target.

First, I used WHOIS to obtain publicly available domain registration information and identify the domain servers. The results provided information about the domain registration and hosting infrastructure.

Then I used WhatWeb to identify technologies used by the website. The results identified WordPress 7.1.4, WP Download Manager 3.3.76, Apache server and IP 192.232.216.135.

Using Nslookup, I resolved the domain name to its IP address. The provided result identified 192.232.216.135.

I used Curl with the `-I` option to inspect the HTTP response headers. This provided additional information on the web application and exposed the WordPress REST API endpoint `/wp-json/`.

Next, I used Wafw00f to determine whether a Web Application Firewall was protecting the website. The results identified ModSecurity (SpiderLabs).

Finally, I used DNSRecon to enumerate DNS records. The results provided information relating to name servers, SPF records, verification records and DNS software information. No SRV record and No DNSSEC were found.

### 4.2 Google Hacking Database - GHDB
I used Google Dorks from GHDB such as `intitle:"Webcam"` and `intitle:"Index of /cam/"` to understand how attackers find exposed cameras, login portals and open directories using search engines. This shows why sensitive pages must not be indexed by Google.

### 4.3 theHarvester - microsoft.com
I ran theHarvester against microsoft.com. It collected 166 IPs, 3 Emails and 9489 Hosts from public sources.
Emails found: dotnet-docker-bot@microsoft.com, opencode@microsoft.com, secure@microsoft.com

### 4.4 Network Scanning with Zenmap
For the second activity, I used Zenmap to perform network discovery on my local network. The practical task was to identify my local IP address and subnet, discover live hosts, identify their IP and MAC addresses, and create a network topology.

I ran `ipconfig` on Windows to identify my local IP address and LAN subnet. I then entered `nmap -sn 192.168.43.0/24` into Zenmap and selected Ping Scan to identify active hosts.

The scan results provided in the practical identified 256 IPs scanned, 2 hosts up in 3.08 seconds:
- 192.168.43.1 (Gateway, MAC 96:93:2A:7D:65:94)
- 192.168.43.137 (DESKTOP-1D34DQ9)

After completing the scan, I opened the Topology section in Zenmap, enabled the legend and saved a screenshot in PDF format as required by the practical task. Quiz: 100%.

## 5. Risk Analysis / Impact
Based on the information collected during the footprinting and network scanning activities, I identified the following risks:

| # | Risk / Finding | Evidence / Observation | Potential Impact |
| :--- | :--- | :--- | :--- |
| 1 | Web technology information exposed | WhatWeb identified WordPress 7.1.4 and WP Download Manager 3.3.76 | Attackers may use exposed technology/version information to identify software requiring further security review |
| 2 | Server IP address identifiable | Nslookup resolved the domain to 192.232.216.135 | Provides information about the network location of the web service |
| 3 | HTTP technical information exposed | Curl returned HTTP response headers and exposed `/wp-json/` | May assist technology fingerprinting and further enumeration |
| 4 | WAF technology identifiable | Wafw00f identified ModSecurity (SpiderLabs) | Reveals information about the web application's security architecture |
| 5 | DNS infrastructure information | DNSRecon identified DNS records, No SRV, No DNSSEC | DNS information can help build a picture of the organisation's infrastructure |
| 6 | Multiple live hosts on local network | Zenmap identified 2 live hosts | Unknown or unauthorised devices may potentially be present on a network |

The risks above are observations from information gathering and host discovery. No exploitation or vulnerability validation was performed as part of these modules.

## 6. Recommendations
Based on the observations from these activities, I recommend the following security improvements:
1. Review publicly exposed technology information - Organisations should regularly review what information about their web technologies, CMS and plugins is publicly available.
2. Keep software updated - CMS platforms, plugins and other web technologies should be regularly updated and reviewed against security advisories.
3. Review HTTP headers - HTTP response headers should be reviewed to determine whether unnecessary technical information is exposed.
4. Review DNS records - DNS records should be periodically reviewed to ensure that only required information and services are exposed.
5. Investigate unknown devices - Unknown devices discovered on a network should be investigated to ensure they are authorised.
6. Maintain network documentation - Network topology should be documented and updated regularly.
7. Reduce security testing with authorisation - Reconnaissance and scanning must always be performed within an authorised scope and only on systems where permission has been granted.
8. Keep the WAF (ModSecurity) enabled and tuned, since it already blocks naive attacks.

## 7. Conclusion
During Week 2 of my Cybersecurity & Ethical Hacking internship, I completed footprinting, GHDB, theHarvester and network scanning activities. The exercises showed that information gathering and scanning must always be performed within an authorised scope.

Finally, I learned that reconnaissance and scanning must always be performed within an authorised scope and that these activities were completed as part of the assigned educational cybersecurity lab.

## 8. Evidences Collected
Screenshots collected as evidence are shown below in the same order as the activities:

![WHOIS](screenshots/01-whois.png)
![WhatWeb](screenshots/02-whatweb.png)
![Nslookup](screenshots/03-nslookup.png)
![Curl](screenshots/04-curl.png)
![Wafw00f](screenshots/05-wafw00f.png)
![DNSRecon](screenshots/06-dnsrecon.png)
![GHDB](screenshots/07-ghdb.png)
![theHarvester Baidu](screenshots/08-harvester-baidu.png)
![theHarvester All Sources](screenshots/09-harvester-all.png)
![Ipconfig](screenshots/10-ipconfig.png)
![Zenmap Output](screenshots/11-zenmap-output.png)
![Zenmap Topology](screenshots/12-zenmap-topology.png)
![Zenmap Quiz](screenshots/13-zenmap-quiz.png)

-End-
