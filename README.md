# ExamPrep period 5
1 - Name attributes of HTTP protocol makes it difficult to use for real time systems.

The question is very poorly written. Maybe a answer could be that the protocol contains a lot of information - information that 
is a overhead. One of the core principles of the HTTP protocol, is the Request - Response model. A client sends a request to the 
server and the server then comes with a appropriate response. This is a great construction for a traditional website where the 
client do an action and gets a response back. Since HTTP is stateless, every single request must have some information about what 
it want to do, where it should be done and who is doing it and so on. All this information that needs to be send every time, adds 
up to alot of bytes which affects the speed of the request - response time.

2 - Explain polling and long-polling strategies, their pros and cons. 
Polling
The client sends a request with a given interval and the server respond every time with a response - even if this is empty due to 
lack of information. Pros: It's very simple to setup, and since it's just XMLHttpRequests, every modern browser supports this.

Cons: traffic between client and server are huge and the server oftens sends empty responses.

Long-polling

Like polling the client sends a request but the server awaits new information before response is returned. When the client gets 4
the response, it then immediately sends another request to the server. Pros: You are notified WHEN(And only when) the server gets 
new information. Since it's just XMLHttpRequests, every modern browser supports this. 

Cons: A bit more complex to setup, and a bit more intensive on the server, since it would have to keep the connection open while 
it's waiting for new information. 

3 - What is HTTP streaming, SSE (Server sent events)? 

The client sends a request using regular HTTP. The server can then send back an event to the client when there's new information 
without closing the connection. 

Pros: Real time traffic from server to client. Uses HTTP for the responses, so no need for a new protocol. 

Cons: Doesn't provide CORS (not able to connect with a server from another domain. Not supported by IE or Edge.

4 - What is WebSocket protocol, how is it different from HTTP communication, what advantages it has over HTTP? 

WebSockets are fast real time system. Instead of sending the usual HTTP(Header, cookies and so on) every time 
(overhead because of the huge informationoverflow a HHTP header contains), it only gets sent on the initial request. 
From there on, the communication is no longer using the HTTP but TCP protocol. This allows really small and low latency 
communication. Both the server and client can communicate back and forth, so there's no request - response pattern anymore.

Pros: Real time traffic from server to client AND from client to server. CORS is possible.

Cons: Not all browsers support websockets

5 - Explain what the WebSocket Protocol brings to the Web-world.

With websockets you have full duplex birectional communication between the server and client with less overhead than traditional 
HTTP based methods. No request-response pattern - the client and server can both initiate communication.

6 - Explain and demonstrate the process of WebSocket communication - From connecting client to server, through sending messages, 
to closing connection. 

Establish connection via handshake - that upgrades the HTTP to a Websocket.

Bidirectonal messages between server and client.

Each side can close the connection

The client estabilshes a WebSocket connection through a Websocket handshake, by sending a regular HTTP request to the server. In the header of this request, there's an Upgrade header which tells the server that the client waats to establish a WebSocket connection.
GET ws://websocket.example.com/ HTTP/1.1
Origin: http://example.com
Connection: Upgrade
Host: websocket.example.com
Upgrade: websocket
If the server supports WebSocket connections, it sends back a response with an Upgrade header.
HTTP/1.1 101 WebSocket Protocol Handshake
Date: Wed, 16 Oct 2013 10:07:34 GMT
Connection: Upgrade
Upgrade: WebSocket

Now that the handshake is complete, all traffic from here on will be using TCP instead of HTTP. Now both the client and server 
can send data to each other. The transfers no longer need all the overhead that a HTTP request normally would, so even though 
there's still a 4-12 bytes overhead about the data send with the payload, the overall size of the transfer is significantly reduced.

7 - What's the advantage of using libraries like Socket.IO, Sock.JS, WS, over pure WebSocket libraries in the backend and standard 
APIs on frontend? Which problems do they solve?

Socket.io solves the problem that not all browsers support websockets - Fallbacks to polling with incompatible browsers.

developers are able to send and receive data without worrying about cross-browser compatibility.

8 - What is Backend as a Service, Database as a Service, why would you consider using Firebase in your projects? 

As a service means that you have outsourced that part of your solution to someone else.

Firebase i smart, fast, easy to implement and use and offers both backend and database. You dont need a ton of code to 
get the job done - Firebase handles it for you.

9 - Explain the pros & cons of using a Backend as a Service Provider like Firebase.

Pros:
Easy to set up and you travel light with almost no backend code on your hand

Hvis der ikke er krav omkring sikker opbevaring  og adgang til dine data - så er det en hurtig og nem løsning for mindre virksomheder.

Cons:

You are totally dependent on the provider - they might change the payment plan over time

When the provider has downtime - you hawe downtime

If you want to change provider it is often difficult to get your data migrated to the new provider

Data is in the hand of a third party - security isuues...

10 - Explain and demonstrate “three-way data binding” using Firebase and Angular 

Angular offers two way binding - when the client is updated the model gets updated as well and the other way around.

By syncing your Angular model with Firebase, your app’s data in the model is synchronized in real-time across all clients. 
When data changes in one client, those updates are immediately persisted to Firebase and rendered across all clients.

11 - Explain and demonstrate the difference between the simple chat system in your own WebSocket + Node.js backend vs. Firebase.









