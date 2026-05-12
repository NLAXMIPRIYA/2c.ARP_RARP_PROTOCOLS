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
```
arp_client.py

import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())




arp_server.py

import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"169.254.196.92":"70:08:10:8E:BA:98","165.165.79.1":"8A:BC:E3:FA"}
while True:
    ip=c.recv(1024).decode()
    try:
       c.send(address[ip].encode())
    except KeyError:
       c.send("Not Found".encode())








```







## OUPUT - ARP


Server Side




<img width="421" height="178" alt="image" src="https://github.com/user-attachments/assets/76b07594-4156-48ce-89eb-718e0aaf9a85" />




Client Side







<img width="419" height="226" alt="image" src="https://github.com/user-attachments/assets/a9373395-c3e6-4da3-beb4-a4b0d195c392" />











## PROGRAM - RARP


```
rarp_server.py
import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)

c, addr = s.accept()

address = {
    "70:08:10:8E:BA:98": "169.254.196.92",
    "8A:BC:E3:FA": "165.165.79.1"
}

while True:
    mac = c.recv(1024).decode()

    try:
        c.send(address[mac].encode())

    except KeyError:
        c.send("Not Found".encode())





rarp_client.py



import socket

s = socket.socket()

s.connect(('localhost', 8000))

while True:

    mac = input("Enter Physical Address : ")

    s.send(mac.encode())

    print("IP Address:", s.recv(1024).decode())



```







## OUPUT -RARP



Server Side 






<img width="435" height="209" alt="image" src="https://github.com/user-attachments/assets/0fdf4c4b-6080-4d6e-a66a-dcde3dbb6dac" />






Client Side 






<img width="331" height="206" alt="image" src="https://github.com/user-attachments/assets/f14a504a-6727-47dc-98cb-bd249f9b9e63" />







## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
