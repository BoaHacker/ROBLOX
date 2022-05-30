local esp = {
	Enabled = false,
	Boxes = true,
	BoxShift = CFrame.new(0,-1.5,0),
	BoxSize = Vector3.new(4,6,0),
	Color = Color3.fromRGB(255, 170, 0),
	FaceCamera = false,
	Names = true,
	TeamColor = true,
	Thickness = 2,
	AttachShift = 1,
	TeamMates = true,
	Players = true,

	Objects = setmetatable({}, {__mode='kv'}),
	Overrides = {}
}

local camera = workspace.CurrentCamera
local player = game.Players.LocalPlayer
local worldToViewportPoint = camera.worldToViewportPoint

local function Draw(obj, props)
	local new = Drawing.new(obj)

	props = props or {}
	for i,v in pairs(props) do
		new[i] = v
	end
	return new
end

function esp:GetTeam(p)
	local ov = self.Overrides.GetTeam
	if ov then
		return ov(p)
	end

	return p and p.Team
end

function esp:IsTeamMate(p)
	local ov = self.Overrides.IsTeamMate
	if ov then
		return ov(p)
	end

	return self:GetTeam(p) == self:GetTeam(player)
end

function esp:GetColor(obj)
	local ov = self.Overrides.GetColor
	if ov then
		return ov(obj)
	end
	local p = self:GetPlrFromChar(obj)
	return p and self.TeamColor and p.Team and p.Team.TeamColor.Color or self.Color
end

function esp:GetPlrFromChar(char)
	local ov = self.Overrides.GetPlrFromChar
	if ov then
		return ov(char)
	end

	return game.Players:GetPlayerFromCharacter(char)
end

function esp:Toggle(bool)
	self.Enabled = bool
	if not bool then
		for i,v in pairs(self.Objects) do
			if v.Type == 'Box' then
				if v.Temporary then
					v:Remove()
				else
					for i,v in pairs(v.Components) do
						v.Visible = false
					end
				end
			end
		end
	end
end

function esp:GetBox(obj)
	return self.Objects[obj]
end

function esp:AddObjectListener(parent, options)
	local function NewListener(c)
		if type(options.Type) == 'string' and c:IsA(options.Type) or options.Type == nil then
			if type(options.Name) == 'string' and c.Name == options.Name or options.Name == nil then
				if not options.Validator or options.Validator(c) then
					local box = esp:Add(c, {
						PrimaryPart = type(options.PrimaryPart) == 'string' and c:WaitForChild(options.PrimaryPart) or type(options.PrimaryPart) == 'function' and options.PrimaryPart(c),
						Color = type(options.Color) == 'function' and options.Color(c) or options.Color,
						ColorDynamic = options.ColorDynamic,
						Name = type(options.CustomName) == 'function' and options.CustomName(c) or options.CustomName,
						IsEnabled = options.IsEnabled,
						RenderInNil = options.RenderInNil
					})
					if options.OnAdded then
						coroutine.wrap(options.OnAdded)(box)
					end
				end
			end
		end
	end

	if options.Recursive then
		parent.DescendantAdded:Connect(NewListener)
		for i,v in pairs(parent:GetDescendants()) do
			coroutine.wrap(NewListener)(v)
		end
	else
		parent.ChildAdded:Connect(NewListener)
		for i,v in pairs(parent:GetChildren()) do
			coroutine.wrap(NewListener)(v)
		end
	end
end

local boxBase = {}
boxBase.__index = boxBase

function boxBase:Remove()
	esp.Objects[self.Object] = nil
	for i,v in pairs(self.Components) do
		v.Visible = false
		v:Remove()
		self.Components[i] = nil
	end
end

