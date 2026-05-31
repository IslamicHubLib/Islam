local players = game:GetService("Players")
local tw = game:GetService("TweenService")
local uis = game:GetService("UserInputService")
local rs = game:GetService("RunService")
local core = game:GetService("CoreGui")
local lp = players.LocalPlayer

if core:FindFirstChild("MyHub") then core:FindFirstChild("MyHub"):Destroy() end
if core:FindFirstChild("MyHubIcon") then core:FindFirstChild("MyHubIcon"):Destroy() end

local W, H = 360, 340
local sideW = 48
local headerH = 42
local accent = Color3.fromRGB(130, 200, 255)

local function t(obj, dur, props, es)
	tw:Create(obj, TweenInfo.new(dur, es or Enum.EasingStyle.Quart, Enum.EasingDirection.Out), props):Play()
end
local function rnd(p, r) local c = Instance.new("UICorner", p); c.CornerRadius = UDim.new(0, r or 8) end
local function brd(p, col, th) local s = Instance.new("UIStroke", p); s.Color = col or Color3.fromRGB(32,32,32); s.Thickness = th or 1; return s end

local sg = Instance.new("ScreenGui")
sg.Name = "MyHub"
sg.ResetOnSpawn = false
sg.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
sg.DisplayOrder = 9999
sg.Parent = core

local root = Instance.new("Frame", sg)
root.Size = UDim2.new(0, W, 0, 0)
root.Position = UDim2.new(0.5, -W/2, 0.5, -H/2)
root.BackgroundColor3 = Color3.fromRGB(7, 7, 7)
root.BorderSizePixel = 0
root.ClipsDescendants = false
rnd(root, 14)
brd(root, Color3.fromRGB(28, 28, 28), 1)

local starCanvas = Instance.new("Frame", root)
starCanvas.Size = UDim2.new(1, 0, 1, 0)
starCanvas.BackgroundTransparency = 1
starCanvas.BorderSizePixel = 0
starCanvas.ZIndex = 1
starCanvas.ClipsDescendants = true
rnd(starCanvas, 14)

local inner = Instance.new("Frame", root)
inner.Size = UDim2.new(1, 0, 1, 0)
inner.BackgroundTransparency = 1
inner.ClipsDescendants = true
inner.ZIndex = 2
rnd(inner, 14)

local dots = {}
math.randomseed(tick())
for i = 1, 28 do
	local d = Instance.new("Frame", starCanvas)
	local sz = math.random(1, 3)
	d.Size = UDim2.new(0, sz, 0, sz)
	d.Position = UDim2.new(math.random(), 0, math.random(), 0)
	d.BackgroundColor3 = Color3.fromRGB(math.random(80,140), math.random(140,200), math.random(200,255))
	d.BackgroundTransparency = math.random(40, 75) / 100
	d.BorderSizePixel = 0
	rnd(d, sz)
	d.ZIndex = 1
	table.insert(dots, { frame=d, speed=math.random(8,24)/1000, ox=math.random(), oy=math.random(), phase=math.random()*math.pi*2, amp=math.random(2,8)/1000 })
end

local elapsed = 0
rs.Heartbeat:Connect(function(dt)
	elapsed += dt
	for _, d in ipairs(dots) do
		local ny = (d.oy + elapsed * d.speed) % 1
		local nx = d.ox + math.sin(elapsed * 0.4 + d.phase) * d.amp
		d.frame.Position = UDim2.new(nx, 0, ny, 0)
	end
end)

local header = Instance.new("Frame", inner)
header.Size = UDim2.new(1, 0, 0, headerH)
header.BackgroundColor3 = Color3.fromRGB(10, 10, 10)
header.BorderSizePixel = 0
rnd(header, 14)
local hfix = Instance.new("Frame", header)
hfix.Size = UDim2.new(1, 0, 0.5, 0)
hfix.Position = UDim2.new(0, 0, 0.5, 0)
hfix.BackgroundColor3 = Color3.fromRGB(10, 10, 10)
hfix.BorderSizePixel = 0
local hline = Instance.new("Frame", header)
hline.Size = UDim2.new(1, 0, 0, 1)
hline.Position = UDim2.new(0, 0, 1, -1)
hline.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
hline.BorderSizePixel = 0

