# Flooxa Lib Gui

**Flooxa Lib Gui** is a custom, standalone UI library built entirely from scratch for Roblox without using any external UI dependencies. It features a modern, futuristic liquid-glass aesthetic specifically inspired by iOS, smooth animations, accordion-style collapsable sections, and floating logo minimization.

## Features
- **Standalone & Lightweight**: No external libraries or UI instances needed.
- **Liquid Glass Theme**: Transparent futuristic blur gradient (Dark to Pink).
- **Floating Minimize Logo**: Minimize to a draggable floating Flooxa logo!
- **Accordion Sections**: Collapsable & expandable categories inside tabs.
- **Components included**: Tabs, Sections, Buttons, Toggles, Sliders, and Notifications (Toast).
- **Supports Icon Menu**: Uses Asset IDs (e.g., FontAwesome Image IDs).

---

## 🚀 Quick Start / Bootstrapping

Load the UI library using `loadstring` from GitHub:

```lua
-- Replace 'URL_TO_YOUR_RAW_GITHUB_FILE' with the raw URL to FlooxaLib.lua
local FlooxaLib = loadstring(game:HttpGet("URL_TO_YOUR_RAW_GITHUB_FILE"))()
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

## 4. Adding Elements (Buttons, Toggles, Sliders)

All UI elements are added **inside a Section**.

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

## 🖼️ Icon Support (FontAwesome)

Because this library accepts direct Roblox Asset IDs for Tab icons, you can use popular FontAwesome image packs uploaded by the Roblox community.

Some common Icon IDs:
- Home / Main: `rbxassetid://3926305904`
- Settings / Gear: `rbxassetid://3926307971`
- User / Player: `rbxassetid://3926305904`
- Target / Combat: `rbxassetid://3926305904`

*(To find more specific icons, you can use the Toolbox in Roblox Studio or search the Creator Marketplace for "FontAwesome")*

---
**Enjoy building with FlooxaLib!**
