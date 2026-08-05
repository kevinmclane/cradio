# cradio — ZMK config

Personal [ZMK](https://zmk.dev) configuration for a Cradio/Sweep (34-key split), macOS only.

| | |
| --- | --- |
| Shield | `cradio_left` / `cradio_right` |
| Board | `nice_nano` (defaults to revision 2.0.0) |
| Host | macOS |
| ZMK | pinned commit, see [config/west.yml](config/west.yml) |
| Studio | enabled on the left (central) half |

---

## Layers

Four layers, indexed by definition order in [config/cradio.keymap](config/cradio.keymap).

| # | Name | Reached by |
| --- | --- | --- |
| 0 | `default_layer` | base |
| 1 | `navigation_layer` | hold `F`, `J`, `Z` or `/` |
| 2 | `symbol_number_layer` | hold `D` or `K` |
| 3 | `system_function_layer` | hold `S` or `L` |

Layers 1–3 sit on both hands so you can always reach a layer's keys with the
hand that isn't holding it down.

In the diagrams below, the **upper** label is the tap and the **lower** label is
the hold.

### 0 — Default

```text
╭───────┬───────┬───────┬───────┬───────╮   ╭───────┬───────┬───────┬───────┬───────╮
│   Q   │   W   │   E   │   R   │   T   │   │   Y   │   U   │   I   │   O   │   P   │
├───────┼───────┼───────┼───────┼───────┤   ├───────┼───────┼───────┼───────┼───────┤
│   A   │   S   │   D   │   F   │   G   │   │   H   │   J   │   K   │   L   │   '   │
│  Alt  │  L3   │  L2   │  L1   │       │   │       │  L1   │  L2   │  L3   │       │
├───────┼───────┼───────┼───────┼───────┤   ├───────┼───────┼───────┼───────┼───────┤
│   Z   │   X   │   C   │   V   │   B   │   │   N   │   M   │  Del  │ Bspc  │   /   │
│  L1   │ Ctrl  │       │       │ Ctrl  │   │       │       │       │       │  L1   │
╰───────┴───────┴───────┼───────┼───────┤   ├───────┼───────┼───────┴───────┴───────╯
                        │   ,   │ Space │   │ Space │   .   │
                        │  Gui  │ Shift │   │ Ctrl  │  Alt  │
                        ╰───────┴───────╯   ╰───────┴───────╯
```

`,` and `.` live on the thumbs; `;` is on layer 2.

### 1 — Navigation / mouse

Arrows and paging on the left, pointer and scroll on the right.

```text
╭───────┬───────┬───────┬───────┬───────╮   ╭───────┬───────┬───────┬───────┬───────╮
│  Tab  │ Home  │  Up   │  End  │ PgUp  │   │       │Scrl ← │       │Scrl → │Scrl ↑ │
├───────┼───────┼───────┼───────┼───────┤   ├───────┼───────┼───────┼───────┼───────┤
│  Esc  │ Left  │ Down  │ Right │ PgDn  │   │Mouse ←│Mouse ↓│Mouse ↑│Mouse →│Scrl ↓ │
│ Ctrl  │       │  Alt  │       │       │   │       │       │       │       │       │
├───────┼───────┼───────┼───────┼───────┤   ├───────┼───────┼───────┼───────┼───────┤
│       │       │ Ctrl` │  Esc  │       │   │       │       │       │       │       │
╰───────┴───────┴───────┼───────┼───────┤   ├───────┼───────┼───────┴───────┴───────╯
                        │  Gui  │ Shift │   │ Click │ Right │
                        │       │       │   │   L   │ click │
                        ╰───────┴───────╯   ╰───────┴───────╯
```

- Left/Right are plain keys so they autorepeat. `Alt` is parked on `Down`
  instead, for Option+arrow word/paragraph jumps.
- Thumbs stay as plain `Gui` / `Shift` here, so Shift+arrow selection works
  while the layer is held.
- ``Ctrl+` `` is the Raycast clipboard-history hotkey (matches Ditto on Windows).
- Mouse move keys follow vim `hjkl` order.

### 2 — Symbols / number pad

Number pad on the right hand, brackets on the left.

```text
╭───────┬───────┬───────┬───────┬───────╮   ╭───────┬───────┬───────┬───────┬───────╮
│   `   │       │       │       │       │   │   /   │   7   │   8   │   9   │   -   │
├───────┼───────┼───────┼───────┼───────┤   ├───────┼───────┼───────┼───────┼───────┤
│ Enter │   -   │       │   [   │   ]   │   │   *   │   4   │   5   │   6   │   =   │
├───────┼───────┼───────┼───────┼───────┤   ├───────┼───────┼───────┼───────┼───────┤
│       │       │       │   (   │   )   │   │   ;   │   1   │   2   │   3   │   \   │
╰───────┴───────┴───────┼───────┼───────┤   ├───────┼───────┼───────┴───────┴───────╯
                        │  Gui  │ Enter │   │ Enter │   0   │
                        │       │ Shift │   │ RShift│       │
                        ╰───────┴───────╯   ╰───────┴───────╯
```

- `-` appears twice on purpose: the left one is a coding roll, the right one is
  part of the number pad.
- Both thumbs carry a Shift here, so shifted symbols (`{`, `}`, `_`, `~`, `:`)
  are cross-hand.

### 3 — System / function

```text
╭───────┬───────┬───────┬───────┬───────╮   ╭───────┬───────┬───────┬───────┬───────╮
│ Reset │       │  Ins  │ Vol + │ BT 0  │   │       │  F7   │  F8   │  F9   │  F10  │
├───────┼───────┼───────┼───────┼───────┤   ├───────┼───────┼───────┼───────┼───────┤
│Studio │       │ PrtSc │ Vol - │ BT 1  │   │       │  F4   │  F5   │  F6   │  F11  │
│unlock │       │       │       │       │   │       │       │       │       │       │
├───────┼───────┼───────┼───────┼───────┤   ├───────┼───────┼───────┼───────┼───────┤
│Btldr  │       │       │BT Clr │ BT 2  │   │       │  F1   │  F2   │  F3   │  F12  │
╰───────┴───────┴───────┼───────┼───────┤   ├───────┼───────┼───────┴───────┴───────╯
                        │ Bspc  │  Del  │   │ Bspc  │  Del  │
                        ╰───────┴───────╯   ╰───────┴───────╯
```

> `Reset` and `Bootloader` sit next to each other on the left pinky, reachable
> from the left-hand layer key (`S`). Prefer entering this layer with `L`.

---

## Behaviors

| Name | Applies to | Tapping term | Quick tap | Prior idle |
| --- | --- | --- | --- | --- |
| `rpi` | letter keys (`A`, `X`, `B`, `Esc`, `Down`) | 200 ms | 200 ms | 100 ms |
| `rpit` | thumb keys | 200 ms | 200 ms | 50 ms |
| `&lt` (overridden) | home row layer taps | 200 ms | 200 ms | 125 ms |

All are `tap-preferred`. `require-prior-idle-ms` forces a tap when the previous
keypress was recent, which is what keeps fast rolls (`df`, `sd`, `jk`, `kl`)
from firing a layer instead of a letter. Stock `&lt` ships with neither
`quick-tap-ms` nor `require-prior-idle-ms`, so it is overridden at the top of
the keymap.

### Pointer tuning

```dts
#define ZMK_POINTING_DEFAULT_MOVE_VAL 1400   // top speed, not constant speed
&mmv { time-to-max-speed-ms = <700>; };      // stock is 300
```

`MOVE_VAL` sets the speed the pointer *ramps up to*, and `acceleration-exponent`
(left at the stock `1`) curves the ramp. With the stock 300 ms ramp you hit top
speed almost immediately, so raising `MOVE_VAL` alone just makes short
corrections twitchy. The longer ramp keeps brief taps slow and precise while
held movement still crosses the screen quickly.

Tuning order: if short nudges overshoot, raise `time-to-max-speed-ms` before
touching `MOVE_VAL`. If long traversals drag, raise `MOVE_VAL` and leave the
ramp alone.

Scroll needs no ramp — `&msc` ships `acceleration-exponent = <0>` (constant), so
`ZMK_POINTING_DEFAULT_SCRL_VAL 20` is a flat doubling of the default.

---

## Config notes

Highlights from [config/cradio.conf](config/cradio.conf):

- **Connection interval 15 ms min/max.** macOS and iOS reject connection
  parameter requests below 15 ms, so a lower minimum just gets renegotiated.
- **2M PHY disabled.** Trades throughput for connection stability.
- **Battery proxy on.** `..._FETCHING` pulls the peripheral's level into the
  central; `..._PROXY` then exposes it to macOS as a second Battery service, so
  both halves show up.
- **No TX power boost.** Radio runs at the stock 0 dBm.
- **ZMK pinned to a commit** rather than tracking `main`, so upstream churn
  can't break a build. Bump it deliberately.

---

## Build & flash

Pushing to this repo runs the GitHub Actions build in
[.github/workflows/build.yml](.github/workflows/build.yml). Download the
`firmware` artifact from the run.

To flash: double-tap the reset button on a half to mount it as a USB drive, then
copy the matching `.uf2` onto it. Flash both halves after a keymap change.

Locally:

```sh
west build -s zmk/app -b nice_nano -- \
  -DSHIELD=cradio_left -DZMK_CONFIG="$PWD/config" \
  -DSNIPPET=studio-rpc-usb-uart
```

## ZMK Studio

Studio runs on the **left half only** (it's the central). It needs two things,
both already in place:

1. `CONFIG_ZMK_STUDIO=y` in [config/cradio.conf](config/cradio.conf)
2. `snippet: studio-rpc-usb-uart` on the left build in
   [build.yaml](build.yaml) — this supplies the RPC transport over USB. Without
   it Studio is compiled in but has no way to connect.

Connect the left half over USB, open [ZMK Studio](https://zmk.studio), then
press **Studio unlock** (layer 3, left home row) to allow edits.
