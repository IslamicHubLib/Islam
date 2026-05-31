# IslamicHub — Beginner Guide

## Step 1 — Load the library

paste this at the very top of your script, always first:

```lua
local hub = loadstring(game:HttpGet("https://raw.githubusercontent.com/IslamicHubLib/Islam/refs/heads/main/IslamicHubLibOPENSOURCE", true))()
```

`hub` is now your main object, everything runs through it.

---

## Step 2 — Create a Tab

```lua
local combat = hub:AddTab("Combat")
```

this creates a new tab in the sidebar called **Combat**.
the variable `combat` is what you use to add stuff inside that tab.
you can make as many tabs as you want:

```lua
local combat = hub:AddTab("Combat")
local player = hub:AddTab("Player")
local misc   = hub:AddTab("Misc")
```

---

## Step 3 — Add a Section (optional but looks clean)

```lua
combat:AddSection("Aimbot")
```

just a small divider label to group your toggles/buttons.
purely visual, does nothing on its own.

---

## Step 4 — Add stuff inside the tab

### Toggle (on/off switch)

```lua
combat:AddToggle("Silent Aim", false, function(v)
    print(v) -- v is true when on, false when off
end)
```

- `"Silent Aim"` — the name shown on screen
- `false` — starts turned off (use `true` to start it on)
- `function(v)` — runs your code whenever someone flips the toggle

---

### Slider (a draggable number picker)

```lua
combat:AddSlider("Fov", 0, 500, 100, function(v)
    print(v) -- v is the current number
end)
```

- `"Fov"` — label
- `0` — minimum number
- `500` — maximum number
- `100` — starts at 100
- `function(v)` — runs with the new number every time you drag it

---

### Button (click to run something)

```lua
combat:AddButton("Teleport to nearest", function()
    -- put your code here, runs when clicked
end)
```

---

### Stats (fps + ping, auto updates)

```lua
misc:AddStats()
```

no setup needed, just call it and it shows live fps and ping.

---

## Full Working Example

```lua
-- load the library
local hub = loadstring(game:HttpGet("https://raw.githubusercontent.com/IslamicHubLib/Islam/refs/heads/main/IslamicHubLibOPENSOURCE", true))()

-- first tab: combat
local combat = hub:AddTab("Combat")
combat:AddSection("Aimbot")
combat:AddToggle("Silent Aim", false, function(v)
    print(v)
end)
combat:AddSlider("Fov", 0, 500, 100, function(v)
    print(v)
end)
combat:AddButton("Teleport to nearest", function()
    -- your teleport code goes here
end)

-- second tab: misc
local misc = hub:AddTab("Misc")
misc:AddSection("Info")
misc:AddStats()
misc:AddButton("Copy Username", function()
    setclipboard(game.Players.LocalPlayer.Name)
end)
```

---

## Quick Reference

| method | what it does |
|---|---|
| `hub:AddTab("name")` | creates a new tab, returns it |
| `tab:AddSection("name")` | adds a divider label |
| `tab:AddToggle(name, default, fn)` | on/off switch |
| `tab:AddSlider(name, min, max, default, fn)` | number slider |
| `tab:AddButton(name, fn)` | clickable button |
| `tab:AddInput(name, default, hint, fn)` | text box |
| `tab:AddLabel(text, color)` | plain text |
| `tab:AddStats()` | live fps and ping |
