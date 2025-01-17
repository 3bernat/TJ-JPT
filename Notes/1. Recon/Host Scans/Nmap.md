# Nmap

## Notes: 
Remember to run nmap with sudo privlieges or set some linux capabilities to give nmap the required privileges it needs. 

To set Linux Capabilities on Nmap:
```
sudo apt-get install libcap2-bin
sudo setcap cap_net_raw,cap_net_admin,cap_net_bind_service+eip $(which nmap)
getcap $(which nmap)
nmap --privileged
```

## Default Scans
- `nmap -sC -sV 172.21.0.0`
- `nmap -Pn -sC -sV -p- 172.21.0.0`
- `nmap -sV -Pn 172.21.0.0`
- `nmap -T4 -sC -sV 172.21.0.0`
- `nmap -vv -Pn -A -sC -sS -T 4 -p- 172.21.10.0/24 -oA fullscan`

## Stealth Scans: 
- `nmap -sS -sC -sV 172.21.0.0`
- `nmap -sS -p- 172.21.0.0`

## UDP Scan: 
- `nmap -sS -sU -Pn -sV 172.21.0.0`
- `nmap -sU -A --top-ports=20 --version-all`
- `nmap -sU -A -p 53,67,68,161,162 --version-all`

## Aggressive Scans: 
Once you have obtain results from your intial scan, run an aggressive scan in the background to obtain more information from the intial scan you executed: 

- `nmap -oA fullscan-aggressive.txt -T4 -vvv --max-rtt-timeout 300ms --max-retries 3 --host-timeout 30m --max-scan-delay 500ms -Pn -p- --version-intensity 1 -iL fullscan.txt`

If scans are not completing or skipping hosts too quickly, change the `--max-rtt-timeout` and `--max-scan-delay` settings. Additionally, for a slower, more complete, stealthier approach, the following can be used:
- `nmap -sT -Pn -p- --max-parallelism 1 --max-retries 0 --max-rtt-timeout 1000ms --max-hostgroup 1 -oX nmap_x.x.x.x-all_ports_slow.xml -iL x.x.x.x_Active_IPs.txt`


## Nmap Scripts: 

Location: /usr/share/nmap/scripts/

- `nmap --scripts vuln,safe,discovery -oN results.txt target-ip`

# Scans through Socks proxy: 

- `nmap --proxies socks4://proxy-ip:8080 target-ip`