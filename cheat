local placeId = 'https://raw.githubusercontent.com/BoaHacker/ROBLOX/main/games/'.. game.PlaceId
local found, notFound = pcall(function()
	game:HttpGet(placeId)
end)

if placeId and found then
	loadstring(game:HttpGet(placeId, true))()
else
	loadstring(game:HttpGet('https://raw.githubusercontent.com/BoaHacker/ROBLOX/main/games/unknown', true))()
end
