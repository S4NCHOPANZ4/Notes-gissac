# Dirsearch

Dirsearch is a Python-based command-line tool used for directory and file brute-forcing. It is widely used for finding hidden files, directories, and other resources on web servers. 

### Basic Syntax  

The basic syntax of Dirsearch is: 

```bash
python3 dirsearch.py -u <target_url> -w <wordlist>
```

## Key Features and Functionalities 

### 1. Directory and File Discovery

Search for hidden directories or files 

```bash
python3 dirsearch.py -u http://example.com -w /path/to/wordlist.txt 
```
### 2. Multithreading 

Increase the speed of brute-forcing 

```bash
python3 dirsearch.py -u http://example.com -w /path/to/wordlist.txt -t 50 
```

### 3. Extensions 

Search for files with specific extensions 

```bash
python3 dirsearch.py -u http://example.com -w /path/to/wordlist.txt -e php,html,js
```

### 4. Recursive Fuzzing 

Automatically fuzz subdirectories discovered during the scan

```bash
python3 dirsearch.py -u http://example.com -w /path/to/wordlist.txt --recursive 
```

### 5. Status Code Filtering 

Show or exclude results based on HTTP status codes 

* Only show results ```200``` or ```301```

```bash
python3 dirsearch.py -u http://example.com -w /path/to/wordlist.txt --exclude-status 404 
```

* Exclude specific codes ```403``` or ```404```

```bash
python3 dirsearch.py -u http://example.com -w /path/to/wordlist.txt --exclude-status 403,404
```
### 6. Proxy Support 

Route traffic through a proxy for anonymity or bypass restrictions 

```bash
python3 dirsearch.py -u http://example.com -w /path/to/wordlist.txt --proxy http://127.0.0.1:8080
```

### 7. Custom User-Agent 

Set a custom User-Agent to mimic different clients

```bash
python3 dirsearch.py -u http://example.com -w /path/to/wordlist.txt -H "User-Agent: Mozilla/5.0"
```

### 8. Authentication 

Hanlde sites that requite HTTP Basic Authenctication

```bash
python3 dirsearch.py -u http://example.com -w /path/to/wordlist.txt --auth user:password
```

### 9. HTTPS Verification 

Bypass SSL/TLS certificate verifications 

```bash
python3 dirsearch.py -u http://example.com -w /path/to/wordlist.txt --no-check-certificate 
```

## Common Use Cases

### 1. Searhing for Admin Panels 

```bash
python3 dirsearch.py -u http://example.com -w /path/to/admin-panels.txt -e php,html 
```

### 2. Testing a large list of URLs 

```bash
python3 dirsearch.py -L targets.txt -w /path/to/wordlist.txt
```




