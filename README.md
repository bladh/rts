# Unnamed scifi rts

## Terrain

Tilemap, with height. Enough damage from explosions can level hills,
create valleys. Different explosions do different kinds of damage:

* Small explosion

No damage worth mentioning, but the tile can reflect some sort of tarnish.

* Medium explosion

Makes the tile "bumpy", slowing down heavy vehicles.

* Large explosion

Lowers the height by 1 unit. Vehicles go slower when going uphill, so
traversing a battlefield littered by these craters would take some time.

Builder units can terraform, levelling out broken terrain so there may be
structures placed on it, or "digging" corridors out of hills.

If two adjacent tiles have less than 1 height level of difference, then
they will "slope" into each other and units can traverse. Otherwise, there
is more of a "hole" and units can not cross.

#### Tunneling

Worker units can dig a tunnel entrance, and the player can switch into
underground view to further order the digging of tunnels, or construction
underground. There is only one "underground" level, for gameplay simplicity
reasons.

## Vision / Fog of war

* Tanks and workers have a very low range of vision.
* Infantry has a medium range of vision.
* Helicopters have a long range of vision.

Heightmap affects the vision, so units may hide in crevasses or craters.
Helicopters ignore this completely since their field of view is from above.

Visible units would show up on the minimap, however the minimap will not be
100% reliable in this game because different units have different "visibility"
values.

Heavy tanks have a high visibility value. Helicopters in flight have a
very high visibility value. As you may expect, infantry have a low visibility
value.

As another interaction to visibility, adjacent units increase each others
visibility value (so a squad of infantry is more visible than a lone infantry).

This visibility affects how enemy units become reported to the minimap, and if
units will automatically attack enemy units that are "in sight".

There are no numbers, but with some tweaking, consider the following:

(Friendly unit *vision* value) - (Distance to enemy unit) - (Enemy unit *visibility* modifier)

If the resulting value is too low, then the enemy unit would not be visible to
the player. Likely this means that unit is too far away, but it also means some
smaller units could inch closer than expected, because they are being stealthy.

If the value is high enough, then the unit would not only be visible, but they
would also be visible as a dot on the minimap.

This should let players do sneaky vision plays, skirting the enemies vision
with a forward infantry scout and gather information their opponent would not
have. Since having units close together should impact their *visibility*
modifier it should discourage players to move around their army in big blobs,
because this would make their army movements very visible to their opponents.
Also consider that this visibility modifier keeps stacking with more units -
if the opponent would mass up a large force of heavy tanks, your infantry may
even sense their movements from further away than they can actually see.

Helicopters give you a lot of vision, very quickly. Their downside is that they
are very visible, so your opponent would know that you know what they're doing.

## Structures

#### Ore excavator / Main building

You only get one! Constantly mines minerals. Can be upgraded a few times,
but each "upgrade level" costs electricity. The Excavator is equipped with
a small reactor that takes care of its basic energy requirements.

#### Barracks

Small, cheap building that can crank out Infantry. Functions without
power, at a bit slower capacity. Needs to be supplied with metals to work.

#### Power generator

Factories require power to operate, vehicles need to be recharged and
the Ore Excavator will require more power if its upgraded.

Power generators may only be built in some places on the map. Maybe they
drill for uranium and need to be built on top of deposits?

#### Power line

Connects buildings to the power generator, if they're too far away from it.

#### Weapons factory

Produces munitions. Munitions must be brought to units for reload.

* Light munition
* Medium munition
* Heavy munition

#### Turret

Building which requires power. It will excel against infantry if equipped
with light munition, and do well against vehicles if equipped with medium
munition.

#### Artillery

Building which requires both power and heavy munition. It will fire at long
range.

## Units

All attacking units require some kind of munition to be able to attack.

Vehicles are electric and need to be charged, or they will become
immobilized. Flying vehicles will make an emergency landing and power off.

#### Infantry

Multi-role unit. Can capture structures. Can help hauling munitions in a pinch.

Infantry can capture vehicles that are out of energy. This will use up
the infantry and convert the vehicle, but it will still need to be recharged.

Infantry uses light munitions and do not require energy to function. Infantry
has long line of sight.

#### Worker

Light vehicle which creates all structures in the game. It can also
do better excavations than Infantry units. Can do some hauling.

Workers do not require energy, but they are rather slow and have very low
line of sight. Workers can be captured by infantry at any time.

#### Mobile battery

Mobile high explosive unit that can serve as a power source for structures or
recharging vehicles. It's very vulnerable.

#### Armored hauler

Can store munitions or infantry. high capacity.

#### Light tank

Armored vehicle with a cannon. Sturdy against infantry, navigates terrain
fairly well. Line of sight is lower than infantry.

#### Heavy tank

Pricier, slower, tougher, longer range. uses more electricity than light tanks.

The heavy tank attack will have splash damage and damage nearby units.

#### Helicopter

Scouts the battlefield quickly, but has only a light gun.

Maybe the helicopter may also carry a small amount of infantry, so they
could be transported quickly.

The helicopter is quite energy intensive and a player looking to use
helicopters would have to invest in mobile batteries for anything beyond
short range scouting around the main base.

Helicopters can land to conserve energy.