function boxBase:Update()
	if not self.PrimaryPart then
		return self:Remove()
	end

	local color
	if esp.Highlighted == self.Object then
		color = esp.HighlightColor
	else
		color = self.Color or self.ColorDynamic and self:ColorDynamic() or esp:GetColor(self.Object) or esp.Color
	end

	local allow = true
	if esp.Overrides.UpdateAllow and not esp.Overrides.UpdateAllow(self) then
		allow = false
	end
	if self.Player and not esp.TeamMates and esp:IsTeamMate(self.Player) then
		allow = false
	end
	if self.Player and not esp.Players then
		allow = false
	end
	if self.IsEnabled and (type(self.IsEnabled) == 'string' and not esp[self.IsEnabled] or type(self.IsEnabled) == 'function' and not self:IsEnabled()) then
		allow = false
	end
	if not workspace:IsAncestorOf(self.PrimaryPart) and not self.RenderInNil then
		allow = false
	end

	if not allow then
		for i,v in pairs(self.Components) do
			v.Visible = false
		end
		return
	end

	if esp.Highlighted == self.Object then
		color = esp.HighlightColor
	end

	local cf = self.PrimaryPart.CFrame
	if esp.FaceCamera then
		cf = CFrame.new(cf.p, camera.CFrame.p)
	end
	local size = self.Size
	local locs = {
		TopLeft = cf * esp.BoxShift * CFrame.new(size.X/2,size.Y/2,0),
		TopRight = cf * esp.BoxShift * CFrame.new(-size.X/2,size.Y/2,0),
		BottomLeft = cf * esp.BoxShift * CFrame.new(size.X/2,-size.Y/2,0),
		BottomRight = cf * esp.BoxShift * CFrame.new(-size.X/2,-size.Y/2,0),
		TagPos = cf * esp.BoxShift * CFrame.new(0,size.Y/2,0),
		Torso = cf * esp.BoxShift
	}

	if esp.Boxes then
		local TopLeft, Vis1 = worldToViewportPoint(camera, locs.TopLeft.p)
		local TopRight, Vis2 = worldToViewportPoint(camera, locs.TopRight.p)
		local BottomLeft, Vis3 = worldToViewportPoint(camera, locs.BottomLeft.p)
		local BottomRight, Vis4 = worldToViewportPoint(camera, locs.BottomRight.p)

		if self.Components.Quad then
			if Vis1 or Vis2 or Vis3 or Vis4 then
				self.Components.Quad.Visible = true
				self.Components.Quad.PointA = Vector2.new(TopRight.X, TopRight.Y)
				self.Components.Quad.PointB = Vector2.new(TopLeft.X, TopLeft.Y)
				self.Components.Quad.PointC = Vector2.new(BottomLeft.X, BottomLeft.Y)
				self.Components.Quad.PointD = Vector2.new(BottomRight.X, BottomRight.Y)
				self.Components.Quad.Color = color
			else
				self.Components.Quad.Visible = false
			end
		end
	else
		self.Components.Quad.Visible = false
	end

	if esp.Names then
		local TagPos, Vis5 = worldToViewportPoint(camera, locs.TagPos.p)

		if Vis5 then
			self.Components.Name.Visible = true
			self.Components.Name.Position = Vector2.new(TagPos.X, TagPos.Y)
			self.Components.Name.Text = self.Name
			self.Components.Name.Color = color

			self.Components.Distance.Visible = true
			self.Components.Distance.Position = Vector2.new(TagPos.X, TagPos.Y + 14)
			self.Components.Distance.Text = math.floor((camera.CFrame.p - cf.p).magnitude) ..'m away'
			self.Components.Distance.Color = color
		else
			self.Components.Name.Visible = false
			self.Components.Distance.Visible = false
		end
	else
		self.Components.Name.Visible = false
		self.Components.Distance.Visible = false
	end

	if esp.Tracers then
		local TorsoPos, Vis6 = worldToViewportPoint(camera, locs.Torso.p)

		if Vis6 then
			self.Components.Tracer.Visible = true
			self.Components.Tracer.From = Vector2.new(TorsoPos.X, TorsoPos.Y)
			self.Components.Tracer.To = Vector2.new(camera.ViewportSize.X/2,camera.ViewportSize.Y/esp.AttachShift)
			self.Components.Tracer.Color = color
		else
			self.Components.Tracer.Visible = false
		end
	else
		self.Components.Tracer.Visible = false
	end
