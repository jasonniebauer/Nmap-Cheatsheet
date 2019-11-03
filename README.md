# Nmap Cheat Sheet
Quick reference guide for the scanning networks with Nmap.

**Table of Contents**
1. [What is Nmap?](#what-is-nmap)  
2. [How to Use Nmap](#how-to-use-nmap)  
    1. [Command Line](#command-line)
        1. [Basic Syntax](#basic-syntax)  
        1. [Get Help](#get-help)  
3. [Basic Scanning Techniques](#basic-scanning-techniques)  
    1. [Scan a Single Target](#scan-a-single-target)  
    2. [Scan Multiple Targets](#scan-multiple-targets)

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

#### Basic Syntax
```
nmap [ <Scan Type> ...] [ <Options> ] { <target specification> }
```

#### Get Help
```shell
nmap -h
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

## Host Discovery
The `-p` switch determines the type of ping to perform.

| Nmap Switch | Description                 |
|:------------|:----------------------------|
| **-PI**     | ICMP ping                   |
| **-Po**     | No ping                     |
| **-PS**     | SYN ping                    |
| **-PT**     | TCP ping                    |

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

## Firewall/IDS Evasion and Spoofing
| Nmap Switch | Description                 |
|:------------|:----------------------------|

## Output

| Nmap Switch    | Description   |
|:---------------|:--------------|
| **-oN**        | Normal output |
| **-oX**        | XML output    |
| **-oA** <BASENAME> | Normal, XML, and Grepable format all at once |

- [X] [Nmap - The Basics](https://www.youtube.com/watch?v=_JvtO-oe8k8)  
- [ ] [Reference link 1](https://hackertarget.com/nmap-cheatsheet-a-quick-reference-guide/)  
- [ ] [Beginner's Guide to Nmap](https://www.linux.com/learn/beginners-guide-nmap)  
- [ ] [Top 32 Nmap Command](https://www.cyberciti.biz/security/nmap-command-examples-tutorials/)  
- [ ] [Nmap Linux man page](https://linux.die.net/man/1/nmap)  
- [ ] [29 Practical Examples of Nmap Commands](https://www.tecmint.com/nmap-command-examples/)  
