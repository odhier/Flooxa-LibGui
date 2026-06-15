# Flooxa Lib Gui

**Flooxa Lib Gui** is a custom, standalone UI library built entirely from scratch for Roblox without using any external UI dependencies. It features a modern, futuristic liquid-glass aesthetic specifically inspired by iOS, smooth animations, accordion-style collapsable sections, and floating logo minimization.

## Features
- **Standalone & Lightweight**: No external libraries or UI instances needed.
- **Liquid Glass Theme**: Transparent futuristic blur gradient (Dark to Pink).
- **Floating Minimize Logo**: Minimize to a draggable floating Flooxa logo!
- **Accordion Sections**: Collapsable & expandable categories inside tabs.
- **Components included**: Tabs, Sections, Buttons, Toggles, Sliders, Dropdowns, Inputs, Radio Groups, Checkboxes, and Notifications (Toast).
- **Default Values**: All interactive components (Toggle, Slider, Dropdown, Input, Radio, Checkbox) support `Default` values for pre-setting states.
- **Supports Icon Menu**: Uses Asset IDs (e.g., FontAwesome Image IDs).

---

## Quick Start / Bootstrapping

Load the UI library using `loadstring` from GitHub:

```lua
local FlooxaLib = loadstring(game:HttpGet("https://raw.githubusercontent.com/odhier/Flooxa-LibGui/refs/heads/main/main.lua"))()
```

---

## 🪟 1. Creating the Window

```lua
local Window = FlooxaLib:CreateWindow({
    Name = "FlooxaHub", 
    Logo = "rbxassetid://79662742873050" -- Put your own asset ID here
})
```

---

## 📑 2. Creating Tabs

To create a tab, you need to use the `MakeTab` method.

```lua
local MainTab = Window:MakeTab({
    Name = "Main",
    Icon = "rbxassetid://3926305904" -- Replace with FontAwesome Image IDs or Roblox Image ID
})

local SettingsTab = Window:MakeTab({
    Name = "Settings",
    Icon = "rbxassetid://3926307971"
})
```

---

## 3. Creating Sections (Accordion)

Sections are placed inside Tabs. They can be clicked to open or close, neatly organizing your content!

```lua
local MainSection = MainTab:MakeSection({
    Name = "Player Cheats"
})
```

---

## 4. Adding Elements

All UI elements are added **inside a Section**.

### Label (Text)
```lua
MainSection:AddLabel({
    Text = "This is an informational text."
})
```

### Input Text
```lua
MainSection:AddInput({
    Name = "Player Name",
    Placeholder = "Enter name here...",
    Default = "Steve",     -- Optional: pre-fills the textbox with this value
    Numeric = false,
    Callback = function(text)
        print("Input given:", text)
    end
})
```

### Input Number / Float
```lua
MainSection:AddInput({
    Name = "Set JumpPower",
    Placeholder = "Numbers only...",
    Default = 50,           -- Optional: pre-fills with this number
    Numeric = true,
    Callback = function(value)
        print("Number given:", value)
    end
})
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `Name` | string | Yes | Label text shown next to the input |
| `Placeholder` | string | No | Placeholder text when input is empty |
| `Default` | string/number | No | Pre-fills the textbox with this value |
| `Numeric` | boolean | No | If `true`, only accepts numbers |
| `Callback` | function | Yes | Called with the input value when focus is lost |

### Dropdown (With Search, Default & Multi-select)
```lua
MainSection:AddDropdown({
    Name = "Select Player",
    Options = {"Player1", "Player2", "Player3"},
    Default = "Player1",  -- Optional: pre-selects this option and shows it in the title
    Multi = false,         -- Set to true for multi-select
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
| `Default` | string | No | Pre-selects this option (shown in title). Only works when `Multi = false` |
| `Multi` | boolean | No | If `true`, allows selecting multiple options |
| `Callback` | function | Yes | Called with selected value (string) or values (table if Multi) |

> **Note:** The dropdown includes a built-in search box to filter options. When `Default` is set, the dropdown title will display the pre-selected value on load.

### Radio Group
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
        print("God Mode:", state)
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
        print("Auto Farm state:", state)
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

You can call a notification toast from anywhere via the `Window` instance. They automatically stack and destroy themselves!

```lua
Window:MakeNotification({
    Title = "Executed!",
    Content = "The script has successfully loaded without errors.",
    Duration = 5 -- In seconds (optional, defaults to 5)
})
```

---

## Icon Support (FontAwesome)

Because this library accepts direct Roblox Asset IDs for Tab icons, you can use popular FontAwesome image packs uploaded by the Roblox community.

Some common Icon IDs:
- Home / Main: `rbxassetid://3926305904`
- Settings / Gear: `rbxassetid://3926307971`
- User / Player: `rbxassetid://3926305904`
- Target / Combat: `rbxassetid://3926305904`

*(To find more specific icons, you can use the Toolbox in Roblox Studio or search the Creator Marketplace for "FontAwesome")*

---
**Enjoy building with FlooxaLib!**
