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

* Infantry has a medium range of vision

* Helicopters have a long range of vision

Heightmap affects the vision, so units may hide in crevasses or craters.
Helicopters ignore this completely since their field of view is from above.

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

Multi-role unit. Can do very basic terraforming and capture structures.
Can help hauling munitions in a pinch.

Infantry can capture vehicles that are out of energy. This will use up
the infantry and convert the vehicle, but it will still need to be recharged.

Infantry uses light munitions and do not require energy to function. Infantry
has long line of sight.

#### Worker

Light vehicle which creates all structures in the game. It can also
do better excavations than Infantry units. Can do some hauling.

Workers do not require energy, but they are rather slow and have very low
line of sight.

#### Mobile battery

Mobile high explosive unit that can serve as a power source for structures or
recharging vehicles. It's very vulnerable.

#### Armored hauler

Can store munitions or infantry. high capacity.

#### Light tank

Armored vehicle with a cannon. Sturdy against infantry, navigates terrain
fairly well. Line of sight is lower than infantry.

#### Heavy tank

Pricier, slower, tougher. uses more electricity than light tanks.

#### Helicopter

Scouts the battlefield quickly, but has only a light gun.

The helicopter is quite energy intensive and a player looking to use
helicopters would have to invest in mobile batteries for anything beyond
short range scouting around the main base.

Helicopters can land to conserve energy.
