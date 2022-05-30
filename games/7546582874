--Fish Game
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

local Player = ui:CreateWindow({
	text = 'Player'
})

local Settings = ui:CreateWindow({
	text = 'Settings'
})

for i, v in pairs(workspace['Lobby Room']:GetChildren()) do
	if v.Name == 'Bed stacks' then
		v:Destroy()
	end
end

local nutcase = Instance.new('Part', workspace)
nutcase.Anchored = true
nutcase.CanCollide = false
nutcase.Position = Vector3.new(1585, 35, 825)
nutcase.Size = Vector3.new(100, 485, 110)

local nutcaseRegion = Region3.new(nutcase.Position - (nutcase.Size/2), nutcase.Position + (nutcase.Size/2))
for i, v in pairs(workspace:FindPartsInRegion3(nutcaseRegion, nil, math.huge)) do
	v.CanCollide = false
end
nutcase:Destroy()

local bloodFloor = Instance.new('Part', workspace)
bloodFloor.Size = Vector3.new(150, 2, 150)
bloodFloor.Anchored = true
bloodFloor.Transparency = 0.5

player.PlayerGui.ScreenGui.TopSub.SubTitles.Text = 'Red Light!'
Main:AddToggle('Autofarm', function(state)
	getgenv().Autofarm = state
	while true do
		if not getgenv().Autofarm then return end
		game.RunService.Stepped:wait()
		local magnitude1 = (workspace['Game Teleport'].Position - player.Character.HumanoidRootPart.Position).magnitude
		player.Character.SprintScript.Disabled = true
		player.Character.Humanoid.WalkSpeed = 25
		if magnitude1 < 175 then
			if magnitude1 > 25 then
				player.Character.Humanoid:MoveTo(workspace['Game Teleport'].Position)
			end
		else
			if player.PlayerGui.ScreenGui.TopSub.SubTitles.Text == 'Red Light!' then
				player.Character.Humanoid:MoveTo(player.Character.HumanoidRootPart.Position)
			else
				local magnitude2 = (workspace.Game1.Girl.skirt3.Position - player.Character.HumanoidRootPart.Position).magnitude
				if magnitude2 >= 8 then
					player.Character.Humanoid:MoveTo(workspace.Game1.Girl.skirt3.Position)
				end
			end
		end
		for i, v in pairs(workspace.Game2.Walls:GetChildren()) do
			v:Destroy()
		end
		bloodFloor.Position = workspace.BloodRising.Blood.Position + Vector3.new(0, workspace.BloodRising.Blood.Size.Y/2, 0)
	end
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
		player.Character.SprintScript.Disabled = true
		player.Character.Humanoid.WalkSpeed = state.Text
	end
end)

Player:AddBox('Jumppower', function(state)
	if tonumber(state.Text) ~= nil then
		player.Character.SprintScript.Disabled = true
		player.Character.Humanoid.JumpHeight = state.Text
	end
end)

Player:AddBox('Gravity', function(state)
	if tonumber(state.Text) ~= nil then
		workspace.Gravity = state.Text
	end
end)

Player:AddButton('Reset to Default', function()
	player.Character.Humanoid.WalkSpeed = 16
	player.Character.Humanoid.JumpHeight = 7.2
	workspace.Gravity = 196.2
	player.Character.SprintScript.Disabled = false
end)

Settings:AddButton('Destroy UI', function()
	ui.gui:Destroy()
	bloodFloor:Destroy()
	antiAFK = false
	getgenv().Autofarm = false
	getgenv().InfiniteJump = false
	getgenv().Fly = false
	getgenv().Noclip = false
	getgenv().ClicktoTP = false
	player.Character.Humanoid.WalkSpeed = 16
	player.Character.Humanoid.JumpHeight = 7.2
	workspace.Gravity = 196.2
	player.Character.SprintScript.Disabled = false
end)
