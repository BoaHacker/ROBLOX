--Fart Simulator
local ui = loadstring(game:HttpGet('https://raw.githubusercontent.com/BoaHacker/ROBLOX/main/ui', true))()

local player = game.Players.LocalPlayer
local mouse = player:GetMouse()
local antiAFK = true
player.Idled:connect(function()
	if antiAFK then
		game.VirtualUser:Button2Down(Vector2.new(0, 0), workspace.CurrentCamera.CFrame)
		wait(1)
		game.VirtualUser:Button2Up(Vector2.new(0, 0), workspace.CurrentCamera.CFrame)
	end
end)

local Main = ui:CreateWindow({
	text = 'Main'
})

local Teleports = ui:CreateWindow({
	text = 'Teleports'
})

local Pets = ui:CreateWindow({
	text = 'Pets'
})

local Player = ui:CreateWindow({
	text = 'Player'
})

local Settings = ui:CreateWindow({
	text = 'Settings'
})

Main:AddToggle('Auto Eat', function(state)
	getgenv().AutoEat = state
	while true do
		if not getgenv().AutoEat then return end
		wait()
		local bTool = player.Backpack:FindFirstChildOfClass('Tool')
		local cTool = player.Character:FindFirstChildOfClass('Tool')
		if bTool then
			bTool.Parent = player.Character
		else
			game.ReplicatedStorage.RemoteFunctions.Request:InvokeServer('ClickableCurrencyAcquired')
		end
	end
end)

local oldSellPosition = workspace.Islands['11'].SellHitPart.CFrame
Main:AddToggle('Auto Sell', function(state)
	getgenv().AutoSell = state
	while true do
		if not getgenv().AutoSell then workspace.Islands['11'].SellHitPart.CFrame = oldSellPosition return end
		wait()
		workspace.Islands['11'].SellHitPart.CFrame = CFrame.new(0, 0, 0)
		workspace.Islands['11'].SellHitPart.CFrame = player.Character.HumanoidRootPart.CFrame
	end
end)

Main:AddToggle('Auto Boss', function(state)
	getgenv().AutoBoss = state
	while true do
		if not getgenv().AutoBoss then return end
		wait()
		local bTool = player.Backpack:FindFirstChildOfClass('Tool')
		local cTool = player.Character:FindFirstChildOfClass('Tool')
		local boss = workspace.Islands['1'].Boss:FindFirstChildOfClass('Model')
		if bTool then
			bTool.Parent = player.Character
		else
			boss.Head.CanCollide = false
			player.Character.HumanoidRootPart.CFrame = boss.Head.CFrame
			game.ReplicatedStorage.RemoteFunctions.Request:InvokeServer('PlayerAttack', boss.HumanoidRootPart)
		end
	end
end)

Main:AddToggle('Auto Spawners', function(state)
	getgenv().AutoSpawners = state
	while true do
		if not getgenv().AutoSpawners then return end
		wait()
		for i, v in pairs(workspace.Islands['1'].CurrencySpawners:GetChildren('Spawner')) do
			if v:FindFirstChildOfClass('Model') then
				player.Character.HumanoidRootPart.CFrame = v.CFrame
			end
		end
	end
end)

Main:AddToggle('Auto Rings', function(state)
	getgenv().AutoRings = state
	while true do
		if not getgenv().AutoRings then return end
		wait()
		for i, v in pairs(workspace.Islands['1'].CurrencyRings:GetChildren('CurrenyRing')) do
			if v.Settings.Used.Value ~= true then
				player.Character.HumanoidRootPart.CFrame = v.HitPart.CFrame
			end
		end
		for i, v in pairs(workspace.Islands['9'].CurrencyRings:GetChildren('CurrenyRing')) do
			if v.Settings.Used.Value ~= true then
				player.Character.HumanoidRootPart.CFrame = v.HitPart.CFrame
			end
		end
		for i, v in pairs(workspace.Islands['12'].CurrencyRings:GetChildren('CurrenyRing')) do
			if v.Settings.Used.Value ~= true then
				player.Character.HumanoidRootPart.CFrame = v.HitPart.CFrame
			end
		end
	end
end)

