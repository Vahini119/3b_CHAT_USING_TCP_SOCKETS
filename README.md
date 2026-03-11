# 3b.CREATION FOR CHAT USING TCP SOCKETS
## AIM
To write a python program for creating Chat using TCP Sockets Links.
## ALGORITHM:
1. Import the necessary modules in python
2. Create a socket connection to using the socket module.
3. Send message to the client and receive the message from the client using the Socket module in
 server
4. Send and receive the message using the send function in socket.
## PROGRAM
```
server.py
import socket
s=socket.socket()
s.bind(('localhost', 8000))
s.listen(1)
print("Waiting for connection...")
c, addr=s.accept()
print("Connected to", addr)
while True:
    clientMessage = c.recv(1024).decode()  
    if clientMessage.lower() == "exit":
        print("Client disconnected")
        break
    print("Client >", clientMessage)
    msg = input("Server > ")
    c.send(msg.encode())
    if msg.lower() == "exit":
        print("Server stopped")
        break
c.close()
s.close()

```
```
client.py
import socket
s=socket.socket()
s.connect(('localhost', 8000))
print("Connected to server")
while True:
    msg = input("Client > ")
    s.send(msg.encode())
    if msg.lower() == "exit":
        print("Disconnected from server")
        break
    serverReply = s.recv(1024).decode()    
    if serverReply.lower() == "exit":
        print("Server closed connection")
        break 
    print("Server >", serverReply)
s.close()

```
## OUPUT
server.py

<img width="1920" height="1080" alt="Screenshot (62)" src="https://github.com/user-attachments/assets/49a25765-d1ce-42c9-bf48-1eea96846661" />


client.py
<img width="1920" height="1080" alt="Screenshot (60)" src="https://github.com/user-attachments/assets/2bede8af-640f-4692-b177-beb77a4fc27f" />


## RESULT
Thus, the python program for creating Chat using TCP Sockets Links was successfully 
created and executed.
