# W.I.P Chat App
Scalable Chat Application

SETUP:
  - W.I.P

Java Backend 
 Intention:
 Backend would be split into 2 parts:
 - Initial Connection Server
    - This server's ip would be static and saved to the settings of the client
    - The server's job is be in communication with all proccessing servers and assign the clients to them
    - It would handle proccessing servers being added and dropped.
    - Possible Next Step - Regionaility:
      - List of primary servers would be saved to the clients, who will then ping the list, and default to the one with the lowest latency
      - Each server would simply be responsible for proccessing servers within their own region
 - Proccessing Server
    - The server would be the responsible for send requests, but will not be saving any information
    - Should handle encrypted text, photos/videos
    - Properly handle group chats
 - Servers should be designed to work on linux, preferably Amazon Linux 2
 - The design is meant to be privacy oriented - But if nothing at all is stored server side, 
 how do we send the messages/media when either client is offline? Maybe store the info temporarily,
 once everyone in the specified chat recieves the items delete them off the server - Which server???
 Easy non-redundant solution: Store directly on the proccessing server, if server fails the information
 is to be deleted once restored, and simply give an error to the client who sent it. OR I am not sure 
 how AWS works yet, but a redundant solution would be to store the information on a shared server,
 that way when a proccessing server is dropped, and the clients have been transferred over to a new one
 it could continue as normal. Method TBD once we learn more about AWS.
 
Clients - Desktop (C/C++) and Andriod (Java) - No current plans for IOS/Web
 - Clients should all share the same features
 - Maintain a consistent, yet appropriate design for each
 - Create a similar request structure - Server should not be concerned with the type of device
 - Store all the information locally
