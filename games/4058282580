--Boxing Simulator
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

Main:AddToggle('Auto Punch', function(state)
	getgenv().AutoPunch = state
	while true do
		if not getgenv().AutoPunch then return end
		wait()
		local bTool = player.Backpack:FindFirstChildOfClass('Tool')
		local cTool = player.Character:FindFirstChildOfClass('Tool')
		if bTool then
			bTool.Parent = player.Character
		else
			cTool:Activate()
		end
	end
end)

Main:AddToggle('Auto Sell', function(state)
	getgenv().AutoSell = state
	while true do
		if not getgenv().AutoSell then return end
		wait()
		game.ReplicatedStorage.Events.SellRequest:FireServer(true)
	end
end)

Main:AddToggle('Auto Upgrade', function(state)
	getgenv().AutoUpgrade = state
	while true do
		if not getgenv().AutoUpgrade then return end
		wait()
		local Frame = player.PlayerGui.Progress.Frame
		if Frame.DNA.Clipped.Full.Fill.BackgroundColor3 == Color3.fromRGB(95, 255, 84) or Frame.Gloves.Clipped.Full.Fill.BackgroundColor3 == Color3.fromRGB(95, 255, 84) then
			game.ReplicatedStorage.Events.BuyAllDNA:FireServer()
			game.ReplicatedStorage.Events.BuyAllGlove:FireServer()
			game.ReplicatedStorage.Events.BuyClass:FireServer(player.Data.HighestClass.Value + 1)
		end
	end
end)

Main:AddToggle('Auto Boss', function(state)
	getgenv().AutoBoss = state
	while true do
		if not getgenv().AutoBoss then return end
		wait()
		local bTool = player.Backpack:FindFirstChildOfClass('Tool')
		local cTool = player.Character:FindFirstChildOfClass('Tool')
		local boss = workspace.Boss:FindFirstChildOfClass('Model')
		if bTool then
			bTool.Parent = player.Character
		else
			boss.Head.CanCollide = false
			player.Character.HumanoidRootPart.CFrame = boss.Head.CFrame
			cTool:Activate()
		end
	end
end)

Main:AddToggle('Auto Spawners', function(state)
	getgenv().AutoSpawners = state
	while true do
		if not getgenv().AutoSpawners then return end
		wait()
		for i, v in pairs(workspace.Canes:GetChildren()) do
			local OldCanePosition = v.HumanoidRootPart.CFrame
			v.HumanoidRootPart.CFrame = player.Character.HumanoidRootPart.CFrame
			wait()
			v.HumanoidRootPart.CFrame = OldCanePosition
		end
		for i, v in pairs(workspace.Coins:GetChildren()) do
			local OldCoinPosition = v.HumanoidRootPart.CFrame
			v.HumanoidRootPart.CFrame = player.Character.HumanoidRootPart.CFrame
			wait()
			v.HumanoidRootPart.CFrame = OldCoinPosition
		end
	end
end)

Main:AddToggle('Auto Gems', function(state)
	getgenv().AutoGems = state
	while true do
		if not getgenv().AutoGems then return end
		wait()
		for i, v in pairs(workspace.Boxes:GetChildren()) do
			local bTool = player.Backpack:FindFirstChildOfClass('Tool')
			local cTool = player.Character:FindFirstChildOfClass('Tool')
			if bTool then
				bTool.Parent = player.Character
			else
				local OldBoxPosition = v.Root.CFrame
				v.Root.CFrame = player.Character.HumanoidRootPart.CFrame
				cTool:Activate()
				wait()
				v.Root.CFrame = OldBoxPosition
			end
		end
	end
end)

Teleports:AddButton('Lobby', function()
	player.Character.HumanoidRootPart.CFrame = workspace.SpawnLocation.CFrame * CFrame.new(0, 5, 0)
end)

Teleports:AddButton('Desert Dream', function()
	player.Character.HumanoidRootPart.CFrame = workspace.IslandTeleport.DesertDream.CFrame
end)

