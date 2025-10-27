# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
## Client:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
## Server:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.
P
## PROGRAM - ARP
### Server 
```python
import socket
import socket
s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)
print("ARP Server is listening on port 8000...")
c, addr = s.accept()
address = {
    "165.165.80.80": "6A:08:AA:C2",
    "165.165.79.1": "8A:BC:E3:FA"
}
while True:
    ip = c.recv(1024).decode()
    print(f"Received IP: {ip}")
    mac = address.get(ip, "Not Found")
    c.send(mac.encode())
```
### Client 
```python
import socket
s = socket.socket()
s.connect(('localhost', 8000))
while True:
    ip = input("Enter Logical Address (IP): ")
    s.send(ip.encode())
    print("MAC Address:", s.recv(1024).decode())
```
## OUPUT - ARP
### Server

<img width="1471" height="916" alt="image" src="https://github.com/user-attachments/assets/7233d180-43d0-4235-a772-b29b3c6a7e8a" />


### Cliect

<img width="1475" height="909" alt="image" src="https://github.com/user-attachments/assets/050365f6-f69c-48cd-8875-f00b4a83d7cb" />


## PROGRAM - RARP

### Server
```python
import socket
s = socket.socket()
s.bind(('localhost', 8001))
s.listen(5)
print("RARP Server is listening on port 8001...")
c, addr = s.accept()

address = {
    "6A:08:AA:C2": "165.165.80.80",
    "8A:BC:E3:FA": "165.165.79.1"
}
while True:
    mac = c.recv(1024).decode()
    print(f"Received MAC: {mac}")
    ip = address.get(mac, "Not Found")
    c.send(ip.encode())
```
### Cliect
```python
import socket
s = socket.socket()
s.connect(('localhost', 8001))
while True:
    mac = input("Enter Physical Address (MAC): ")
    s.send(mac.encode())
    print("IP Address:", s.recv(1024).decode())
```
## OUPUT -RARP

### Server
<img width="1475" height="989" alt="image" src="https://github.com/user-attachments/assets/b1c76c65-5d3e-4cc0-95fb-d04edb7d645b" />

### Cliect
<img width="1484" height="976" alt="image" src="https://github.com/user-attachments/assets/3a4013fb-07f8-4497-9767-18cc21619a2f" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