local oldSecretWaterfallChestPosition = workspace.Islands['1'].RewardChests.SecretWaterfallChest.ChestHitPart.CFrame
local oldTopWaterfallChestPosition = workspace.Islands['1'].RewardChests.TopWaterfallChest.ChestHitPart.CFrame
local oldDuckIslandFirst = workspace.Islands['1'].RewardChests.DuckIslandFirst.ChestHitPart.CFrame
local oldDuckIslandSecond = workspace.Islands['1'].RewardChests.DuckIslandSecond.ChestHitPart.CFrame
local old1CenterChestPosition = workspace.Islands['1'].RewardChests.CenterChest.ChestHitPart.CFrame
local oldDuckIslandThird = workspace.Islands['1'].RewardChests.DuckIslandThird.ChestHitPart.CFrame
local oldFarChestPosition = workspace.Islands['1'].RewardChests.FarChest.ChestHitPart.CFrame
local oldJewelChestPosition = workspace.Islands['2'].RewardChests.JewelChest.ChestHitPart.CFrame
local old5CenterChestPosition = workspace.Islands['5'].RewardChests.CenterChest.ChestHitPart.CFrame
local old7CenterChestPosition = workspace.Islands['7'].RewardChests.CenterChest.ChestHitPart.CFrame
local old10CenterChestPosition = workspace.Islands['10'].RewardChests.CenterChest.ChestHitPart.CFrame
Main:AddButton('Collect Daily Chests', function()
	workspace.Islands['1'].RewardChests.SecretWaterfallChest.ChestHitPart.CFrame = player.Character.HumanoidRootPart.CFrame
	workspace.Islands['1'].RewardChests.TopWaterfallChest.ChestHitPart.CFrame = player.Character.HumanoidRootPart.CFrame
	workspace.Islands['1'].RewardChests.DuckIslandFirst.ChestHitPart.CFrame = player.Character.HumanoidRootPart.CFrame
	workspace.Islands['1'].RewardChests.DuckIslandSecond.ChestHitPart.CFrame = player.Character.HumanoidRootPart.CFrame
	workspace.Islands['1'].RewardChests.CenterChest.ChestHitPart.CFrame = player.Character.HumanoidRootPart.CFrame
	workspace.Islands['1'].RewardChests.DuckIslandThird.ChestHitPart.CFrame = player.Character.HumanoidRootPart.CFrame
	workspace.Islands['1'].RewardChests.FarChest.ChestHitPart.CFrame = player.Character.HumanoidRootPart.CFrame
	workspace.Islands['2'].RewardChests.JewelChest.ChestHitPart.CFrame = player.Character.HumanoidRootPart.CFrame
	workspace.Islands['5'].RewardChests.CenterChest.ChestHitPart.CFrame = player.Character.HumanoidRootPart.CFrame
	workspace.Islands['7'].RewardChests.CenterChest.ChestHitPart.CFrame = player.Character.HumanoidRootPart.CFrame
	workspace.Islands['10'].RewardChests.CenterChest.ChestHitPart.CFrame = player.Character.HumanoidRootPart.CFrame
	wait()
	workspace.Islands['1'].RewardChests.SecretWaterfallChest.ChestHitPart.CFrame = oldSecretWaterfallChestPosition
	workspace.Islands['1'].RewardChests.TopWaterfallChest.ChestHitPart.CFrame = oldTopWaterfallChestPosition
	workspace.Islands['1'].RewardChests.DuckIslandFirst.ChestHitPart.CFrame = oldDuckIslandFirst
	workspace.Islands['1'].RewardChests.DuckIslandSecond.ChestHitPart.CFrame = oldDuckIslandSecond
	workspace.Islands['1'].RewardChests.CenterChest.ChestHitPart.CFrame = old1CenterChestPosition
	workspace.Islands['1'].RewardChests.DuckIslandThird.ChestHitPart.CFrame = oldDuckIslandThird
	workspace.Islands['1'].RewardChests.FarChest.ChestHitPart.CFrame = oldFarChestPosition
	workspace.Islands['2'].RewardChests.JewelChest.ChestHitPart.CFrame = oldJewelChestPosition
	workspace.Islands['5'].RewardChests.CenterChest.ChestHitPart.CFrame = old5CenterChestPosition
	workspace.Islands['7'].RewardChests.CenterChest.ChestHitPart.CFrame = old7CenterChestPosition
	workspace.Islands['10'].RewardChests.CenterChest.ChestHitPart.CFrame = old10CenterChestPosition
end)

