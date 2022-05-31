--Muscle Legends
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

Main:AddToggle('Auto Strenght', function(state)
	getgenv().AutoStrenght = state
	while true do
		if not getgenv().AutoStrenght then return end
		wait()
		player.muscleEvent:FireServer('rep')
		player.muscleEvent:FireServer('rep', player.machineInUse.Value)
	end
end)

Main:AddToggle('Auto Speed Keypress', function(state)
	getgenv().AutoSpeedKeypress = state
	while true do
		if not getgenv().AutoSpeedKeypress then game.VirtualUser:SetKeyUp('w') return end
		wait()
		game.VirtualUser:SetKeyUp('w')
		game.VirtualUser:SetKeyDown('w')
	end
end)

Main:AddToggle('Auto Rebirth', function(state)
	getgenv().AutoRebirth = state
	while true do
		if not getgenv().AutoRebirth then return end
		wait()
		game.ReplicatedStorage.rEvents.rebirthRemote:InvokeServer('rebirthRequest')
	end
end)

game.ReplicatedStorage.brawlInProgress.Changed:Connect(function(state)
	if not getgenv().AutoJoinBrawl then return end
	if state then
		game.ReplicatedStorage.rEvents.brawlEvent:FireServer('joinBrawl')
		wait()
		player.PlayerGui.gameGui.brawlJoinLabel.Visible = false
	end
end)
Main:AddToggle('Auto Join Brawl', function(state)
	getgenv().AutoJoinBrawl = state
end)

Main:AddButton('Redeem Codes', function()
	game.ReplicatedStorage.rEvents.codeRemote:InvokeServer('millionwarriors')
	game.ReplicatedStorage.rEvents.codeRemote:InvokeServer('frostgems10')
	game.ReplicatedStorage.rEvents.codeRemote:InvokeServer('musclestorm50')
	game.ReplicatedStorage.rEvents.codeRemote:InvokeServer('spacegems50')
	game.ReplicatedStorage.rEvents.codeRemote:InvokeServer('megalift50')
	game.ReplicatedStorage.rEvents.codeRemote:InvokeServer('speedy50')
	game.ReplicatedStorage.rEvents.codeRemote:InvokeServer('skyagility50')
	game.ReplicatedStorage.rEvents.codeRemote:InvokeServer('galaxycrystal50')
	game.ReplicatedStorage.rEvents.codeRemote:InvokeServer('supermuscle100')
	game.ReplicatedStorage.rEvents.codeRemote:InvokeServer('superpunch100')
	game.ReplicatedStorage.rEvents.codeRemote:InvokeServer('epicreward500')
	game.ReplicatedStorage.rEvents.codeRemote:InvokeServer('launch250')
end)

local oldmythicalChestPosition = workspace.mythicalChest.circleInner.CFrame
local oldmagmaChestPosition = workspace.magmaChest.circleInner.CFrame
local oldgroupRewardsCirclePosition = workspace.groupRewardsCircle.circleInner.CFrame
local oldgoldenChestPosition = workspace.goldenChest.circleInner.CFrame
local oldenchantedChestPosition = workspace.enchantedChest.circleInner.CFrame
local oldlegendsChestPosition = workspace.legendsChest.circleInner.CFrame
Main:AddButton('Collect Daily Chests', function()
	workspace.mythicalChest.circleInner.CFrame = player.Character.HumanoidRootPart.CFrame
	workspace.magmaChest.circleInner.CFrame = player.Character.HumanoidRootPart.CFrame
	workspace.groupRewardsCircle.circleInner.CFrame = player.Character.HumanoidRootPart.CFrame
	workspace.goldenChest.circleInner.CFrame = player.Character.HumanoidRootPart.CFrame
	workspace.enchantedChest.circleInner.CFrame = player.Character.HumanoidRootPart.CFrame
	workspace.legendsChest.circleInner.CFrame = player.Character.HumanoidRootPart.CFrame
	wait()
	workspace.mythicalChest.circleInner.CFrame = oldmythicalChestPosition
	workspace.magmaChest.circleInner.CFrame = oldmagmaChestPosition
	workspace.groupRewardsCircle.circleInner.CFrame = oldgroupRewardsCirclePosition
	workspace.goldenChest.circleInner.CFrame = oldgoldenChestPosition
	workspace.enchantedChest.circleInner.CFrame = oldenchantedChestPosition
	workspace.legendsChest.circleInner.CFrame = oldlegendsChestPosition
end)

