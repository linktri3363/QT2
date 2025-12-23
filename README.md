# QuickTrade 2 (qt2)

A Windower addon for Final Fantasy XI that automates repetitive NPC trades.

**Author:** Valok@Asura  
**Version:** 1.0.0  
**Dependency:** Requires the **TradeNPC** addon to be loaded

## Installation

1. Place `qt2.lua` in your `Windower/addons/qt2/` folder
2. Load both required addons:
   ```
   //lua load tradenpc
   //lua load qt2
   ```
3. Optionally add both to your `Windower/scripts/init.txt` for auto-loading

## Commands

| Command | Description |
|---------|-------------|
| `//qt2` | Trade items to targeted NPC |
| `//qt2 loop` | Repeat trading until out of items |
| `//qt2 loop [#]` | Repeat trading a specific number of times |
| `//qt2 loop pull` | Loop and pull items from satchel/sack/case as needed |
| `//qt2 pull` | Pull items from storage for a single trade |
| `//qt2 autoconfirm` | Toggle auto-confirm for A.M.A.N. Reclaimer trades |
| `//qt2 ex` | Toggle example mode (shows commands without executing) |
| `//qt2 xyz` | Copy targeted NPC's coordinates to clipboard |
| `//qt2 spam [item]` | Repeatedly use an item (e.g., Forbidden Keys) |

## Usage

1. Target an NPC that's in the addon's database (or stand near one)
2. Run `//qt2` — it auto-detects what items you can trade based on the NPC
3. Use `//qt2 loop` to repeat trades automatically

## Supported Content

- **A.M.A.N. Reclaimer** — JSE Capes (with auto-confirm)
- **Domain Invasion** — Refractive Crystals
- **Geas Fete** — Pop items for Escha/Reisenjima NMs
- **Abyssea** — NM pop items and Sturdy Pyxis (Forbidden Keys)
- **Trust Ciphers** — Gondebaud and other cipher NPCs
- **Mog Garden** — Mineral Vein, Arboreal Grove
- **Field Gathering** — Mining, Logging, Harvesting points
- **Einherjar** — Entry Gate lamps
- **Various Quests** — Thick Shells, Tiger's Teeth, Fear of the Dark, etc.
- **Coffer/Chest Keys** — Multiple zones supported

## A.M.A.N. Reclaimer Auto-Confirm

When trading JSE capes to the A.M.A.N. Reclaimer, the addon will automatically confirm the "Would you like X reclamation marks?" prompt and re-target the NPC for continuous looping.

- Enabled by default
- Toggle with `//qt2 autoconfirm`

## Adding New NPCs/Items

Trade groups are defined at the bottom of the lua file. Use `//qt2 xyz` while targeting an NPC to copy its coordinates for adding new entries.

Basic format:
```lua
tradeGroup.YourGroupName = {
    NPC = {
        {name = "NPC Name"}
    },
    {item = "Item Name"}
}
```

### Item Tags

| Tag | Description |
|-----|-------------|
| `unique = true` | Trade only this item type, don't mix with others |
| `max = 1` | Maximum items per trade |
| `exact = 5` | Trade exactly this quantity |
| `group = "Name"` | Group items that must be traded together |
| `keyItem = "KI Name"` | Skip if key item already owned (Geas Fete) |
| `zone = "Zone Name"` | Only match NPC in this zone |

## Configuration

At the top of the lua file:
- `debug = true/false` — Show debug output in Windower console
- `exampleOnly = true/false` — Test mode without actual trades
- `autoConfirmReclaimer = true/false` — Auto-confirm Reclaimer trades

## License

Public Domain (Unlicense) — Free to copy, modify, and distribute.
