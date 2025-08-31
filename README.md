game.Players.LocalPlayer
local gui = Instance.new("ScreenGui", player.PlayerGui)
gui.Name = "ScriptHubGui"

local frame = Instance.new("Frame", gui)
frame.Size = UDim2.new(0, 400, 0, 500)
frame.Position = UDim2.new(0.5, -200, 0.5, -250)
frame.BackgroundColor3 = Color3.fromRGB(139, 0, 0)
frame.BorderSizePixel = 0

local buttonNames = {"Get Tools", "Use Tools", "Super Speed", "Super Jump", "Infinite Money", "Teleport", "Fly", "God Mode"}
for i, name in ipairs(buttonNames) do
    local btn = Instance.new("TextButton", frame)
    btn.Size = UDim2.new(0, 350, 0, 40)
    btn.Position = UDim2.new(0, 25, 0, 25 + (i-1)*50)
    btn.BackgroundColor3 = Color3.fromRGB(80, 0, 0)
    btn.TextColor3 = Color3.fromRGB(255, 255, 255)
    btn.Font = Enum.Font.SourceSansBold
    btn.Text = name
    btn.Name = name:gsub(" ", "")
    btn.BorderSizePixel = 0
    btn.TextSize = 22
end

-- Example Button Functionality
frame.GetTools.MouseButton1Click:Connect(function()
    -- Example: Give all tools in workspace to player
    for _, tool in ipairs(workspace:GetChildren()) do
        if tool:IsA("Tool") then
            tool.Parent = player.Backpack
        end
    end
end)

frame.UseTools.MouseButton1Click:Connect(function()
    -- Example: Equip all tools in backpack
    for _, tool in ipairs(player.Backpack:GetChildren()) do
        if tool:IsA("Tool") then
            player.Character.Humanoid:EquipTool(tool)
        end
    end
end)

-- Add more functionality for other buttons as needed...g = 
