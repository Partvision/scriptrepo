# Brainrot Hub & SimpleLib

Complete Roblox script collection with modern UI library framework.

---

## Brainrot Hub

A collection of Roblox scripts with convenient hub access and game-specific utilities.

### Center Hub

All-in-one hub featuring every script created. Access everything from one central location with organized navigation and easy script management.

```lua
loadstring(game:HttpGet("https://raw.githubusercontent.com/Partvision/scriptrepo/refs/heads/main/Brainrot%20Hub%20Weight%20Game"))()
```

**Features:**
- Access all scripts from one central location
- Organized script library
- Easy navigation

### Get HEAVY for Brainrots

Weight Game Script with keyless teleportation. A beginner-friendly script focused on teleportation mechanics.

```lua
loadstring(game:HttpGet("https://raw.githubusercontent.com/Partvision/scriptrepo/refs/heads/main/Brainrot%20Hub%20Weight%20Game"))()
```

**Features:**
- Instant teleportation – No key required
- Lightweight & fast performance
- Beginner-friendly – Great for learning

---

## SimpleLib: Red Edition

A modern, lightweight, fully resizable, and highly optimized Roblox UI Library. Originally designed by **Esore** and completely refactored for fluidity, performance, and responsive scaling.

Features smooth tweened dragging, a dynamic resizing engine, auto-canvas scaling, and robust memory management to prevent client-side execution leaks.

### Installation

```lua
local SimpleLib = loadstring(game:HttpGet("https://raw.githubusercontent.com/Partvision/scriptrepo/refs/heads/main/ModernUI%202.0"))()
```

### Features

**True Responsive Layout**
Interface elements dynamically adjust their size and layout mapping as you drag-resize the window.

**Fluid Tweening**
Leverages optimized `TweenService` mechanics for window dragging, handle hovering, and input focus animations.

**Memory Leak Prevention**
Built-in connection lifecycle tracker automatically safely disconnects user inputs and hooks upon closing the GUI.

**Sleek Red Palette**
Dark aesthetic baseline accented with vibrant crimson and lighter red feedback visuals.

---

## API Documentation

### 1. Creating a Window

Initializes the main ScreenGui container, sets up window properties, and injects drag/resize tracking.

```lua
local Window = SimpleLib:Window("My Script Hub")
```

**Parameters:**
- `winName` (string) — The title visible on the main upper header bar.

**Returns:** A Tabs navigation module object.

---

### 2. Adding Sections (Tabs)

Sections allow you to organize script choices across different categories. Tabs automatically fit horizontally.

```lua
local CombatTab = Window:AddSection("Combat")
local VisualsTab = Window:AddSection("Visuals")
```

**Parameters:**
- `SectionName` (string) — The label text written inside the tab button.

**Returns:** A Contents injector module object specific to that layout section.

---

### 3. Section Elements

Once a tab/section object is generated, you can use the following elements inside of it:

#### Button

Executes an active chunk of execution logic when pressed. Includes hover glow mapping.

```lua
CombatTab:Button("Kill Aura", function()
    print("Kill Aura toggled on!")
end)
```

#### Label

Static informative display indicators. Returns an interface object allowing runtime text mutations.

```lua
local StatusLabel = VisualsTab:Label("Status: Idle")

-- Update label text dynamically later in execution loop:
StatusLabel:Update("Status: Rendering ESP...")
```

#### Toggle

Maintains a Boolean flag state (true / false) with built-in micro-icon switches.

```lua
CombatTab:Toggle("Auto Farm", false, function(state)
    if state then
        print("Auto Farm Active")
    else
        print("Auto Farm Inactive")
    end
end)
```

**Tip:** Set the second parameter (`val`) to `true` to default activate it.

#### TextBox

Captures input string blocks. Fires its callback sequence when the user presses Enter or clicks away from the element block.

```lua
VisualsTab:TextBox("WalkSpeed Modifier", function(text, enterPressed)
    local speed = tonumber(text)
    if speed then
        game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = speed
    end
end)
```

---

## Complete Example

Here is a ready-to-run implementation structure using the full library schema:

```lua
local SimpleLib = loadstring(game:HttpGet("https://raw.githubusercontent.com/Partvision/scriptrepo/refs/heads/main/ModernUI%202.0"))()

-- Create Window
local UI = SimpleLib:Window("Nexus Hub | 2026 Edition")

-- Generate Separate Navigation Views
local LocalPlayerTab = UI:AddSection("Main Profile")
local TeleportTab = UI:AddSection("Teleports")

-- Populate Main Tab Elements
LocalPlayerTab:Label("Player Information Panel")

LocalPlayerTab:Toggle("Infinite Jump Enable", false, function(bool)
    _G.InfJump = bool
    game:GetService("UserInputService").JumpRequest:Connect(function()
        if _G.InfJump then
            game.Players.LocalPlayer.Character:FindFirstChildOfClass('Humanoid'):ChangeState("Jumping")
        end
    end)
end)

LocalPlayerTab:TextBox("Set Jump Power", function(text)
    local num = tonumber(text)
    if num then
        game.Players.LocalPlayer.Character.Humanoid.JumpPower = num
    end
end)

-- Populate Teleport View
TeleportTab:Button("Teleport to Map Center", function()
    local player = game.Players.LocalPlayer
    if player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
        player.Character.HumanoidRootPart.CFrame = CFrame.new(0, 50, 0)
    end
end)
```

---

## Usage

1. Copy the script code for the desired hub or library
2. Paste into your Roblox script executor
3. Run and enjoy!

---

## Disclaimer

These scripts are for educational purposes and authorized private use only. Always check Roblox's Terms of Service and game-specific rules before using scripts.

---

## License & Credits

**Brainrot Hub:** Created by Partvision

**SimpleLib UI Library:** Original design by Esore. Refactoring & resizing optimizations by Community.

Note: Feel free to customize structural layout adjustments. Please preserve original author header strings out of respect.
