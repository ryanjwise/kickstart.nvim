# ZSA Voyager Keyboard Layout Reference

**Purpose**: Reference for configuring Neovim keybindings that work well with custom keyboard layers

**Last Updated**: 2025-12-01 (from Oryx export)

---

## Layer Overview

- **Layer 0**: Selection layer (switches to other layers) - NOT USED on this Mac
- **Layer 1**: QWERTY macOS (⭐ BASE LAYER on this computer) - BLUE
- **Layer 2**: QWERTY (Alt variant, Linux/Windows-style) - CYAN
- **Layer 3**: QWERTY (Another variant) - RED
- **Layer 4**: Symbols & Numbers (accessed via left thumb) - MIXED COLORS
- **Layer 5**: Navigation & Media (accessed via right thumb) - ORANGE/PINK
- **Layer 6**: Gaming layer - GREEN/BLUE

**NOTE**: On this Mac, the keyboard boots directly into Layer 1, not Layer 0.

---

## Layer 1: Primary QWERTY (macOS-style)
**LED Color**: Blue
**Access**: `TO(1)` from Layer 0

### Layout Diagram
```
┌─────────┬────┬────┬────┬────┬────┐       ┌────┬────┬────┬────┬────┬─────┐
│ =/ESC   │ 1  │ 2  │ 3  │ 4  │ 5  │       │ 6  │ 7  │ 8  │ 9  │ 0  │  -  │
│(TD)     │    │    │    │    │    │       │    │    │    │    │    │     │
├─────────┼────┼────┼────┼────┼────┤       ├────┼────┼────┼────┼────┼─────┤
│  TAB    │ Q  │ W  │ E  │ R  │ T  │       │ Y  │ U  │ I  │ O  │ P  │  \  │
├─────────┼────┼────┼────┼────┼────┤       ├────┼────┼────┼────┼────┼─────┤
│ L-SHIFT │ A  │ S  │ D  │ F  │ G  │       │ H  │ J  │ K  │ L  │ ;  │ '/" │
│         │    │    │    │    │    │       │    │    │    │    │    │SHIFT│
├─────────┼────┼────┼────┼────┼────┤       ├────┼────┼────┼────┼────┼─────┤
│ L-GUI   │Z/  │X/  │ C  │ V  │ B  │       │ N  │ M  │ ,  │./ │// │R-CTL│
│  (⌘)    │ALT │CTL │    │    │    │       │    │    │    │CTL │ALT │     │
└─────────┴────┴────┴────┴────┴────┘       └────┴────┴────┴────┴────┴─────┘
                    ┌────────┬────────┐   ┌────────┬────────┐
                    │ SPACE/ │ ENTER/ │   │  BSPC  │ SPACE/ │
                    │ Layer4 │  CTRL  │   │        │ Layer5 │
                    └────────┴────────┘   └────────┴────────┘
```

### Key Features:
- **Tap Dance (top-left)**: Tap = `=`, Hold = `ESC`
- **Left Thumb**: Space (tap) / Layer 4 - Symbols (hold)
- **Right Thumb**: Backspace, Space (tap) / Layer 5 - Navigation (hold)
- **Home Row Mods**:
  - Left: Z/Alt, X/Ctrl
  - Right: ./Ctrl, //Alt, '/Shift
- **macOS Style**: Left GUI (⌘) in bottom-left corner

### IMPORTANT for Neovim:
- `<leader>` is probably Space → This means Layer 4 access via HOLD
- Right thumb Space also goes to Layer 5 when held
- ESC requires HOLDING the tap-dance key (not quick access!)

---

## Layer 4: Symbols & Numbers
**LED Color**: Mixed (purple/cyan highlights)
**Access**: Hold left thumb Space from Layer 1/2/3

