--Legends Of Speed
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

Main:AddToggle('Auto Spawners', function(state)
	getgenv().AutoSpawners = state
	while true do
		if not getgenv().AutoSpawners then return end
		wait()
		for i, v in pairs(workspace.orbFolder[player.currentMap.Value]:GetChildren()) do
			if v:FindFirstChildOfClass('MeshPart') then
				v.outerGem.CFrame = player.Character.HumanoidRootPart.CFrame
			end
			if v:FindFirstChildOfClass('Part') then
				v.outerOrb.CFrame = player.Character.HumanoidRootPart.CFrame
			end
		end
	end
end)

Main:AddToggle('Auto Rings', function(state)
	getgenv().AutoRings = state
	while true do
		if not getgenv().AutoRings then return end
		wait()
		for i, v in pairs(workspace.Hoops:GetChildren()) do
			local oldHoopPosition = v.CFrame
			v.CFrame = player.Character.HumanoidRootPart.CFrame
			wait()
			v.CFrame = oldHoopPosition
		end
	end
end)

Main:AddToggle('Auto Rebirth', function(state)
	getgenv().AutoRebirth = state
	while true do
		if not getgenv().AutoRebirth then return end
		wait()
		game.ReplicatedStorage.rEvents.rebirthEvent:FireServer('rebirthRequest')
	end
end)

game.ReplicatedStorage.raceInProgress.Changed:Connect(function(state)
	if not getgenv().AutoRace then return end
	if state then
		game.ReplicatedStorage.rEvents.raceEvent:FireServer('joinRace')
		wait()
		player.PlayerGui.gameGui.raceJoinLabel.Visible = false
	end
end)
game.ReplicatedStorage.raceStarted.Changed:Connect(function(state)
	if not getgenv().AutoRace then return end
	if state then
		for i, v in pairs(workspace.raceMaps:GetChildren()) do
			local oldFinishPosition = v.finishPart.CFrame
			v.finishPart.CFrame = player.Character.HumanoidRootPart.CFrame
			wait()
			v.finishPart.CFrame = oldFinishPosition
		end
	end
end)
Main:AddToggle('Auto Race', function(state)
	getgenv().AutoRace = state
end)

Main:AddButton('Redeem Codes', function()
	game.ReplicatedStorage.rEvents.codeRemote:InvokeServer('hyper250')
	game.ReplicatedStorage.rEvents.codeRemote:InvokeServer('legends500')
	game.ReplicatedStorage.rEvents.codeRemote:InvokeServer('launch200')
	game.ReplicatedStorage.rEvents.codeRemote:InvokeServer('sparkles300')
	game.ReplicatedStorage.rEvents.codeRemote:InvokeServer('sprint250')
	game.ReplicatedStorage.rEvents.codeRemote:InvokeServer('speedchampion000')
	game.ReplicatedStorage.rEvents.codeRemote:InvokeServer('racer300')
end)

local oldGoldenChestPosition = workspace.goldenChest.circleInner.CFrame
local oldEnchantedChestPosition = workspace.enchantedChest.circleInner.CFrame
local oldMagmaChestPosition = workspace.magmaChest.circleInner.CFrame
local oldGroupRewardsPosition = workspace.groupRewardsCircle.circleInner.CFrame
Main:AddButton('Collect Daily Chests', function()
	workspace.goldenChest.circleInner.CFrame = player.Character.HumanoidRootPart.CFrame
	workspace.enchantedChest.circleInner.CFrame = player.Character.HumanoidRootPart.CFrame
	workspace.magmaChest.circleInner.CFrame = player.Character.HumanoidRootPart.CFrame
	workspace.groupRewardsCircle.circleInner.CFrame = player.Character.HumanoidRootPart.CFrame
	wait()
	workspace.goldenChest.circleInner.CFrame = oldGoldenChestPosition
	workspace.enchantedChest.circleInner.CFrame = oldEnchantedChestPosition
	workspace.magmaChest.circleInner.CFrame = oldMagmaChestPosition
	workspace.groupRewardsCircle.circleInner.CFrame = oldGroupRewardsPosition
end)