Teleports:AddButton('Lobby', function()
	player.Character.HumanoidRootPart.CFrame = workspace.SpawnLocation.CFrame * CFrame.new(0, 5, 0)
end)

Teleports:AddButton('Skybridge', function()
	player.Character.HumanoidRootPart.CFrame = workspace.Islands['2'].IslandNameDisplay.CFrame
end)

Teleports:AddButton('Frost Island', function()
	player.Character.HumanoidRootPart.CFrame = workspace.Islands['3'].IslandNameDisplay.CFrame
end)

Teleports:AddButton('The Oasis', function()
	player.Character.HumanoidRootPart.CFrame = workspace.Islands['4'].IslandNameDisplay.CFrame
end)

Teleports:AddButton('Candy Land', function()
	player.Character.HumanoidRootPart.CFrame = workspace.Islands['5'].IslandNameDisplay.CFrame
end)

Teleports:AddButton('Area 51', function()
	player.Character.HumanoidRootPart.CFrame = workspace.Islands['6'].IslandNameDisplay.CFrame
end)

Teleports:AddButton('Dreamland', function()
	player.Character.HumanoidRootPart.CFrame = workspace.Islands['7'].IslandNameDisplay.CFrame
end)

Teleports:AddButton('Fairy Island', function()
	player.Character.HumanoidRootPart.CFrame = workspace.Islands['8'].IslandNameDisplay.CFrame
end)

Teleports:AddButton('Lava Land', function()
	player.Character.HumanoidRootPart.CFrame = workspace.Islands['9'].IslandNameDisplay.CFrame
end)

Teleports:AddButton('Money Land', function()
	player.Character.HumanoidRootPart.CFrame = workspace.Islands['10'].IslandNameDisplay.CFrame
end)

Teleports:AddButton('Rainbow Land', function()
	player.Character.HumanoidRootPart.CFrame = workspace.Islands['11'].IslandNameDisplay.CFrame
end)

Teleports:AddButton('Pirate Island', function()
	player.Character.HumanoidRootPart.CFrame = workspace.Islands['12'].IslandNameDisplay.CFrame
end)

local coolDown = 0.1
Pets:AddToggle('Auto Hatch Starter', function(state)
	getgenv().AutoStarter = state
	while true do
		if not getgenv().AutoStarter then return end
		wait(coolDown)
		game.ReplicatedStorage.RemoteFunctions.RequestPurchase:InvokeServer('EggX1', 'Starter Egg')
	end
end)

Pets:AddToggle('Auto Hatch Beginners', function(state)
	getgenv().AutoBeginners = state
	while true do
		if not getgenv().AutoBeginners then return end
		wait(coolDown)
		game.ReplicatedStorage.RemoteFunctions.RequestPurchase:InvokeServer('EggX1', 'Beginners Egg')
	end
end)

Pets:AddToggle('Auto Hatch Frost', function(state)
	getgenv().AutoFrost = state
	while true do
		if not getgenv().AutoFrost then return end
		wait(coolDown)
		game.ReplicatedStorage.RemoteFunctions.RequestPurchase:InvokeServer('EggX1', 'Frost Egg')
	end
end)

Pets:AddToggle('Auto Hatch Space', function(state)
	getgenv().AutoSpace = state
	while true do
		if not getgenv().AutoSpace then return end
		wait(coolDown)
		game.ReplicatedStorage.RemoteFunctions.RequestPurchase:InvokeServer('EggX1', 'Space Egg')
	end
end)

