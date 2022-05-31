--MeepCity: StarBall - Volcanic
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

function Win()
	while true do
		wait()
		for i, v in pairs(workspace.MapObject:GetChildren()) do
			if v.Name == 'STAR' then
				v.CFrame = workspace['Ball_'.. player.UserId].CFrame
				wait()
				v.CFrame = CFrame.new(0, 0, 0)
			end
			if v.Name == 'FINISH' and v.ClassName == 'Part' then
				local main = player.PlayerGui.ScreenGui.Game.Main
				local yellowStar = 'rbxassetid://303890071'
				if main.Star1.Image == yellowStar and main.Star2.Image == yellowStar and main.Star3.Image == yellowStar then
					v.CanCollide = false
					v.CFrame = workspace['Ball_'.. player.UserId].CFrame
					wait()
					v.CFrame = CFrame.new(0, 0, 0)
				end
			end
		end
	end
end
workspace.MapObject.DescendantAdded:Connect(function(state)
	if not getgenv().Autofarm then return end
	Win()
end)
Main:AddToggle('Autofarm', function(state)
	getgenv().Autofarm = state
	if not getgenv().Autofarm then return end
	Win()
end)

Settings:AddButton('Destroy UI', function()
	ui.gui:Destroy()
	antiAFK = false
	getgenv().Autofarm = false
end)
