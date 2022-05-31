--Red Light Green Light
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

for i, v in pairs(workspace.Mechanics.Houses:GetDescendants()) do
	if v.ClassName == 'Part' or v.ClassName == 'UnionOperation' then
		v.CanCollide = false
	end
end
for i, v in pairs(workspace.Walls:GetChildren()) do
	if v.ClassName == 'Part' then
		v.CanCollide = false
	end
end
Main:AddToggle('Autofarm', function(state)
	getgenv().Autofarm = state
	while true do
		if not getgenv().Autofarm then return end
		game.RunService.Stepped:wait()
		local music = game.ReplicatedStorage.Assets.Sounds.Music
		if music.EqualizerSoundEffect.HighGain ~= 0 and music.EqualizerSoundEffect.LowGain ~= 0 and music.EqualizerSoundEffect.MidGain ~= 0 then
			if player.PlayerGui.GuardUI.DialogueFrame.Information.Text == 'Make your way to the first game.' or player.PlayerGui.GuardUI.DialogueFrame.Information.Text == 'Make your way to the second game.' or player.PlayerGui.GuardUI.DialogueFrame.Information.Text == 'Make your way to the third game.' or player.PlayerGui.GuardUI.DialogueFrame.Information.Text == 'Make your way to the fourth game.' or player.PlayerGui.GuardUI.DialogueFrame.Information.Text == 'Make your way to the fifth game.' or player.PlayerGui.GuardUI.DialogueFrame.Information.Text == 'Make your way to the sixth game.' then
				game.ReplicatedStorage.Remotes.ReachedGoal:FireServer(workspace.Mechanics.GoalPart1)
				player.PlayerGui.GuardUI.DialogueFrame.Information.Text = 'Teleported to the next game!'
			end
			if player.PlayerGui.GuardUI.DialogueFrame.Information.Text == 'On green light, get as far as you can towards the end. If you move on red light, you will be eliminated.' then
				if player.PlayerGui.RLGL.Light.TextLabel.Text == 'Red Light!' then
					player.Character.Humanoid.WalkSpeed = 16
					player.Character.Humanoid:MoveTo(player.Character.HumanoidRootPart.Position)
				else
					player.Character.Humanoid.WalkSpeed = 20
					player.Character.Humanoid:MoveTo(workspace.Mechanics.GFDoll.Skirt.Position)
				end
			end
			if player.PlayerGui.GuardUI.DialogueFrame.Information.Text == 'Carefully trace out your cookie without breaking it!' and workspace.Camera.CameraType == Enum.CameraType.Scriptable then
				game.ReplicatedStorage.Remotes.HoneyCombResult:FireServer(true)
				workspace.Camera.CameraType = Enum.CameraType.Custom
				wait(1)
				player.Character.Humanoid:UnequipTools()
				game.UserInputService.ModalEnabled = false
			end
			if player.PlayerGui.FrontmanUI.MarbleChoose.Visible == true then
				game.ReplicatedStorage.Remotes.MarblesPlayerChoice:FireServer('Classic')
				player.PlayerGui.FrontmanUI.MarbleChoose.Visible = false
			end
			if player.PlayerGui.GuardUI.DialogueFrame.Information.Text == 'Use the green arrow to aim your marble, knock out as many marbles as possible.' and workspace.Camera.CameraSubject ~= player.Character.Humanoid or player.PlayerGui.GuardUI.DialogueFrame.Information.Text == 'When its your turn, use the green arrow to aim your marble, knock out as many marbles as possible.' and workspace.Camera.CameraSubject ~= player.Character.Humanoid then
				local cameraSubject = workspace.Camera.CameraSubject
				cameraSubject.EndPoint.WorldPosition = cameraSubject.Parent.LoseMarbles:FindFirstChild('Marble').Position
				cameraSubject.Beam.Enabled = false
				game.ReplicatedStorage.Remotes.MarbleRemote:FireServer()
				cameraSubject:ApplyImpulse(cameraSubject.EndPoint.Position.Unit * math.clamp(cameraSubject.EndPoint.Position.Magnitude, 6, 6) * Vector3.new(1.5, 0, 1.5))
				workspace.Camera.CameraSubject = player.Character.Humanoid
				player.PlayerGui.MarbleUi.MarbleFrame.Frame_MOBILE.Visible = false
				player.PlayerGui.MarbleUi.MarbleFrame.Frame.Visible = false
			end
			if player.PlayerGui.GuardUI.DialogueFrame.Information.Text == 'Hint: glass that glows is safe, try to memorize the pattern.' then
				local magnitude = (Vector3.new(-501, 80, -481) - player.Character.HumanoidRootPart.Position).magnitude
				if magnitude > 10 then
					player.Character.HumanoidRootPart.CFrame = CFrame.new(-501, 80, -481)
				end
			end
			if player.PlayerGui.GuardUI.DialogueFrame.Information.Text == 'be te last standing player' then
				local bTool = player.Backpack:FindFirstChild('Fists')
				local cTool = player.Character:FindFirstChild('Fists')
				if bTool then
					bTool.Parent = player.Character
				else
					for i, v in pairs(game.Players:GetChildren()) do
						if v ~= player then
							game.ReplicatedStorage.Remotes.PunchEvent:FireServer(v.Character)
						end
					end
				end
				local magnitude = (Vector3.new(-314, 3, 327) - player.Character.HumanoidRootPart.Position).magnitude
				if magnitude > 5 then
					player.Character.HumanoidRootPart.CFrame = CFrame.new(-314, 3, 327)
				end
			end
			game.ReplicatedStorage.Pull:FireServer(1)
		end
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
	player.Character.Humanoid.WalkSpeed = 25
	player.Character.Humanoid.JumpPower = 50
	workspace.Gravity = 196.2
end)

Settings:AddButton('Destroy UI', function()
	ui.gui:Destroy()
	antiAFK = false
	getgenv().Autofarm = false
	getgenv().InfiniteJump = false
	getgenv().Fly = false
	getgenv().Noclip = false
	getgenv().ClicktoTP = false
	player.Character.Humanoid.WalkSpeed = 25
	player.Character.Humanoid.JumpPower = 50
	workspace.Gravity = 196.2
end)
