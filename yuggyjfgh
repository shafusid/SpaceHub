-- Services
local Players = game:GetService("Players")
local RunService = game:GetService("RunService")

-- Configuration
local HIGHLIGHT_COLOR = Color3.fromRGB(255, 0, 255) -- Magenta (you can change this)
local OUTLINE_TRANSPARENCY = 0 -- 0 is fully opaque, 1 is fully transparent
local FILL_TRANSPARENCY = 0.5 -- How transparent the fill color is

-- Function to create a highlight for a given character
local function createHighlightForCharacter(character)
    if character and character:IsA("Model") and character:FindFirstChildOfClass("Humanoid") then
        local highlight = Instance.new("Highlight")
        highlight.FillColor = HIGHLIGHT_COLOR
        highlight.OutlineColor = HIGHLIGHT_COLOR
        highlight.FillTransparency = FILL_TRANSPARENCY
        highlight.OutlineTransparency = OUTLINE_TRANSPARENCY
        highlight.Adornee = character -- Attaches the highlight to the entire character model
        highlight.Parent = character -- Parent it to the character model
        return highlight
    end
    return nil
end

-- Function to highlight all existing players
local function highlightExistingPlayers()
    for _, player in ipairs(Players:GetPlayers()) do
        if player ~= Players.LocalPlayer then -- Don't highlight the local player
            local character = player.Character or player.CharacterAdded:Wait()
            if character then
                createHighlightForCharacter(character)
            end
        end
    end
end

-- Connect to PlayerAdded to highlight new players
Players.PlayerAdded:Connect(function(player)
    if player ~= Players.LocalPlayer then
        -- Wait for the character to load
        player.CharacterAdded:Connect(function(character)
            createHighlightForCharacter(character)
        end)
    end
end)

-- Initial highlighting for players already in the game
highlightExistingPlayers()

print("H")