local hubIconWrap = Instance.new("Frame", header)
hubIconWrap.Size = UDim2.new(0, 26, 0, 26)
hubIconWrap.Position = UDim2.new(0, 9, 0.5, -13)
hubIconWrap.BackgroundColor3 = Color3.fromRGB(15, 15, 15)
hubIconWrap.BorderSizePixel = 0
hubIconWrap.ZIndex = 3
rnd(hubIconWrap, 8)
local hubIcon = Instance.new("ImageLabel", hubIconWrap)
hubIcon.Size = UDim2.new(1, 0, 1, 0)
hubIcon.BackgroundTransparency = 1
hubIcon.Image = "rbxassetid://100472790998431"
hubIcon.ZIndex = 4
rnd(hubIcon, 8)

local titleLbl = Instance.new("TextLabel", header)
titleLbl.Size = UDim2.new(1, -80, 1, 0)
titleLbl.Position = UDim2.new(0, 42, 0, 0)
titleLbl.BackgroundTransparency = 1
titleLbl.Text = "IslamicHub  |  الله"
titleLbl.TextColor3 = Color3.fromRGB(245, 245, 245)
titleLbl.TextSize = 12
titleLbl.Font = Enum.Font.GothamBold
titleLbl.TextXAlignment = Enum.TextXAlignment.Left
titleLbl.ZIndex = 3

local closeBtn = Instance.new("TextButton", header)
closeBtn.Size = UDim2.new(0, 22, 0, 22)
closeBtn.Position = UDim2.new(1, -30, 0.5, -11)
closeBtn.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
closeBtn.Text = "x"
closeBtn.TextColor3 = Color3.fromRGB(130, 130, 130)
closeBtn.TextSize = 11
closeBtn.Font = Enum.Font.GothamBold
closeBtn.BorderSizePixel = 0
closeBtn.AutoButtonColor = false
closeBtn.ZIndex = 3
rnd(closeBtn, 6)

local iconSg = Instance.new("ScreenGui")
iconSg.Name = "MyHubIcon"
iconSg.ResetOnSpawn = false
iconSg.DisplayOrder = 9998
iconSg.Parent = core

local iconWrap = Instance.new("Frame", iconSg)
iconWrap.Size = UDim2.new(0, 38, 0, 38)
iconWrap.Position = UDim2.new(0.5, -19, 0, 8)
iconWrap.BackgroundColor3 = Color3.fromRGB(10, 10, 10)
iconWrap.BorderSizePixel = 0
iconWrap.Visible = false
rnd(iconWrap, 10)
brd(iconWrap, Color3.fromRGB(36, 36, 36), 1)
local iconBtn = Instance.new("ImageButton", iconWrap)
iconBtn.Size = UDim2.new(1, 0, 1, 0)
iconBtn.BackgroundTransparency = 1
iconBtn.Image = "rbxassetid://100472790998431"
iconBtn.BorderSizePixel = 0
rnd(iconBtn, 10)

closeBtn.Activated:Connect(function()
	t(root, 0.2, { Size = UDim2.new(0, W, 0, 0) })
	task.delay(0.22, function()
		root.Visible = false
		iconWrap.Visible = true
	end)
end)
iconBtn.Activated:Connect(function()
	iconWrap.Visible = false
	root.Visible = true
	t(root, 0.35, { Size = UDim2.new(0, W, 0, H) }, Enum.EasingStyle.Back)
end)

