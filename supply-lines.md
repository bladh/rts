# Setting up supply lines

There are three types of supplies in this game:

* Metal
* Electricity
* Munitions

which interacts with units in different ways. Metal and Electricity are needed
for structures. Electricity is needed for vehicles. Munitions is needed for
combat units.

From the IMC side of things, Metals and Munitions can be stored in Depots.
Electricity is created by power generators and stored in Batteries.

Workers and Armored Haulers can be ordered to move a set amount of
metal/munitions from any structure to any structure (the game would not prevent
the player from accidentally moving metals back to the mine, for example)

Workers can carry much less than Haulers, move slower and have less armor.
However they are smaller and cheaper, and inside a secured base they will
suffice as their drawbacks won't be relevant.

A unit may define two structures, as well as define basic conditions:

* If *structure a* has *more than* x amount of metal
* and *structure b* has *less than* x amount of metal
* move x amount of metal from *structure a* to *structure b*

The same goes for munitions. The default condition would be if structure a
has more than 0 of the resource, and structure b has less than the maximum
capacity of the resource.

Batteries are high quality enough that they don't lose charge after being
charged, but mobile batteries will deplete a bit of the stored energy as the
vehicle is moving. This means that batteries that are far away from a power
source would be penalized of the distance, since the mobile batteries would
consume some of the electricity on the way. This could be solved by
constructing power lines, but they are harder to defend than a caravan of
mobile batteries would be.

So when assaulting a player which is far away, there are a few options:

### Send units from home

Units are built at home, haulers are brought over with munitions and mobile
batteries are brought over to recharge the vehicles. If this defeats the enemy,
great! If not, hopefully you have enough electricity to go home, or your army
will just depower at his doorstep, essentially donating him free units.

### Establish a small base

Some enemies don't just die from the first push. For an extended assault,
you would want to bring back units for repair and resupply munitions. But
bringing them back home every time would be very time consuming. An option
is to build up some defences around batteries and depots, and have haulers
constantly resupply these with munitions and electricity. Might want to
spare some of the army to protect the caravans though, as well as the base.

### Establish a big base

You could build your units and munitions right outside the enemys doorstep,
as long as you bring over what you need. It's a bigger investmen though, and
would be a serious hit in case the enemy strikes back and destroys it. Since
you only have one place of producing metals, if the enemy cuts off the metal
supply for your base, you won't be able to produce units or munitions, and he
could just starve it out until he can capture it for his own.
