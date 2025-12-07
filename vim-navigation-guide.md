# Vim Navigation Mastery Guide

A progressive learning path for navigating codebases in Vim/Neovim with Kickstart.nvim.

**Setup Notes:**
- Using **Kickstart.nvim** (not LazyVim) - simpler, more direct keybindings
- Reduced size keyboard with layers - prefer alphanumeric keybinds over symbols/numbers

---

## Table of Contents

1. [Why You Reach for VSCode](#why-you-reach-for-vscode)
2. [The Mindset Shift](#the-mindset-shift)
3. [Understanding LazyVim's Keybinding System](#understanding-lazyvims-keybinding-system)
4. [The Core 15 - Start Here](#the-core-15---start-here)
5. [Phase 1: Foundation (Week 1-2)](#phase-1-foundation-week-1-2)
6. [Phase 2: Code-Level Navigation (Week 3-4)](#phase-2-code-level-navigation-week-3-4)
7. [Phase 3: Project-Wide Navigation (Week 5-6)](#phase-3-project-wide-navigation-week-5-6)
8. [Phase 4: Advanced Patterns (Week 7-8)](#phase-4-advanced-patterns-week-7-8)
9. [Customizing Direct Keybindings](#customizing-direct-keybindings)
10. [Learning Strategies](#learning-strategies)
11. [Common Pitfalls & Solutions](#common-pitfalls--solutions)
12. [The 30-Day Challenge](#the-30-day-challenge)
13. [Resources](#resources)

---

## Why You Reach for VSCode

You're reaching for VSCode because it **shows you everything visually**:
- Sidebar with all files visible
- Click to navigate
- Ctrl+P to fuzzy find
- Breadcrumbs showing location
- Tabs showing open files

**The Vim mindset shift**: Instead of **seeing** where to go, you **think** where to go and let the editor take you there instantly.

---

## The Mindset Shift

**VSCode thinking**: "Where is the file? Let me click to it."

**Vim thinking**: "What am I looking for? Let me search for it."

The power of vim isn't in having everything visible - it's in being able to **instantly jump to what you're thinking about** without taking your hands off the keyboard.

---

## Understanding Kickstart's Keybinding System

### Direct Keybindings

Kickstart keeps it simple - most keybindings execute immediately:

```vim
gd                " Go to definition
gr                " Go to references
K                 " Show hover documentation
<leader><space>   " Find files
<leader>b         " List buffers
<leader>sg        " Live grep
```

Which-key shows hints after `<leader>` but commands still work in 2 keystrokes.

---

## The Core 15 - Start Here

Master these 15 keybindings FIRST. They require no intermediary menus and cover 80% of navigation needs:

```
═══════════════════════════════════
        VIM CORE 15 KEYBINDS
═══════════════════════════════════

FILES:
  <leader><space>  Find file
  <S-h> / <S-l>    Switch buffers

CODE NAVIGATION:
  gd               Go to definition
  gr               Go to references
  K                Show docs
  <C-o> / <C-i>    Jump back/forward

IN-FILE:
  /word            Search
  *                Search word under cursor
  n / N            Next/prev match
  { / }            Jump paragraphs

WINDOWS:
  <C-h/j/k/l>      Move between splits
═══════════════════════════════════
```

**Challenge**: Use ONLY these 15 keybindings for one week. Master them completely before moving on.

---

## Phase 1: Foundation (Week 1-2) - "Stop Using the Mouse"

### Core Principle
**Navigation should be thought-driven, not sight-driven.**

### Essential Keybindings to Memorize

**File Navigation:**
```vim
<leader><space>  " Find files
<leader>sg       " Live grep - search inside files
<leader>b        " List open buffers
<leader>/        " Search in current file
\\               " Toggle Neo-tree
```

**Window/Split Navigation:**
```vim
<C-h/j/k/l>      " Move between splits (left/down/up/right)
<C-w>v           " Vertical split
<C-w>s           " Horizontal split
<C-w>q           " Close split
```

**Buffer (Tab) Navigation:**
```vim
<S-h>            " Previous buffer
<S-l>            " Next buffer
<leader>b        " List all buffers
```

### Week 1-2 Challenge: **Force Yourself**

1. **Disable VSCode** (uninstall or hide it)
2. Pick a **small personal project** you know well
3. **Only use these 10 keybindings** for navigation
4. Time yourself: "How long to find and open `UserController.js`?"

**Goal**: Get comfortable with `<leader><space>` and buffer switching. This should feel natural by end of week 2.

---

## Phase 2: Code-Level Navigation (Week 3-4) - "Jump, Don't Scroll"

### Core Principle
**Use motions to jump, not scroll line-by-line.**

### Within-File Navigation

**You already know:**
```vim
gg               " Go to top of file
G                " Go to bottom of file
{                " Previous paragraph/block
}                " Next paragraph/block
```

**Learn these:**
```vim
gd               " Go to definition (LSP)
gr               " Go to references (LSP)
gI               " Go to implementation
gy               " Go to type definition
gD               " Go to declaration
K                " Show documentation hover
<C-o>            " Jump back to previous location
<C-i>            " Jump forward to next location
%                " Jump between matching brackets
```

**Search navigation:**
```vim
/searchterm      " Search forward
?searchterm      " Search backward
n                " Next match
N                " Previous match
*                " Search for word under cursor
#                " Search for word under cursor (backward)
```

### LSP Navigation (Language Server)

Kickstart sets these up automatically:

```vim
gd               " Go to definition
gD               " Go to declaration
gI               " Go to implementation
gr               " Show references (in Telescope!)
<leader>ca       " Code actions
<leader>rn       " Rename symbol
]d               " Next diagnostic/error
[d               " Previous diagnostic/error
```

### Surround Operations (mini.surround)

Change brackets, quotes, and tags efficiently:

```vim
sa{motion}{char} " Surround Add - add surrounding
saiw)            " Surround Add Inner Word with ()
sa2w"            " Surround Add 2 words with quotes

sd{char}         " Surround Delete - remove surrounding
sd)              " Delete surrounding ()
sd"              " Delete surrounding quotes

sr{old}{new}     " Surround Replace - change surrounding
sr)]             " Replace () with []
sr'"             " Replace '' with ""
sr)"             " Replace () with quotes
```

**Common use cases:**
```ruby
# Cursor anywhere inside
foo             → Press saiw)  → (foo)
(bar)           → Press sr)]   → [bar]
"text"          → Press sd"    → text
function()      → Press sr)(   → function{}
```

**Note:** `s` key is disabled in your config to make mini.surround instant (no delay). Use `cl` or `r` if you need character substitution.

### Week 3-4 Challenge: **Stop Scrolling**

1. Open a file you need to edit
2. **Never use j/k to scroll** - always use motions
3. Practice: "Find the function that handles user login" → Use `<leader>sg` to grep "login", then `gd` to jump to definition

**Goal**: Break the habit of scrolling. Every movement should be intentional.

---

## Phase 3: Project-Wide Navigation (Week 5-6) - "Think in Symbols, Not Files"

### Core Principle
**Find code by what it does, not where it lives.**

### Telescope Power Patterns

**Find by name:**
```vim
<leader><space>  " Find files
```

**Find by content (crucial!):**
```vim
<leader>sg       " Live grep - search all files
<leader>sw       " Grep word under cursor
```

**Find by symbol (game-changer):**
```vim
<leader>ss       " Document symbols (functions/classes in current file)
<leader>sS       " Workspace symbols (search all symbols in project)
```

**Find by recent activity:**
```vim
<leader>s.       " Recent files
<leader>b        " Open buffers
<leader>sr       " Resume last search
```

**Git integration:**
```vim
" Kickstart includes gitsigns for in-buffer git indicators
" Use left terminal panes for git commands
```

### Real-World Workflow Examples

**Scenario 1: Fix a bug in user authentication**
```
1. <leader>sg → Type "authenticate" → See all occurrences
2. Pick the relevant file
3. gd → Jump to definition
4. <C-o> → Jump back
5. gr → See all references
6. Fix the bug
7. ]d → Check for any new errors
```

**Scenario 2: Understand how payments work**
```
1. <leader>sS → Type "payment" → See all payment-related symbols
2. Select PaymentController
3. % → Jump through matching brackets/blocks
4. gd → Follow call chains
5. <C-o> → Jump back when needed
```

**Scenario 3: Refactor a function name**
```
1. Place cursor on function name
2. <leader>rn → Rename
3. Type new name
4. LSP updates all references automatically
```

### Week 5-6 Challenge: **Think Task, Not Location**

1. Work on a real bug or feature
2. **Before opening any file**, ask: "What am I looking for?"
3. Choose the right tool:
   - Know the filename? → `<leader><space>`
   - Know the function/class? → `<leader>sS`
   - Know a keyword? → `<leader>sg`
   - Recently worked on it? → `<leader>fr`

**Goal**: Stop thinking "where is the file?" Start thinking "what am I looking for?"

---

## Phase 4: Advanced Patterns (Week 7-8) - "Flow State"

### Quickfix Lists

When Telescope shows multiple results:

```vim
<C-q>            " Send results to quickfix list
:copen           " Open quickfix window
:cn              " Next item
:cp              " Previous item
]q / [q          " LazyVim shortcuts for quickfix navigation
```

**Use case**: Found 20 occurrences of a function call, want to review each one.

### Marks (Bookmarks)

```vim
ma               " Set mark 'a' at cursor
'a               " Jump to mark 'a'
:marks           " List all marks
```

**Use case**: "I need to come back here" - mark it, explore, return.

### Jump List Mastery

```vim
<C-o>            " Jump to previous location
<C-i>            " Jump to next location
:jumps           " See jump history
```

**Use case**: Deep dive into 5 files, then retrace your steps.

### Window/Split Workflows

```vim
<C-w>v           " Vertical split
<C-w>s           " Horizontal split
<leader><space>  " Open file in split
<C-w>=           " Equalize split sizes
<C-w>o           " Close all other splits
```

**Use case**: Compare test file with implementation side-by-side.

### Week 7-8 Challenge: **Build Real Workflows**

1. **Bug investigation workflow**: Use `<leader>sg` → quickfix → `]q` to review each occurrence
2. **Feature implementation workflow**: Mark starting point → explore dependencies → jump back to implement
3. **Code review workflow**: Split windows → compare files → use `]d` to find issues

**Goal**: Develop muscle memory for complex navigation patterns.

---

## Customizing Direct Keybindings

### Where to Add Custom Keybindings

**Kickstart**: Add directly to `~/.config/nvim/init.lua` after line 210

### Example Custom Direct Keybindings

```lua
-- Add to init.lua after line 210
-- Prefer alphanumeric keys (easier with keyboard layers)

vim.keymap.set("n", "<leader>o", "<cmd>Telescope lsp_document_symbols<cr>", { desc = "Outline" })
vim.keymap.set("n", "<leader>O", "<cmd>Telescope lsp_dynamic_workspace_symbols<cr>", { desc = "Find Symbol" })
```

### The Strategy: One Key = One Action

Instead of:
- `<leader>s` → menu → `g` → live_grep

You get:
- `<leader>a` → live_grep (think: "**A**ll files")

Instead of:
- `<leader>s` → menu → `s` → document symbols

You get:
- `<leader>o` → document symbols (think: "**O**utline")

---

## Learning Strategies

### The "Replace One at a Time" Method

**Week 1: Master ONE new keybinding**
- Pick ONE keybinding you use VSCode for
- Example: "I use Ctrl+Shift+F to search all files"
- Replace with: `<leader>a` (or `<leader>sg`)
- Use it 20+ times this week
- Don't learn anything else

**Week 2: Master the NEXT ONE**
- Pick the next most common action
- Example: "I click files in the sidebar"
- Replace with: `<leader><space>`
- Use it exclusively this week

**Week 3: Keep going...**

### The "Sticky Note" Method

1. Write ONE keybinding on a sticky note
2. Put it on your monitor
3. Every time you reach for the mouse, use the keybinding instead
4. When it feels automatic (usually 3-5 days), remove the note and add a new one

### The "Punishment" Method

Every time you reach for the mouse or use an old pattern:
1. Press `u` to undo
2. Use the correct keybinding
3. Repeat the action

Sounds annoying? Good! You'll learn fast to avoid the punishment.

### The "Know Your Bindings" Command

In vim, type this to see ALL your keybindings:
```vim
:Telescope keymaps
```

This shows you every keybinding available! Search for what you want to do.

### Build Your Own "Top 10"

Based on what you actually do most often. Here's a template:

```
═══════════════════════════════════
      MY TOP 10 VIM KEYBINDS
═══════════════════════════════════

1. _____________ : _____________
2. _____________ : _____________
3. _____________ : _____________
4. _____________ : _____________
5. _____________ : _____________
6. _____________ : _____________
7. _____________ : _____________
8. _____________ : _____________
9. _____________ : _____________
10. _____________ : _____________
═══════════════════════════════════
```

**How to fill it out:**
1. What's the ONE thing you do most? (Probably open files)
2. What's the second most? (Probably search in files)
3. Keep going...

Only learn these 10. Ignore everything else.

---

## Common Pitfalls & Solutions

### Pitfall 1: "I don't know what file I'm looking for"

**Solution**: Use content-based search, not file-based:
- `<leader>sg` → Search for a function/class/keyword you know exists
- `<leader>sS` → Search workspace symbols

### Pitfall 2: "I keep getting lost"

**Solution**: Use jump list and marks:
- `<C-o>` is your "back button"
- Mark important places with `ma`, `mb`, etc.
- Use `:jumps` to see where you've been

### Pitfall 3: "I forget which buffer has what"

**Solution**: Use descriptive buffer navigation:
- `<leader>fb` → See all open buffers with content preview
- `<leader>bb` → Toggle between last two files (like Alt+Tab)

### Pitfall 4: "VSCode shows me file structure"

**Solution**: Use symbol navigation:
- `<leader>ss` → See all functions/classes in current file
- `\\` → Open Neo-tree when you need spatial context

### Pitfall 5: "The keybindings don't work as listed"

**Solution**: Check your actual keybindings:
- Run `:Telescope keymaps` to see all available keybindings
- Some bindings have intermediary menus (which-key)
- Create custom direct bindings (see [Customizing section](#customizing-direct-keybindings))

---

## The 30-Day Challenge

### Week 1-2: File Navigation Only
- Master `<leader><space>`, `<leader>sg`, `<leader>fb`
- No VSCode allowed

### Week 3-4: Add Code Navigation
- Master `gd`, `gr`, `<C-o>`, `*`
- Stop scrolling with j/k

### Week 5-6: Add Symbol Navigation
- Master `<leader>sS`, `<leader>ss`
- Think tasks, not files

### Week 7-8: Add Advanced Patterns
- Quickfix, marks, splits
- Build personal workflows

### After 30 Days
- Vim should feel **faster** than VSCode
- You should **think** your way to code, not **browse**

---

## Resources

### Built-in Resources
- `:Tutor` - Built into vim, great for fundamentals
- `vimtutor` - Classic terminal tutorial
- `:Telescope keymaps` - See all your current keybindings
- `:help <command>` - Get help on any vim command

### External Resources
- [Learn Vim (the Smart Way)](https://github.com/iggredible/Learn-Vim) - Comprehensive guide
- [Kickstart.nvim](https://github.com/nvim-lua/kickstart.nvim) - Your distribution
- ThePrimeagen on YouTube - Real-world vim workflows
- [Neovim Documentation](https://neovim.io/doc/) - Official docs

### Recommended Plugins to Add Later

**1. flash.nvim** (enhanced f/t motions)
```lua
-- Jump anywhere in visible text with 2 keystrokes
s{char}{label}    " Jump to any visible word
```

**2. harpoon** (by ThePrimeagen)
```lua
-- Pin frequently used files for instant access
<leader>ha        " Add file to harpoon
<leader>hh        " Toggle harpoon menu
<C-1/2/3/4>       " Jump to pinned file 1/2/3/4
```

**3. vim-matchup** (better % matching)
```lua
%                 " Jump between matching keywords (if/else, def/end, etc)
```

---

## Quick Reference Card

Print this and keep it visible:

```
═══════════════════════════════════════════════════════════
                    VIM NAVIGATION CHEAT SHEET
═══════════════════════════════════════════════════════════

FILES & BUFFERS:
  <leader><space>     Find files
  <leader>sg          Search in all files (live grep)
  <leader>b           List open buffers
  <leader>s.          Recent files
  <S-h> / <S-l>       Previous/Next buffer
  \\                  Toggle Neo-tree

CODE NAVIGATION (LSP):
  gd                  Go to definition
  gr                  Go to references
  gI                  Go to implementation
  gy                  Go to type definition
  K                   Show documentation
  <leader>ca          Code actions
  <leader>rn          Rename symbol

SYMBOLS:
  <leader>ss          Document symbols (outline current file)
  <leader>sS          Workspace symbols (search all symbols)

SURROUND (mini.surround):
  sa{motion}{char}    Add surrounding (saiw) for word)
  sd{char}            Delete surrounding (sd" for quotes)
  sr{old}{new}        Replace surrounding (sr)] for () to [])

SEARCH IN FILE:
  /pattern            Search forward
  ?pattern            Search backward
  *                   Search word under cursor
  n / N               Next/Previous match

NAVIGATION:
  <C-o> / <C-i>       Jump back/forward in jump list
  { / }               Previous/Next paragraph
  % / %               Match bracket/keyword
  gg / G              Top/Bottom of file
  ]d / [d             Next/Prev diagnostic

WINDOWS:
  <C-h/j/k/l>         Move between splits
  <C-w>v              Vertical split
  <C-w>s              Horizontal split
  <C-w>q              Close split

MARKS:
  ma                  Set mark 'a'
  'a                  Jump to mark 'a'

UTILITY:
  :Telescope keymaps  Show all keybindings
  :jumps              Show jump history
  :marks              Show all marks
═══════════════════════════════════════════════════════════
```

---

## Action Plan

### This Week:

1. **Verify `gd` actually works** (it should!)
   - Put cursor on a function call
   - Press `gd`
   - Did it jump to the definition? YES! You already know it!

2. **Pick 3 keybindings from the "Core 15" list**
   - Write them on sticky notes
   - Use ONLY these three this week
   - Ignore everything else

3. **Run `:Telescope keymaps` in vim**
   - Search for actions you do frequently
   - Find the actual keybinding (might be simpler than you think!)

### Next Week:

4. **Add 3 more keybindings**
   - Remove old sticky notes
   - Add new ones
   - Repeat

### Keep Going:

- Replace one VSCode habit per week with a vim keybinding
- When you find yourself struggling, check this guide
- Don't try to learn everything at once - master one pattern at a time

---

## Remember

**You don't need to learn everything.** Most vim users only use 20-30 keybindings regularly.

**Stop trying to learn vim. Start solving problems.**

Instead of "I need to learn all vim keybindings", think:
- "I need to find this function faster" → Learn `gd`
- "I need to see all TODO comments" → Learn `<leader>sg` + search "TODO"
- "I keep getting lost" → Learn `<C-o>`

Focus on what you actually need, and let the rest come naturally.

---

Good luck on your vim journey! 🚀
