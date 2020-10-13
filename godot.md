# Godot implementation

## Vision

Area2D and CollisionShapes will be our friends, as well as using collision
layers. All collision shapes are circular, except, obviously, the selection
box.

Each unit will have 3 collision shapes:

* Unit collision

The most obvious one, handles collisions with units and structures.

It will be set to the Unit collision layer.

* Vision collision

A large circle (not rendered in-game) surrounding the unit and controlling
what it can see. When run on the server, if a `visibility collision`
collides with the Vision collision object, then the player owning the vision
collision will recieve information about the unit belonging to the collided
`visibility collision`.

It will be set in the Vision collision layer.

* Visibility collision

The `visibility` of infantry matches their `vision`, but this is not the case
for tanks. In their case, the `visibility collision` is much larger. This is
also a large circle around the unit.

The visibility collision shape should increase in size if the unit is moving or
attacking.

This one is also set in the Vision collision layer.

### Line of sight?

Taking the visibility a step further, once a circle collision has been detected
we can proceed to raycasting, casting a simple ray from the unit to see if the
enemy is actually visible from the current position. This means that if you
escort your tank with a single infantry the infantrys vision will be obscured!

It also means that units can hide behind structures. Maybe some sort of
"peeking" behaviour should be implemented to allow for base infiltration.

The visible fog of war should reflect the line of sight, so players would know
what to expect.

### Weird things!

Consider the following scenario:

The pirates have an attacking renegade tank sitting behind a bunker.
The bunker is empty, and has a low `visibility` modifier. An infantry sees
the tank, but not the bunker. Will the raycast line of sight be blocked by the
bunker rendering the tank invisible?

The raycast should only collide with units whose visibility collision has
collided with the units vision collision!

But what if the bunker was indeed manned and starts firing. Will this make the
tank invisible?

Hmmm.... Maybe this scenario is too niched :)

### Heightmap?

The heightmap takes the collision detection into the 3D realm. It could be as
simple as units that are higher up would have larger vision circles, but it
might not work out as expected since multiple units at high up would detect
each other at further range than units that are on lower elevation, unless
we have different hitboxes interact differently with different elevations,
but then we lose the simplicity that we have. Maybe just fuck the heightmap
for visibility :)

## Unit selection

When the player has released a right-click, a simple 2D collision shape will be
drawn between `mouse pressed` and `mouse released` positions, and then godot
will check for everything on the `unit` collision layer colliding with it.
The affected units are then selected. If the player just clicks then it'd work
just the same.

## Reasoning

Instead of reinventing the wheel and coding these things, we will take
advantage of Godots built-in collision handling. They are subject to
optimizations in the engine that may be more efficient than what GDScript can
achieve.
