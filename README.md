## Reflection 2.1

Server
![](/images/server.png)

Client 1
![](/images/client1.png)

Client 2
![](/images/client2.png)

Client 3
![](/images/client3.png)

This can be done by opening 4 terminals, with 1 terminal for server and the other 3 for clients. Type `cargo run --bin server` to run the server and type `cargo run --bin client` to run the clients.

When a client types a message, it is sent to the server. The server broadcasts messages received to all connected clients using a shared sender channel. Each client receive the incoming messages and prints them. 

## Reflection 2.2

In the `server.rs` file, the server binds to address and port `TcpListener::bind("127.0.0.1:2000)`, which needs to be fixed to `TcpListener::bind("127.0.0.1:8080)` to listen on port 8080 (the port client is using). The program uses WebSockets, indicated by the `ws://` prefix in the URI (written in `client.rs`). In the server side, WebSocket messages are implemented using the `tokio-websockets`. The server listens on TCP port 8080, accepts connections, upgrades them to WebSocket connections.

## Reflection 2.3

I changed the code in `server.rs`:

| Before | After |
|--------|-------|
| ![](/images/before_server.png) |  ![](/images/after_server.png) |

Now, the terminal from server looks like this:
![](/images/after_server1.png)

Previously, the log message only displayed the IP address and port number of the connecting client. Now, since we added the label `Min's Computer`, it gives more information on where this connection is from. 