### Layout Diagram
```
┌─────────┬────┬────┬────┬────┬────┐       ┌────┬────┬────┬────┬────┬─────┐
│  ESC    │ F1 │ F2 │ F3 │ F4 │ F5 │       │ F6 │ F7 │ F8 │ F9 │F10 │ F11 │
├─────────┼────┼────┼────┼────┼────┤       ├────┼────┼────┼────┼────┼─────┤
│    `    │ ~  │ @  │ #  │ $  │ %  │       │ 7  │ 8  │ 9  │ -  │ /  │ F12 │
├─────────┼────┼────┼────┼────┼────┤       ├────┼────┼────┼────┼────┼─────┤
│  ----   │ `  │ <  │ >  │ (  │ )  │       │ 4  │ 5  │ 6  │ +  │ *  │BSPC │
├─────────┼────┼────┼────┼────┼────┤       ├────┼────┼────┼────┼────┼─────┤
│  ----   │----│ [  │ ]  │ {  │ }  │       │ 1  │ 2  │ 3  │ .  │ =  │ENTER│
└─────────┴────┴────┴────┴────┴────┘       └────┴────┴────┴────┴────┴─────┘
                    ┌────────┬────────┐   ┌────────┬────────┐
                    │  ----  │  ----  │   │  ----  │   0    │
                    └────────┴────────┘   └────────┴────────┘
```

### Key Features:
- **Function Keys**: F1-F12 on top row
- **Symbols**: Left side has brackets, angles, special chars
- **Numpad**: Right side is 7-8-9 / 4-5-6 / 1-2-3 / 0
- **Math Operators**: +, -, *, /, = easily accessible

### IMPORTANT for Neovim:
- Numbers require Layer 4 access (not on base layer)
- Symbol-heavy keybindings (`<leader>1`, `<leader>[`) need layer switching
- Consider avoiding number-based keybindings for frequent operations

---

## Layer 5: Navigation & Media
**LED Color**: Orange/Pink
**Access**: Hold right thumb Space from Layer 1/2/3

### Layout Diagram
```
┌─────────┬────┬────┬────┬────┬────┐       ┌────┬────┬────┬────┬────┬─────┐
│RGB TOGL │TCOL│RGBM│RGBS│VAL-│VAL+│       │----│----│----│----│----│BOOT │
├─────────┼────┼────┼────┼────┼────┤       ├────┼────┼────┼────┼────┼─────┤
│  ----   │----│VOL-│VOL+│MUTE│----│       │PGUP│HOME│ UP │END │----│ --- │
├─────────┼────┼────┼────┼────┼────┤       ├────┼────┼────┼────┼────┼─────┤
│  ----   │PREV│NEXT│STOP│PLAY│----│       │PGDN│LEFT│DOWN│RGHT│----│ --- │
├─────────┼────┼────┼────┼────┼────┤       ├────┼────┼────┼────┼────┼─────┤
│  ----   │----│----│RED │YLLW│CYAN│       │----│C-S-│ C- │----│----│ TO0 │
│         │    │    │LED │LED │LED │       │    │ TAB│ TAB│    │    │     │
└─────────┴────┴────┴────┴────┴────┘       └────┴────┴────┴────┴────┴─────┘
                    ┌────────┬────────┐   ┌────────┬────────┐
                    │  ----  │  ----  │   │  ----  │  ----  │
                    └────────┴────────┘   └────────┴────────┘
```

### Key Features:
- **Navigation**: Arrow keys (right hand, JKL; position)
- **Page Nav**: Home, End, PgUp, PgDn
- **Media**: Volume, Play/Pause, Next/Prev track
- **RGB Controls**: Left side for keyboard lighting
- **Tab Switching**: Ctrl+Tab / Ctrl+Shift+Tab (browser/app tabs)
- **Exit**: `TO(0)` returns to layer selection

### IMPORTANT for Neovim:
- Arrow keys require Layer 5 hold
- Vim navigation (hjkl) conflicts with needing to hold Space
- This is why learning hjkl in Neovim is CRITICAL for your setup
- Home/End/PgUp/PgDn also on Layer 5

---

## Layer 6: Gaming Layer
**LED Color**: Green/Blue
**Access**: `TO(6)` from Layer 0

