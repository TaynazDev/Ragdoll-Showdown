# Ragdoll Showdown

A chaotic first-person physics brawler in a single HTML file. You and a blocky NPC knock each other around with a blaster, flying potted plants and your bare hands. Anyone who takes a hit goes full ragdoll, and the loser might end up in the bin.

Play solo against the NPC, or invite a friend on another computer for a three-way free-for-all.

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
| Open / close the bin | **E** (when standing next to it) |
| Escape a closed bin | Mash **E** |
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
| *He's taking you to the bin!* | He carries you to the bin, hoists you overhead, lobs you in and slams the lid. |

He shouts when he gets hit, panics and runs off after getting back up, and jumps out of the bin when he lands in it.

---

## The bin 🗑️

A green wheelie bin with a hinged lid sits in the arena.

- Throw or drop people in, then press **E** next to it to close the lid.
- Anyone inside a closed bin is **stuck**: they can't get up, and shots and grabs can't reach them through the walls.
- Escaping depends on who's inside:
  - **Players** mash **E** to push the lid open (6 presses), or burst out on their own after 15 seconds.
  - **The NPC** bangs on the lid and bursts out after about 5 seconds.
- Once the lid is open, whoever's inside stands up and **jumps out** over the front wall.

---

## Playing with a friend

1. Copy `ragdoll.html` to both computers and open it in Chrome or Edge.
2. On one computer, click **👥 Play with a friend → Host a game** to get a **4-letter room code**.
3. On the other, click **👥 Play with a friend**, enter the code and press **Join**.

**How it works:**
- **Mode:** free-for-all, so everyone can shoot, plant and grab everyone, including the NPC.
- **The NPC:** picks a random player to attack.
- **Scoreboard:** shows hits for **You · Friend · NPC**.
- **Reset:** pressing **R** on either computer resets the match.
- **Leaving:** **Leave game** drops back to solo. The host's room stays open so the friend can rejoin.

**Under the hood:**
- The **host runs all the physics**, so use the faster computer to host.
- The guest sends its movement and actions to the host and receives the game state about 30 times a second.
- Players find each other through PeerJS's free public signalling server. After that, the game connects directly device-to-device, which works best on the **same Wi-Fi**.
- If PeerJS's server is unreachable, joining fails, but solo play still works.

> Movement needs a keyboard, so phones can watch and tap to shoot but can't walk.

---

## Tweaking

These constants near the top of the `<script>` in `ragdoll.html` are easy to change:

| Constant | Default | What it does |
|---|---|---|
| `COOLDOWN` | `{ blaster: 2.0, plant: 4.0 }` | Seconds between shots and plant throws |
| `HOLD_MAX` | `4.5` | How far in front of you a grabbed person is held |
| `CHARGE_TIME` | `1.5` | Seconds of right-click needed for a full-power throw |
| `GRAVITY` | `30` | World gravity |
| `ARENA` | `22` | Half-width of the arena |
| `BIN` | `{ x: -13, z: 6, … }` | Bin position and size |

---

## Built with

- **[three.js](https://threejs.org/)** 0.160 for rendering
- **[cannon-es](https://pmndrs.github.io/cannon-es/)** 0.20 for physics and ragdolls
- **[PeerJS](https://peerjs.com/)** 1.5.4 for room codes and the peer-to-peer connection
- Character proportions and colours come from a blocky character modelled in Blender.

Everything else (models, animation, AI, networking and UI) is plain JavaScript in one self-contained file.