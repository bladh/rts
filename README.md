# Unnamed scifi rts

## Setting

Gritty, used futuristic. Smaller factions battling it out over mining minerals
on some far away moon. The energy tech implies a more advanced civilization,
but ammunition and gear are relatively low tech, so most likely the technically
advanced stuff is either too expensive or too far away to be used in these
conflicts. Units are humble (mostly infantry, some tanks and some helicopters)

People depicted in this game are implied to be rather low cast in society, due
to being left fighting each other in some remote location (that mines some
basic ore and whoever is buying does not care who is selling).

Technology is crude and factions should be human. Not opposed to adding some
primitive alien race (like xenomorphs) that doesn't have any higher ambition
than eating.

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

## Factions design

See the [factions](factions.md) document for more information.

## Gameplay scenario

See the [gameplay scenario](scenario.md) document.

## How would supply lines work?

See the [supply lines](supply-lines.md) design document.