Teleports:AddButton('Winter Wonderland', function()
	player.Character.HumanoidRootPart.CFrame = workspace.IslandTeleport.WinterWonderland.CFrame
end)

Teleports:AddButton('Mysterious Moon', function()
	player.Character.HumanoidRootPart.CFrame = workspace.IslandTeleport.MysteriousMoon.CFrame
end)

Teleports:AddButton('Glistering Galaxy', function()
	player.Character.HumanoidRootPart.CFrame = workspace.IslandTeleport.GlisteringGalaxy.CFrame
end)

Teleports:AddButton('Fascinating Fire', function()
	player.Character.HumanoidRootPart.CFrame = workspace.IslandTeleport.FascinatingFire.CFrame
end)

Teleports:AddButton('Vast Volcanoes', function()
	player.Character.HumanoidRootPart.CFrame = workspace.IslandTeleport.VastVolcanoes.CFrame
end)

Teleports:AddButton('Wacky Waters', function()
	player.Character.HumanoidRootPart.CFrame = workspace.IslandTeleport.WackyWaters.CFrame
end)

Teleports:AddButton('Sparky Storms', function()
	player.Character.HumanoidRootPart.CFrame = workspace.IslandTeleport.SparkyStorms.CFrame
end)

Teleports:AddButton('Imaginative Infinity', function()
	player.Character.HumanoidRootPart.CFrame = workspace.IslandTeleport.ImaginativeInfinity.CFrame
end)

Teleports:AddButton('Mighty Magma', function()
	player.Character.HumanoidRootPart.CFrame = workspace.IslandTeleport.MightyMagma.CFrame
end)

local coolDown = 0.1
Pets:AddToggle('Auto Hatch Basic', function(state)
	getgenv().AutoBasic = state
	while true do
		if not getgenv().AutoBasic then return end
		wait(coolDown)
		game.ReplicatedStorage.Events.BuyEgg:FireServer('basic', false)
	end
end)

Pets:AddToggle('Auto Hatch Sand', function(state)
	getgenv().AutoSand = state
	while true do
		if not getgenv().AutoSand then return end
		wait(coolDown)
		game.ReplicatedStorage.Events.BuyEgg:FireServer('uncommon', false)
	end
end)

Pets:AddToggle('Auto Hatch Earth', function(state)
	getgenv().AutoEarth = state
	while true do
		if not getgenv().AutoEarth then return end
		wait(coolDown)
		game.ReplicatedStorage.Events.BuyEgg:FireServer('rare', false)
	end
end)

Pets:AddToggle('Auto Hatch Gummy', function(state)
	getgenv().AutoGummy = state
	while true do
		if not getgenv().AutoGummy then return end
		wait(coolDown)
		game.ReplicatedStorage.Events.BuyEgg:FireServer('epic', false)
	end
end)

Pets:AddToggle('Auto Hatch Void', function(state)
	getgenv().AutoVoid = state
	while true do
		if not getgenv().AutoVoid then return end
		wait(coolDown)
		game.ReplicatedStorage.Events.BuyEgg:FireServer('legendary', false)
	end
end)

Pets:AddToggle('Auto Hatch Epic', function(state)
	getgenv().AutoEpic = state
	while true do
		if not getgenv().AutoEpic then return end
		wait(coolDown)
		game.ReplicatedStorage.Events.BuyEgg:FireServer('godly', false)
	end
end)

Pets:AddToggle('Auto Hatch Dominus', function(state)
	getgenv().AutoDominus = state
	while true do
		if not getgenv().AutoDominus then return end
		wait(coolDown)
		game.ReplicatedStorage.Events.BuyEgg:FireServer('mythical', false)
	end
end)

Pets:AddToggle('Auto Hatch Moon', function(state)
	getgenv().AutoMoon = state
	while true do
		if not getgenv().AutoMoon then return end
		wait(coolDown)
		game.ReplicatedStorage.Events.BuyEgg:FireServer('divine', false)
	end
end)