Pets:AddToggle('Auto Hatch Alien', function(state)
	getgenv().AutoAlien = state
	while true do
		if not getgenv().AutoAlien then return end
		wait(coolDown)
		game.ReplicatedStorage.RemoteFunctions.RequestPurchase:InvokeServer('EggX1', 'Alien Egg')
	end
end)

Pets:AddToggle('Auto Hatch Godly', function(state)
	getgenv().AutoGodly = state
	while true do
		if not getgenv().AutoGodly then return end
		wait(coolDown)
		game.ReplicatedStorage.RemoteFunctions.RequestPurchase:InvokeServer('EggX1', 'Godly Egg')
	end
end)

Pets:AddToggle('Auto Hatch Lava', function(state)
	getgenv().AutoLava = state
	while true do
		if not getgenv().AutoLava then return end
		wait(coolDown)
		game.ReplicatedStorage.RemoteFunctions.RequestPurchase:InvokeServer('EggX1', 'Lava Egg')
	end
end)

Pets:AddToggle('Auto Hatch Captains', function(state)
	getgenv().AutoCaptains = state
	while true do
		if not getgenv().AutoCaptains then return end
		wait(coolDown)
		game.ReplicatedStorage.RemoteFunctions.RequestPurchase:InvokeServer('EggX1', 'Captains Egg')
	end
end)

Pets:AddToggle('Auto Hatch Tropical', function(state)
	getgenv().AutoTropical = state
	while true do
		if not getgenv().AutoTropical then return end
		wait(coolDown)
		game.ReplicatedStorage.RemoteFunctions.RequestPurchase:InvokeServer('EggX1', 'Tropical Egg')
	end
end)

Pets:AddLabel('Hatch Wait Time:')
Pets:AddDropdown({'0.1', '0.5', '1', '2'}, function(state)
	coolDown = tonumber(state)
end)

Player:AddToggle('Infinite Jump', function(state)
	getgenv().InfiniteJump = state
	game.UserInputService.JumpRequest:connect(function()
		if not getgenv().InfiniteJump then return end
		player.Character.Humanoid:ChangeState('Jumping')
	end)
end)

for i, v in pairs(workspace:GetChildren()) do
	if v.Name == 'Core' then
		v:Destroy()
	end
end
local Core = Instance.new('Part', workspace)
Core.Name = 'Core'
Core.Size = Vector3.new(0.05, 0.05, 0.05)
Core.CanCollide = false
workspace:WaitForChild('Core')
local torso = workspace.Core
local speed = 10
local keys = {a = false, d = false, w = false, s = false}
local e1
local e2
local function Fly()
	local pos = Instance.new('BodyPosition', torso)
	local gyro = Instance.new('BodyGyro', torso)
	pos.maxForce = Vector3.new(math.huge, math.huge, math.huge)
	pos.position = torso.Position
	gyro.maxTorque = Vector3.new(9e9, 9e9, 9e9)
	gyro.cframe = torso.CFrame
	repeat
		wait()
		player.Character.Humanoid.PlatformStand = true
		local new = gyro.cframe - gyro.cframe.p + pos.position
		if not keys.w and not keys.s and not keys.a and not keys.d then
			speed = 5
		end
		if keys.w then
			new = new + workspace.CurrentCamera.CoordinateFrame.lookVector * speed
			speed = speed + 0
		end
		if keys.s then
			new = new - workspace.CurrentCamera.CoordinateFrame.lookVector * speed
			speed = speed + 0
		end
		if keys.d then
			new = new * CFrame.new(speed, 0, 0)
			speed = speed + 0
		end
		if keys.a then
			new = new * CFrame.new(-speed, 0, 0)
			speed = speed + 0
		end
		if speed > 10 then
			speed = 5
		end
		pos.position = new.p
		if keys.w then
			gyro.cframe = workspace.CurrentCamera.CoordinateFrame * CFrame.Angles(-math.rad(speed * 0), 0, 0)
		elseif keys.s then
			gyro.cframe = workspace.CurrentCamera.CoordinateFrame * CFrame.Angles(math.rad(speed * 0), 0, 0)
		else
			gyro.cframe = workspace.CurrentCamera.CoordinateFrame
		end
	until getgenv().Fly == false
	if gyro then gyro:Destroy() end
	if pos then pos:Destroy() end
	player.Character.Humanoid.PlatformStand = false
	speed = 10