local sidebar = Instance.new("Frame", inner)
sidebar.Size = UDim2.new(0, sideW, 1, -headerH)
sidebar.Position = UDim2.new(0, 0, 0, headerH)
sidebar.BackgroundColor3 = Color3.fromRGB(9, 9, 9)
sidebar.BorderSizePixel = 0
local sline = Instance.new("Frame", sidebar)
sline.Size = UDim2.new(0, 1, 1, 0)
sline.Position = UDim2.new(1, -1, 0, 0)
sline.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
sline.BorderSizePixel = 0

local avFrame = Instance.new("Frame", sidebar)
avFrame.Size = UDim2.new(0, 28, 0, 28)
avFrame.Position = UDim2.new(0.5, -14, 0, 10)
avFrame.BackgroundColor3 = Color3.fromRGB(18, 18, 18)
avFrame.BorderSizePixel = 0
rnd(avFrame, 14)
brd(avFrame, Color3.fromRGB(38, 38, 38), 1)
local avImg = Instance.new("ImageLabel", avFrame)
avImg.Size = UDim2.new(1, 0, 1, 0)
avImg.BackgroundTransparency = 1
avImg.ScaleType = Enum.ScaleType.Crop
rnd(avImg, 14)
task.spawn(function()
	local ok, img = pcall(function()
		return players:GetUserThumbnailAsync(lp.UserId, Enum.ThumbnailType.HeadShot, Enum.ThumbnailSize.Size48x48)
	end)
	if ok then avImg.Image = img end
end)

local divDots = Instance.new("TextLabel", sidebar)
divDots.Size = UDim2.new(1, 0, 0, 12)
divDots.Position = UDim2.new(0, 0, 0, 42)
divDots.BackgroundTransparency = 1
divDots.Text = "..."
divDots.TextColor3 = Color3.fromRGB(32, 32, 32)
divDots.TextSize = 10
divDots.Font = Enum.Font.Gotham

local tabList = Instance.new("Frame", sidebar)
tabList.Size = UDim2.new(1, 0, 1, -58)
tabList.Position = UDim2.new(0, 0, 0, 58)
tabList.BackgroundTransparency = 1
tabList.BorderSizePixel = 0
local tabLL = Instance.new("UIListLayout", tabList)
tabLL.SortOrder = Enum.SortOrder.LayoutOrder
tabLL.Padding = UDim.new(0, 2)
local tabPad = Instance.new("UIPadding", tabList)
tabPad.PaddingTop = UDim.new(0, 4)
tabPad.PaddingLeft = UDim.new(0, 6)
tabPad.PaddingRight = UDim.new(0, 6)

local indicator = Instance.new("Frame", sidebar)
indicator.Size = UDim2.new(0, 2, 0, 16)
indicator.Position = UDim2.new(1, -2, 0, 0)
indicator.BackgroundColor3 = accent
indicator.BorderSizePixel = 0
rnd(indicator, 1)
indicator.Visible = false

local contentArea = Instance.new("Frame", inner)
contentArea.Size = UDim2.new(1, -sideW, 1, -headerH)
contentArea.Position = UDim2.new(0, sideW, 0, headerH)
contentArea.BackgroundTransparency = 1
contentArea.BorderSizePixel = 0
contentArea.ClipsDescendants = true

local dragging, ds, sp = false, nil, nil
header.InputBegan:Connect(function(i)
	if i.UserInputType ~= Enum.UserInputType.MouseButton1 and i.UserInputType ~= Enum.UserInputType.Touch then return end
	if i.Position.X > root.AbsolutePosition.X + root.AbsoluteSize.X - 40 then return end
	dragging = true
	ds = i.Position
	sp = root.Position
end)
uis.InputChanged:Connect(function(i)
	if not dragging then return end
	if i.UserInputType ~= Enum.UserInputType.MouseMove and i.UserInputType ~= Enum.UserInputType.Touch then return end
	local d = i.Position - ds
	root.Position = UDim2.new(sp.X.Scale, sp.X.Offset + d.X, sp.Y.Scale, sp.Y.Offset + d.Y)
end)
uis.InputEnded:Connect(function(i)
	if i.UserInputType == Enum.UserInputType.MouseButton1 or i.UserInputType == Enum.UserInputType.Touch then
		dragging = false
	end
end)

