# 2a_Stop_and_Wait_Protocol
## AIM 
To write a python program to perform stop and wait protocol
## ALGORITHM
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
server.py
```
import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(1)

print("Waiting for connection...")
conn, addr = s.accept()
print("Connected to", addr)

while True:
    data = conn.recv(1024).decode()
    if not data:
        break

    print("Frame received:", data)
    conn.send("ACK".encode())

conn.close()
```
client.py
```
import socket

s = socket.socket()
s.connect(('localhost', 8000))

n = int(input("Enter number of frames: "))

for i in range(n):
    msg = input("Enter frame: ")
    s.send(msg.encode())

    ack = s.recv(1024).decode()
    print("Received:", ack)

s.close()
```
## OUTPUT
<img width="1097" height="352" alt="Screenshot 2026-11-04 100004" src="https://github.com/user-attachments/assets/5c5d50de-8151-47ee-ba03-3f6c53d24426" />
<img width="1105" height="412" alt="Screenshot 2026-11-04 095950" src="https://github.com/user-attachments/assets/048dc166-0a66-4a46-87b4-399973537ff3" />
## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
