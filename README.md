# Ragdoll Showdown

A chaotic first-person physics brawler in a single HTML file. You and a blocky NPC knock each other around with a blaster, flying potted plants and your bare hands. Anyone who takes a hit goes full ragdoll, and the loser might end up in the bin, the fridge, the wardrobe or the chest freezer.

Play solo against the NPC, or invite up to three friends for a five-way free-for-all (4 players + the NPC).

---

## Getting started

1. Open the game in **Chrome or Edge**: https://taynazdev.github.io/Ragdoll-Showdown/
2. Click the scene to lock the mouse, then start causing trouble.

> An internet connection is needed the first time, because the page loads three.js, cannon-es and PeerJS from a CDN.

---

## Controls

| Action | Key / mouse |
|---|---|
| Move | **W A S D** or arrow keys |
| Jump | **Space** |
| Sprint | **Shift** |
| Look around | Move the mouse (once locked) · right-drag if mouse lock is blocked |
| Free the mouse | **Esc** |
| Blaster | **1** |
| Plant | **2** |
| Grab | **3** |
| Sniper | **4** (hold **right-click** to use the scope) |
| Use tool | **Left-click** (hold for auto-fire with the blaster) |
| Charge a throw (while grabbing) | Hold **right-click**, release to throw |
| Open / close a container | **E** (when standing next to it) |
| Hide inside an open container | **F** (press **E** or **F** again to come out) |
| NPC on / ragdoll dummy | **N** (or the 🤖 NPC button) |
| Escape when shut inside | Mash **E** |
| Reset the match | **R** |

---

### Touch controls 📱

On a phone or tablet, the touch controls appear as soon as you touch the screen:

| Control | What it does |
|---|---|
| **Joystick** (bottom-left) | Walk. Push it all the way to sprint. |
| **Drag anywhere else** | Look around |
| **Big button** (🔫 / 🪴 / ✋) | Use your current tool (hold for auto-fire or to keep holding someone) |
| **⤒** | Jump |
| **E** / **F** | Open or close containers / hide |
| **🔭** | Appears with the sniper: tap to look down the scope, tap again to stop |
| **💪** | Appears while you're holding someone: hold it to charge a throw, let go to throw |

Pick tools with the buttons along the top. You aim with the crosshair in the middle of the screen.

---

## Tools

### 🔫 Blaster
A hitscan blaster that fires on a **2-second cooldown**. The first shot on someone standing launches them high into the air. You can keep shooting ragdolls to bounce them around.

### 🪴 Plant
Throws a potted plant in an arc that lands where you aim, on a **4-second cooldown**. If you aim at someone running, it leads the throw for you. Plants stay in the arena (up to 24) and can be pushed, shot and re-hit.

### 🎯 Sniper
A long-range rifle with a **3-second cooldown**. Each shot hits about twice as hard as the blaster and sends people flying.
- **Hold right-click** to look down the scope. The view zooms right in, the scope's crosshairs appear and aiming slows down so you can line up long shots. Let go to stop. (On touch, tap **🔭** to scope in and out.)

### ✋ Grab
A first-person arm picks people up. You can grab from up to 14 units away, but they're pulled in and held at most 4.5 units in front of you.
- **Hold right-click** to charge a throw. A *THROW POWER* bar fills over 1.5 seconds: a quick tap is a gentle toss, and a full charge sends them flying.
- **Let go of left-click** to drop them, or flick the camera as you release to fling them.

Cooldown bars appear under the crosshair and along the bottom of each tool button.

---

## Ragdolls

Every character is a six-part physics ragdoll: head, torso, two arms and two legs, connected by limited joints.

- Getting hit by a shot, a plant or a throw turns a character into a ragdoll.
- When **you** get ragdolled, the camera pops out to **third person** so you can watch yourself tumble. Moving the mouse orbits the camera and scrolling zooms.
- Once a ragdoll settles, it blends smoothly back to standing.

---

## The NPC

The NPC wanders the arena and attacks every few seconds. A red banner warns the player he's going after:

