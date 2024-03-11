# 3a.CREATION FOR ECHO CLIENT AND ECHO SERVER USING TCP SOCKETS
# AIM
To write a python program for creating Echo Client and Echo Server using TCP
Sockets Links.
## ALGORITHM:
1. Import the necessary modules in python
2. Create a socket connection to using the socket module.
3. Send message to the client and receive the message from the client using the Socket module in
 server .
4. Send and receive the message using the send function in socket.
## PROGRAM
```import socket

# Echo Server
def echo_server():
    HOST = '127.0.0.1'
    PORT = 65432

    with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as server_socket:
        server_socket.bind((HOST, PORT))
        server_socket.listen()
        print('Server is listening...')
        
        conn, addr = server_socket.accept()
        
        with conn:
            print('Connected by', addr)
            while True:
                data = conn.recv(1024)
                if not data:
                    break
                conn.sendall(data)

# Echo Client
def echo_client():
    HOST = '127.0.0.1'
    PORT = 65432

    with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as client_socket:
        client_socket.connect((HOST, PORT))
        
        while True:
            message = input("Enter message to send to server (type 'exit' to quit): ")
            if message.lower() == 'exit':
                break
            
            client_socket.sendall(message.encode())
            
            data = client_socket.recv(1024)
            print('Received from server:', data.decode())

import threading

server_thread = threading.Thread(target=echo_server)
client_thread = threading.Thread(target=echo_client)

server_thread.start()
client_thread.start()

server_thread.join()
client_thread.join()
```
## OUPUT
![image](https://github.com/RahulvVenugopal/3a.Sockets_Creation_for_Echo_Client_and_Echo_Server/assets/144132514/b5f94dc3-7058-48cc-b643-553a02a22a17)

## RESULT
Thus, the python program for creating Echo Client and Echo Server using TCP Sockets Links 
was successfully created and executed.
