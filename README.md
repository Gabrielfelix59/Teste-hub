local player = game.Players.LocalPlayer
local screenGui = Instance.new("ScreenGui")
local mainFrame = Instance.new("Frame")
local titleLabel = Instance.new("TextLabel")
local startFarmButton = Instance.new("TextButton")
local World1, World2, World3 = false, false, false

if game.PlaceId == 2753915549 then
    World1 = true
elseif game.PlaceId == 4442272183 then
    World2 = true
elseif game.PlaceId == 7449423635 then
    World3 = true
else
    player:Kick("Do not Support, Please wait...")
end

function CheckQuest() 
    local MyLevel = player.Data.Level.Value
    local currentQuest = ""

    if World1 then
        if MyLevel >= 1 and MyLevel <= 9 then
            currentQuest = "Missão: Bandit Quest (Nível 1)"
        elseif MyLevel >= 10 and MyLevel <= 14 then
            currentQuest = "Missão: Jungle Quest (Monkey)"
        elseif MyLevel >= 15 and MyLevel <= 29 then
            currentQuest = "Missão: Jungle Quest (Gorilla)"
        elseif MyLevel >= 30 and MyLevel <= 39 then
            currentQuest = "Missão: Buggy Quest (Pirate)"
        elseif MyLevel >= 40 and MyLevel <= 59 then
            currentQuest = "Missão: Buggy Quest (Brute)"
        elseif MyLevel >= 60 and MyLevel <= 74 then
            currentQuest = "Missão: Desert Quest (Desert Bandit)"
        elseif MyLevel >= 75 and MyLevel <= 89 then
            currentQuest = "Missão: Desert Quest (Desert Officer)"
        elseif MyLevel >= 90 and MyLevel <= 99 then
            currentQuest = "Missão: Snow Quest (Snow Bandit)"
        elseif MyLevel >= 100 and MyLevel <= 119 then
            currentQuest = "Missão: Snow Quest (Snowman)"
        elseif MyLevel >= 120 and MyLevel <= 149 then
            currentQuest = "Missão: Chief Petty Officer"
        else
            currentQuest = "Nível fora das missões disponíveis"
        end
    end

    return currentQuest
end

function ActivateFarm()
    local questName = CheckQuest()
    print("Farming ativado! " .. questName)
end

screenGui.Parent = player.PlayerGui

mainFrame.Size = UDim2.new(0.25, 0, 0.15, 0)
mainFrame.Position = UDim2.new(0.375, 0, 0.425, 0)
mainFrame.BackgroundColor3 = Color3.new(0.1, 0.1, 0.1)
mainFrame.BorderSizePixel = 0
mainFrame.Active = true
mainFrame.Draggable = true
mainFrame.Parent = screenGui

titleLabel.Size = UDim2.new(1, 0, 0.3, 0)
titleLabel.Position = UDim2.new(0, 0, 0, 0)
titleLabel.BackgroundColor3 = Color3.new(0.2, 0.2, 0.2)
titleLabel.TextColor3 = Color3.new(1, 1, 1)
titleLabel.Text = "Farm Level"
titleLabel.TextScaled = true
titleLabel.Parent = mainFrame

startFarmButton.Size = UDim2.new(0.8, 0, 0.4, 0)
startFarmButton.Position = UDim2.new(0.1, 0, 0.3, 0)
startFarmButton.BackgroundColor3 = Color3.new(0, 0.5, 0)
startFarmButton.TextColor3 = Color3.new(1, 1, 1)
startFarmButton.Text = "Ativar Farm"
startFarmButton.TextScaled = true
startFarmButton.Parent = mainFrame

startFarmButton.MouseButton1Click:Connect(function()
    ActivateFarm()
end)

local initialQuest = CheckQuest()
titleLabel.Text = initialQuest
