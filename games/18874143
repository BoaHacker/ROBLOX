--MeepCity Racing: Lobby

local player = game.Players.LocalPlayer
local antiAFK = true
player.Idled:connect(function()
	if antiAFK then
		game.VirtualUser:Button2Down(Vector2.new(0, 0), workspace.CurrentCamera.CFrame)
		wait(1)
		game.VirtualUser:Button2Up(Vector2.new(0, 0), workspace.CurrentCamera.CFrame)
	end
end)

game.ReplicatedStorage.PlayerData[player.UserId].PLUS.Value = true