| Warning | What happens |
|---|---|
| *He's aiming at you!* | He raises his purple blaster and fires three slightly inaccurate shots. |
| *Incoming plant!* | He winds up and lobs a plant at where you're heading. |
| *He's coming to grab you!* | He sprints over, grabs you, drags your ragdoll away and flings you. |
| *He's coming to grab you while you're down!* | Knocked over? He'll often come and pick you up. |
| *He's taking you to the bin! / fridge / wardrobe / freezer* | He carries you to a free container, shoves you inside and shuts it. |
| *He saw you hide!* | He spotted you climbing in. He runs over, yanks it open, drags you out and might stuff you in a different container. |
| *BOO! He was hiding in there!* | Sometimes he hides in a container himself, then jumps out on whoever comes close (or opens it) and chases them. |

He shouts when he gets hit, panics and runs off after getting back up, and jumps out of any container he lands in.

Press **N** (or the **🤖 NPC** button) to switch him to a **ragdoll dummy**: he goes limp, stops attacking and stays a ragdoll for you to shoot, grab and throw around. Press it again to wake him up.

---

## The house 🏠

A two-storey house stands in the back-left of the arena, with a garden behind it.

- **Ground floor:** kitchen (fridge and chest freezer), living room (sofa, coffee table, TV) and a dining table with chairs.
- **Doors:** there are front, side and back doors. Walk into a door to push it open (it swings away from you), and it swings shut again once nobody is touching it. You can also throw people through the open windows.
- **Upstairs:** climb the stairs along the right-hand wall. Up there are a bedroom (bed, nightstand and **two wardrobes**), a desk, a bookshelf and a second sofa. The stairwell has a railing, but you can still fall down it.
- The **bin** stands outside, next to the house's right-hand wall.
- **The garden** (out the back door, or round the side) has grass, flower beds, trees, a picnic table, garden gnomes and a **barbecue** you can shove people into.
- The roof disappears while you're indoors so you can see what's going on.

### Furniture 🛋️

Every piece of furniture is a physics object:

- **Walk into it** to push it around.
- **Grab it** (✋ tool), carry it and drop it. Heavy pieces like the bed and sofa are slower to throw.
- **Throw it at someone** (hold right-click to charge) to knock them into a ragdoll. It counts as a hit.
- **Shoot it** to send it skidding. For a couple of seconds after being shot it knocks over anyone it hits too.

**R** puts all the furniture back where it started.

---

## The towers 🗼 🏙️

Two really tall buildings both have a spiral staircase round an open shaft:

- **The stone tower** (60 units tall) stands in the far right-hand corner, with a battlemented lookout and a flag on top.
- **The skyscraper** (120 units tall) stands in the near left-hand corner. It is modern, with a blue glass curtain wall, steel mullions, floor bands, an entrance canopy and an antenna with a blinking red light on the roof. Inside, a concrete ramp spirals twelve times up to the roof.

- Walk in through the doorway and climb the **spiral staircase**. Over the last half-turn the top is open, so you come out onto the lookout or the roof.
- The middle is an **open shaft**. Step off the inner edge of the stairs, or jump from the top, and you **ragdoll all the way down**.
- The stone tower has windows up the sides that let you (or anyone you throw) fly out.
- The NPC can follow you up the stairs.

**Falling in general:** any big fall turns you into a ragdoll, so going down the tower shaft or off the edge of the house's stairwell sends you tumbling.

---

## Containers 🗑️ 🧊 🚪

Six containers (the bin outside, the barbecue in the garden, the fridge and freezer downstairs, and two wardrobes upstairs) all work the same way:

- 🗑️ **Bin**: green wheelie bin with a lid
- 🧊 **Fridge**: tall, with a front door
- 🚪 **Wardrobes** (×2, upstairs): tall, with double doors that swing apart
- ❄️ **Chest freezer**: long and low, with a lid
- 🔥 **Barbecue** (in the garden): a grill with glowing coals and a lid

