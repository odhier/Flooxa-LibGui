<p align="center">
  <img src="https://flooxa.odhier.site/assets/logo.png" alt="Flooxa Logo" width="450"/>
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
local FlooxaLib = loadstring(game:HttpGet("[https://raw.githubusercontent.com/odhier/Flooxa-LibGui/refs/heads/main/main.lua](https://raw.githubusercontent.com/odhier/Flooxa-LibGui/refs/heads/main/main.lua)"))()
