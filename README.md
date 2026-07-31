<p align="center">
  <img src="https://flooxa.web.id/assets/logo.png" alt="Flooxa Logo" width="450"/>
</p>

# Flooxa Lib Gui

**A custom UI library created by Flooxa.** I built this UI library completely from scratch for Roblox because I needed a standalone interface that just works—without dealing with annoying external dependencies. It rocks a modern, futuristic liquid-glass look heavily inspired by iOS, featuring buttery-smooth animations, collapsible accordion-style sections to keep things clean, and a floating minimize feature that shrinks your UI into a draggable logo.

## Key Features
- **Completely Standalone:** No external libraries or extra UI assets needed. Just load it and go.
- **Liquid Glass Aesthetic:** Transparent, futuristic blur with a clean Dark-to-Pink gradient.
- **Floating Minimize Logo:** Minimize the menu into a tiny, draggable Flooxa logo anywhere on your screen.
- **Accordion Sections:** Easily expand or collapse categories inside tabs to keep your script organized.
- **Packed with Components:** Comes right out of the box with Tabs, Sections, Buttons, Toggles, Sliders, Dropdowns, Inputs, Radio Groups, Checkboxes, and Toast Notifications.
- **State Persistence:** All interactive components support `Default` values so you can pre-set states easily.
- **Icon Support:** Works flawlessly with Roblox Asset IDs (perfect for FontAwesome image IDs).

---

## 🚀 Quick Start / Bootstrapping

Just load the UI library using `loadstring` straight from GitHub:

```lua
local FlooxaLib = loadstring(game:HttpGet("https://raw.githubusercontent.com/odhier/Flooxa-LibGui/refs/heads/main/main.lua"))()
```
---

## 1. Creating the Window

First things first, initialize your main hub window:

```lua
local Window = FlooxaLib:CreateWindow({
    Name = "FlooxaHub", 
    Logo = "rbxassetid://79662742873050" -- Swap this out with your own Asset ID
})
```

---

## 2. Setting Up Tabs

Tabs help split your features into different pages. Use the `MakeTab` method:

```lua
local MainTab = Window:MakeTab({
    Name = "Main",
    Icon = "rbxassetid://3926305904" -- Use FontAwesome Image IDs or standard Roblox Image IDs
})

local SettingsTab = Window:MakeTab({
    Name = "Settings",
    Icon = "rbxassetid://3926307971"
})
```

---

## 3. Creating Sections (Accordion)

Sections live inside Tabs. They can be clicked to expand or collapse, which is perfect for keeping your layout neat.

```lua
local MainSection = MainTab:MakeSection({
    Name = "Player Cheats"
})
```

---

## 4. Adding UI Elements

Remember, all interactive elements must be placed **inside a Section**.

### Label (Info Text)
```lua
MainSection:AddLabel({
    Text = "This is just some informational text."
})
```

### Text Input
```lua
MainSection:AddInput({
    Name = "Player Name",
    Placeholder = "Type a name here...",
    Default = "Steve",      -- Optional: pre-fills the textbox
    Numeric = false,
    Callback = function(text)
        print("Input received:", text)
    end
})
```

### Number / Float Input
```lua
MainSection:AddInput({
    Name = "Set JumpPower",
    Placeholder = "Numbers only...",
    Default = 50,           -- Optional: pre-fills the number
    Numeric = true,         -- Only allows numbers to be typed
    Callback = function(value)
        print("Number updated to:", value)
    end
})
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `Name` | string | Yes | Label text shown next to the input |
| `Placeholder` | string | No | Placeholder text when empty |
| `Default` | string/number | No | Pre-fills the textbox on load |
| `Numeric` | boolean | No | If `true`, blocks non-number inputs |
| `Callback` | function | Yes | Fires with the value when focus is lost |

### Dropdown (Searchable, Pre-select & Multi-select)
```lua
MainSection:AddDropdown({
    Name = "Select Player",
    Options = {"Player1", "Player2", "Player3"},
    Default = "Player1",  -- Optional: pre-selects this option
    Multi = false,        -- Set to true if you want multi-selection
    Callback = function(selected)
        -- 'selected' is a string if Multi is false, or a table if Multi is true
        print("Selected:", selected)
    end
})
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `Name` | string | Yes | Label text for the dropdown |
| `Options` | table | Yes | Array of string options to choose from |
| `Default` | string | No | Pre-selects this option (Only works when `Multi = false`) |
| `Multi` | boolean | No | Set to `true` to allow selecting multiple items |
| `Callback` | function | Yes | Returns selected value (string) or values (table) |

> **Note:** Dropdowns come with a built-in search box to filter options automatically. When `Default` is used, it will show up directly in the dropdown title right away.

### Radio Group
Perfect when you only want users to pick a single choice out of a few options.
```lua
MainSection:AddRadioGroup({
    Name = "ESP Mode",
    Options = {"Box", "Skeleton", "Tracers"},
    Default = "Box",
    Callback = function(selected)
        print("ESP Mode changed to:", selected)
    end
})
```

### Checkbox
```lua
MainSection:AddCheckbox({
    Name = "God Mode",
    Default = false,
    Callback = function(state)
        print("God Mode active:", state)
    end
})
```

### Button
```lua
MainSection:AddButton({
    Name = "Print Hello",
    Callback = function()
        print("Hello Flooxa!")
    end
})
```

### Toggle
```lua
MainSection:AddToggle({
    Name = "Auto Farm",
    Default = false,
    Callback = function(state)
        print("Auto Farm toggled:", state)
    end
})
```

### Slider
```lua
MainSection:AddSlider({
    Name = "WalkSpeed",
    Min = 16,
    Max = 100,
    Default = 16,
    Callback = function(value)
        game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = value
    end
})
```

---

## 5. Notifications (Toast)

You can trigger a sleek notification toast from literally anywhere in your script using your `Window` instance. They stack up nicely and clean themselves up automatically.

```lua
Window:MakeNotification({
    Title = "Executed!",
    Content = "The script loaded successfully without any errors.",
    Duration = 5 -- In seconds (Optional, defaults to 5)
})
```

---

## 🎨 Icon Support

You can use any standard Roblox image asset ID for your tabs or component icons. 

---
**Enjoy building with FlooxaLib! 🚀**

