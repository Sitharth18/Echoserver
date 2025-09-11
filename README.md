# Echoserver
Echo server and client using python socket

# AIM:

To develop a simple webserver to serve html programming pages.

## DESIGN STEPS:

### Step 1:

Design of echo server and client using python socket

### Step 2:

Implementation using Python code

### Step 3:

Testing the server and client 

## PROGRAM:
server.py
```
import socket

# Create a TCP/IP socket
server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Bind the socket to an address and port
server_socket.bind(('localhost', 12345))
server_socket.listen(1)

print("Server is listening on port 12345...")

# Wait for a connection
conn, addr = server_socket.accept()
print(f"Connected by {addr}")

while True:
    data = conn.recv(1024)
    if not data:  # If no data, client closed connection
        break
    print(f"Received from client: {data.decode()}")
    conn.sendall(data)  # Echo back the same data

conn.close()
```
client.py
```
import socket

# Create a TCP/IP socket
client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Connect to the server
client_socket.connect(('localhost', 12345))

while True:
    msg = input("Enter message (type 'exit' to quit): ")
    if msg.lower() == 'exit':
        break
    client_socket.sendall(msg.encode())
    data = client_socket.recv(1024)
    print(f"Echo from server: {data.decode()}")

client_socket.close()
```

## OUTPUT:
![s s](https://github.com/user-attachments/assets/9ccf3c20-946d-4821-8565-dc1b399d77e4)

![c s](https://github.com/user-attachments/assets/5d975c97-3ec0-4eaa-98b9-d89c8980d9f9)

## RESULT:
The program is executed successfully
