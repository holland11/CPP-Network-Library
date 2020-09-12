The main idea of this project was to build a simple networking 
library that would abstract away many of network implementation
details and just leave an application with a relatively simple
interface to deal with connections and messages.

The library is made up of net_server, net_client, and net_message.
Each of which have a cpp and hpp file associated with them.

To facilitate building, fine-tuning, testing, and demonstrating the library,
I put together a chatroom application and a connect4 game application.
Each of which is split into a server app and a client app.

To use the net_server library, you provide it with two callback functions.
One of the functions (the accept_handler) gets called anytime a client
connects or disconnects. The other function (the read_handler) gets called
anytime the server receives a message.

The net_client library is similar, except you only need to provide it with 
a read_handler callback that gets called whenever the client receives a message.

To run the chatroom, build the project into a build directory, then with one
terminal, run the chat_server executable. This will spin up the server.
Then, with as many terminals as you'd like, run the chat_client executable.
This will connect a client to the server and the chatroom usage should be fairly
intuitive from there.

The connect4 game is setup the same way (connect4_server and connect4_client
executables).

Both applications use the ncurses library for having a little more control over
the terminal input and output. This library occasionally has some unfortunate behaviour
over SSH so you may encounter that if testing over SSH.

One last note is that if you are running these programs over SSH, you need to make
sure that each of your terminals is SSH'd into the same lab machine.
For example, if you run <netlink>@ugls.ece.uvic.ca, it will connect you to a 
specific ugls machine. Let's say it connects you to ugls4. Now, for every other
terminal, you need to ssh into ugls4 <netlink>@ugls4.ece.uvic.ca.

If this is not done, the clients won't be able to connect to the server.