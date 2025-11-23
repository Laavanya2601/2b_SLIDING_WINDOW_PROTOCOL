# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM:
To write a python program to implement sliding window protocol
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM

## SERVER:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    print(s.recv(1024).decode())
    s.send("acknowledgement received from the server".encode())
```
## CLIENT:
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames to send : "))
l=list(range(size))
s=int(input("Enter Window Size : "))
st=0
i=0
while True:
    while(i<len(l)):
        st+=s
        c.send(str(l[i:st]).encode())
        ack=c.recv(1024).decode()
        if ack:
            print(ack)
            i+=s
```
## OUTPUT:
## SERVER:
<img width="1028" height="273" alt="Screenshot 2025-11-23 085714" src="https://github.com/user-attachments/assets/303b9c9c-992d-4ee3-b5d9-4a34e2e6b229" />

## CLIENT:
<img width="1035" height="263" alt="Screenshot 2025-11-23 085722" src="https://github.com/user-attachments/assets/c3ed557d-6622-4a41-b4c6-39c44e1a8044" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
