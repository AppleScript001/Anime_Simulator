local Library = loadstring(game:HttpGet("https://pastebin.com/raw/KNBp0LRy"), "Coastified UI")()
repeat wait() until game:IsLoaded()
game:GetService("Players").LocalPlayer.Idled:connect(function()
game:GetService("VirtualUser"):ClickButton2(Vector2.new())
end)
local Window = Library:NewWindow("Animal Simulator")

local Section = Window:NewSection("AutoFarm")
local Toggle = Section:CreateToggle("Auto Exp", function(Value)
_G.Exp = Value
while _G.Exp do 
wait(1)
for _,v in pairs(workspace.CoinContainer:GetDescendants()) do
  if v:IsA("TouchTransmitter") then
  firetouchinterest(game.Players.LocalPlayer.Character.HumanoidRootPart, v.Parent, 0) --0 is touch
  firetouchinterest(game.Players.LocalPlayer.Character.HumanoidRootPart, v.Parent, 1) -- 1 is untouch
end
end
end
end)
local Section = Window:NewSection("Boss")
Section:CreateLabel("Select - NPCs")

local PlayerTP1
local TweenService = game:GetService("TweenService")

local Dropdown = Section:CreateDropdown("Select !", {"LavaGorilla", "Griffin", "DragonGiraffe", "CENTAUR"}, Selected1, function(Value)
    Selected1 = Value
end)

local Toggle = Section:CreateToggle("Auto [Hit]", function(Value)
_G.Hit = Value
while _G.Hit do
wait(1)  -- Wait for 1 second before checking for enemies
pcall(function()
for i,v in pairs(workspace.NPC:GetDescendants()) do
if v.Name == Selected1 then
if v.Humanoid.Health > 0 then
repeat
  local args = {
    [1] = workspace:WaitForChild("NPC"):WaitForChild(Selected1):WaitForChild("Humanoid"),
    [2] = math.huge
}

game:GetService("ReplicatedStorage"):WaitForChild("jdskhfsIIIllliiIIIdchgdIiIIIlIlIli"):FireServer(unpack(args))

game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * CFrame.new(0,0,5)
wait()  -- Wait a short time before checking again
until not _G.Hit or v.Humanoid.Health <= 0
end
end
end
end)
local Player = game.Players.LocalPlayer
local function onCharacterAdded(character)
character.Archivable = false
character:WaitForChild("HumanoidRootPart").Anchored = false
if Player.Character then
onCharacterAdded(Player.Character)
end
end

Player.CharacterAdded:Connect(onCharacterAdded)
end
end)
local Section = Window:NewSection("Extra")
local Button = Section:CreateButton("Get Animal [All]", function()
  for i,v in pairs(workspace.Eggs:GetDescendants()) do
    if v.Name == "clickPart" then
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.CFrame
    end
end
wait(0.1)
for i,v in pairs(workspace.Eggs:GetDescendants()) do
if v:IsA("ClickDetector") then
fireclickdetector(v, 1)
end
end
end)
