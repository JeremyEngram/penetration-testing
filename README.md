# Basics of offensive penetration testing

**NOTE:** Some exercises in this repository include answers to [HackTheBox penetration challenges](hackthebox.eu). To respect [accepted rules & terms of the HackTheBox website](https://www.hackthebox.eu/tos), spoiler information of hacking servers in their test network environment is not published in this repository. This policy will change *only if* the following conditions are met: 1) the particular computers are retired or offline. In any other circumstances, information of hacking HackTheBox-related computer servers is not published in this repository. Thank you.

The information in this repository will be re-evaluated later.

-------------------

- Aim of this repository is to present and simulate multiple attack types against web applications and various OSes, including Microsoft Windows

- This repository 

  - utilizes [OWASP top 10 list of the most common attack types](https://www.owasp.org/images/7/72/OWASP_Top_10-2017_%28en%29.pdf.pdf)

  - utilizes multiple penetration methods with various tools, including [Kali Linux](https://www.kali.org) and [Metasploit Framework](https://www.metasploit.com)

- The repository is mainly set up as a requirement by a school cource in Haaga-Helia University of Applied Sciences, Helsinki, Finland.

- The repository contains various exercises, currently presented in Finnish but will be translated into English later.

## Table of Contents

- [Exercise 1 (Harjoitus 1)](exercises/h1.md)

- [Exercise 2 (Harjoitus 2)](exercises/h2.md)

- [Exercise 3 (Harjoitus 3)](exercises/h3.md)

- [Exercise 4 (Harjoitus 4)](exercises/h4.md)

## Other contents

### [BlackArch Linux - Personal configurations](blackarch/)

  - [OWASP WebGoat](blackarch/webgoat) - Install [OWASP WebGoat](https://www.owasp.org/index.php/Category:OWASP_WebGoat_Project) as a systemd user service
  
  - [OWASP Zed Attack Proxy](blackarch/zaproxy-systemd) - Install [OWASP ZAP](https://www.owasp.org/index.php/OWASP_Zed_Attack_Proxy_Project) as a systemd user service
  
  - [MATE Desktop/myGtkMenu](blackarch/mate-desktop) - Convert BlackArch Openbox penetration tool menu entries into [myGtkMenu](https://sites.google.com/site/jvinla/mygtkmenu) compliant format, use these entries with myGtkMenu
  
### Iptables ruleset for a simple server

Iptables firewall ruleset featuring the following:

> 1) Do not respond to ping echoes by clients (possibly reduce spambots)

> 2) Reject connection if too intense attempts. Useful against port scanners such as [Nmap](https://nmap.org/) and other brute force scanners such as [Dirbuster](https://www.owasp.org/index.php/Category:OWASP_DirBuster_Project).

> 3) Drop all incoming connections, apply only SSH, HTTP and HTTPS

- [[File] iptables.rules / Fincer - Linux server setup](https://github.com/Fincer/linux-server-setup/blob/master/other/iptables.rules)

### Fake Apache server HTTP response codes

- [[Patch] Apache - Manipulate standard HTTP header response codes](https://github.com/Fincer/linux-server-setup/blob/master/patches/patch_apache_break_http_code_standard.patch)

  - Manipulate HTTP header response codes returned to a client by Apache HTTP server.
  
> 1) Server HTTP response codes in range 402-451 are returned as error code 400 response instead.
  
> 2) Server HTTP response codes in range 500-511 are returned as error code 400 response instead.
  
> 3) Server HTTP response codes in range 100-308 are returned normally, including 200 OK message.

- [[Patch] Apache - Remove default HTML error message from all error pages](https://github.com/Fincer/linux-server-setup/blob/master/patches/patch_apache_disable_html_errormsg.patch)

  - Remove default error pages returned by an erroneous HTTP client request.
  
  - Remove additional HTML error messages as well (such as ones generated by servers behind an Apache proxy, if [ProxyErrorOverride On](https://httpd.apache.org/docs/2.4/mod/mod_proxy.html#proxyerroroverride) directive is used)
  
**NOTE:** These are experimental patches for Apache HTTP web server, use with caution. Feel free to modify them! The server configuration can easily break because we break very deep standards here, just be aware and proceed with care! Thanks!

**NOTE:** This patchset is useful in some cases but it can bury underneath problems in server
configuration. Thus, use discretion before implementing the patches in your Apache server.

**NOTE:** Apache *will complain* about missing error codes after you have applied this patchset and if you have custom error redirections in your `.htaccess` or in other settings. This is why you need to adjust your custom `ErrorDocument` and equivalent settings (RewriteRules, for instance) in your VirtualHost/Page configuration file (`/etc/{apache2,httpd}/sites-available/*.conf`).

## Disclaimer

Author of this repository is not responsible for any possible illegal or malicious usage of any files or instructions provided by this repository. The repository is provided as an act of good will and does not intend to encourage users to participate in any illegal activities. All exercises presented in this repository have been carried out in a pre-configured test environment, minimizing any possible attack vectors or unintended harm to outside parties.
