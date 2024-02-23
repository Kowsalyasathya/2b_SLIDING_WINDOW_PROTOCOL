# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM:
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM:
### CLIENT:
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
### SERVER:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True: 
 print(s.recv(1024).decode())
 s.send("acknowledgement recived from the server".encode())
```
## OUPUT:
### CLIENT:
![307230211-01fdeaa1-8fb5-483b-b789-a239fef3c9cb](https://github.com/Kowsalyasathya/2b_SLIDING_WINDOW_PROTOCOL/assets/118671457/0df7780b-36a1-4a4f-a230-d0bbe1038992)
### SERVER:
![307230226-9709b736-28c9-46de-a7a3-7a6bfa1671c9](https://github.com/Kowsalyasathya/2b_SLIDING_WINDOW_PROTOCOL/assets/118671457/5af702a8-0fd2-4c34-8a17-b0c9c28aecca)

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
