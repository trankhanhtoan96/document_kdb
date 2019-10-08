KDB+ allows one process to communicate with another process through interprocess communication. Kdb+ processes can connect to any other kdb+ on the same computer, the same network, or even remotely. We just need to specify the port and then the clients can talk to that port. Any q process can communicate with any other q process as long as it is accessible on the network and is listening for connections.

- a server process listens for connections and processes any requests
- a client process initiates the connection and sends commands to be executed

Client and server can be on the same machine or on different machines. A process can be both a client and a server.

A communication can be,

- Synchronous (wait for a result to be returned)
- Asynchronous (no wait and no result returned)

# Initialize Server
```q
`::5001              / server and client on same machine
`:jack:5001          / server on machine jack
`:192.168.0.156      / server on specific IP address
`:www.myfx.com:5001  / server at www.myfx.com
```
To start the connection, we use the function “hopen” which returns an integer connection handle. This handle is used for all subsequent client requests.
```q
q)h:hopen `::5001
q)h"til 5"
0 1 2 3 4
q)hclose h
```
# Synchronous Message 
Once a message is sent, it waits on and returns the result
`handle"<q cmd>"`

# Asynchronous Message
After sending a message, start processing the next statement immediately without having to wait and return a result.
`neg[handle] "<q cmd>"`

On client
```q
h:hopen `::5000
q) h "6*7"
42
q) h "t:123"
q) (neg h) (`cub3; 5)
```

On server
```q
q) t
123

q) cub3:{0N!x*x*x}

q) 125
```

# Handler message and callback
on server
```q
q) cub3:{x*x*x}
q) worker:{[arg; callback] res:cub3 arg; (neg .z.w) (callback; res)}
```

on client
```q
q) continue:{0N!x}
q) (neg h) (`worker; 5; `continue)
125
```