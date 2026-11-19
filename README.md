## DATE:- 19/11/2026
## NAME:- PULLA KAVYA
## REG NO:- 212225240110

# 3c.CREATION-FOR-FILE-TRANSFER-USING-TCP-SOCKETS
## AIM

To write a python program for creating File Transfer using TCP Sockets Links

## ALGORITHM:
 
 Import the necessary python modules.

Create a socket connection using socket module.

Send the message to write into the file to the client file.

Open the file and then send it to the client in byte format.

In the client side receive the file from server and then write the content into it.


## PROGRAM

## SERVER
```
import socket

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.bind((socket.gethostname(), 60000))
s.listen(5)

conn, addr = s.accept()
print("Connected:", addr)

data = conn.recv(1024)
print("Server received:", data.decode())

with open("mytext.txt", "rb") as f:
    while True:
        data = f.read(1024)
        if not data:
            break
        conn.sendall(data)

print("File sent successfully")

conn.close()
s.close()
```
## CLIENT 
```
import socket

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.connect((socket.gethostname(), 60000))

s.sendall("Hello server!".encode())

with open("received_file.txt", "wb") as f:
    while True:
        data = s.recv(1024)
        if not data:
            break
        f.write(data)

print("Successfully received the file")
s.close()
print("Connection closed")
```
## OUPUT
## SERVER

<img width="817" height="322" alt="image" src="https://github.com/user-attachments/assets/36a7db1a-0aef-4055-8759-b20788861125" />

## CLIENT

<img width="762" height="283" alt="image" src="https://github.com/user-attachments/assets/5780a684-163f-44f9-b72c-b609f27518ef" />

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was successfully created and executed.