Teleports:AddButton('Lobby', function()
	player.currentMap.Value = 'Beach'
	local folder = workspace.spawnsFolder:GetChildren()
	local spawn = folder[math.random(1, #folder)]
	player.Character.HumanoidRootPart.CFrame = spawn.CFrame * CFrame.new(0, 5, 0)
end)

Teleports:AddButton('Tiny Island', function()
	player.currentMap.Value = 'Tiny Island'
	player.Character.HumanoidRootPart.CFrame = workspace.areaTeleportParts.beachToTinyIsland.CFrame
end)

Teleports:AddButton('Frost Gym', function()
	player.currentMap.Value = 'Frost Gym'
	player.Character.HumanoidRootPart.CFrame = workspace.areaTeleportParts.beachToFrostGym.CFrame
end)

Teleports:AddButton('Mystical Gym', function()
	player.currentMap.Value = 'Mystical Gym'
	player.Character.HumanoidRootPart.CFrame = workspace.areaTeleportParts.beachToMysticalGym.CFrame
end)

Teleports:AddButton('Eternal Gym', function()
	player.currentMap.Value = 'Eternal Gym'
	player.Character.HumanoidRootPart.CFrame = workspace.areaTeleportParts.beachToEternalGym.CFrame
end)

Teleports:AddButton('Legends Gym', function()
	player.currentMap.Value = 'Legends Gym'
	player.Character.HumanoidRootPart.CFrame = workspace.areaTeleportParts.beachToLegendsGym.CFrame
end)

Teleports:AddButton('Muscle King', function()
	player.currentMap.Value = 'Muscle King'
	player.Character.HumanoidRootPart.CFrame = workspace.areaTeleportParts.beachToMuscleKing.CFrame
end)

Teleports:AddButton('Battle Island', function()
	player.currentMap.Value = 'Battle Island'
	player.Character.HumanoidRootPart.CFrame = workspace.areaTeleportParts.beachToBattleIsland.CFrame
end)

local coolDown = 0.1
Pets:AddToggle('Auto Blue', function(state)
	getgenv().AutoBlue = state
	while true do
		if not getgenv().AutoBlue then return end
		wait(coolDown)
		game.ReplicatedStorage.rEvents.openCrystalRemote:InvokeServer('openCrystal', 'Blue Crystal')
	end
end)

Pets:AddToggle('Auto Green', function(state)
	getgenv().AutoGreen = state
	while true do
		if not getgenv().AutoGreen then return end
		wait(coolDown)
		game.ReplicatedStorage.rEvents.openCrystalRemote:InvokeServer('openCrystal', 'Green Crystal')
	end
end)

Pets:AddToggle('Auto Frost', function(state)
	getgenv().AutoFrost = state
	while true do
		if not getgenv().AutoFrost then return end
		wait(coolDown)
		game.ReplicatedStorage.rEvents.openCrystalRemote:InvokeServer('openCrystal', 'Frost Crystal')
	end
end)

Pets:AddToggle('Auto Mythical', function(state)
	getgenv().AutoMythical = state
	while true do
		if not getgenv().AutoMythical then return end
		wait(coolDown)
		game.ReplicatedStorage.rEvents.openCrystalRemote:InvokeServer('openCrystal', 'Mythical Crystal')
	end
end)

Pets:AddToggle('Auto Inferno', function(state)
	getgenv().AutoInferno = state
	while true do
		if not getgenv().AutoInferno then return end
		wait(coolDown)
		game.ReplicatedStorage.rEvents.openCrystalRemote:InvokeServer('openCrystal', 'Inferno Crystal')
	end
end)

Pets:AddToggle('Auto Legends', function(state)
	getgenv().AutoLegends = state
	while true do
		if not getgenv().AutoLegends then return end
		wait(coolDown)
		game.ReplicatedStorage.rEvents.openCrystalRemote:InvokeServer('openCrystal', 'Legends Crystal')
	end
end)

Pets:AddToggle('Auto DarkNebula', function(state)
	getgenv().AutoDarkNebula = state
	while true do
		if not getgenv().AutoDarkNebula then return end
		wait(coolDown)
		game.ReplicatedStorage.rEvents.openCrystalRemote:InvokeServer('openCrystal', 'Dark Nebula Crystal')
	end
end)

Pets:AddToggle('Auto Muscle Elite', function(state)
	getgenv().AutoMuscleElite = state
	while true do
		if not getgenv().AutoMuscleElite then return end
		wait(coolDown)
		game.ReplicatedStorage.rEvents.openCrystalRemote:InvokeServer('openCrystal', 'Muscle Elite Crystal')
	end
end)

Pets:AddToggle('Auto Galaxy Oracle', function(state)
	getgenv().AutoGalaxyOracle = state
	while true do
		if not getgenv().AutoGalaxyOracle then return end
		wait(coolDown)
		game.ReplicatedStorage.rEvents.openCrystalRemote:InvokeServer('openCrystal', 'Galaxy Oracle Crystal')
	end
end)

Pets:AddToggle('Auto Battle Legends', function(state)
	getgenv().AutoBattleLegends = state
	while true do
		if not getgenv().AutoBattleLegends then return end
		wait(coolDown)
		game.ReplicatedStorage.rEvents.openCrystalRemote:InvokeServer('openCrystal', 'Battle Legends Crystal')
	end
end)

Pets:AddToggle('Auto Sky Eclipse', function(state)
	getgenv().AutoSkyEclipse = state
	while true do
		if not getgenv().AutoSkyEclipse then return end
		wait(coolDown)
		game.ReplicatedStorage.rEvents.openCrystalRemote:InvokeServer('openCrystal', 'Sky Eclipse Crystal')
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
	game.ReplicatedStorage.rEvents.changeSpeedSizeRemote:InvokeServer('changeSpeed', 14)
	game.ReplicatedStorage.rEvents.changeSpeedSizeRemote:InvokeServer('changeSpeed', math.huge)
	player.Character.Humanoid.JumpPower = 50
	workspace.Gravity = 196.2
end)

Settings:AddToggle('Hide Popups', function(state)
	getgenv().HidePopups = state
	if not getgenv().HidePopups then player.PlayerGui.statEffectsGui.Enabled = true return end
	player.PlayerGui.statEffectsGui.Enabled = false
end)

Settings:AddButton('Destroy UI', function()
	ui.gui:Destroy()
	antiAFK = false
	getgenv().AutoStrenght = false
	if getgenv().AutoSpeedKeypress then game.VirtualUser:SetKeyUp('w') getgenv().AutoSpeedKeypress = false end
	getgenv().AutoRebirth = false
	getgenv().AutoJoinBrawl = false
	getgenv().AutoBlue = false
	getgenv().AutoGreen = false
	getgenv().AutoFrost = false
	getgenv().AutoMythical = false
	getgenv().AutoInferno = false
	getgenv().AutoLegends = false
	getgenv().AutoDarkNebula = false
	getgenv().AutoMuscleElite = false
	getgenv().AutoGalaxyOracle = false
	getgenv().AutoBattleLegends = false
	getgenv().AutoSkyEclipse = false
	getgenv().InfiniteJump = false
	getgenv().Fly = false
	getgenv().Noclip = false
	getgenv().ClicktoTP = false
	if getgenv().HidePopups then player.PlayerGui.statEffectsGui.Enabled = true getgenv().HidePopups = false end
	game.ReplicatedStorage.rEvents.changeSpeedSizeRemote:InvokeServer('changeSpeed', 14)
	game.ReplicatedStorage.rEvents.changeSpeedSizeRemote:InvokeServer('changeSpeed', math.huge)
	player.Character.Humanoid.JumpPower = 50
	workspace.Gravity = 196.2
end)
