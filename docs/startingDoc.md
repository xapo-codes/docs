Starting Out
This page explains how to start using NodeTunnel in a Godot project.
It covers:


What NodeTunnel needs to exist


What the basic setup looks like


How connecting, hosting, and joining work


Code snippets are intentionally small. They show structure, not full implementations.

NodeTunnel Installed
NodeTunnel must already be available in your project.
You should be able to reference the class:
var peer := NodeTunnelPeer.new()

If this errors, NodeTunnel is not installed correctly.

Creating a NodeTunnel Peer
NodeTunnel works by providing a custom multiplayer peer.
Create it like this:
var peer := NodeTunnelPeer.new()

This peer handles:


Relay connections


Rooms


Peer communication



Assigning the Multiplayer Peer
NodeTunnel must be assigned to Godot’s multiplayer system:
multiplayer.multiplayer_peer = peer

Until this is assigned, NodeTunnel will not be used.

Connecting to a Relay
Before hosting or joining rooms, the peer must connect to a relay server:
peer.connect_to_relay("45.33.64.148:8080", "my_game")



The relay address points to the NodeTunnel relay


The app ID separates your game from others using the same relay


This is usually called once when multiplayer starts.

Authentication
Relay connection is asynchronous.
You must wait for authentication before hosting or joining rooms:
peer.authenticated.connect(func():
	print("Relay authenticated")
)

If this signal does not fire, hosting and joining will fail.

Hosting a Room
Once authenticated, you can host a room:
peer.host_room(true, "My Lobby", 4)

This:


Registers a room with the relay


Makes this client the host


Allows other clients to join



Joining a Room
To join an existing room, use its room ID:
peer.join_room(room_id)

Room IDs are typically obtained from a room list.

Room Connection
Hosting or joining is complete only when room_connected fires:
peer.room_connected.connect(func(room_id):
	print("Connected to room:", room_id)
)

Do not assume hosting or joining succeeded until this signal fires.

Disconnects
Always handle forced disconnects:
peer.forced_disconnect.connect(func():
	print("Disconnected from relay")
)

This signal fires when the relay disconnects the client.