end
e1 = mouse.KeyDown:connect(function(key)
	if not torso or not torso.Parent then e1:disconnect() e2:disconnect() return end
	if key == 'w' then
		keys.w = true
	elseif key == 's' then
		keys.s = true
	elseif key == 'a' then
		keys.a = true
	elseif key == 'd' then
		keys.d = true
	end
end)
e2 = mouse.KeyUp:connect(function(key)
	if key == 'w' then
		keys.w = false
	elseif key == 's' then
		keys.s = false
	elseif key == 'a' then
		keys.a = false
	elseif key == 'd' then
		keys.d = false
	end
end)
Player:AddToggle('Fly', function(state)
	getgenv().Fly = state
	if not getgenv().Fly then for i, v in pairs(workspace:FindFirstChild('Core'):GetChildren()) do v:Destroy() end return end
	local Weld = Instance.new('Weld', Core)
	Weld.Part0 = Core
	Weld.Part1 = player.Character.HumanoidRootPart
	Weld.C0 = CFrame.new(0, 0, 0)
	Fly()
end)

Player:AddToggle('Noclip', function(state)
	getgenv().Noclip = state
	while true do
		if not getgenv().Noclip then return end
		game.RunService.Stepped:wait()
		for i, v in pairs(player.Character:GetDescendants()) do
			if v:IsA('BasePart') then
				v.CanCollide = false
			end
		end
	end
end)

Player:AddToggle('Click to TP', function(state)
	getgenv().ClicktoTP = state
	mouse.Button1Down:Connect(function()
		if not getgenv().ClicktoTP then return end
		player.Character.HumanoidRootPart.CFrame = CFrame.new(mouse.Hit.x, mouse.Hit.y + 5, mouse.Hit.z) * CFrame.Angles(0, math.rad(player.Character.HumanoidRootPart.Orientation.Y), 0)
	end)
end)

Player:AddBox('Walkspeed', function(state)
	if tonumber(state.Text) ~= nil then
		player.Character.Humanoid.WalkSpeed = state.Text
	end
end)

Player:AddBox('Jumppower', function(state)
	if tonumber(state.Text) ~= nil then
		player.Character.Humanoid.JumpPower = state.Text
	end
end)

Player:AddBox('Gravity', function(state)
	if tonumber(state.Text) ~= nil then
		workspace.Gravity = state.Text
	end
end)

Player:AddButton('Reset to Default', function()
	player.Character.Humanoid.WalkSpeed = 20
	player.Character.Humanoid.JumpPower = 50
	workspace.Gravity = 196.2
end)

Settings:AddToggle('Hide Popups', function(state)
	getgenv().HidePopups = state
	if not getgenv().HidePopups then player.PlayerGui.MainUI.PopUps.Visible = true return end
	player.PlayerGui.MainUI.PopUps.Visible = false
end)

Settings:AddButton('Destroy UI', function()
	ui.gui:Destroy()
	antiAFK = false
	getgenv().AutoEat = false
	getgenv().AutoSell = false
	getgenv().AutoBoss = false
	getgenv().AutoSpawners = false
	getgenv().AutoRings = false
	getgenv().AutoStarter = false
	getgenv().AutoBeginners = false
	getgenv().AutoFrost = false
	getgenv().AutoSpace = false
	getgenv().AutoAlien = false
	getgenv().AutoGodly = false
	getgenv().AutoLava = false
	getgenv().AutoCaptains = false
	getgenv().AutoTropical = false
	getgenv().InfiniteJump = false
	getgenv().Fly = false
	getgenv().Noclip = false
	getgenv().ClicktoTP = false
	if getgenv().HidePopups then player.PlayerGui.MainUI.PopUps.Visible = true getgenv().HidePopups = false end
	player.Character.Humanoid.WalkSpeed = 20
	player.Character.Humanoid.JumpPower = 50
	workspace.Gravity = 196.2
end)