local allTabs = {}
local activeTab = nil
local tabCount = 0

local function setActive(tab)
	if activeTab == tab then return end
	if activeTab then
		t(activeTab.btn, 0.15, { TextColor3 = Color3.fromRGB(65, 65, 65) })
		local old = activeTab.page
		t(old, 0.18, { Position = UDim2.new(0, -12, 0, 0) })
		task.delay(0.2, function() old.Visible = false end)
	end
	activeTab = tab
	local by = tab.btn.AbsolutePosition.Y - sidebar.AbsolutePosition.Y
	local bh = tab.btn.AbsoluteSize.Y
	indicator.Visible = true
	t(indicator, 0.22, { Position = UDim2.new(1, -2, 0, by + bh/2 - 8) })
	t(tab.btn, 0.15, { TextColor3 = accent })
	tab.page.Position = UDim2.new(0, 12, 0, 0)
	tab.page.Visible = true
	t(tab.page, 0.22, { Position = UDim2.new(0, 0, 0, 0) })
end

local fpsCount, fpsTime, fpsVal, pingVal = 0, 0, "--", "--"
rs.Heartbeat:Connect(function(dt)
	fpsCount += 1
	fpsTime += dt
	if fpsTime >= 0.5 then
		fpsVal = tostring(math.floor(fpsCount / fpsTime))
		fpsCount = 0
		fpsTime = 0
	end
end)
task.spawn(function()
	while task.wait(2) do
		local ok, p = pcall(function() return lp:GetNetworkPing() end)
		if ok then pingVal = math.floor(p * 1000) .. "ms" end
	end
end)

local hub = {}
hub.__index = hub

