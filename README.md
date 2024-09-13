# Alpha-Emperor-Recon-Checklist
Checklist for performing the most comprehensive recon operations on your unfortunate target

This list is from my book "Enumerating Esoteric Attack Surfaces" by Jann Moon, released 2024

Note: Some steps may not apply to your target.
## Check Acquisitions
  - Company blogs, Websites and Social Media Pages
  - Financial Reports and SEC Filing Data
  - Newsletters and Private Reports
  - Misc Sources (Press releases, job postings, etc..)
  - Third Party Sites (intellizence.com, owler.com, crunchbase.com, mergerlinks.com, mergr.com, aleph.occrp.org)

## ASN 
  - bgp.he.net
  - discover if target actually owns an ASN and hosts their own domains
- `amass intel -org ORGANIZATION_NAME`
- `amass intel -asn ASN_NUMBER`
- nitefood's tool "asn", projectdiscovery's "asnmap" or harleo's "asnip"
- Shodan dork `asn:asXXXXXX`
- Censys dork `autonomous_system.asn:XXXXXX` or `autonomous_system.name:"ORGANIZATION"`
- zoomeye `asn:XXXXXX`
- Fofa: `asn="XXXX"`

## Reverse Whois
- whoxy.com/reverse-whois
- gwen001's "related-domains"

## CIDRs and IPs
- `asnmap -d domain.com`
- `nmap --script targets-asn --script-args targets-asn.asn=XXXXXX`
- `prips 10.10.10.0/24 | hakrevdns`
- `prips 10.10.10.0/24 | hakip2host`
- `prips 10.10.10.0/24 | hakoriginfinder -h URL`
- ImAyrix's "cut-cdn"

## Ports
- masscan
- nmap
- naabu
- rustscan

## Shodan
- `ssl.cert.subject.cn:"domain.com"`
- `ssl:"Organization Inc."`
- `http.html:"ua-XXXXX"` (Google Analytics Code)
- Favicon Hash tools (MurMurHash)
- `http.favicon.hash:XXXXXXXX`
- nrich

## Censys

## Nelas.io

## Fullhunt.io
- `http_favicon_hash:XXXXXXX`
- `domain:domain.com`

## Onyphe.io
## Viz.Greynoise.io
## Analyzeid.com
## Dnslytics.com

## Google Dorks
  - site:domain.com -site:www.domain.com
  - Google Groups, Docs
  - Dorks looking for config files, backup files, api documentation
  - Tools like go-dork or dorksearch.com

## Github Dorks
- Tools like gwen001's github-subdomains, github-endpoints, github-regex, michenriksen's gitrob or trufflesecurity's trufflehod
- Manual searching

# Subdomains
## Passive Discovery
  - Shodan, Censys, Third-Party Services
  - Query rapiddns.io, JLDC, riddler.io, Archive.org, DNSDumpster and more
  - Passive subdomain tools like projectdiscovery's"subfinder", OWASPs "amass", Findomain, hueristiq's "xsubfinder", ARPSyndicate's "puncia"
### Certificates
  - crt.sh
  - Censys Certificates Search (443.https.tls.certificate.parsed.subject.common_name:domain.com)
  - cero
  - CSP or Oxbharath's domains-from-csp tool
  - SPF or 0xbharath's assets-from-spf tool
  - ui.ctsearch.entrust.com/ui/ctsearchui
### ProjectDiscovery's "Uncover"

## Active Subdomain Hunting
  - Zone Transfers
  - Brute Force
  - Permutations
  - VHOSTs

## Content Discovery
  - Passive URL collection (archive.org, urlscan.io, commoncrawl.org, alienvault.org)
  - xnl-h4ck3r's "waymore", devanshbatham's "paramspider", hueristiq's "xurlfind3r" or lc's "gau"
  - Spidering website
  - projectdiscovery's "katana", jaeles-project's "gospider", Jason Haddix's Burp Suite Passive Collection while you browse target method
  - Extract endpoints from JS files
  - Pull from collected URLs and feed to 003Random's "GetJS"
  - Grep for interesting strings or use tomnomnom's "gf"
  - use 0xsha's "GoLinkFinder", kacakb's "jsfinder", leddcode's "Aranea", channyein1337's "jsleak" or BishopFox's "jsluice"
  - Pull source maps
  - Hunt for secrets
  - m4ll0k's "secretfinder", edoardott's "cariddid"

## Fingerprinting
  - projectdiscovery's "httpx -td", urbanadventurer's "whatweb", praetorian-inc's "fingerprintx", ShielderSec "webtech", projectdiscovery's "nuclei" w/ technology maps or rverton's "webanalyze"
  - use Wappalyzer, builtwith.com or retire.js
  
## Fuzzing endpoints with wordlists
  - General wordlists
  - Targeted wordlists based on fingerprinting data
  - Custom wordlists based on content
.

## Fuzzing Parameters
  - s0md3v's "arjun" and Sh1Yo's "x8"
    
## Fuzz Headers to Bypass 401s and 403s

## Cloud-Based Asset Enumeration

## Misc Tips
- Google Analytics Tags
- Copyright and Footer search in Google
- Extract endpoints from APK files
- EXIF data extraction from PDFs and Images
