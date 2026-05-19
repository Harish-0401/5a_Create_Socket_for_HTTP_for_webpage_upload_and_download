# 5a_Create_Socket_for_HTTP_for_webpage_upload_and_download
## AIM :
To write a PYTHON program for socket for HTTP for web page upload and download
## Algorithm

1.Start the program.
<BR>
2.Get the frame size from the user
<BR>
3.To create the frame based on the user request.
<BR>
4.To send frames to server from the client side.
<BR>
5.If your frames reach the server it will send ACK signal to client otherwise it will send NACK signal to client.
<BR>
6.Stop the program
<BR>
## Program
## Service 
~~~
import socket
from pythonping import ping

s = socket.socket()

s.bind(('localhost', 8000))
s.listen(5)

print("Server waiting for connection...")

c, addr = s.accept()
print("Connected to:", addr)

while True:
    hostname = c.recv(1024).decode()

    if not hostname:
        break

    try:
        result = ping(hostname, verbose=False)
        c.send(str(result).encode())

    except Exception:
        c.send("Not Found".encode())

c.close()
s.close()
~~~
## Client 
~~~

import socket

s = socket.socket()

s.connect(('localhost', 8000))

while True:
    ip = input("Enter the website you want to ping: ")

    s.send(ip.encode())

    response = s.recv(1024).decode()

    print(response)
~~~

## OUTPUT
<img width="1227" height="247" alt="image" src="https://github.com/user-attachments/assets/6360092d-bbac-4089-b852-1d3673cd50f7" />

## Result
Thus the socket for HTTP for web page upload and download created and Executed
