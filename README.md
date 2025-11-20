# 3b.CREATION FOR CHAT USING TCP SOCKETS

## NAME : SUDEEP RAJ C R
## REG NO : 212224040333

## AIM
To write a python program for creating Chat using TCP Sockets Links.

## ALGORITHM:
1. Import the necessary modules in python
2. Create a socket connection to using the socket module.
3. Send message to the client and receive the message from the client using the Socket module in
 server
4. Send and receive the message using the send function in socket.

## PROGRAM
# client
```
import socket

s = socket.socket()
s.connect(('localhost', 8000))

while True:
    msg = input("Client > ")
    s.send(msg.encode())
    if msg.lower() == "exit":
        print("Closing connection...")
        break

    data = s.recv(1024).decode()
    if not data:
        print("Server closed the connection.")
        break
    print("Server >", data)

s.close()
```
# server
```
import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(1)
print("Server listening on port 8000...")

c, addr = s.accept()
print("Connected with", addr)

while True:
    client_msg = c.recv(1024).decode()
    if not client_msg:
        print("Client disconnected.")
        break
    print("Client >", client_msg)
    
    msg = input("Server > ")
    if msg.lower() == "exit":
        c.send("Server closing connection...".encode())
        break
    c.send(msg.encode())

c.close()
s.close()
```

## OUTPUT
<img width="1920" height="1140" alt="image" src="https://github.com/user-attachments/assets/7e1f4b55-0a7e-4e59-a5d4-b4f224c29fb4" />


## RESULT
Thus, the python program for creating Chat using TCP Sockets Links was successfully 
created and executed.