end

function esp:Add(obj, options)
	if not obj.Parent and not options.RenderInNil then
		return warn(obj, 'has no parent')
	end

	local box = setmetatable({
		Name = options.Name or obj.Name,
		Type = 'Box',
		Color = options.Color,
		Size = options.Size or self.BoxSize,
		Object = obj,
		Player = options.Player or game.Players:GetPlayerFromCharacter(obj),
		PrimaryPart = options.PrimaryPart or obj.ClassName == 'Model' and (obj.PrimaryPart or obj:FindFirstChild('HumanoidRootPart') or obj:FindFirstChildWhichIsA('BasePart')) or obj:IsA('BasePart') and obj,
		Components = {},
		IsEnabled = options.IsEnabled,
		Temporary = options.Temporary,
		ColorDynamic = options.ColorDynamic,
		RenderInNil = options.RenderInNil
	}, boxBase)

	if self:GetBox(obj) then
		self:GetBox(obj):Remove()
	end

	box.Components['Quad'] = Draw('Quad', {
		Thickness = self.Thickness,
		Color = color,
		Transparency = 1,
		Filled = false,
		Visible = self.Enabled and self.Boxes
	})
	box.Components['Name'] = Draw('Text', {
		Text = box.Name,
		Color = box.Color,
		Center = true,
		Outline = true,
		Size = 19,
		Visible = self.Enabled and self.Names
	})
	box.Components['Distance'] = Draw('Text', {
		Color = box.Color,
		Center = true,
		Outline = true,
		Size = 19,
		Visible = self.Enabled and self.Names
	})

	box.Components['Tracer'] = Draw('Line', {
		Thickness = esp.Thickness,
		Color = box.Color,
		Transparency = 1,
		Visible = self.Enabled and self.Tracers
	})
	self.Objects[obj] = box

	obj.AncestryChanged:Connect(function(_, parent)
		if parent == nil and esp.AutoRemove ~= false then
			box:Remove()
		end
	end)
	obj:GetPropertyChangedSignal('Parent'):Connect(function()
		if obj.Parent == nil and esp.AutoRemove ~= false then
			box:Remove()
		end
	end)

	local hum = obj:FindFirstChildOfClass('Humanoid')
	if hum then
		hum.Died:Connect(function()
			if esp.AutoRemove ~= false then
				box:Remove()
			end
		end)
	end

	return box
end

local function CharAdded(char)
	local p = game.Players:GetPlayerFromCharacter(char)
	if not char:FindFirstChild('HumanoidRootPart') then
		local ev
		ev = char.ChildAdded:Connect(function(c)
			if c.Name == 'HumanoidRootPart' then
				ev:Disconnect()
				esp:Add(char, {
					Name = p.Name,
					Player = p,
					PrimaryPart = c
				})
			end
		end)
	else
		esp:Add(char, {
			Name = p.Name,
			Player = p,
			PrimaryPart = char.HumanoidRootPart
		})
	end
end
local function PlayerAdded(p)
	p.CharacterAdded:Connect(CharAdded)
	if p.Character then
		coroutine.wrap(CharAdded)(p.Character)
	end
end
game.Players.PlayerAdded:Connect(PlayerAdded)
for i,v in pairs(game.Players:GetPlayers()) do
	if v ~= player then
		PlayerAdded(v)
	end
end

game.RunService.RenderStepped:Connect(function()
	for i,v in (esp.Enabled and pairs or ipairs)(esp.Objects) do
		if v.Update then
			local s,e = pcall(v.Update, v)
			if not s then warn('[EU]', e, v.Object:GetFullName()) end
		end
	end
end)

return esp