Pets:AddToggle('Auto Hatch Planet', function(state)
	getgenv().AutoPlanet = state
	while true do
		if not getgenv().AutoPlanet then return end
		wait(coolDown)
		game.ReplicatedStorage.Events.BuyEgg:FireServer('arcane', false)
	end
end)

Pets:AddToggle('Auto Hatch Fire', function(state)
	getgenv().AutoFire = state
	while true do
		if not getgenv().AutoFire then return end
		wait(coolDown)
		game.ReplicatedStorage.Events.BuyEgg:FireServer('mystic', false)
	end
end)

Pets:AddToggle('Auto Hatch Magma', function(state)
	getgenv().AutoCelestial = state
	while true do
		if not getgenv().AutoCelestial then return end
		wait(coolDown)
		game.ReplicatedStorage.Events.BuyEgg:FireServer('celestial', false)
	end
end)

Pets:AddToggle('Auto Hatch Water', function(state)
	getgenv().AutoWater = state
	while true do
		if not getgenv().AutoWater then return end
		wait(coolDown)
		game.ReplicatedStorage.Events.BuyEgg:FireServer('supreme', false)
	end
end)

Pets:AddToggle('Auto Hatch Infinity', function(state)
	getgenv().AutoInfinity = state
	while true do
		if not getgenv().AutoInfinity then return end
		wait(coolDown)
		game.ReplicatedStorage.Events.BuyEgg:FireServer('infinity', false)
	end
end)

Pets:AddToggle('Auto Hatch Magma', function(state)
	getgenv().AutoMagma = state
	while true do
		if not getgenv().AutoMagma then return end
		wait(coolDown)
		game.ReplicatedStorage.Events.BuyEgg:FireServer('magma', false)
	end
end)

Pets:AddToggle('Auto Hatch Easter', function(state)
	getgenv().AutoEaster = state
	while true do
		if not getgenv().AutoEaster then return end
		wait(coolDown)
		game.ReplicatedStorage.Events.BuyEgg:FireServer('easter', false)
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
	player.Character.Humanoid.WalkSpeed = 16
	player.Character.Humanoid.JumpPower = 50
	workspace.Gravity = 196.2
end)

Settings:AddToggle('Hide Popups', function(state)
	getgenv().HidePopups = state
	if not getgenv().HidePopups then player.PlayerGui.Notifications.Enabled = true player.PlayerGui.Frames.SellNotify.Main.Visible = true player.PlayerGui.Effects.Enabled = true return end
	player.PlayerGui.Notifications.Enabled = false
	player.PlayerGui.Frames.SellNotify.Main.Visible = false
	player.PlayerGui.Effects.Enabled = false
end)

Settings:AddButton('Destroy UI', function()
	ui.gui:Destroy()
	antiAFK = false
	getgenv().AutoPunch = false
	getgenv().AutoSell = false
	getgenv().AutoUpgrade = false
	getgenv().AutoBoss = false
	getgenv().AutoSpawners = false
	getgenv().AutoGems = false
	getgenv().AutoBasic = false
	getgenv().AutoSand = false
	getgenv().AutoEarth = false
	getgenv().AutoGummy = false
	getgenv().AutoVoid = false
	getgenv().AutoEpic = false
	getgenv().AutoDominus = false
	getgenv().AutoMoon = false
	getgenv().AutoPlanet = false
	getgenv().AutoFire = false
	getgenv().AutoCelestial = false
	getgenv().AutoWater = false
	getgenv().AutoInfinity = false
	getgenv().AutoMagma = false
	getgenv().AutoEaster = false
	getgenv().InfiniteJump = false
	getgenv().Fly = false
	getgenv().Noclip = false
	getgenv().ClicktoTP = false
	if getgenv().HidePopups then player.PlayerGui.Notifications.Enabled = true player.PlayerGui.Frames.SellNotify.Main.Visible = true player.PlayerGui.Effects.Enabled = true getgenv().HidePopups = false end
	player.Character.Humanoid.WalkSpeed = 16
	player.Character.Humanoid.JumpPower = 50
	workspace.Gravity = 196.2
end)
