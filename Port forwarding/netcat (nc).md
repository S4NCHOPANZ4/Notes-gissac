# NETCAT (nc) - Port Forwarding

Netcat (nc) is a simple yet powerful tool for networking tasks such as port scanning, creating connections, and implementing port forwarding. It's widely used in system administration and penetration testing because of its flexibility.

## Types of Port Forwarding 

Redirects traffic from a local port to another service locally or remotely 

### Local Port Forwarding 

Forward local port 8080 to port 80 on a remote server 

```bash
nc -lvp 8080 -c "nc remote-server 80"
```

* ```-l``` Listens for incoming connections 
* ```-v``` Enables verbose mode for detailed output
* ```-p``` Specifies the local port 
* ```-c``` Runs a command when a connections is recived (in this case, forwards traffic to the remote server)

### Remote Port Forwarding 

Redirects traffic fromn a remote machine to another destination 

#### Scenario

#### * Machine A (public): Runs a service on port 80 
#### * Machine B (private): Uses ```nc ``` to connect Machine A and Machine B

#### On Machine A

```bash
nc -lvp 8080 
```
#### On Machine B

```bash
mc public-server 8080 -c "nc internal-server 80"
```

This redirects connections recoved on Machines A's port 8080 to port 80 of an internal server.

### Reverse Port Forwarding 

Enables a remote machine to acccess services on your local machine.

#### On your local machine 

```bash
nc -lvp 8080
```

#### On the remote machine 

```bash
nc your-local-ip 8080 -c "nc localhost 80" 
```

### Network relay Port Forwarding 

Acts as bridge between two networks, forwarding all incoming traffic from one port to a remote service 

```bash
nc -lvp 9000 -c "nc 192.168.1.100 80"
```
Traffic to local port 9000 if forwarded to port 80 on the remote IP 192.168.1.100

## Limitations of ```netcat``` for Port Forwarding

* No encryption: Traffic is transmitted in plain text, making it insecure over public networks
* Basic Fuctionality: Lacks advanced features like access control or compression 
* Permission Requirements: You need elevated permissions to use ports below 1024

--------------------------------------------------------------

## Best Practices

### Secure Connections

* For secure environments, pair ```nc``` with tools like ```ssh``` for encrypted tunnels

### Check Port Availability

* Use ```nc``` to scan ports before setting up forwarding

```bash
nc -zv host-ip port 
```

### Local Network Testing 

* Use ```nc``` for connectivity testing or to emulate services quickly within a provate network




