# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
   
**NAME:SRIDHAR C <br>
REG NO:212225040425**

## PROGRAM
### client.py
```python
import socket 
s = socket.socket() 
host = socket.gethostname() 
port = 60000 
s.connect((host, port)) 
s.send("Hello server!".encode()) 
with open('received_file', 'wb') as f: 
    while True: 
        print('receiving data...') 
        data = s.recv(1024) 
        print('data=%s', (data)) 
        if not data: 
            break 
        f.write(data) 
f.close() 
print('Successfully get the file') 
s.close() 
print('connection closed')
```
### server.py
```python
import socket
port = 60000
s = socket.socket()
host = socket.gethostname()
s.bind((host, port))
s.listen(5)
while True:
    conn, addr = s.accept()
    data = conn.recv(1024)
    print('Server received', repr(data))
    filename='mytext.txt'
    f = open(filename,'rb')
    l = f.read(1024)
    while (l):
        conn.send(l)
        print('Sent ',repr(l))
        l = f.read(1024)
    f.close()
    print('Done sending')
    conn.send('Thank you for connecting'.encode())
    conn.close()
```
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/61d4c6dc-6e3b-4219-8c92-9442f5972f11" />

## OUPUT
<img width="739" height="243" alt="image" src="https://github.com/user-attachments/assets/33ffb861-bf06-4e8c-a2fd-d6beb4dc94e1" />

<img width="1044" height="200" alt="image" src="https://github.com/user-attachments/assets/a5726d24-a831-42a8-b771-c70d7dae4d79" />
<img width="1063" height="277" alt="image" src="https://github.com/user-attachments/assets/372519ea-44b7-473f-96e0-1a2f745b212a" />

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
