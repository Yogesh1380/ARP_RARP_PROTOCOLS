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
CLIENT
```
import socket
s=socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"};
while True:
   ip=c.recv(1024).decode()
   try:
     c.send(address[ip].encode())
   except KeyError:
     c.send("Not Found".encode())
```
SERVER
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())
```
## OUPUT - ARP
CLIENT

![422190329-0dc6208a-582e-455a-9e3d-8d06e41f341e](https://github.com/user-attachments/assets/4aac7c63-c23f-4850-a2fe-076b2e98c001)

SERVER

![422190396-3a74a8a7-edb8-4c46-8b3f-956bde38da75](https://github.com/user-attachments/assets/925a45b5-290b-4e03-bf13-d202b538a610)

## PROGRAM - RARP
CLIENT
```
import socket
s=socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"};
while True:
   ip=c.recv(1024).decode()
   try:
     c.send(address[ip].encode())
   except KeyError:
     c.send("Not Found".encode())
```
SERVER
```
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
 ip=input("Enter MAC Address : ")
 s.send(ip.encode())
 print("Logical Address",s.recv(1024).decode())
```
## OUPUT -RARP
CLIENT

![422191046-c3715042-1d85-4c6d-b301-2ead4a7ceb5f](https://github.com/user-attachments/assets/3af2e511-4e1c-48e0-9151-e1e6cb09a8ee)

SERVER

![422191145-478d7a33-0966-4dc4-9577-6f1a2375a36a](https://github.com/user-attachments/assets/ed6e797b-efea-447c-85fb-c0954bac453a)


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
