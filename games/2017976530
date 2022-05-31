--Soda Drinking Simulator
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

local Player = ui:CreateWindow({
	text = 'Player'
})

local Settings = ui:CreateWindow({
	text = 'Settings'
})

Main:AddToggle('Auto Drink', function(state)
	getgenv().AutoDrink = state
	while true do
		if not getgenv().AutoDrink then return end
		wait()
		local bTool = player.Backpack:FindFirstChildOfClass('Tool')
		local cTool = player.Character:FindFirstChildOfClass('Tool')
		if bTool then
			bTool.Parent = player.Character
		else
			player.Character.Soda.Drink:FireServer()
		end
	end
end)

Main:AddToggle('Auto Burp', function(state)
	getgenv().AutoBurp = state
	while true do
		if not getgenv().AutoBurp then return end
		wait()
		player.Character.Soda.Burp:FireServer()
	end
end)

Main:AddToggle('Auto Stunt', function(state)
	getgenv().AutoStunt = state
	while true do
		if not getgenv().AutoStunt then return end
		wait()
		player.Character.Humanoid.Jump = true
		game.ReplicatedStorage.PerformStunt:FireServer(player.Character.HumanoidRootPart.Position.Y)
	end
end)

Main:AddToggle('Auto Rebirth', function(state)
	getgenv().AutoRebirth = state
	while true do
		if not getgenv().AutoRebirth then return end
		wait()
		game.ReplicatedStorage.RebirthMe:FireServer()
	end
end)

Main:AddToggle('Auto Upgrade', function(state)
	getgenv().AutoUpgrade = state
	while true do
		if not getgenv().AutoUpgrade then return end
		wait()
		game.ReplicatedStorage.EquipSoda:FireServer(player.otherstats.SodaCan.Value + 1)
		game.ReplicatedStorage.EquipStunt:FireServer(player.otherstats.Stunt.Value + 1)
	end
end)

Teleports:AddButton('Lobby', function()
	local folder = workspace['Main Area'].Spawns:GetChildren()
	local spawn = folder[math.random(1, #folder)]
	player.Character.HumanoidRootPart.CFrame = spawn.CFrame * CFrame.new(0, 5, 0)
end)

Teleports:AddButton('PVP Area', function()
	local folder = workspace['PVP Area'].Spawns:GetChildren()
	local spawn = folder[math.random(1, #folder)]
	player.Character.HumanoidRootPart.CFrame = spawn.CFrame * CFrame.new(0, 5, 0)
end)

Teleports:AddButton('Fourth of July Area', function()
	local folder = workspace['Fourth of July Area'].Spawns:GetChildren()
	local spawn = folder[math.random(1, #folder)]
	player.Character.HumanoidRootPart.CFrame = spawn.CFrame * CFrame.new(0, 5, 0)
end)

Teleports:AddButton('Moke Area', function()
	local folder = workspace['Moke Area'].Spawns:GetChildren()
	local spawn = folder[math.random(1, #folder)]
	player.Character.HumanoidRootPart.CFrame = spawn.CFrame * CFrame.new(0, 5, 0)
end)

Teleports:AddButton('Cyber Area', function()
	local folder = workspace['Cyber Area'].Spawns:GetChildren()
	local spawn = folder[math.random(1, #folder)]
	player.Character.HumanoidRootPart.CFrame = spawn.CFrame * CFrame.new(0, 5, 0)
end)

Teleports:AddButton('Disco Party', function()
	local folder = workspace['Disco Party'].Spawns:GetChildren()
	local spawn = folder[math.random(1, #folder)]
	player.Character.HumanoidRootPart.CFrame = spawn.CFrame * CFrame.new(0, 5, 0)
end)

Teleports:AddButton('Candy Land', function()
	local folder = workspace['Candy Land'].Spawns:GetChildren()
	local spawn = folder[math.random(1, #folder)]
	player.Character.HumanoidRootPart.CFrame = spawn.CFrame * CFrame.new(0, 5, 0)
end)

Teleports:AddButton('Jungle', function()
	local folder = workspace['Jungle'].Spawns:GetChildren()
	local spawn = folder[math.random(1, #folder)]
	player.Character.HumanoidRootPart.CFrame = spawn.CFrame * CFrame.new(0, 5, 0)
end)

Teleports:AddButton('Disco Dancer', function()
	player.Character.HumanoidRootPart.CFrame = workspace['Disco Party']['Disco Balls']['Big Disco Ball'].Part.CFrame
end)

Teleports:AddButton('Coconut Man', function()
	workspace.Jungle.Props.Meteorite.Main.CanCollide = false
	player.Character.HumanoidRootPart.CFrame = workspace.Jungle.Props.Meteorite.Main.CFrame
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
	player.Character.Humanoid.WalkSpeed = player.speedstats.MaxSpeed.Value
	player.Character.Humanoid.JumpPower = 50
	workspace.Gravity = 196.2
end)

Settings:AddButton('Destroy UI', function()
	ui.gui:Destroy()
	antiAFK = false
	getgenv().AutoDrink = false
	getgenv().AutoBurp = false
	getgenv().AutoStunt = false
	getgenv().AutoRebirth = false
	getgenv().AutoUpgrade = false
	getgenv().InfiniteJump = false
	getgenv().Fly = false
	getgenv().Noclip = false
	getgenv().ClicktoTP = false
	player.Character.Humanoid.WalkSpeed = player.speedstats.MaxSpeed.Value
	player.Character.Humanoid.JumpPower = 50
	workspace.Gravity = 196.2
end)
