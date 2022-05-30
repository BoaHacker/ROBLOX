--Laundry Simulator
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

function Teleport(cframe)
	player.Character.HumanoidRootPart.CFrame = CFrame.new(cframe.x, cframe.y + 5, cframe.z)
end

function GetBestClothing()
	local clothes = workspace.Debris.Clothing:GetChildren()
	local tiers = {
		Silver = {
			Multiplier = 3,
			UIColour = Color3.fromRGB(161, 161, 161)
		},
		Gold = {
			Multiplier = 10,
			UIColour = Color3.fromRGB(255, 170, 0)
		},
		Emerald = {
			Multiplier = 25,
			UIColour = Color3.fromRGB(18, 236, 6)
		},
		Ruby = {
			Multiplier = 25,
			UIColour = Color3.fromRGB(239, 0, 0)
		},
		Sapphire = {
			Multiplier = 25,
			UIColour = Color3.fromRGB(79, 215, 255)
		}
	}
	local topMultiplier = 1
	local topClothing = nil
	for i = 1, #clothes do
		local clothing = clothes[i]:FindFirstChildOfClass('StringValue')
		if clothing then
			if tiers[clothing.Value].Multiplier == 25 then return clothes[i] end
			if topMultiplier < tiers[clothing.Value].Multiplier then
				topClothing = clothes[i]
				topMultiplier = tiers[clothing.Value].Multiplier
			end
		end
	end
	if topClothing == nil then return workspace.Debris.Clothing:FindFirstChildOfClass('MeshPart') end
	return topClothing
end

function FillBasket()
	local timesToLoop = player.NonSaveVars.TotalWashingMachineCapacity.Value - player.NonSaveVars.BackpackAmount.Value
	if timesToLoop > player.NonSaveVars.BasketSize.Value then timesToLoop = player.NonSaveVars.BasketSize.Value end
	while player.NonSaveVars.BackpackAmount.Value ~= player.NonSaveVars.TotalWashingMachineCapacity.Value and player.NonSaveVars.BackpackAmount.Value ~= player.NonSaveVars.BasketSize.Value do
		local clothingPart = GetBestClothing()
		if clothingPart == nil then clothingPart = workspace.Debris.Clothing:FindFirstChildOfClass('MeshPart') end
		if clothingPart then
			Teleport(clothingPart.CFrame)
			game.ReplicatedStorage.Events.GrabClothing:FireServer(clothingPart)
		end
		wait(0.1)
	end
end

Main:AddToggle('Autofarm', function(state)
	getgenv().Autofarm = state
	while true do
		if not getgenv().Autofarm then return end
		wait()
		local washers = workspace.Plots[tostring(player.NonSaveVars.OwnsPlot.Value)].WashingMachines:GetChildren()
		for i = 1, #washers do
			local thisWasher = washers[i]
			if player.NonSaveVars.BasketStatus.Value == 'Clean' and player.NonSaveVars.BackpackAmount.Value > 0 then
				Teleport(workspace._FinishChute.Hinge.CFrame)
				game.ReplicatedStorage.Events.DropClothesInChute:FireServer()
			elseif thisWasher.Config.CycleFinished.Value then
				if player.NonSaveVars.BackpackAmount.Value == 0 or player.NonSaveVars.BasketStatus.Value == 'Clean' then
					Teleport(thisWasher.Parts.Part.CFrame)
					game.ReplicatedStorage.Events.UnloadWashingMachine:FireServer(thisWasher)
				end
			elseif thisWasher.Config.Started.Value == false then
				FillBasket()
				wait(0.1)
				Teleport(thisWasher.Parts.Part.CFrame)
				game.ReplicatedStorage.Events.LoadWashingMachine:FireServer(thisWasher)
			end
		end
	end
end)

Main:AddButton('Shop', function()
	Teleport(workspace.ArchysShopEntrance.Open.CFrame)
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

Settings:AddButton('Destroy UI', function()
	ui.gui:Destroy()
	antiAFK = false
	getgenv().Autofarm = false
	getgenv().InfiniteJump = false
	getgenv().Fly = false
	getgenv().Noclip = false
	getgenv().ClicktoTP = false
	player.Character.Humanoid.WalkSpeed = 20
	player.Character.Humanoid.JumpPower = 50
	workspace.Gravity = 196.2
end)