function hub:AddTab(name)
	tabCount += 1
	local internal = { order = 0 }

	local btn = Instance.new("TextButton", tabList)
	btn.Size = UDim2.new(1, 0, 0, 30)
	btn.BackgroundTransparency = 1
	btn.Text = string.sub(name, 1, 2)
	btn.TextColor3 = Color3.fromRGB(65, 65, 65)
	btn.TextSize = 10
	btn.Font = Enum.Font.GothamBold
	btn.BorderSizePixel = 0
	btn.AutoButtonColor = false
	btn.LayoutOrder = tabCount

	local page = Instance.new("ScrollingFrame", contentArea)
	page.Size = UDim2.new(1, 0, 1, 0)
	page.BackgroundTransparency = 1
	page.BorderSizePixel = 0
	page.ScrollBarThickness = 2
	page.ScrollBarImageColor3 = Color3.fromRGB(36, 36, 36)
	page.CanvasSize = UDim2.new(0, 0, 0, 0)
	page.AutomaticCanvasSize = Enum.AutomaticSize.Y
	page.Visible = false
	page.ScrollingEnabled = true
	local pl = Instance.new("UIListLayout", page)
	pl.SortOrder = Enum.SortOrder.LayoutOrder
	pl.Padding = UDim.new(0, 5)
	local pp = Instance.new("UIPadding", page)
	pp.PaddingLeft = UDim.new(0, 10)
	pp.PaddingRight = UDim.new(0, 10)
	pp.PaddingTop = UDim.new(0, 10)
	pp.PaddingBottom = UDim.new(0, 10)

	internal.btn = btn
	internal.page = page

	btn.Activated:Connect(function() setActive(internal) end)
	table.insert(allTabs, internal)
	if #allTabs == 1 then task.defer(function() setActive(internal) end) end

	local function nxt() internal.order += 1; return internal.order end

	local tabApi = {}

	function tabApi:AddSection(sname)
		local wrap = Instance.new("Frame", page)
		wrap.Size = UDim2.new(1, 0, 0, 22)
		wrap.BackgroundTransparency = 1
		wrap.BorderSizePixel = 0
		wrap.LayoutOrder = nxt()
		local sep = Instance.new("Frame", wrap)
		sep.Size = UDim2.new(1, 0, 0, 1)
		sep.Position = UDim2.new(0, 0, 0.5, 0)
		sep.BackgroundColor3 = Color3.fromRGB(22, 22, 22)
		sep.BorderSizePixel = 0
		local lbl = Instance.new("TextLabel", wrap)
		lbl.BackgroundColor3 = Color3.fromRGB(7, 7, 7)
		lbl.BackgroundTransparency = 0
		lbl.AutomaticSize = Enum.AutomaticSize.X
		lbl.Size = UDim2.new(0, 0, 1, 0)
		lbl.Position = UDim2.new(0, 4, 0, 0)
		lbl.Text = "  " .. sname .. "  "
		lbl.TextColor3 = Color3.fromRGB(72, 72, 72)
		lbl.TextSize = 9
		lbl.Font = Enum.Font.GothamBold
		lbl.BorderSizePixel = 0
		lbl.TextXAlignment = Enum.TextXAlignment.Center
	end

	function tabApi:AddToggle(tname, default, cb)
		local state = default or false
		local row = Instance.new("Frame", page)
		row.Size = UDim2.new(1, 0, 0, 36)
		row.BackgroundColor3 = Color3.fromRGB(11, 11, 11)
		row.BorderSizePixel = 0
		row.LayoutOrder = nxt()
		rnd(row, 8)
		brd(row, Color3.fromRGB(24, 24, 24))
		local lbl = Instance.new("TextLabel", row)
		lbl.Size = UDim2.new(1, -56, 1, 0)
		lbl.Position = UDim2.new(0, 10, 0, 0)
		lbl.BackgroundTransparency = 1
		lbl.Text = tname
		lbl.TextColor3 = Color3.fromRGB(195, 195, 195)
		lbl.TextSize = 11
		lbl.Font = Enum.Font.GothamSemibold
		lbl.TextXAlignment = Enum.TextXAlignment.Left
		local pill = Instance.new("Frame", row)
		pill.Size = UDim2.new(0, 34, 0, 17)
		pill.Position = UDim2.new(1, -44, 0.5, -8.5)
		pill.BackgroundColor3 = Color3.fromRGB(26, 26, 26)
		pill.BorderSizePixel = 0
		rnd(pill, 9)
		local dot = Instance.new("Frame", pill)
		dot.Size = UDim2.new(0, 11, 0, 11)
		dot.Position = UDim2.new(0, 3, 0.5, -5.5)
		dot.BackgroundColor3 = Color3.fromRGB(90, 90, 90)
		dot.BorderSizePixel = 0
		rnd(dot, 6)
		local function refresh()
			t(dot, 0.16, {
				Position = state and UDim2.new(0, 20, 0.5, -5.5) or UDim2.new(0, 3, 0.5, -5.5),
				BackgroundColor3 = state and accent or Color3.fromRGB(90, 90, 90),
			})
			t(pill, 0.16, { BackgroundColor3 = state and Color3.fromRGB(18, 36, 20) or Color3.fromRGB(26, 26, 26) })
		end
		refresh()
		local hb = Instance.new("TextButton", row)
		hb.Size = UDim2.new(1, 0, 1, 0)
		hb.BackgroundTransparency = 1
		hb.Text = ""
		hb.AutoButtonColor = false
		hb.Activated:Connect(function()
			state = not state
			refresh()
			pcall(cb, state)
		end)
		return {
			Set = function(_, v) state = v; refresh(); pcall(cb, state) end,
			Get = function() return state end
		}
	end

	function tabApi:AddButton(bname, cb)
		local b = Instance.new("TextButton", page)
		b.Size = UDim2.new(1, 0, 0, 36)
		b.BackgroundColor3 = Color3.fromRGB(12, 12, 12)
		b.Text = bname
		b.TextColor3 = Color3.fromRGB(215, 215, 215)
		b.TextSize = 11
		b.Font = Enum.Font.GothamBold
		b.BorderSizePixel = 0
		b.AutoButtonColor = false
		b.LayoutOrder = nxt()
		rnd(b, 8)
		brd(b, Color3.fromRGB(26, 26, 26))
		b.MouseEnter:Connect(function() t(b, 0.1, { BackgroundColor3 = Color3.fromRGB(17, 17, 17) }) end)
		b.MouseLeave:Connect(function() t(b, 0.1, { BackgroundColor3 = Color3.fromRGB(12, 12, 12) }) end)
		b.Activated:Connect(function() pcall(cb) end)
	end

	function tabApi:AddSlider(sname, min, max, default, cb)
		local value = math.clamp(default or min, min, max)
		local wrap = Instance.new("Frame", page)
		wrap.Size = UDim2.new(1, 0, 0, 50)
		wrap.BackgroundColor3 = Color3.fromRGB(11, 11, 11)
		wrap.BorderSizePixel = 0
		wrap.LayoutOrder = nxt()
		rnd(wrap, 8)
		brd(wrap, Color3.fromRGB(24, 24, 24))
		local top = Instance.new("Frame", wrap)
		top.Size = UDim2.new(1, -16, 0, 18)
		top.Position = UDim2.new(0, 8, 0, 6)
		top.BackgroundTransparency = 1
		local nlbl = Instance.new("TextLabel", top)
		nlbl.Size = UDim2.new(0.7, 0, 1, 0)
		nlbl.BackgroundTransparency = 1
		nlbl.Text = sname
		nlbl.TextColor3 = Color3.fromRGB(185, 185, 185)
		nlbl.TextSize = 10
		nlbl.Font = Enum.Font.GothamSemibold
		nlbl.TextXAlignment = Enum.TextXAlignment.Left
		local vlbl = Instance.new("TextLabel", top)
		vlbl.Size = UDim2.new(0.3, 0, 1, 0)
		vlbl.Position = UDim2.new(0.7, 0, 0, 0)
		vlbl.BackgroundTransparency = 1
		vlbl.Text = tostring(value)
		vlbl.TextColor3 = accent
		vlbl.TextSize = 10
		vlbl.Font = Enum.Font.GothamBold
		vlbl.TextXAlignment = Enum.TextXAlignment.Right
		local track = Instance.new("Frame", wrap)
		track.Size = UDim2.new(1, -16, 0, 3)
		track.Position = UDim2.new(0, 8, 0, 34)
		track.BackgroundColor3 = Color3.fromRGB(24, 24, 24)
		track.BorderSizePixel = 0
		rnd(track, 2)
		local fill = Instance.new("Frame", track)
		fill.Size = UDim2.new((value - min) / (max - min), 0, 1, 0)
		fill.BackgroundColor3 = accent
		fill.BorderSizePixel = 0
		rnd(fill, 2)
		local function upd(x)
			local pct = math.clamp((x - track.AbsolutePosition.X) / track.AbsoluteSize.X, 0, 1)
			value = math.floor(min + pct * (max - min) + 0.5)
			vlbl.Text = tostring(value)
			t(fill, 0.05, { Size = UDim2.new(pct, 0, 1, 0) })
			pcall(cb or function() end, value)
		end
		local sliding = false
		local hb = Instance.new("TextButton", wrap)
		hb.Size = UDim2.new(1, 0, 1, 0)
		hb.BackgroundTransparency = 1
		hb.Text = ""
		hb.AutoButtonColor = false
		hb.InputBegan:Connect(function(i)
			if i.UserInputType == Enum.UserInputType.MouseButton1 or i.UserInputType == Enum.UserInputType.Touch then
				sliding = true; upd(i.Position.X)
			end
		end)
		uis.InputChanged:Connect(function(i)
			if sliding and (i.UserInputType == Enum.UserInputType.MouseMove or i.UserInputType == Enum.UserInputType.Touch) then
				upd(i.Position.X)
			end
		end)
		uis.InputEnded:Connect(function(i)
			if i.UserInputType == Enum.UserInputType.MouseButton1 or i.UserInputType == Enum.UserInputType.Touch then
				sliding = false
			end
		end)
		return {
			Get = function() return value end,
			Set = function(_, v)
				value = math.clamp(v, min, max)
				local pct = (value - min) / (max - min)
				vlbl.Text = tostring(value)
				t(fill, 0.1, { Size = UDim2.new(pct, 0, 1, 0) })
				pcall(cb or function() end, value)
			end
		}
	end

	function tabApi:AddInput(iname, default, ph, cb)
		local wrap = Instance.new("Frame", page)
		wrap.Size = UDim2.new(1, 0, 0, 54)
		wrap.BackgroundTransparency = 1
		wrap.BorderSizePixel = 0
		wrap.LayoutOrder = nxt()
		local lbl = Instance.new("TextLabel", wrap)
		lbl.Size = UDim2.new(1, 0, 0, 14)
		lbl.BackgroundTransparency = 1
		lbl.Text = iname
		lbl.TextColor3 = Color3.fromRGB(100, 100, 100)
		lbl.TextSize = 9
		lbl.Font = Enum.Font.GothamSemibold
		lbl.TextXAlignment = Enum.TextXAlignment.Left
		lbl.Position = UDim2.new(0, 2, 0, 0)
		local box = Instance.new("Frame", wrap)
		box.Size = UDim2.new(1, 0, 0, 32)
		box.Position = UDim2.new(0, 0, 0, 18)
		box.BackgroundColor3 = Color3.fromRGB(11, 11, 11)
		box.BorderSizePixel = 0
		rnd(box, 8)
		brd(box, Color3.fromRGB(26, 26, 26))
		local tb = Instance.new("TextBox", box)
		tb.Size = UDim2.new(1, -14, 1, 0)
		tb.Position = UDim2.new(0, 8, 0, 0)
		tb.BackgroundTransparency = 1
		tb.Text = default or ""
		tb.PlaceholderText = ph or "..."
		tb.TextColor3 = Color3.fromRGB(225, 225, 225)
		tb.PlaceholderColor3 = Color3.fromRGB(55, 55, 55)
		tb.TextSize = 11
		tb.Font = Enum.Font.GothamSemibold
		tb.TextXAlignment = Enum.TextXAlignment.Left
		tb.ClearTextOnFocus = false
		tb:GetPropertyChangedSignal("Text"):Connect(function() pcall(cb or function() end, tb.Text) end)
		return {
			Get = function() return tb.Text end,
			Set = function(_, v) tb.Text = tostring(v) end
		}
	end

	function tabApi:AddLabel(ltext, col)
		local lbl = Instance.new("TextLabel", page)
		lbl.Size = UDim2.new(1, 0, 0, 22)
		lbl.BackgroundTransparency = 1
		lbl.Text = ltext or ""
		lbl.TextColor3 = col or Color3.fromRGB(80, 80, 80)
		lbl.TextSize = 9
		lbl.Font = Enum.Font.Gotham
		lbl.TextXAlignment = Enum.TextXAlignment.Left
		lbl.TextWrapped = true
		lbl.LayoutOrder = nxt()
		return {
			Set = function(_, v) lbl.Text = v end,
			Color = function(_, c) lbl.TextColor3 = c end,
		}
	end

	function tabApi:AddStats()
		local flbl = self:AddLabel("Fps: --")
		local plbl = self:AddLabel("Ping: --")
		rs.Heartbeat:Connect(function()
			flbl:Set("Fps: " .. fpsVal)
			plbl:Set("Ping: " .. pingVal)
		end)
	end

	return tabApi
end

t(root, 0.35, { Size = UDim2.new(0, W, 0, H) }, Enum.EasingStyle.Back)

return hub

