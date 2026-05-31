# IslamicHub — Usage Guide

## Loading the library

```lua
local hub = loadstring(game:HttpGet("https://raw.githubusercontent.com/IslamicHubLib/Islam/refs/heads/main/IslamicHubLibOPENSOURCE", true))()
```

---

## Adding a Tab

```lua
local combat = hub:AddTab("Combat")
```

the name you pass in shows as the tab label in the sidebar.

---

## Methods

### AddSection

```lua
combat:AddSection("Aimbot")
```

adds a divider label to group things together.

---

### AddToggle

```lua
combat:AddToggle("Silent Aim", false, function(v)
    print(v)
end)
```

| param | type | description |
|---|---|---|
| name | string | label shown on the toggle |
| default | bool | starting state |
| callback | function | fires with true/false on change |

returns `{ Get(), Set(value) }`

---

### AddSlider

```lua
combat:AddSlider("Fov", 0, 500, 100, function(v)
    print(v)
end)
```

| param | type | description |
|---|---|---|
| name | string | label |
| min | number | minimum value |
| max | number | maximum value |
| default | number | starting value |
| callback | function | fires with new value |

returns `{ Get(), Set(value) }`

---

### AddButton

```lua
combat:AddButton("Do Something", function()
    print("clicked")
end)
```

---

### AddInput

```lua
combat:AddInput("Player Name", "", "enter name...", function(v)
    print(v)
end)
```

| param | type | description |
|---|---|---|
| name | string | label above box |
| default | string | starting text |
| placeholder | string | grey hint text |
| callback | function | fires on text change |

returns `{ Get(), Set(value) }`

---

### AddLabel

```lua
combat:AddLabel("some info text", Color3.fromRGB(100, 160, 100))
```

returns `{ Set(text), Color(color3) }`

---

### AddStats

```lua
misc:AddStats()
```

auto adds live fps and ping labels, no setup needed.

---

## Full Example

```lua
local hub = loadstring(game:HttpGet("https://raw.githubusercontent.com/IslamicHubLib/Islam/refs/heads/main/IslamicHubLibOPENSOURCE", true))()

local combat = hub:AddTab("Combat")
combat:AddSection("Aimbot")
combat:AddToggle("Silent Aim", false, function(v) print(v) end)
combat:AddSlider("Fov", 0, 500, 100, function(v) print(v) end)
combat:AddButton("Teleport to nearest", function()
    -- your code
end)

local misc = hub:AddTab("Misc")
misc:AddSection("Info")
misc:AddStats()
misc:AddButton("Copy Username", function()
    setclipboard(game.Players.LocalPlayer.Name)
end)
```
