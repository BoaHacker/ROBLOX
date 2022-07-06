--Granny
local ui = loadstring(game:HttpGet('https://raw.githubusercontent.com/BoaHacker/ROBLOX/main/ui', true))()
local esp = loadstring(game:HttpGet('https://raw.githubusercontent.com/BoaHacker/ROBLOX/main/esp', true))()

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

local maps = {
	[1] = 'House',
	[2] = 'HouseEz',
	[3] = 'House 2',
	[4] = 'House 2Ez',
	[5] = 'House 3',
	[6] = 'House 3Ez',
	[7] = 'School',
	[8] = 'Ski resort'
}

esp.Overrides.GetColor = function(model)
	if model.Name == 'Enemy' then return Color3.fromRGB(255, 0, 0) end
	return Color3.fromRGB(0, 255, 0)
end
Main:AddToggle('ESP', function(state)
	esp:Toggle(state)
end)

Main:AddToggle('Auto Escape Traps', function(state)
	getgenv().AutoEscapeTraps = state
	while true do
		if not getgenv().AutoEscapeTraps then return end
		wait()
		local character = player.Character or player.CharacterAdded:Wait()
		if character:WaitForChild('Humanoid').WalkSpeed == 0 then
			character:WaitForChild('Humanoid').WalkSpeed = 9
		end
		game.ReplicatedStorage.Events.EscapeTrap:FireServer()
	end
end)

Main:AddButton('Kill All (Granny)', function()
	if not player.Character:FindFirstChild('IsEnemy') or killing then return end
	killing = true
	for i, v in pairs(game.Players:GetChildren()) do
		if v ~= player and v.Character then
			repeat
				game.ReplicatedStorage.Events.Attack:FireServer()
				player.Character.HumanoidRootPart.CFrame = v.Character.HumanoidRootPart.CFrame
				wait()
			until v.Character:FindFirstChild('Dead')
		end
	end
	wait(1)
	killing = false
end)

local winA = {
	[1] = CFrame.new(118, 26, 81),
	[2] = CFrame.new(118, 26, 81),
	[3] = CFrame.new(13, 39, -161),
	[4] = CFrame.new(13, 39, -161),
	[5] = CFrame.new(13, 39, -239),
	[6] = CFrame.new(13, 39, -239),
	[7] = CFrame.new(-38, 5, -10),
	[8] = CFrame.new(57, 18, 76)
}
Teleports:AddButton('WinA', function()
	player.Character.HumanoidRootPart.CFrame = winA[game.ReplicatedStorage.Game.Mapid.Value]
end)

local winB = {
	[1] = CFrame.new(128, 7, 50),
	[2] = CFrame.new(128, 7, 50),
	[3] = CFrame.new(-14, 9, -180),
	[4] = CFrame.new(-14, 9, -180),
	[5] = CFrame.new(-52, 6, -212),
	[6] = CFrame.new(-52, 6, -212),
	[7] = CFrame.new(-89, 4, 75),
	[8] = CFrame.new(56, 18, 8)
}
Teleports:AddButton('WinB', function()
	player.Character.HumanoidRootPart.CFrame = winB[game.ReplicatedStorage.Game.Mapid.Value]
end)

Teleports:AddButton('Random Tool', function()
	function teleport()
		local folder = workspace.Map[maps[game.ReplicatedStorage.Game.Mapid.Value]].Tools.Map:GetChildren()
		local tool = folder[math.random(1, #folder)]
		if not tool.Item:FindFirstChild('Disabled') then
			player.Character.HumanoidRootPart.CFrame = tool.Handle.CFrame
		else
			teleport()
		end
	end
	teleport()
end)

Player:AddToggle('Infinite Jump', function(state)
	getgenv().InfiniteJump = state
	if not getgenv().InfiniteJump then if not getgenv().Noclip and player.Character.Humanoid.WalkSpeed == 9 and player.Character.Humanoid.JumpPower == 0 then player.Character.System.Disabled = false player.PlayerScripts.Client.Disabled = false end return end
	game.UserInputService.JumpRequest:connect(function()
		if not getgenv().InfiniteJump then return end
		player.PlayerScripts.Client.Disabled = true
		player.Character.System.Disabled = true
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
		if not getgenv().Noclip then if not getgenv().InfiniteJump and player.Character.Humanoid.WalkSpeed == 9 and player.Character.Humanoid.JumpPower == 0 then player.Character.HumanoidRootPart.CanCollide = true player.Character.System.Disabled = false player.PlayerScripts.Client.Disabled = false end return end
		player.PlayerScripts.Client.Disabled = true
		player.Character.System.Disabled = true
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
		player.PlayerScripts.Client.Disabled = true
		player.Character.System.Disabled = true
		player.Character.Humanoid.WalkSpeed = state.Text
	end
end)

Player:AddBox('Jumppower', function(state)
	if tonumber(state.Text) ~= nil then
		player.PlayerScripts.Client.Disabled = true
		player.Character.System.Disabled = true
		player.Character.Humanoid.JumpPower = state.Text
	end
end)

Player:AddBox('Gravity', function(state)
	if tonumber(state.Text) ~= nil then
		workspace.Gravity = state.Text
	end
end)

Player:AddButton('Reset to Default', function()
	player.Character.Humanoid.WalkSpeed = 9
	player.Character.Humanoid.JumpPower = 0
	workspace.Gravity = 196.2
	player.Character.System.Disabled = false
	player.PlayerScripts.Client.Disabled = false
end)

Settings:AddButton('Destroy UI', function()
	ui.gui:Destroy()
	antiAFK = false
	esp:Toggle(false)
	getgenv().AutoEscapeTraps = false
	getgenv().InfiniteJump = false
	getgenv().Fly = false
	getgenv().Noclip = false
	getgenv().ClicktoTP = false
	player.Character.Humanoid.WalkSpeed = 9
	player.Character.Humanoid.JumpPower = 0
	workspace.Gravity = 196.2
	player.Character.System.Disabled = false
	player.PlayerScripts.Client.Disabled = false
end)
