# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM
# SERVER 
```
import socket
port = 60000
s = socket.socket()
host = socket.gethostname()
s.bind((host, port))
s.listen(5)
print("Server listening on port", port)
while True:
    conn, addr = s.accept()
    print("Connected to", addr)
    data = conn.recv(1024)
    print('Server received', repr(data))
    filename = 'C:\\Users\\admin\\OneDrive\\Desktop\\computer networks\\EXP 3C\\mytext.txt'
    with open(filename, 'rb') as f:
        l = f.read(1024)
        while l:
            conn.send(l)
            print('Sent', repr(l))
            l = f.read(1024)
    print('Done sending')
    conn.send('Thank you for connecting'.encode())
    conn.close()
```
# CLIENT
```
import socket
s = socket.socket()
host = socket.gethostname()
port = 60000
s.connect((host, port))
s.send("Hello server!".encode())
with open('received_file', 'wb') as f:
    print('receiving data...')
    while True:
        data = s.recv(1024)
        print('data=%s', (data))
        if not data:
            break
        f.write(data)
print('Successfully received the file')
s.close()
print('connection closed')
```
## OUPUT

![image](https://github.com/JAGADEESHJ97/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/152129419/26014e19-bd74-4667-a29b-37c830cc1ce1)

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
