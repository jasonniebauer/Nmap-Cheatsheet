# Nmap Cheat Sheet
Reference guide for scanning networks with Nmap.

**Table of Contents**
1. [What is Nmap?](#what-is-nmap)  
2. [How to Use Nmap](#how-to-use-nmap)  
    1. [Command Line](#command-line) 
3. [Basic Scanning Techniques](#basic-scanning-techniques)  
    1. [Scan a Single Target](#scan-a-single-target)  
    2. [Scan Multiple Targets](#scan-multiple-targets)  
    3. [Scan a List of Targets](#scan-a-list-of-targets)  
    4. [Scan a Range of Hosts](#scan-a-range-of-hosts)  
    5. [Scan an Entire Subnet](#scan-an-entire-subnet)  
    6. [Scan Random Hosts](#scan-random-hosts)  
    7. [Exclude Targets From a Scan](#exclude-targets-from-a-scan)  
    8. [Exclude Targets Using a List](#exclude-targets-using-a-list)  
    9. [Perform an Aggresive Scan](#perform-an-aggressive-scan)  
    10. [Scan an IPv6 Target](#scan-an-ipv6-target)  
4. [Port Scanning Options](#port-scanning-options)  
    1. [Perform a Fast Scan](#perform-a-fast-scan)  
    2. [Scan Specific Ports](#scan-specific-ports)  
    3. [Scan Ports by Name](#scan-ports-by-name)  
    4. [Scan Ports by Protocol](#scan-ports-by-protocol)  
    5. [Scan All Ports](#scan-all-ports)  
    6. [Scan Top Ports](#scan-top-ports)  
    7. [Perform a Sequential Port Scan](#perform-a-sequential-port-scan)  
    8. [Attempt to Guess an Unknown OS](#attempt-to-guess-an-unkown-os)  
    9. [Service Version Detection](#service-version-detection)  
    10. [Troubleshoot Version Scan](#troubleshoot-version-scan)  
    11. [Perform a RPC Scan](#perform-a-rpc-scan) 
5. [Discovery Options](#discovery-options)  
    1. [Perform a Ping Only Scan](#perform-a-ping-only-scan)  
    2. [Do Not Ping](#do-not-ping)  
    3. [TCP SYN Ping](#tcp-syn-ping)  
    3. [TCP ACK Ping](#tcp-ack-ping)  
    4. [UDP Ping](#udp-ping)  
    5. [SCTP INIT Ping](#sctp-init-ping)  
    6. [ICMP Echo Ping](#icmp-echo-ping)  
    7. [ICMP Timestamp Ping](#icmp-timestamp-ping)  
    8. [ICMP Address Mask Ping](#icmp-address-mask-ping)  
    9. [IP Protocol Ping](#ip-protocol-ping)  
    10. [ARP Ping](#arp-ping)  
    11. [Traceroute](#traceroute)  
    12. [Force Reverse DNS Resolution](#force-reverse-dns-resolution)  
    13. [Disable Reverse DNS Resolution](#disable-reverse-dns-resolution)  
    14. [Alternative DNS Lookup](#alternate-dns-lookup)  
    15. [Manually Specify DNS Server](#manually-specify-dns-server)  
    16. [Create a Host List](#create-a-host-list)  
6. [Firewall Evasion Techniques](#firewall-evasion-techniques)  
    1. [Fragment Packets](#fragment-packets)  
    2. [Specify a Specific MTU](#specify-a-specify-mtu)  
    3. [Use a Decoy](#use-a-decoy)  
    4. [Idle Zombie Scan](#idle-zombie-scan)  
    5. [Manually Specify a Source Port](#manually-specify-a-source-port)  
    6. [Append Random Data](#append-random-data)  
    7. [Randomize Target Scan Order](#randomize-target-scan-order)  
    8. [Spoof MAC Address](#spoof-mac-address)  
    9. [Send Bad Checksums](#send-bad-checksums)  
7. [Advanced Scanning Functions](#advanced-scanning-functions)  
    1. [TCP SYN Scan](#tcp-syn-scan)  
    2. [TCP Connect Scan](#tcp-connect-scan)  
    3. [UDP Scan](#udp-scan)  
    4. [TCP NULL Scan](#tcp-null-scan)  
    5. [TCP FIN Scan](#tcp-fin-scan)  
    6. [Xmas Scan](#xmas-scan)  
    7. [TCP ACK Scan](#tcp-ack-scan)  
    8. [Custom TCP Scan](#custom-tcp-scan)  
    9. [IP Protocol Scan](#ip-protocol-scan)  
    10. [Send Raw Ethernet Packets](#send-raw-ethernet-packets)  
    11. [Send IP Packets](#send-ip-packets)    
8. [Timing Options](#timing-options)  
    1. [Timing Templates](#timing-templates)  
    2. [Set the Packet TTL](#set-the-packet-ttl)  
    3. [Minimum Number of Parallel Operations](#minimum-number-of-parallel-operations)  
    4. [Maximum Number of Parallel Operations](#maximum-number-of-parallel-operations)  
    5. [Minimum Host Group Size](#minimum-host-group-size)  
    6. [Maximum Host Group Size](#maximum-host-group-size)  
    7. [Maximum RTT Timeout](#maximum-rtt-timeout)  
    8. [Initial RTT TImeout](#initial-rtt-timeout)  
    10. [Maximum Number of Retries](#maximum-number-of-retries)  
    11. [Host Timeout](#host-timeout)  
    12. [Minimum Scan Delay](#minimum-scan-delay)  
    13. [Maximum Scan Delay](#maximum-scan-delay)  
    14. [Minimum Packet Rate](#minimum-packet-rate)  
    15. [Maximum Packet Rate](#maximum-packet-rate)  
    16. [Defeat Reset Rate Limits](#defeat-reset-rate-limits)  
9. [Output Options](#output-options)  
    1. [Save Output to a Text File](#save-output-to-a-text-file)  
    2. [Save Output to a XML File](#save-output-to-a-xml-file)  
    3. [Grepable Output](#grepable-output)  
    4. [Output All Supported File Types](#output-all-supported-file-types)  
    5. [Periodically Display Statistics](#periodically-display-statistics)  
    6. [1337 Output](#1337-output)  
10. [Compare Scans](#compare-scans)  
    1. [Comparison Using Ndiff](#comparison-using-ndiff)  
    2. [Ndiff Verbose Mode](#ndiff-verbose-mode)  
    3. [XML Output Mode](#xml-output-mode)  
11. [Troubleshooting and Debugging](#troubleshooting-and-debugging)  
    1. [Get Help](#get-help)  
    2. [Display Nmap Version](#display-nmap-version)  
    3. [Verbose Output](#verbose-output)  
    4. [Debugging](#debugging)  
    5. [Display Port State Reason](#display-port-state-reason)  
    6. [Only Display Open Ports](#only-display-open-ports)  
    7. [Trace Packets](#trace-packets)  
    8. [Display Host Networking](#display-host-networking)  
    9. [Specify a Network Interface](#specify-a-network-interface)  
12. Nmap Scripting Engine  
    1. [Execute Individual Scripts](#execute-individual-scripts)  
    2. [Execute Multiple Scripts](#execute-multiple-scripts)  
    3. [Execute Scripts by Category](#execute-scripts-by-category)  
    4. [Execute Multiple Script Categories](#execute-multiple-script-categories)  
    5. [Troubleshoot Scripts](#troubleshoot-scripts)  
    6. [Update the Script Database](#update-the-script-database)  

## What is Nmap?
Nmap ("Network Mapper") is a free and open source utility for network discovery and security auditing. Many systems and network administrators also find it useful for tasks such as network inventory, managing service upgrade schedules, and monitoring host or service uptime. Nmap uses raw IP packets in novel ways to determine what hosts are available on the network, what services (application name and version) those hosts are offering, what operating systems (and OS versions) they are running. It was designed to rapidly scan large networks, but works fine against single hosts.

## How to Use Nmap
Nmap can be used in a variety of ways depending on the user's level of technical expertise.

| Technical Expertise | Usage |
|:--------------------|:------|
| Beginner            | [Zenmap](https://nmap.org/zenmap/) the graphical user interface for Nmap |
| Intermediate        | [Command line](https://nmap.org/) |
| Advanced            | Python scripting with the [Python-Nmap](https://pypi.org/project/python-nmap/) package |

### Command Line
```shell
nmap [ <Scan Type> ...] [ <Options> ] { <target specification> }
```

## Basic Scanning Techniques
The `-s` switch determines the type of scan to perform.

| Nmap Switch | Description                 |
|:------------|:----------------------------|
| **-sA**     | ACK scan                    |
| **-sF**     | FIN scan                    |
| **-sI**     | IDLE scan                   |
| **-sL**     | DNS scan (a.k.a. list scan) |
| **-sN**     | NULL scan                   |
| **-sO**     | Protocol scan               |
| **-sP**     | Ping scan                   |
| **-sR**     | RPC scan                    |
| **-sS**     | SYN scan                    |
| **-sT**     | TCP connect scan            |
| **-sW**     | Windows scan                |
| **-sX**     | XMAS scan                   |

### Scan a Single Target
```shell
nmap [target]
```

### Scan Multiple Targets
```shell
nmap [target1, target2, etc]
```

### Scan a List of Targets
```shell
nmap -iL [list.txt]
```

### Scan a Range of Hosts
```shell
nmap [range of IP addresses]
```

### Scan an Entire Subnet
```shell
nmap [ip address/cdir]
```

### Scan Random Hosts
```shell
nmap -iR [number]
```

### Exclude Targets From a Scan
```shell
nmap [targets] --exclude [targets]
```

### Exclude Targets Using a List
```shell
nmap [targets] --excludefile [list.txt]
```

### Perform an Aggresive Scan
```shell
nmap -A [target]
```

### Scan an IPv6 Target
```shell
nmap -6 [target]
```

## Port Scanning Options

### Perform a Fast Scan
```shell
nmap -F [target]
```

### Scan Specific Ports
```shell
nmap -p [port(s)] [target]
```

### Scan Ports by Name
```shell
nmap -p [port name(s)] [target]
```

### Scan Ports by Protocol
```shell
nmap -sU -sT -p U:[ports],T:[ports] [target]
```

### Scan All Ports
```shell
nmap -p 1-65535 [target]
```

### Scan Top Ports
```shell
nmap --top-ports [number] [target]
```

### Perform a Sequential Port Scan
```shell
nmap -r [target]
```

### Attempt to Guess an Unknown OS
```shell
nmap -O --osscan-guess [target]
```

### Service Version Detection
```shell
nmap -sV [target]
```

### Troubleshoot Version Scan
```shell
nmap -sV --version-trace [target]
```

### Perform a RPC Scan
```shell
nmap -sR [target]
```

## Discovery Options
**Host Discovery**
The `-p` switch determines the type of ping to perform.

| Nmap Switch | Description                 |
|:------------|:----------------------------|
| **-PI**     | ICMP ping                   |
| **-Po**     | No ping                     |
| **-PS**     | SYN ping                    |
| **-PT**     | TCP ping                    |

### Perform a Ping Only Scan
```shell
nmap -sn [target]
```

### Do Not Ping
```shell
nmap -Pn [target]
```

### TCP SYN Ping
```shell
nmap -PS [target]
```

### TCP ACK Ping
```shell
nmap -PA [target]
```

### UDP Ping
```shell
nmap -PU [target]
```

### SCTP INIT Ping
```shell
nmap -PY [target]
```

### ICMP Echo Ping
```shell
nmap -PE [target]
```
### ICMP Timestamp Ping
```shell
nmap -PP [target]
```

### ICMP Address Mask Ping
```shell
nmap -PM [target]
```

### IP Protocol Ping
```shell
nmap -PO [target]
```

### ARP ping
```shell
nmap -PR [target]
```

### Traceroute
```shell
nmap --traceroute [target]
```

### Force Reverse DNS Resolution
```shell
nmap -R [target]
```

### Disable Reverse DNS Resolution
```shell
nmap -n [target]
```

### Alternative DNS Lookup
```shell
nmap --system-dns [target]
```

### Manually Specify DNS Server
Can specify a single server or multiple.
```shell
nmap --dns-servers [servers] [target]
```

### Create a Host List
```shell
nmap -sL [targets]
```

## Port Specification and Scan Order

| Nmap Switch | Description                 |
|:------------|:----------------------------|

## Service/Version Detection

| Nmap Switch | Description                  |
|:------------|:-----------------------------|
| **-sV**     | Enumerates software versions |

## Script Scan

| Nmap Switch | Description             |
|:------------|:------------------------|
| **-sC**     | Run all default scripts |

## OS Detection

| Nmap Switch | Description                 |
|:------------|:----------------------------|

## Timing and Performance
The `-t` switch determines the speed and stealth performed.

| Nmap Switch | Description                 |
|:------------|:----------------------------|
| **-T0**     | Serial, slowest scan        |
| **-T1**     | Serial, slow scan           |
| **-T2**     | Serial, normal speed scan   |
| **-T3**     | Parallel, normal speed scan |
| **-T4**     | Parallel, fast scan         |

Not specifying a `T` value will default to `-T3`, or normal speed.

## Firewall Evasion Techniques

### Firewall/IDS Evasion and Spoofing
| Nmap Switch | Description                 |
|:------------|:----------------------------|

### Fragment Packets
```shell
nmap -f [target]
```

### Specify a Specific MTU
```shell
nmap --mtu [MTU] [target]
```

### Use a Decoy
```shell
nmap -D RND:[number] [target]
```

### Idle Zombie Scan
```shell
nmap -sI [zombie] [target]
```

### Manually Specify a Source Port
```shell
nmap --source-port [port] [target]
```

### Append Random Data
```shell
nmap --data-length [size] [target]
```

### Randomize Target Scan Order
```shell
nmap --randomize-hosts [target]
```

### Spoof MAC Address
```shell
nmap --spoof-mac [MAC|0|vendor] [target]
```

### Send Bad Checksums
```shell
nmap --badsum [target]
```
  
## Advanced Scanning Functions

### TCP SYN Scan
```shell
nmap -sS [target]
```

### TCP Connect Scan
```
nmap -sT [target]
```

### UDP Scan
```shell
nmap -sU [target]
```

### TCP NULL Scan
```shell
nmap -sN [target]
```

### TCP FIN Scan
```shell
nmap -sF [target]
```

### Xmas Scan
```shell
nmap -sA [target]
```

### TCP ACK Scan
```shell
nmap -sA [target]
```

### Custom TCP Scan
```shell
nmap --scanflags [flags] [target]
```

### IP Protocol Scan
```shell
nmap -sO [target]
```

### Send Raw Ethernet Packets
```shell
nmap --send-eth [target]
```

### Send IP Packets
```shell
nmap --send-ip [target]
```

## Timing Options

### Timing Templates
```shell
nmap -T[0-5] [target]
```

### Set the Packet TTL
```shell
nmap --ttl [time] [target]
```

### Minimum NUmber of Parallel Operations
```shell
nmap --min-parallelism [number] [target]
```

### Maximum Number of Parallel Operations
```shell
nmap --max-parallelism [number] [target]
```

### Minimum Host Group Size
```shell
nmap --min-hostgroup [number] [targets]
```

### Maximum Host Group Size
```shell
nmap --max-hostgroup [number] [targets]
```

### Maximum RTT Timeout
```shell
nmap --initial-rtt-timeout [time] [target]
```

### Initial RTT Timeout
```shell
nmap --max-rtt-timeout [TTL] [target]
```

### Maximum Number of Retries
```shell
nmap --max-retries [number] [target]
```

### Host Timeout
```shell
nmap --host-timeout [time] [target]
```

### Minimum Scan Delay
```shell
nmap --scan-delay [time] [target]
```

### Maxmimum Scan Delay
```shell
nmap --max-scan-delay [time] [target]
```

### Minimum Packet Rate
```shell
nmap --min-rate [number] [target]
```

### Maximum Packet Rate
```shell
nmap --max-rate [number] [target]
```

### Defeat Reset Rate Limits
```shell
nmap --defeat-rst-ratelimit [target]
```

## Output Options

| Nmap Switch | Description   |
|:------------|:--------------|
| ``-oN``     | Normal output |
| ``-oX``     | XML output    |
| ``-oA``     | Normal, XML, and Grepable format all at once |

### Save Output to a Text File
```shell
nmap -oN [scan.txt] [target]
```

### Save Output to a XML File
```shell
nmap -oX [scan.xml] [target]
```

### Grepable Output
```shell
nmap -oG [scan.txt] [target]
```

### Output All Supported File Types
```shell
nmap -oA [path/filename] [target]
```

### Periodically Display Statistics
```shell
nmap --stats-every [time] [target]
```

### 1337 Output
```shell
nmap -oS [scan.txt] [target]
```

## Compare Scans

### Comparison Using Ndiff
```shell
ndiff [scan1.xml] [scan2.xml]
```

### Ndiff Verbose Mode
```shell
ndiff -v [scan1.xml] [scan2.xml]
```

### XML Output Mode
```shell
ndiff --xml [scan1.xml] [scan2.xml]
```

## Troubleshooting and Debugging

### Get Help
```shell
nmap -h
```

### Display Nmap Version
```shell
nmap -V
```

### Verbose Output
```shell
nmap -v [target]
```

### Debugging
```shell
nmap -d [target]
```

### Display Port State Reason
```shell
nmap --reason [target]
```

### Only Display Open Ports
```shell
nmap --open [target]
```

### Trace Packets
```shell
nmap --packet-trace [target]
```

### Display Host Networking
```shell
nmap --iflist
```

### Specify a Network Interface
```shell
nmap -e [interface] [target]
```

## Nmap Scripting Engine

### Execute Individual Scripts
```shell
nmap --script [script.nse] [target]
```

### Execute Multiple Scripts
```shell
nmap --script [expression] [target]
```

### Execute Scripts by Category
```shell
nmap --script [category] [target]
```

### Execute Multiple Script Categories
```shell
nmap --script [category1,category2,etc]
```

### Troubleshoot Scripts
```shell
nmap --script [script] --script-trace [target]
```

### Update the Script Database
```shell
nmap --script-updatedb
```


**Reference Sites**
- [X] [Nmap - The Basics](https://www.youtube.com/watch?v=_JvtO-oe8k8)  
- [ ] [Reference link 1](https://hackertarget.com/nmap-cheatsheet-a-quick-reference-guide/)  
- [ ] [Beginner's Guide to Nmap](https://www.linux.com/learn/beginners-guide-nmap)  
- [ ] [Top 32 Nmap Command](https://www.cyberciti.biz/security/nmap-command-examples-tutorials/)  
- [ ] [Nmap Linux man page](https://linux.die.net/man/1/nmap)  
- [ ] [29 Practical Examples of Nmap Commands](https://www.tecmint.com/nmap-command-examples/)  
- [ ] [Nmap Scanning Types, Scanning Commands , NSE Scripts](https://medium.com/@infosecsanyam/nmap-cheat-sheet-nmap-scanning-types-scanning-commands-nse-scripts-868a7bd7f692)  
- [ ] [Nmap CheatSheet](https://www.cheatography.com/netwrkspider/cheat-sheets/nmap-cheatsheet/)  
- [ ] [Nmap Cheat Sheet](https://highon.coffee/blog/nmap-cheat-sheet/)  
- [ ] [Nmap Cheat Sheet: From Discovery to Exploits](https://resources.infosecinstitute.com/nmap-cheat-sheet/)  
- [ ] [Nmap: my own cheatsheet](https://www.andreafortuna.org/2018/03/12/nmap-my-own-cheatsheet/)  
- [ ] [NMAP Commands Cheatsheet](https://hackersonlineclub.com/nmap-commands-cheatsheet/)  
- [ ] [Nmap Cheat Sheet](https://www.stationx.net/nmap-cheat-sheet/)  
- [ ] [Nmap Cheat Sheet](http://nmapcookbook.blogspot.com/2010/02/nmap-cheat-sheet.html)  
