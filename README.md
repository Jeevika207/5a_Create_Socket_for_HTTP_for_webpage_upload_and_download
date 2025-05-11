# 5a_Create_Socket_for_HTTP_for_webpage_upload_and_download
## NAME : JEEVIKA R
## REGISTER NUMBER : 212224040137
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
```
import socket

def send_request(host, port, request):
    with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
        s.connect((host, port))
        s.sendall(request.encode())
        response = s.recv(4096).decode()
    return response

def download_file(host, port, filename):
    request = f"GET /{filename} HTTP/1.1\r\nHost: {host}\r\n\r\n"
    response = send_request(host, port, request)
    # Assuming the response contains the file content after the headers
    file_content = response.split('\r\n\r\n', 1)[1]
    with open(filename, 'wb') as file:
        file.write(file_content.encode())

if __name__ == "__main__":
    host = 'localhost'  # Use localhost for local server
    port = 8080  # Port where your local HTTP server is running

    # Test downloading a file from the local server
    download_file(host, port, 'example.txt')
    print("File downloaded successfully.")

```
## OUTPUT
![image](https://github.com/user-attachments/assets/fc6887ab-3c62-44aa-99fb-58d4e710d067)

## Result
Thus the socket for HTTP for web page upload and download created and Executed
