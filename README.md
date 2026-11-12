# W2-PM-FINAL - Report v2

**Pentester:** Olasumbo Olanubi
**Program/Batch:** B084-Networkwalks
**Date:** 12 November 2026
**Modules:** W2-PM1, W2-PM2, W2-PM4, W2-PM5

## Targets
1. Networkwalks (written permission secured)
2. My own local LAN Network - 192.168.43.0/24

## Results

### PM1 - networkwalks.com
- WHOIS: GoDaddy, Created 2019-11-06, Expiry 2027-11-06
- WhatWeb: WordPress 7.1.4, WP Download Manager 3.3.76, Apache, 192.232.216.135
- Nslookup: 192.232.216.135
- Curl: HTTP/2 200, Server Apache, /wp-json/ exposed
- Wafw00f: ModSecurity (SpiderLabs)
- DNSRecon: No SRV, No DNSSEC, MX mail.networkwalks.com, TXT SPF + Google verification

### PM2 - GHDB
Dorks like `intitle:"Webcam"` and `intitle:"Index of /cam/"` exposing cameras, login portals, open directories.

### PM4 - theHarvester microsoft.com
- 166 IPs, 3 Emails, 9489 Hosts
- Emails: dotnet-docker-bot@microsoft.com, opencode@microsoft.com, secure@microsoft.com

### PM5 - Zenmap
- `nmap -sn 192.168.43.0/24`
- 256 IPs scanned, 2 hosts up in 3.08 seconds
- 192.168.43.1 (Gateway) + 192.168.43.137 (DESKTOP-1D34DQ9)
- Quiz: 100%

> Note on PM3 Maltego: Not completed - Nigeria is not listed for Maltego Community Edition verification.

## Files
- `W2-PM-FINAL-Report-v2.pdf` - Full Report
- `/screenshots/` - Evidences

## Author
Olasumbo Olanubi - https://www.linkedin.com/in/olasumbo-olanubi-52921348
