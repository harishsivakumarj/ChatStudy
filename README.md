# Ex. No:1b 			Study of Client Server Chat Applications

## Aim: 
To perform a study on Client Server Chat Applications
## Introduction:
Client-server chat applications are a category of networked software that enables real-time communication between users over a network. This study explores the key components, architecture, and considerations in the development of client-server chat applications, highlighting their significance and common implementation practices.
Client-server chat applications are software systems that enable real-time communication between users over a network. These applications follow a client-server model, where one component (the server) manages connections and facilitates communication, while the other component (the client) interacts with the server to send and receive messages. Below are the fundamental aspects and components involved in the basics of client-server chat applications:
## 1. Client-Server Model:
•	Server:
•	The server is a central component that listens for incoming connections from clients.
•	It manages the communication channels and facilitates the exchange of messages between clients.
•	It may handle user authentication, message routing, and other core functionalities.
•	Client:
•	Clients are users or devices that connect to the server to participate in the chat.
•	Each client has a unique identity, often represented by a username.
•	Clients interact with the server to send and receive messages.
## 2. Communication Protocols:
•	Communication between clients and servers often relies on established protocols. The choice of protocol influences the behavior of the chat application.
•	TCP (Transmission Control Protocol):
•	Provides reliable, connection-oriented communication.
•	Ensures the ordered and error-free exchange of messages.

•	UDP (User Datagram Protocol):
•	Connectionless and operates in a best-effort mode.
•	Faster but may result in message loss or disorder.
## 3. Socket Programming:
•	Sockets:

•	Sockets serve as communication endpoints.
•	Each client and the server has a socket for sending and receiving data.

•	Functions:
•	Socket programming involves functions for creating, binding, listening, accepting connections, and sending/receiving data through sockets.
## 4. User Authentication:
•	For security and privacy, chat applications often implement user authentication mechanisms.
•	Users are required to provide credentials (e.g., username and password) to access the chat system.
•	More advanced methods like tokens or secure protocols can enhance authentication.
5. Message Routing:
•	The server is responsible for routing messages from one client to another.
•	It ensures that messages are delivered to the intended recipients.
•	Message routing may involve maintaining a list of connected users and their associated sockets.

## Architecture:
## Client-Server Model:
Client-server chat applications typically follow the client-server model, where one entity acts as the server, managing connections and facilitating communication, and one or more entities act as clients, initiating communication with the server.

## Communication Protocols:
The choice of communication protocol is crucial. Many chat applications use TCP (Transmission Control Protocol) for reliable, connection-oriented communication to ensure the ordered and error-free exchange of messages.
User Authentication:
User authentication mechanisms are essential to ensure secure and authorized access to the chat system. This can involve username-password authentication or more advanced methods like tokens.
## Components of Client-Server Chat Applications:
## Server-Side Components:

•	Socket Handling: The server manages incoming client connections using sockets, creating a separate thread or process for each connected client.
•	User Management: Maintaining information about connected users, their status, and handling login/logout functionality.
•	Message Routing: Implementing logic to route messages from one client to another, ensuring proper delivery.

## Considerations in Development:
1.	Concurrency and Multithreading:
•	Chat applications often require handling multiple connections simultaneously. The server must be designed to support concurrency, commonly achieved through multithreading or asynchronous programming.
2.	Security:
•	Ensuring the security of user data and messages is paramount. Encryption techniques, such as SSL/TLS, can be implemented to secure data in transit. Proper user authentication mechanisms help prevent unauthorized access.
3.	Scalability:
•	As the number of users grows, the chat application must be scalable. This involves optimizing server-side architecture to handle increasing loads efficiently.
4.	Persistence:
•	Some chat applications implement message persistence, allowing users to retrieve past messages. This may involve using databases to store and retrieve chat history.

5.	Notification Systems:
•	Implementing real-time notifications to inform users of new messages, user presence changes, or other relevant events.


Client-server chat applications are versatile tools that facilitate real-time communication between users over a network. They incorporate various components, including server-side and client-side elements, and must consider factors such as security, scalability, and concurrency. As technology continues to advance, client-server chat applications remain integral for collaborative communication in various domains.

Client-server chat applications are foundational to real-time communication over networks. They incorporate principles of socket programming, communication protocols, and security mechanisms to provide a seamless user experience. Understanding the basics of client-server chat applications is essential for developers involved in networked application development, as they form the backbone of various collaborative communication systems. As technology evolves, chat applications continue to adapt, incorporating new features and technologies to enhance user interaction and connectivity.

## Program:
Client
```
import socket


def client_program():
    host = socket.gethostname()  # as both code is running on same pc
    port = 5000  # socket server port number

    client_socket = socket.socket()  # instantiate
    client_socket.connect((host, port))  # connect to the server

    message = input(" -> ")  # take input

    while message.lower().strip() != 'bye':
        client_socket.send(message.encode())  # send message
        data = client_socket.recv(1024).decode()  # receive response

        print('Received from server: ' + data)  # show in terminal

        message = input(" -> ")  # again take input

    client_socket.close()  # close the connection


if __name__ == '__main__':
    client_program()
```
Server
```
import socket
def server_program():
    # get the hostname
    host = socket.gethostname()
    port = 5000  # initiate port no above 1024

    server_socket = socket.socket()  # get instance
    # look closely. The bind() function takes tuple as argument
    server_socket.bind((host, port))  # bind host address and port together

    # configure how many client the server can listen simultaneously
    server_socket.listen(2)
    conn, address = server_socket.accept()  # accept new connection
    print("Connection from: " + str(address))
    while True:
        # receive data stream. it won't accept data packet greater than 1024 bytes
        data = conn.recv(1024).decode()
        if not data:
            # if data is not received break
            break
        print("from connected user: " + str(data))
        data = input(' -> ')
        conn.send(data.encode())  # send data to the client

    conn.close()  # close the connection


if __name__ == '__main__':
    server_program()
```
## Output:
Client
![image](https://github.com/user-attachments/assets/8b7d7b03-a82b-48d2-b7fb-ef19718a312f)
Server
![image](https://github.com/user-attachments/assets/1c188541-4731-498f-8052-13c7c44088fd)

## Result:

Thus the study on Client Server Chat Applications has been performed
