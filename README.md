# Recon

# Who am i?
Hai Semuanya saya Syarif Muhammad Sajjad, Bug Bounty Hunter asal Indonesia. Dan ini adalah repositori tentang alur recon saya

# Subdomain Enumeration
```
https://crt.sh/?q=%25.target.com
https://securitytrails.com/list/apex_domain/target.com
https://www.shodan.io/search?query=Ssl.cert.subject.CN%3A%22target.com%22

-Single Domain:
amass enum -passive -norecursive -noalts –d domain .com -o  sub-list.txt

-Domains List:
amass enum -passive -norecursive -noalts -df domians.txt -o  subs-list.txt

After collecting everything remove the duplicate subs 
cat full-subdomain-list.txt | sort -u > sub-list.txt 
```

# Filter subdomain

```
Filter the subs with httpx 
cat sub-list.txt | httpx -o live-subs.txt
```

# Scan port
```
naabu -list sub-list.txt -top-ports 1000 -exclude-ports 80,443,21,22,25 -o ports.txt
naabu -list sub-list.txt -p -  -exclude-ports 80,443,21,22,25 -o ports.txt
```

# COLLECTING URLS ENDPOINTS

```
https://urlscan.io/search/#target.com
https://web.archive.org/cdx/search/cdx?url=*.target.com&fl=original&collapse=urlkey

Google dorking
site:target.com

Bing dorking
site:target.com
```

# SEARCH FOR SOURCES/BACKUP FILES
```
Tip:
-orwa.iwcon.com
-orwa.iwcon.com/orwa.zip - iwcon.zip – admin.zip – backup.zip
-orwa. iwcon.com/orwa/orwa.zip - wicon.zip – admin.zip – backup.zip
-orwa. iwcon.com/iwcon/orwa.zip - iwcon.zip – admin.zip – backup.zip
-orwa. iwcon.com/admin/orwa.zip - iwcon.zip – admin.zip – backup.zip

-https://github.com/musana/fuzzuli 
-for fuzzing on backups 
```

# Tips for PII

```
site:docs.google.com/spreadsheets "company name“
site:groups.google.com "company name"
```
