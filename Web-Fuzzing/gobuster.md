# Gobuster - fuzzing 

Gobuster is a powerful tool for brute-forcing various resources, including directories, subdomains, DNS entries, S3 buckets, and more. Written in Go, it is fast and efficient. Here's a detailed guide:

## Basic Command 

```bash
gobuster dir -u http://example.com -w  /path/to/wordlist.txt
```

### Key Parameters 

* ```-u``` Target URL
* ```-w``` Wordlist for brute-forcing
* ```-x``` Specific file extensions (e.g. ```php, txt, html```) 
* ```-o``` Save output to a file
* ```-t``` Number of threads (default is 10)

### Example

```bash
gobuster dir -u http://example.com -w /path/to/wordlist.txt -x php,htp -o output.txt -t 50
```

## Subdomain Fuzzing 

Find active subdomains via DNS resolution

```bash
gobuster dns -d example.com -w /path/to/wordlist.txt
```

### Key parameters

* ```-d``` Target domain
* ```-w``` Wordlist for subdomains
* ```-o``` Save results to a file
* ```-r``` Custom DNS server (useful to bypass blocks)

### Example 

```bash
gobuster dns -d example.com -w /usr/share/wordlist/dns/subdomain.txt -o output.txt
```

## S3 Bucket Fuzzing 

S3 bucket fuzzing refers to the process of systematically testing and discovering misconfigured or publicly accessible Amazon S3 buckets by trying different combinations of bucket names or URLs. This is often done to identify exposed data that may have been left unsecured, either inadvertently or due to poor security practices.

### Common command

```bash
gobuster s3 -w /path/to/wordlist.txt 
```

### Key parameters

* ```-w``` Wordlist bucket name
* ```-o``` Save output 
* ```-t``` Number of therads

## API Fuzzing (General Fuzzing)

Use the fuzz mode to test parameters, routes, or any part of an API.

### Common command

```bash
gobuster fuzz -u "http://example.com/{{FUZZ}}" -w /path/to/wordlist.txt
```

### Key parameters

* ```-u``` URL with the ```{{FUZZ}}``` marker
* ```-w``` Wordlist
* ```-o``` Save results to a file

## Advance Options

#### Exclude Specific HTTP Codes

Ignore responses withspecific status codes, like ```403``` or ```404```

```bash
--exclude-status 403,404
```

#### Set timeout 

Control the maximum wait for each connection 

```bash
--timeout 5s
```

#### Filter Specific Status Codes 

Only Show responses with specific HTTP status codes, such as ```200``` or ```301```

```bash
--status-codes 200,301
```

#### Custom Headers 

Useful for APIs or sites that require authentication tokens 

```bash
-H "Authorization: Bearer TOKEN"  
```

## Practical Use Cases

#### Finding Directories on a PHP Website

```bash
gobuster dir -u http://example.com -w /usr/share/wordlists/dirbuster/wordlist.txt -x php
```

#### Searching for Subdomains 

```bash
gobuster dns -d example.com -w /usr/share/seclists/Discovery/DNS/wordlist.txt
```

#### API Fuzzing

```bash
gobuster fuzz -u "http://api.example.com/{{FUZZ}}" -w /usr/share/wordlists/dirb/common.txt
```


## Tips 

1.  Use context-specific wordlists (e.g. DNS or directory wordlists)
2. Adjust thread counts for better speed, depending on your network and the target server
3. Save results to a file for easier analysis ~ bruh












