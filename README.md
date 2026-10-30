NOTE by Startide2025: THIS README.md has been auto-translated by Google Translate. I did not change it other than this note at the top.
I am hosting this in pokesurvivo.netlify.app for my friends, since pokesurvivor.com is blocked by admin, and I have to do a small edit in index.html to do that.
NO OTHER CODE WAS CHANGED. NO PROFIT IS ATTEMPTING TO BE MADE.
I have not checked the code (it is HEAVILY obfuscated by the owner), so I don't know if anything is broken.


# PokéSurvivor · Mystery Dungeon

A "bullet-heaven" game featuring Pokémon, in the style of *Survivor.io* and *Megabonk*. It utilizes sprites from *Pokémon Mystery Dungeon*, incorporates roguelike mechanics, and includes **966 Pokémon from all 9 generations**, along with shiny variants and a region-based gacha system. The music and sound effects were composed specifically for this game.

Built using HTML, CSS, and vanilla JavaScript on a 2D Canvas. No build process, no external dependencies, and **entirely local**—no internet connection is required to play.

> **Authorship**
>
> *PokéSurvivor* (including its source code and original music) was created by, and is the property of, **Jonathan Piera Torregrosa**—the owner of this GitHub account (JPTER78) and pokesurvivor.com. A Google copyright removal request (**4-2352000042234**) regarding *pokesurvivor.co* was submitted by me.

> **Crypto Disclaimer**
>
> *PokéSurvivor* has **no official cryptocurrency, token, or NFT**, and I have not created any. Any token using the game's name has been created by third parties. **I assume no responsibility for any purchases, sales, or investments** you may make involving such tokens; nothing presented here constitutes investment advice. The game is free and will remain free. ## Playing the Game

Double-click `index.html`. Create an account or log in as a guest, take the personality test, and head into the dungeon.

| Key | Action |
|---|---|
| `W` `A` `S` `D` / Arrow keys | Move |
| `1` `2` `3` `4` | Select active move |
| `Q` / `E` | Cycle through moves |
| `Esc` / `P` | Pause |

**On mobile or tablet** (in landscape mode): place your finger anywhere on the screen and drag to move (a joystick will appear where you touch). Tap an attack icon at the bottom to select it, and use the button in the top-right corner to pause. You can install the game as an app (select "Add to Home Screen"). In the **Settings** menu, you can adjust sound, graphics quality (including an automatic mode), damage numbers, screen shake intensity, and FPS settings, or manage your account.

Your Pokémon only uses its currently active move—unless you have a **link** (defeating a Legendary Pokémon allows you to fuse moves, letting you fire multiple attacks simultaneously from a single slot, up to a maximum of 4). Rocks, chests, and tall grass can be destroyed; walls and trees block enemy projectiles; water slows you down, while lava deals damage (to both you and your enemies).

The map contains **altars of power**, **healing springs**, **locked chests** (stay near them for a few seconds to open them), and **traps** that can also damage enemies. Occasionally, a **rift** may appear—enter it to face a **Legendary Pokémon** in a separate arena. There is a **type chart** (for instance, a Bubble Beam deals more damage to a Charmander), and occasionally, **weather conditions** (sun, rain, sandstorm, snow, fog) that boost certain types while weakening others.

There are daily (and weekly) **missions** that reward you with tickets and coins; **achievements** grant medals and titles, and your **profile** displays your 3 favorite Pokémon, your records, and your medals. During runs, you can find **items** (such as Leftovers or a Choice Band), and your moves can **evolve** once they reach their maximum level. Enemies have distinct personalities: some heal, others deploy shields, call for their pack, or signal their attacks with a warning indicator on the ground.

**Upgrades** are specific to each Pokémon. The **gacha** system uses **tickets** earned through gameplay (single tickets for standard Pokémon; 10-pull tickets for bosses and legendary Pokémon), and you "pull" by using a pixel-art slot machine.

Every enemy has a 1/4096 chance of being **shiny**—it will glow, and an arrow at the edge of the screen will point toward its location; if you defeat it, you get to keep it. In the gacha, there is a 1/100 chance for a pull to result in a shiny. In your collection, you can choose whether your companion appears in its normal or shiny form.

The music begins playing after the first click (as browsers prevent audio from playing automatically). You can adjust the volume or mute the game using the speaker icon in the top-right corner or via the pause menu.

Your save data is stored in the browser's `localStorage`; if you clear your site data, your progress will be lost.

The `videos/` folder contains gameplay recordings (including the in-game music) showing a boss battle, the capture of a wild shiny Pokémon, and a shiny pull from the gacha. ## Cloud Saving and Publishing

