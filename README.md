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
~~~
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
~~~
client.py
~~~
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
~~~
## OUTPUT
server.py
<img width="1478" height="202" alt="Screenshot 2026-03-12 140133" src="https://github.com/user-attachments/assets/fbcb3b82-5440-4ded-8360-087231f61eac" />
client.py
<img width="1474" height="271" alt="Screenshot 2026-03-12 140120" src="https://github.com/user-attachments/assets/32d3fda3-83d6-42d5-bf70-1a8cd164614a" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