Teleports:AddButton('Lobby', function()
	player.currentMap.Value = 'City'
	player.Character.HumanoidRootPart.CFrame = workspace.SpawnLocation.CFrame * CFrame.new(0, 5, 0)
end)

Teleports:AddButton('Snow City', function()
	player.currentMap.Value = 'Snow City'
	player.Character.HumanoidRootPart.CFrame = workspace.areaTeleportParts.mysteriousCaveToSnowCity.CFrame
end)

Teleports:AddButton('Magma City', function()
	player.currentMap.Value = 'Magma City'
	player.Character.HumanoidRootPart.CFrame = workspace.areaTeleportParts.infernoCaveToMagmaCity.CFrame
end)

Teleports:AddButton('Legends Highway', function()
	player.currentMap.Value = 'Legends Highway'
	player.Character.HumanoidRootPart.CFrame = workspace.areaTeleportParts.electroCaveToLegendsHighway.CFrame
end)

local outerSpaceBindable = Instance.new('BindableFunction')
function outerSpaceBindable.OnInvoke(state)
	if state == 'Yes' then
		game.TeleportService:Teleport(3232996272, player)
	end
end
Teleports:AddButton('Outer Space', function()
	game.StarterGui:SetCore('SendNotification', {
		Title = 'Outer Space',
		Text = 'Teleport to Another Place?',
		Duration = 5,
		Callback = outerSpaceBindable,
		Button1 = 'Yes',
		Button2 = 'No'
	})
end)

local speedDesertBindable = Instance.new('BindableFunction')
function speedDesertBindable.OnInvoke(state)
	if state == 'Yes' then
		game.TeleportService:Teleport(3276265788, player)
	end
end
Teleports:AddButton('Speed Desert', function()
	game.StarterGui:SetCore('SendNotification', {
		Title = 'Speed Desert',
		Text = 'Teleport to Another Place?',
		Duration = 5,
		Callback = speedDesertBindable,
		Button1 = 'Yes',
		Button2 = 'No'
	})
end)

Teleports:AddLabel('Parkours:')
Teleports:AddButton('Grass Course', function()
	player.currentMap.Value = 'City'
	player.Character.HumanoidRootPart.CFrame = workspace.areaTeleportParts.cityToGrassCourse.CFrame
end)

Teleports:AddButton('Frost Course', function()
	player.currentMap.Value = 'City'
	player.Character.HumanoidRootPart.CFrame = workspace.areaTeleportParts.cityToFrostCourse.CFrame
end)

Teleports:AddButton('Parkour Challenge', function()
	player.currentMap.Value = 'City'
	player.Character.HumanoidRootPart.CFrame = workspace.areaTeleportParts.cityToParkourChallenge.CFrame
end)

Teleports:AddButton('Pirate Course', function()
	player.currentMap.Value = 'Snow City'
	player.Character.HumanoidRootPart.CFrame = workspace.areaTeleportParts.snowCityToPirateCourse.CFrame
end)

local coolDown = 0.1
Pets:AddToggle('Auto Red', function(state)
	getgenv().AutoRed = state
	while true do
		if not getgenv().AutoRed then return end
		wait(coolDown)
		game.ReplicatedStorage.rEvents.openCrystalRemote:InvokeServer('openCrystal', 'Red Crystal')
	end
end)

Pets:AddToggle('Auto Blue', function(state)
	getgenv().AutoBlue = state
	while true do
		if not getgenv().AutoBlue then return end
		wait(coolDown)
		game.ReplicatedStorage.rEvents.openCrystalRemote:InvokeServer('openCrystal', 'Blue Crystal')
	end
end)

Pets:AddToggle('Auto Purple', function(state)
	getgenv().AutoPurple = state
	while true do
		if not getgenv().AutoPurple then return end
		wait(coolDown)
		game.ReplicatedStorage.rEvents.openCrystalRemote:InvokeServer('openCrystal', 'Purple Crystal')
	end
end)

