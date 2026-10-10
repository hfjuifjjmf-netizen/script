
-- YASSINE HUB | Compact Mobile UI
-- UI demo only: does not change real Gacha odds or grant free rolls.

local Players = game:GetService("Players")
local player = Players.LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")

local old = playerGui:FindFirstChild("YASSINE_HUB")
if old then old:Destroy() end

local purple = Color3.fromRGB(125, 95, 255)
local bg = Color3.fromRGB(22, 24, 36)
local panel = Color3.fromRGB(34, 37, 53)
local white = Color3.fromRGB(245, 245, 255)
local gray = Color3.fromRGB(175, 180, 200)

local gui = Instance.new("ScreenGui")
gui.Name = "YASSINE_HUB"
gui.ResetOnSpawn = false
gui.Parent = playerGui

local main = Instance.new("Frame")
main.Size = UDim2.fromOffset(260, 220)
main.Position = UDim2.new(0.5, -130, 0.5, -110)
main.BackgroundColor3 = bg
main.BorderSizePixel = 0
main.Parent = gui

Instance.new("UICorner", main).CornerRadius = UDim.new(0, 12)

local outline = Instance.new("UIStroke", main)
outline.Color = purple
outline.Thickness = 1.5

local header = Instance.new("Frame")
header.Size = UDim2.new(1, 0, 0, 38)
header.BackgroundColor3 = panel
header.BorderSizePixel = 0
header.Parent = main
Instance.new("UICorner", header).CornerRadius = UDim.new(0, 12)

local title = Instance.new("TextLabel")
title.Size = UDim2.new(1, -65, 1, 0)
title.Position = UDim2.fromOffset(10, 0)
title.BackgroundTransparency = 1
title.Text = "✦ YASSINE HUB"
title.TextColor3 = white
title.Font = Enum.Font.GothamBold
title.TextSize = 15
title.TextXAlignment = Enum.TextXAlignment.Left
title.Parent = header

local close = Instance.new("TextButton")
close.Size = UDim2.fromOffset(28, 26)
close.Position = UDim2.new(1, -33, 0, 6)
close.BackgroundColor3 = Color3.fromRGB(220, 70, 85)
close.Text = "×"
close.TextColor3 = white
close.TextSize = 19
close.Font = Enum.Font.GothamBold
close.Parent = header
Instance.new("UICorner", close).CornerRadius = UDim.new(0, 7)

local content = Instance.new("Frame")
content.Position = UDim2.fromOffset(10, 48)
content.Size = UDim2.new(1, -20, 1, -58)
content.BackgroundTransparency = 1
content.Parent = main

local info = Instance.new("TextLabel")
info.Size = UDim2.new(1, 0, 0, 75)
info.Position = UDim2.fromOffset(0, 0)
info.BackgroundColor3 = panel
info.TextColor3 = white
info.TextSize = 13
info.Font = Enum.Font.Gotham
info.TextWrapped = true
info.Text = "Welcome!\nSelect a button below."
info.Parent = content
Instance.new("UICorner", info).CornerRadius = UDim.new(0, 9)

local buttons = Instance.new("Frame")
buttons.Size = UDim2.new(1, 0, 0, 38)
buttons.Position = UDim2.new(0, 0, 1, -38)
buttons.BackgroundTransparency = 1
buttons.Parent = content

local layout = Instance.new("UIListLayout")
layout.FillDirection = Enum.FillDirection.Horizontal
layout.HorizontalAlignment = Enum.HorizontalAlignment.Center
layout.VerticalAlignment = Enum.VerticalAlignment.Center
layout.Padding = UDim.new(0, 5)
layout.Parent = buttons

local function makeButton(name, callback)
    local button = Instance.new("TextButton")
    button.Size = UDim2.new(0, 76, 0, 34)
    button.BackgroundColor3 = purple
    button.Text = name
    button.TextColor3 = white
    button.TextSize = 11
    button.Font = Enum.Font.GothamBold
    button.Parent = buttons
    Instance.new("UICorner", button).CornerRadius = UDim.new(0, 7)
    button.Activated:Connect(callback)
end

makeButton("HOME", function()
    info.Text = "YASSINE HUB\nBlox Fruits UI\nWorlds: First, Second, Third"
end)

makeButton("GACHA", function()
    info.Text = "GACHA INFO\nReal odds are controlled by the game server.\nThis UI cannot grant free rolls."
end)

makeButton("SETTINGS", function()
    info.Text = "SETTINGS\nUse × to close the interface."
end)

close.Activated:Connect(function()
    gui:Destroy()
end)

print("YASSINE HUB UI loaded")

