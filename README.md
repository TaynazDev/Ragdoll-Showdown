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
| Use tool | **Left-click** (hold for auto-fire with the blaster) |
| Charge a throw (while grabbing) | Hold **right-click**, release to throw |
| Open / close a container | **E** (when standing next to it) |
| Hide inside an open container | **F** (press **E** or **F** again to come out) |
| NPC on / ragdoll dummy | **N** (or the 🤖 NPC button) |
| Escape when shut inside | Mash **E** |
| Reset the match | **R** |

---

## Tools

### 🔫 Blaster
A hitscan blaster that fires on a **2-second cooldown**. The first shot on someone standing launches them high into the air. You can keep shooting ragdolls to bounce them around.

### 🪴 Plant
Throws a potted plant in an arc that lands where you aim, on a **4-second cooldown**. If you aim at someone running, it leads the throw for you. Plants stay in the arena (up to 24) and can be pushed, shot and re-hit.

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

## Containers 🗑️ 🧊 🚪

Four containers sit around the arena, and they all work the same way:

- 🗑️ **Bin**: green wheelie bin with a lid
- 🧊 **Fridge**: tall, with a front door
- 🚪 **Wardrobe**: tall, with double doors that swing apart
- ❄️ **Chest freezer**: long and low, with a lid

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

1. Open the game on every device in Chrome or Edge.
2. On one computer, click **👥 Play with friends → Host a game** to get a **4-letter room code**.
3. On up to three other devices, click **👥 Play with friends**, enter the code and press **Join**. Each friend takes the next free slot (P2–P4) with their own outfit.

**How it works:**
- **Mode:** free-for-all, so everyone can shoot, plant and grab everyone, including the NPC.
- **The NPC:** picks a random player to attack.
- **Scoreboard:** shows hits for **you, every other player and the NPC**.
- **Reset:** pressing **R** on any device resets the match.
- **Leaving:** **Leave game** drops back to solo. The host's room stays open so friends can rejoin. A full room turns away a fifth player.

**Under the hood:**
- The **host runs all the physics**, so use the faster computer to host.
- Each guest sends its movement and actions to the host and receives the game state about 30 times a second.
- Players find each other through PeerJS's free public signalling server. After that, the game connects directly device-to-device, which works best on the **same Wi-Fi**.
- If PeerJS's server is unreachable, joining fails, but solo play still works.

> Movement needs a keyboard, so phones can watch and tap to shoot but can't walk.

---

## Tweaking

These constants near the top of the `<script>` in `index.html` are easy to change:

| Constant | Default | What it does |
|---|---|---|
| `COOLDOWN` | `{ blaster: 2.0, plant: 4.0 }` | Seconds between shots and plant throws |
| `HOLD_MAX` | `4.5` | How far in front of you a grabbed person is held |
| `CHARGE_TIME` | `1.5` | Seconds of right-click needed for a full-power throw |
| `GRAVITY` | `30` | World gravity |
| `ARENA` | `32` | Half-width of the arena |
| `CONTAINERS` | bin, fridge, wardrobe, freezer | Position, size, rotation and look of each container |

---

## Built with

- **[three.js](https://threejs.org/)** 0.160 for rendering
- **[cannon-es](https://pmndrs.github.io/cannon-es/)** 0.20 for physics and ragdolls
- **[PeerJS](https://peerjs.com/)** 1.5.4 for room codes and the peer-to-peer connection
- Character proportions and colours come from a blocky character modelled in Blender.

Everything else (models, animation, AI, networking and UI) is plain JavaScript in one self-contained file.