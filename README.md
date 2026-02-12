# 3a.CREATION FOR ECHO CLIENT AND ECHO SERVER USING TCP SOCKETS

## Ref. No.: 212225040312

## AIM
To write a python program for creating Echo Client and Echo Server using TCP
Sockets Links.

## ALGORITHM:
1. Import the necessary modules in python
2. Create a socket connection to using the socket module.
3. Send message to the client and receive the message from the client using the Socket module in
 server .
4. Send and receive the message using the send function in socket.

## PROGRAM
# server.py
~~~
import socket

HOST = '127.0.0.1'  
PORT = 65432        

with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as server_socket:
    server_socket.bind((HOST, PORT))
    server_socket.listen()

    print(f"Server is listening on {HOST}:{PORT}")
    while True:
        conn, addr = server_socket.accept()
        with conn:
            print(f"Connected by {addr}")
            while True:
                data = conn.recv(1024)
                if not data:
                    break
                conn.sendall(data)
                print(f"Echoed: {data.decode('utf-8')}")
~~~

# client.py
~~~
import socket

HOST = '127.0.0.1'  
PORT = 65432  

with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as client_socket:
    client_socket.connect((HOST, PORT))

    message = 'Hello, Server!'
    client_socket.sendall(message.encode('utf-8'))

    data = client_socket.recv(1024)
    print(f"Received echo: {data.decode('utf-8')}")

~~~

## OUPUT
# Server

<img width="693" height="98" alt="Screenshot 2026-02-12 100616" src="https://github.com/user-attachments/assets/3ee9eec3-43de-4120-a0a4-412577f71a58" />

# Client

<img width="473" height="83" alt="Screenshot 2026-02-12 100646" src="https://github.com/user-attachments/assets/7a6ad44a-cf51-4552-9720-688bdc47edd6" />

## RESULT
Thus, the python program for creating Echo Client and Echo Server using TCP Sockets Links 
was successfully created and executed.
