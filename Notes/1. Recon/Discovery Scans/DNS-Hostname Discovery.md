# DNS/Hostname Discovery

DNSRecon: 

- `dnsrecon -d www.example.com -a`
- `dnsrecon -d www.example.com -t axfr`
- `dnsrecon -d <startIP-endIP>`
- `dnsrecon -d www.example.com -D <namelist> -t brt`

Dig: 

- `dig www.example.com + short`
- `dig www.example.com MX`
- `dig www.example.com NS`
- `dig www.example.com> SOA`
- `dig www.example.com ANY +noall +answer`
- `dig -x www.example.com`
- `dig -4 www.example.com` (For IPv4)
- `dig -6 www.example.com` (For IPv6)
- `dig www.example.com mx +noall +answer example.com ns +noall +answer`
- `dig -t AXFR www.example.com`

Dnsenum Enumeration:

- `dnsenum --dnsserver 172.21.0.0 -enum intranet.megacorpone.xx`
- `dnsenum --dnsserver 172.21.0.0 -enum management.megacorpone.xx`
- `dnsenum --dnsserver 172.21.0.0 -enum www.megacorpone.xx`

dnsX Enumeration: 
- `dnsx -l domains.txt -resp -a -aaaa -cname -mx -ns -soa -txt`
- `dnsx -silent -d megacorpone.com -w /usr/share/seclists/Discovery/DNS/dns-Jhaddix.txt`

Using with subfinder: 
- `subfinder -silent -d megacorpone.com | dnsx -silent`
- `subfinder -silent -d megacorpone.com | dnsx -silent -a -resp`
- `subfinder -silent -d megacorpone.com | dnsx -silent -a -resp-only`
- `subfinder -silent -d megacorpone.com | dnsx -silent -cname -resp`
- `subfinder -silent -d megacorpone.com | dnsx -silent -asn`


Nmap Enumeration: 
```
$ ls -lh /usr/share/nmap/scripts/ | grep dns
-rw-r--r-- 1 root root  1499 Oct 12 09:29 broadcast-dns-service-discovery.nse
-rw-r--r-- 1 root root  5329 Oct 12 09:29 dns-blacklist.nse
-rw-r--r-- 1 root root 10100 Oct 12 09:29 dns-brute.nse
-rw-r--r-- 1 root root  6639 Oct 12 09:29 dns-cache-snoop.nse
-rw-r--r-- 1 root root 15152 Oct 12 09:29 dns-check-zone.nse
-rw-r--r-- 1 root root 14826 Oct 12 09:29 dns-client-subnet-scan.nse
-rw-r--r-- 1 root root 10168 Oct 12 09:29 dns-fuzz.nse
-rw-r--r-- 1 root root  3803 Oct 12 09:29 dns-ip6-arpa-scan.nse
-rw-r--r-- 1 root root 12702 Oct 12 09:29 dns-nsec3-enum.nse
-rw-r--r-- 1 root root 10580 Oct 12 09:29 dns-nsec-enum.nse
-rw-r--r-- 1 root root  3441 Oct 12 09:29 dns-nsid.nse
-rw-r--r-- 1 root root  4364 Oct 12 09:29 dns-random-srcport.nse
-rw-r--r-- 1 root root  4363 Oct 12 09:29 dns-random-txid.nse
-rw-r--r-- 1 root root  1456 Oct 12 09:29 dns-recursion.nse
-rw-r--r-- 1 root root  2195 Oct 12 09:29 dns-service-discovery.nse
-rw-r--r-- 1 root root  5679 Oct 12 09:29 dns-srv-enum.nse
-rw-r--r-- 1 root root  5765 Oct 12 09:29 dns-update.nse
-rw-r--r-- 1 root root  2123 Oct 12 09:29 dns-zeustracker.nse
-rw-r--r-- 1 root root 26574 Oct 12 09:29 dns-zone-transfer.nse
-rw-r--r-- 1 root root  3910 Oct 12 09:29 fcrdns.nse
```

- `nmap x.x.x.x -v -p 53 --script=exampleScript1.nse,exampleScript2.nse`