Pets:AddToggle('Auto Yellow', function(state)
	getgenv().AutoYellow = state
	while true do
		if not getgenv().AutoYellow then return end
		wait(coolDown)
		game.ReplicatedStorage.rEvents.openCrystalRemote:InvokeServer('openCrystal', 'Yellow Crystal')
	end
end)

Pets:AddToggle('Auto Lightning', function(state)
	getgenv().AutoLightning = state
	while true do
		if not getgenv().AutoLightning then return end
		wait(coolDown)
		game.ReplicatedStorage.rEvents.openCrystalRemote:InvokeServer('openCrystal', 'Lightning Crystal')
	end
end)

Pets:AddToggle('Auto Snow', function(state)
	getgenv().AutoSnow = state
	while true do
		if not getgenv().AutoSnow then return end
		wait(coolDown)
		game.ReplicatedStorage.rEvents.openCrystalRemote:InvokeServer('openCrystal', 'Snow Crystal')
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

Pets:AddToggle('Auto Lava', function(state)
	getgenv().AutoLava = state
	while true do
		if not getgenv().AutoLava then return end
		wait(coolDown)
		game.ReplicatedStorage.rEvents.openCrystalRemote:InvokeServer('openCrystal', 'Lava Crystal')
	end
end)

Pets:AddToggle('Auto Electro Legends', function(state)
	getgenv().AutoElectroLegends = state
	while true do
		if not getgenv().AutoElectroLegends then return end
		wait(coolDown)
		game.ReplicatedStorage.rEvents.openCrystalRemote:InvokeServer('openCrystal', 'Electro Legends Crystal')
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
	game.ReplicatedStorage.rEvents.changeSpeedJumpRemote:InvokeServer('changeSpeed', 2)
	game.ReplicatedStorage.rEvents.changeSpeedJumpRemote:InvokeServer('changeJump', 50)
	game.ReplicatedStorage.rEvents.changeSpeedJumpRemote:InvokeServer('changeSpeed', math.huge)
	game.ReplicatedStorage.rEvents.changeSpeedJumpRemote:InvokeServer('changeJump', math.huge)
	workspace.Gravity = 196.2
end)

Settings:AddToggle('Hide Popups', function(state)
	getgenv().HidePopups = state
	if not getgenv().HidePopups then player.PlayerGui.orbGui.Enabled = true player.PlayerGui.gameGui.trailsNotificationsFrame.Visible = true return end
	player.PlayerGui.orbGui.Enabled = false
	player.PlayerGui.gameGui.trailsNotificationsFrame.Visible = false
end)

Settings:AddButton('Destroy UI', function()
	ui.gui:Destroy()
	outerSpaceBindable:Destroy()
	speedDesertBindable:Destroy()
	antiAFK = false
	getgenv().AutoSpawners = false
	getgenv().AutoRings = false
	getgenv().AutoRebirth = false
	getgenv().AutoRace = false
	getgenv().AutoRed = false
	getgenv().AutoBlue = false
	getgenv().AutoPurple = false
	getgenv().AutoYellow = false
	getgenv().AutoLightning = false
	getgenv().AutoSnow = false
	getgenv().AutoInferno = false
	getgenv().AutoLava = false
	getgenv().AutoElectroLegends = false
	getgenv().InfiniteJump = false
	getgenv().Fly = false
	getgenv().Noclip = false
	getgenv().ClicktoTP = false
	if getgenv().HidePopups then player.PlayerGui.orbGui.Enabled = true player.PlayerGui.gameGui.trailsNotificationsFrame.Visible = true getgenv().HidePopups = false end
	game.ReplicatedStorage.rEvents.changeSpeedJumpRemote:InvokeServer('changeSpeed', 2)
	game.ReplicatedStorage.rEvents.changeSpeedJumpRemote:InvokeServer('changeJump', 50)
	game.ReplicatedStorage.rEvents.changeSpeedJumpRemote:InvokeServer('changeSpeed', math.huge)
	game.ReplicatedStorage.rEvents.changeSpeedJumpRemote:InvokeServer('changeJump', math.huge)
	workspace.Gravity = 196.2
end)
