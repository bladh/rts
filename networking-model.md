# Multiplayer for RTS

## Hybrid lockstep

* Good latency between player and server
* Prevents map hacks

#### How it works

Player A and Server run the same simulation by using deterministic lockstep.
Player A moves a handful of units, and sends the command to the server. The
server makes the move, and acknowledges this to the player. Since we are in a
synchronized lockstep, the units move "at the same time".

Player B has no knowledge of Player A, but has the same relationship with the
server. Player B moves his tank westward, sending the move command to the
server. Much like Player As infantry, this move is synchronized between the
player and the server.

Having special line-of-sight code, the server knows that the eastward moving
infantry from Player A and the westward moving tank of player B are not yet
within vision of each other. Each player will unknowingly move towards each
other.

The infantry, having longer line of sight, sees the tank on the server.
Wrapping up a nice package of the current state of the tank, where it's moving
the next few seconds (retrieved from interpolation), how busted it is, etc,
the Server sends this information to player A. Player As client receives the
information, and neatly draws out the incoming tank on the screen.

Player A decides to divert their infantry out of the way, avoiding player B's
detection. Running north and slightly west, the infantry ducks out of the way.
Equipped with information that a tank is on the way, Player A makes some
preparations back home, but still sneaking on with his infantry past the tank.

Player B, fully unaware of what just happened, keeps moving westward. The
server never notified him of the infantry, so even if he hacked his client
he wouldn't know.

The tank moves out of the infantrys line of sight, and the server stops
updating player A about its whereabouts. Since the information from the server
about the tank becomes outdated, Player As client stops drawing the Tank. It
has disappeared into the fog of war.

## The order queue

Every order the player issues gets placed in a simple queue. Every 100 ms:

* The queue is cleared of duplicate entries (spamclicked same order too many
times)
* The queue is reduced to a maximum of x orders (to prevent a bot from issuing
commands for a player achieving godlike micro management)

Once the server receives the queue, the server will:

* Cut the queue to a maximum of size x (in case a hacked client tries to
circumvent the maximum order queue size)
* Step through each order, verify that the units can actually execute them
* Acknowledge the orders by sending them back to the player.

So the client expects 10 updates per second.

## Desync!

In a typical lockstep deterministic multiplayer game, a desync is
catastrophical, since there is now no way to determine what is the actual
current game state. In our case, we have a central authority who can enforce
what is actually happening.

The client will every so often send a hash of what's currently happening. This
includes all unit positions, health, ammo, etc. The server will then compare
this hash with one of its own, that it computed in the same way. If these
hashes for some reason don't line up then the server will have to restore
reality:

* Pause the game for all players
* Notify the offending client that the hash signifies a desync
* For each of that players units, compile a large message of their positions,
what their orders are, their health, etc.
* Send the message to the client
* The client will then clear out *every* unit and structure, and recreate them
after the hosts recipe
* The client will take a hash of what's currently going on, and send it to the
server
* The server will verify the hash
* If everything is good, then the game will resume.

Since other players have received information about the offending clients units
in a different way, they should already line up with what's going on in the
server, so their clients are unaffected by this. At its worst, a unit should
just shift slightly to a different position, or the amount of mined metals will
change by a few. The desync is caught early, so most likely the player will not
even notice what's different. The whole resynchronization may take a while
though, so hopefully it won't happen often.

Optionally, the offending player may, on receiving news of the desync, send
a message containing the current state of all their units and structures to
the server. The server can compile a report with:

* The servers point of view
* The clients point of view
* The servers host OS
* The clients host OS
* The past x seconds worth of queued orders, so that a debug environment may
"load" up the full state and execute the orders backwards hopefully finding
the cause of the desync

This report will then be sent in some way back to us.

## Summary

* Client/Server use a lockstep deterministic model to communicate orders
* Information about enemy units arrive from the server
* Server keeps track which when enemy units are kept in the client, and updates
them while they're there

There are two schools of thought when it comes to enemy units

* Update what they do every "tick"

May be slow, but its safe. Doesn't exactly desync.

* Update their orders and execute in the client

May send more information than should be, and consider the following scenario:

* Player B sends one order to his 10 tanks to move
* Player A has seen 3 tanks

Basically each unit needs to hold a "Current Order" variable, so that the
server can gather up a command block for the 3 tanks to send to player A. In
the next few ticks when player A sees the rest of the tanks, there would be a
new command block incorporating more of the tanks. Too complex?