### Layout Diagram
```
┌─────────┬────┬────┬────┬────┬────┐       ┌────┬────┬────┬────┬────┬─────┐
│  ESC    │ 1  │ 2  │ 3  │ 4  │BSPC│       │ 6  │ 7  │ 8  │ 9  │ 0  │  -  │
├─────────┼────┼────┼────┼────┼────┤       ├────┼────┼────┼────┼────┼─────┤
│  TAB    │ Q  │ W  │ E  │ R  │ T  │       │ Y  │ U  │ I  │ O  │ P  │  \  │
├─────────┼────┼────┼────┼────┼────┤       ├────┼────┼────┼────┼────┼─────┤
│ L-SHIFT │ A  │ S  │ D  │ F  │ G  │       │ H  │ J  │ K  │ L  │ ;  │  '  │
├─────────┼────┼────┼────┼────┼────┤       ├────┼────┼────┼────┼────┼─────┤
│ L-CTRL  │Z/  │ X  │ C  │ V  │ B  │       │ N  │ M  │ ,  │ .  │ /  │ --- │
│         │ALT │    │    │    │    │       │    │    │    │    │    │     │
└─────────┴────┴────┴────┴────┴────┘       └────┴────┴────┴────┴────┴─────┘
                    ┌────────┬────────┐   ┌────────┬────────┐
                    │ SPACE  │ ENTER  │   │  ----  │  TO5   │
                    └────────┴────────┘   └────────┴────────┘
```

### Key Features:
- Numbers accessible on base layer (1-4 on left, gaming standard)
- Pure tap keys (no dual-function confusion during gaming)
- ESC easily accessible (top-left)
- Right thumb goes to Layer 5, not Layer 0

---

## Critical Insights for Neovim Configuration

### 1. **ESC is NOT easily accessible**
- Tap-dance key requires HOLD for ESC on Layer 1/2/3
- Consider mapping `jk` or `jj` to ESC in Neovim
- Or use `Ctrl+[` which should work with your X/Ctrl mod

### 2. **Numbers require layer access**
- `<leader>1`, `<leader>2` type bindings need two hand positions
- Prefer alphabetic keybindings for frequent operations
- This aligns with your "reduced keyboard" preferences

### 3. **Arrow keys vs hjkl**
- Arrow keys are on Layer 5 (right thumb hold)
- Using hjkl in Neovim is ESSENTIAL for your layout
- You can't easily use arrows without breaking flow

### 4. **Space as Leader**
- Left thumb Space is likely your `<leader>` key
- But holding Space = Layer 4 access
- This is actually perfect for Neovim leader combos!
- Example: `<leader>f` = Space+F = Layer 4 + F finger stays in place

### 5. **Modifier Combinations**
- Home row mods mean some Ctrl/Alt combos feel different
- `Ctrl+w` in Neovim requires X/Ctrl hold + W press
- Consider your muscle memory when adding custom keybindings

### 6. **Thumb Cluster is Prime Real Estate**
- Left thumb: Space / Layer 4 toggle
- Right thumb: Backspace / Layer 5 toggle
- These are your most accessible keys
- Use them for high-frequency Neovim operations

---

## Quick Reference: Accessibility Tiers

### Tier 1: Base Layer - No Hold Required
- All letter keys (QWERTY)
- Tab, Shift, Ctrl, Alt, GUI (modifiers)
- Left thumb: Space, Enter
- Right thumb: Backspace

### Tier 2: Single Layer Hold
- **Layer 4** (left thumb hold): Symbols, brackets, F-keys, numbers
- **Layer 5** (right thumb hold): Navigation, arrows, media, page nav

### Tier 3: Difficult Access
- Numbers 1-0 (requires Layer 4)
- Arrow keys (requires Layer 5)
- ESC (tap-dance hold on Layer 1/2/3)

### Tier 4: Two-Hand Layer Switching
- Layer 0 combinations (requires explicit layer switch)
- RGB controls (Layer 5)
- Gaming layer (requires TO(6) toggle)

---

## Recommended Neovim Keybinding Strategy

Based on your keyboard layout:

1. **Use alphabetic `<leader>` combos** instead of numbered ones
2. **Map `jk` or `jj` to ESC** for quick normal mode access
3. **Leverage hjkl heavily** - arrow keys are not accessible
4. **Keep frequently used commands in Tier 1/2** accessibility
5. **Consider thumb cluster fatigue** - Space is doing double duty
6. **Avoid complex Ctrl+number combos** - requires two layers

---

## Notes
- TD = Tap Dance (tap vs hold behavior)
- MT = Mod-Tap (modifier when held, key when tapped)
- LT = Layer-Tap (layer when held, key when tapped)
- ---- = Transparent (passes through to lower layer)
- Numbers in parentheses = Layer numbers for TO() switching