- **Database (Firebase):** Use an account (username + password or Google) to continue your game on any computer. 
Without an account, the game saves only within your browser, as before.
- **Play with friends (up to 4) and Leaderboards:** With a cloud account, you gain access to the **Friends** menu (add by nickname, invite to your lobby) and **Leaderboards** (track survival time—solo or in a group; view stats from today or all-time; filter by friends or specific Pokémon).
- **Publish for free on GitHub Pages:** [docs/PUBLISHING.md](docs/PUBLISHING.md).
- If you play on two computers simultaneously or while offline, your game data will **merge**: your collections are combined (you will never lose a Pokémon or a shiny), upgrades and statistics stay with the maximum, and coins and companion with the most recent version. Changes from another computer arrive live.

##License

Code under [PolyForm Noncommercial 1.0.0](LICENSE-NONCOMMERCIAL.md) from the 10-14-2026: can be used, studied and modified, but **not for commercial** (neither sell the game nor charge anything within it). The versions until commit `b297089` were published under MIT. The sprites (CC BY-NC 4.0), the source (OFL) and Pokémon brands have their own conditions: see [LICENSE](LICENSE) and [CREDITS.md](CREDITS.md). Fan project without intention of profit.

**The only official website is [pokesurvivor.com](https://pokesurvivor.com).** game is and will be free: if someone asks you to pay, it's not us.

## Structure

```
index.html screens + loading order
css/style.css Mysterious World style interface
assets/pokemon/{dex}/ sprite sheets PMD (Idle, Walk, Attack, Shoot, Charge, Hurt, Faint)
assets/pokemon/{dex}/s/ the same in shiny version
assets/fonts/ Pixelify Sans (OFL) and its version with redrawn numbers (tools/make_font.py)
js/ 
net/ social (nickname, friends, rooms), net (WebRTC + relay), 
coop (group play), ranking 
core/ util, db (saved), audio (synth + effects), input, 
sprites (PMD animator), camera 
data/ pokedex*, sprites-meta*, moves, starters (+ test), enemies, 
upgrades, music (scores) 
world/tiles (pixel art in code), world (terrain, objects, collisions) 
entities/ player, enemy, projectile, pickup, fx 
systems/combat, spawner, levelup, gacha 
ui/ icons (pixel art), ui, hud, login, test, menu, gacha-ui, run-ui, 
social-ui, ranking-ui 
game.js flow and main loop
tools/ scripts that regenerate files marked with *
```

`*` = generated. To redo them (you need Python 3 + Pillow and internet, just that one time):

```
python tools/fetch_sprites.py # normal and shiny sprites + js/data/sprites-meta.js 
# (~20 min; can be cut and restarted: use tools/cache/)
python tools/fetch_pokedex.py #js/data/pokedex.js
python tools/fetch_credits.py # CREDITS.md
```

##Implementation notes

- **PMD sprites.** Columns = frames, rows = 8 directions (Down, DownRight, 
Right, UpRight, Up, UpLeft, Left, DownLeft — checked with `-Offsets.png`). 
Each animation has its own frame size, so they are aligned by the 
**ground anchor** taken from `-Shadow.png`; Without that the sprite would jump when attacking.
- **Coordinates.** `(x, y)` of an entity are its **feet**. The collisions 
occur on the ground plane; the projectiles fly in that plane and are drawn 
elevated with their shadow below.
- **World.** 16×16 tile chunks: *data* (terrain, objects) are cheap and 
they are always generated; the *image* is baked at fine art resolution by writing on a 
`ImageData` (~4 ms per chunk in Chrome) and only for visible ones.
- **Performance.** Spatial grid of enemies rebuilt every frame. With 420 
enemies, simulation + full render ≈ 3 ms per frame in Chrome.
- **Metadata in `.js`, not `.json`**, because `fetch()` is locked in `file://`.
- **Shiny.** SpriteCollab shiny ones are the same drawing with another palette; are 
in `s/` and only 30 have different geometry (field `sa` in the metadata). 
Sheets are saved as PNG with exact palette: same image, half the weight.
- **Audio.** Web Audio synthesizer with advance scheduler (schedules 
notes 150 ms ahead) and convolution reverb with a generated impulse. 
The sheet music is in `js/data/music.js` in its own text format. 
The effects have minimal separation between repeats and a vocal cap, 
so that 400 enemies hit at once do not saturate.
- **Icons.** Character maps converted to canvas and data URLs; always to 
integer multiples of its size so that the pixel is clean.

## Credits and license

Sprites from [SpriteCollab](https://github.com/PMDCollab/SpriteCollab) under **CC BY-NC 4.0** — **non-commercial** use and with attribution; the list of artists is in [`CREDITS.md`](CREDITS.md). Pokémon is owned by Nintendo, Creatures Inc. and GAME FREAK. Non-profit fan project.