- They all start **closed**. Press **E** next to one to open it.
- Throw or drop people in, then press **E** next to it to close it.
- Anyone shut inside is **stuck**: they can't get up, and shots and grabs can't reach them through the walls.
- Escaping depends on who's inside:
  - **Players** mash **E** to push it open (6 presses), or burst out on their own after 15 seconds.
  - **The NPC** bangs on it and bursts out after about 5 seconds.
- Once it's open, whoever's inside stands up and **jumps out** the front.
- **Hiding:** stand next to an open, empty container and press **F** to climb in and shut it behind you. If the NPC **sees you climb in** (you're close enough, in front of him and not behind another container), he comes to drag you back out. If he didn't see, he won't come after you, and you can stay as long as you like. Press **E** or **F** to come out. If someone opens it, you've been found!

---

## Playing with friends (up to 4 players)

You can play on the same Wi-Fi **or across the internet** with friends on different networks.

1. Open the game in Chrome or Edge.
2. Click **👥 Play with friends → Host a game**. You get a **4-letter room code** and an **invite link**. Press **Copy link**.
3. Send the link to up to three friends. Opening it starts the game and joins your room automatically. (They can also open the game, click **👥 Play with friends**, enter the code and press **Join**.) Each friend takes the next free slot (P2–P4) with their own outfit.

**How it works:**
- **Mode:** free-for-all, so everyone can shoot, plant and grab everyone, including the NPC.
- **The NPC:** picks a random player to attack.
- **Scoreboard:** shows hits for **you, every other player and the NPC**.
- **Reset:** pressing **R** on any device resets the match.
- **Leaving:** **Leave game** drops back to solo. The host's room stays open so friends can rejoin. A full room turns away a fifth player.

**Under the hood:**
- The **host runs all the physics**, so use the faster computer and the better connection to host. Keep the host's game tab in front: browsers pause background tabs, which freezes the game for everyone.
- Each guest sends its movement and actions to the host and receives the game state about 30 times a second. Only furniture that moved is sent.
- Players find each other through PeerJS's free public matchmaking server. The game then connects device-to-device, using STUN servers to find a way through each home router.
- When a direct connection isn't possible (some strict routers, office or school networks and mobile data), it falls back to PeerJS's free **TURN relay**, which passes the traffic along.
- **Still can't connect?** In the dialog, open **Can't connect? Use your own relay server** and enter a TURN server you have access to (address, username and password). Everyone in the game should add the same one. It's saved in that browser only.
- **Invite links** point at the public copy of the game (https://taynazdev.github.io/Ragdoll-Showdown/) when you host from a local file or a local dev server, so they work for friends elsewhere. That public copy needs this version of the game, so push it to GitHub Pages first.
- If PeerJS's server is unreachable, online play fails, but solo play still works.

> On phones and tablets, touch controls appear as soon as you touch the screen (see **Touch controls** above).

---

## Tweaking

These constants near the top of the `<script>` in `index.html` are easy to change:

| Constant | Default | What it does |
|---|---|---|
| `COOLDOWN` | `{ blaster: 2.0, plant: 4.0, sniper: 3.0 }` | Seconds between shots and plant throws |
| `HOLD_MAX` | `4.5` | How far in front of you a grabbed person is held |
| `CHARGE_TIME` | `1.5` | Seconds of right-click needed for a full-power throw |
| `GRAVITY` | `30` | World gravity |
| `ARENA` | `44` | Half-width of the arena |
| `CONTAINERS` | bin, fridge, 2 wardrobes, freezer, barbecue | Position, size, rotation, floor and look of each container |
| `HOUSE` / `STAIRS` | corner house, 9-unit floors | House size and where the stairs run |
| `TOWERS` | stone tower (60 tall), skyscraper (120 tall) | Position, size, height and how steep each spiral is |

---

## Built with

- **[three.js](https://threejs.org/)** 0.160 for rendering
- **[cannon-es](https://pmndrs.github.io/cannon-es/)** 0.20 for physics and ragdolls
- **[PeerJS](https://peerjs.com/)** 1.5.4 for room codes and the peer-to-peer connection
- Character proportions and colours come from a blocky character modelled in Blender.

Everything else (models, animation, AI, networking and UI) is plain JavaScript in one self-contained file.
