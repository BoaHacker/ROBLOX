--MeepCity Racing: Pyramids
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

local Settings = ui:CreateWindow({
	text = 'Settings'
})

local nodes = 0
for i, v in pairs(workspace.Map.Nodes:GetChildren()) do
	nodes = nodes + 1
end
Main:AddToggle('Autofarm', function(state)
	getgenv().Autofarm = state
	while true do
		if not getgenv().Autofarm then return end
		wait()
		game.ReplicatedStorage.ConnectionEvent:FireServer(2, 1)
		game.ReplicatedStorage.ConnectionEvent:FireServer(2, 2)
		game.ReplicatedStorage.ConnectionEvent:FireServer(2, nodes)
	end
end)

Settings:AddButton('Destroy UI', function()
	ui.gui:Destroy()
	antiAFK = false
	getgenv().Autofarm = false
end)
