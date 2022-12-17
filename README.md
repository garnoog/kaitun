pcall(function()
            game:GetService("Lighting").FantasySky:Destroy()
            local g = game
            local w = g.Workspace
            local l = g.Lighting
            local t = w.Terrain
            t.WaterWaveSize = 0
            t.WaterWaveSpeed = 0
            t.WaterReflectance = 0
            t.WaterTransparency = 0
            l.GlobalShadows = false
            l.FogEnd = 9e9
            l.Brightness = 0
            settings().Rendering.QualityLevel = "Level01"
            for i, v in pairs(g:GetDescendants()) do
                if v:IsA("Part") or v:IsA("Union") or v:IsA("CornerWedgePart") or v:IsA("TrussPart") then 
                    v.Material = "Plastic"
                    v.Reflectance = 0
                elseif v:IsA("Decal") or v:IsA("Texture") then
                    v.Transparency = 1
                elseif v:IsA("ParticleEmitter") or v:IsA("Trail") then
                    v.Lifetime = NumberRange.new(0)
                elseif v:IsA("Explosion") then
                    v.BlastPressure = 1
                    v.BlastRadius = 1
                elseif v:IsA("Fire") or v:IsA("SpotLight") or v:IsA("Smoke") or v:IsA("Sparkles") then
                    v.Enabled = false
                elseif v:IsA("MeshPart") then
                    v.Material = "Plastic"
                    v.Reflectance = 0
                    v.TextureID = 10385902758728957
                end
            end
            for i, e in pairs(l:GetChildren()) do
                if e:IsA("BlurEffect") or e:IsA("SunRaysEffect") or e:IsA("ColorCorrectionEffect") or e:IsA("BloomEffect") or e:IsA("DepthOfFieldEffect") then
                    e.Enabled = false
                end
            end
            for i, v in pairs(game:GetService("Workspace").Camera:GetDescendants()) do
                if v.Name == ("Water;") then
                    v.Transparency = 1
                    v.Material = "Plastic"
                end
            end
        end)

local ZenHub = Instance.new("ScreenGui")
local Open = Instance.new("TextButton")
local fuckshit = Instance.new("UICorner")
local MODILEMAGE = Instance.new("ImageLabel")
local posto = Instance.new("UIStroke")

fuckshit.Parent = Open

local ScreenGui = Instance.new("ScreenGui")
local ImageButton = Instance.new("ImageButton")


ScreenGui.Parent = game.CoreGui
ScreenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

ImageButton.Parent = ScreenGui
ImageButton.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
ImageButton.BorderSizePixel = 0
ImageButton.Position = UDim2.new(0.120833337, 0, 0.0952890813, 0)
ImageButton.Size = UDim2.new(0, 40, 0, 40)
ImageButton.Draggable = true
ImageButton.Image = "http://www.roblox.com/asset/?id=11538629932"
ImageButton.MouseButton1Down:connect(function()
game:GetService("VirtualInputManager"):SendKeyEvent(true,305,false,game)
 game:GetService("VirtualInputManager"):SendKeyEvent(false,305,false,game)
end)

 MODILEMAGE.Name = "MODILEMAGE"
 MODILEMAGE.Parent = Open
 MODILEMAGE.BackgroundColor3 = Color3.fromRGB(51,255,255)
 MODILEMAGE.BackgroundTransparency = 1.000
 MODILEMAGE.BorderSizePixel = 0
 MODILEMAGE.Position = UDim2.new(0, 0.5, 0, 0)
 MODILEMAGE.Size = UDim2.new(0, 38, 0, 31)
 MODILEMAGE.Image = "rbxassetid://9896553189"
 
posto.Name = "posto"
 posto.Parent = Open
 posto.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
 posto.Color = Color3.fromRGB(51,255,255)
 posto.LineJoinMode = Enum.LineJoinMode.Round
 posto.Thickness = 1
 posto.Transparency = 0
 posto.Enabled = true
 posto.Archivable = true



_G.WindowBackgroundColor = Color3.fromRGB(12,12,12)
_G.BackgroundItemColor = Color3.fromRGB(20, 20, 20)
_G.TabWindowColor = Color3.fromRGB(255, 30, 30)
_G.ContainerColor = Color3.fromRGB(30, 30, 30)
_G.TitleTextColor = Color3.fromRGB(150, 150, 150)
_G.ImageColor = Color3.fromRGB(150, 150, 150)
_G.LineThemeColor = Color3.fromRGB(255, 0, 0)
_G.TabTextColor = Color3.fromRGB(150, 150, 150)
_G.TabImageColor = Color3.fromRGB(150, 150, 150)
_G.TabThemeColor = Color3.fromRGB(250, 0, 0)
_G.SectionColor = Color3.fromRGB(50, 255, 255)
_G.SectionImageColor = Color3.fromRGB(150, 150, 150)
_G.SectionTextColor = Color3.fromRGB(50, 255, 255)
_G.SectionOn = Color3.fromRGB(0, 250, 0)

_G.Color1 = Color3.fromRGB(0,0,255)
do local GUI = game.CoreGui:FindFirstChild("1xliiUI");if GUI then GUI:Destroy();end;if _G.Color == nil then
_G.Color = Color3.fromRGB(255,0,0)
end 
end

local tween = game:GetService("TweenService")
local tweeninfo = TweenInfo.new
local input = game:GetService("UserInputService")
local run = game:GetService("RunService")
local plr = game.Players.LocalPlayer
local mouse = plr:GetMouse()

local UserInputService = game:GetService("UserInputService")
local TweenService = game:GetService("TweenService")

local function MakeDraggable(topbarobject, object)
	local Dragging = nil
	local DragInput = nil
	local DragStart = nil
	local StartPosition = nil

	local function Update(input)
		local Delta = input.Position - DragStart
		local pos = UDim2.new(StartPosition.X.Scale, StartPosition.X.Offset + Delta.X, StartPosition.Y.Scale, StartPosition.Y.Offset + Delta.Y)
		local Tween = TweenService:Create(object, TweenInfo.new(0.15), {Position = pos})
		Tween:Play()
	end

	topbarobject.InputBegan:Connect(
		function(input)
			if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
				Dragging = true
				DragStart = input.Position
				StartPosition = object.Position

				input.Changed:Connect(
					function()
						if input.UserInputState == Enum.UserInputState.End then
							Dragging = false
						end
					end
				)
			end
		end
	)

	topbarobject.InputChanged:Connect(
		function(input)
			if
				input.UserInputType == Enum.UserInputType.MouseMovement or
				input.UserInputType == Enum.UserInputType.Touch
			then
				DragInput = input
			end
		end
	)

	UserInputService.InputChanged:Connect(
		function(input)
			if input == DragInput and Dragging then
				Update(input)
			end
		end
	)
end

local Update = {}

function Update:AddWindow(name,logo,keybind)
	local uihide = false
	local abc = false
	local logo = logo or 0
	local currentpage = ""
	local keybind = keybind or Enum.KeyCode.RightControl
	local yoo = string.gsub(tostring(keybind),"Enum.KeyCode.","")
	
	local SOMEXHUB = Instance.new("ScreenGui")
	SOMEXHUB.Name = "1xliiUI"
	SOMEXHUB.Parent = game.CoreGui
	SOMEXHUB.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

local osfunc = {}
 local osfunc2 = {}
	local Main = Instance.new("Frame")
	local WindowStrokemain = Instance.new("UIStroke")
	Main.Name = "Main"
	Main.Parent = SOMEXHUB
	Main.ClipsDescendants = true
	Main.AnchorPoint = Vector2.new(0.5,0.5)
	Main.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
	Main.Position = UDim2.new(0.5, 0, 0.5, 0)
	Main.Size = UDim2.new(0, 0, 0, 0)
	
	WindowStrokemain.Name = "WindowStroke"
 WindowStrokemain.Parent = Main
 WindowStrokemain.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
 WindowStrokemain.Color = Color3.fromRGB(51,255,255)
 WindowStrokemain.LineJoinMode = Enum.LineJoinMode.Round
 WindowStrokemain.Thickness = 1
 WindowStrokemain.Transparency = 0
 WindowStrokemain.Enabled = true
 WindowStrokemain.Archivable = true
	
	Main:TweenSize(UDim2.new(0, 560, 0, 350),"Out","Quad",0.4,true)

	local MCNR = Instance.new("UICorner")
	MCNR.Name = "MCNR"
	MCNR.Parent = Main

	local Top = Instance.new("Frame")
	Top.Name = "Top"
	Top.Position = UDim2.new(0,0,0,4)
	Top.Parent = Main
	Top.BackgroundColor3 = Color3.fromRGB(42, 42, 42)
	Top.Size = UDim2.new(0, 560, 0, 27)

	local TCNR = Instance.new("UICorner")
	TCNR.Name = "TCNR"
	TCNR.Parent = Top

	local Logo = Instance.new("ImageLabel")
	Logo.Name = "Logo"
	Logo.Parent = Top
	Logo.BackgroundColor3 = Color3.fromRGB(51,255,255)
	Logo.BackgroundTransparency = 1.000
	Logo.Position = UDim2.new(0, 13, 0, 1)
	Logo.Size = UDim2.new(0, 25, 0, 25)
	Logo.Image = "rbxassetid://9896553189"

	local Name = Instance.new("TextLabel")
	Name.Name = "Name"
	Name.Parent = Top
	Name.BackgroundColor3 = Color3.fromRGB(51,255,255)
	Name.BackgroundTransparency = 1.000
	Name.Position = UDim2.new(0.1, 0, 0, 0)
	Name.Size = UDim2.new(0, 10, 0, 27)
	Name.Font = Enum.Font.Code
	Name.RichText = true;
	Name.Text = name
	Name.TextColor3 = Color3.fromRGB(225, 225, 225)
	Name.TextSize = 15.000


	local ServerTime = Instance.new("TextButton")
 local ServerDate = Instance.new("TextButton")
ServerTime.Name = "ServerTime"
 ServerTime.Parent = Top
 ServerTime.BackgroundColor3 = _G.WindowBackgroundColor
 ServerTime.AutoButtonColor = false
 ServerTime.BackgroundTransparency = 1.000
 ServerTime.Position = UDim2.new(0, 159, 0, 0)
 ServerTime.Size = UDim2.new(0, 225, 0, 25)
 ServerTime.Font = Enum.Font.Code
 ServerTime.Text = ""
 ServerTime.TextSize = 13.000
 ServerTime.TextColor3 = Color3.fromRGB(0, 250, 0)
 ServerTime.TextXAlignment = Enum.TextXAlignment.Center
 
 
 ServerDate.Name = "ServerDate"
 ServerDate.Parent = Top
 ServerDate.BackgroundColor3 = _G.WindowBackgroundColor
 ServerDate.AutoButtonColor = false
 ServerDate.BackgroundTransparency = 1.000
 ServerDate.Position = UDim2.new(0, 300, 0, 0)
 ServerDate.Size = UDim2.new(0, 250, 0, 25)
 ServerDate.Font = Enum.Font.Code
 ServerDate.Text = ""
 ServerDate.TextSize = 13.000
 ServerDate.TextColor3 = Color3.fromRGB(250, 0, 0)
 ServerDate.TextXAlignment = Enum.TextXAlignment.Center
 
local LocalizationService = game:GetService("LocalizationService")
 local Players = game:GetService("Players")
 local player = Players.LocalPlayer
 local name = player.Name
 local result, code = pcall(function()
	 return LocalizationService:GetCountryRegionForPlayerAsync(player)
 end)
 
function osfunc:Refresh(textadd)
 ServerTime.Text = textadd
 end
 function osfunc2:Refresh(textadd2)
 ServerDate.Text = textadd2
 end
local function UpdateOS()
 local date = os.date("*t")
 local hour = (date.hour) % 24
 local ampm = hour < 12 and "AM" or "PM"
 local timezone = string.format("%02i:%02i:%02i %s", ((hour -1) % 12) + 1, date.min, date.sec, ampm)
 local datetime = string.format("%02d/%02d/%04d", date.day, date.month, date.year)
 osfunc:Refresh(" | TIME : " .. timezone)
 osfunc2:Refresh(" | DATE : " .. datetime .. " [" .. code .. "]")
 end
 spawn(function()
 while true do
UpdateOS()
game:GetService("RunService").RenderStepped:Wait()
 end
 end)

local ListNof = Instance.new("Frame")
	local NofList = Instance.new("UIListLayout")

	ListNof.Name = "ListNof"
	ListNof.Parent = SOMEXHUB
	ListNof.BackgroundColor3 = Color3.fromRGB(51,255,255)
	ListNof.BackgroundTransparency = 1.000
	ListNof.Position = UDim2.new(0.778017223, 0, -0.00217864919, 0)
	ListNof.Size = UDim2.new(0, 206, 0, 460)

	NofList.Name = "NofList"
	NofList.Parent = ListNof
	NofList.SortOrder = Enum.SortOrder.LayoutOrder
	NofList.VerticalAlignment = Enum.VerticalAlignment.Top
	
	function Update:Nof(txt,tine)
		spawn(function()
			local Nof1 = Instance.new("Frame")
			local Nof2 = Instance.new("Frame")
			local Nof3 = Instance.new("Frame")
			local NofLabel = Instance.new("TextLabel")
			local slidenof = Instance.new("Frame")
			local Slide2 = Instance.new("Frame")

			Nof1.Name = "Nof1"
			Nof1.Parent = ListNof
			Nof1.BackgroundColor3 = Color3.fromRGB(51,255,255)
			Nof1.BackgroundTransparency = 1.000
			Nof1.BorderSizePixel = 0
			Nof1.Size = UDim2.new(0, 206, 0, 83)

			Nof2.Name = "Nof2"
			Nof2.Parent = Nof1
			Nof2.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
			Nof2.BorderColor3 = Color3.fromRGB(0, 0, 0)
			Nof2.Position = UDim2.new(0, 0, 0.0120481923, 0)
			Nof2.Size = UDim2.new(0, 189, 0, 65)
			Instance.new("UICorner",Nof2)
			Instance.new("UICorner",slidenof)
			Instance.new("UICorner",Slide2)


			Nof3.Name = "Nof3"
			Nof3.Parent = Nof1
			Nof3.BackgroundColor3 = Color3.fromRGB(90, 90, 255)
			Nof3.BackgroundTransparency = 1
			Nof3.BorderSizePixel = 0
			Nof3.Position = UDim2.new(0, 0, 0.638554215, 0)
			Nof3.Size = UDim2.new(0, 189, 0, 7)

			NofLabel.Name = "NofLabel"
			NofLabel.Parent = Nof1
			NofLabel.BackgroundColor3 = Color3.fromRGB(51,255,255)
			NofLabel.BackgroundTransparency = 1.000
			NofLabel.BorderSizePixel = 0
			NofLabel.Position = UDim2.new(0, 0, 0.00463949936, 0)
			NofLabel.Size = UDim2.new(0, 188, 0, 52)
			NofLabel.ZIndex = 4
			NofLabel.Font = Enum.Font.Code
			NofLabel.TextColor3 = main_color or Color3.fromRGB(51,255,255)
			NofLabel.TextScaled = false
			NofLabel.TextSize = 18.000
			NofLabel.TextStrokeTransparency = 0.100
			NofLabel.TextTransparency = 0.100
			NofLabel.TextWrapped = true
			NofLabel.Text = txt or ""

			slidenof.Name = "slidenof"
			slidenof.Parent = Nof1
			slidenof.BackgroundColor3 = Color3.fromRGB(100, 100, 255)
			slidenof.BorderSizePixel = 0
			slidenof.Position = UDim2.new(0, 0, 0.638554215, 0)
			slidenof.Size = UDim2.new(0, 189, 0, 7)

			Slide2.Name = "Slide2"
			Slide2.Parent = Nof1
			Slide2.BorderSizePixel = 0
			Slide2.BackgroundColor3 = main_color or Color3.fromRGB(51,255,255)
			Slide2.BorderColor3 = Color3.fromRGB(0, 0, 0)
			Slide2.Position = UDim2.new(0, 0, 0.0120481923, 0)
			Slide2.Size = UDim2.new(0, 0, 0, 65)
			Slide2.ZIndex = 15
			Slide2.Visible = false

			tween:Create(slidenof,tweeninfo(tine or 2),{Size = UDim2.new(0, 0, 0, 7)}):Play()
			wait(tine or 2)
			Slide2.Visible = true
			tween:Create(Slide2,tweeninfo(0.2),{Size = UDim2.new(0, 190, 0, 65)}):Play()
			wait(0.2)
			tween:Create(Slide2,tweeninfo(0.2),{Size = UDim2.new(0, 0, 0, 65)}):Play()
			tween:Create(Nof3,tweeninfo(0.2),{Size = UDim2.new(0, 0, 0, 7)}):Play()
			tween:Create(NofLabel,tweeninfo(0.2),{Size = UDim2.new(0, 0, 0, 52)}):Play()
			tween:Create(Nof2,tweeninfo(0.2),{Size = UDim2.new(0, 0, 0, 65)}):Play()
			wait(0.2)
			Nof2.Visible = false
			game.Debris:AddItem(Nof1,0)
		end)
	end

 
 function Update:AddNotification(textdesc)
 local NotificationHold = Instance.new("TextButton")
 local NotificationFrame = Instance.new("Frame")
 local OkayBtn = Instance.new("TextButton")
 local OkayBtnCorner = Instance.new("UICorner")
 local OkayBtnTitle = Instance.new("TextLabel")
 local NotificationTitle = Instance.new("TextLabel")
 local NotificationDesc = Instance.new("TextLabel")
 local NotifCorner = Instance.new("UICorner")
 local NotifHolderUIStroke = Instance.new("UIStroke")
 local Line = Instance.new("Frame")
 
 NotificationHold.Name = "NotificationHold"
 NotificationHold.Parent = Main
 NotificationHold.BackgroundColor3 = _G.WindowBackgroundColor
 NotificationHold.BackgroundTransparency = 0.4
 NotificationHold.BorderSizePixel = 0
 NotificationHold.Size = UDim2.new(0, 589, 0, 378)
 NotificationHold.AutoButtonColor = false
 NotificationHold.Font = Enum.Font.SourceSans
 NotificationHold.Text = ""
 NotificationHold.TextColor3 = _G.SectionTextColor
 NotificationHold.TextSize = 13.000
 
 TweenService:Create(NotificationHold, TweenInfo.new(.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {BackgroundTransparency = 0.4}):Play()
 wait(0.4)
 
 NotificationFrame.Name = "NotificationFrame"
 NotificationFrame.Parent = NotificationHold
 NotificationFrame.AnchorPoint = Vector2.new(0.5, 0.5)
 NotificationFrame.BackgroundColor3 = Color3.fromRGB(15, 15, 15)
 NotificationFrame.BorderColor3 = _G.SectionColor
 NotificationFrame.BorderSizePixel = 0
 NotificationFrame.ClipsDescendants = true
 NotificationFrame.Position = UDim2.new(0, 295, 0, 190)
 NotificationFrame.Size = UDim2.new(0, 0, 0, 0)		
 
 NotificationFrame:TweenSize(UDim2.new(0, 400, 0, 250), Enum.EasingDirection.Out, Enum.EasingStyle.Quart, .6, true)
 
 NotifCorner.Name = "NotifCorner"
 NotifCorner.Parent = NotificationFrame
 NotifCorner.CornerRadius = UDim.new(0, 5)
 
 NotifHolderUIStroke.Name = "NotifHolderUIStroke"
 NotifHolderUIStroke.Parent = NotificationFrame
 NotifHolderUIStroke.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
 NotifHolderUIStroke.Color = _G.SectionColor
 NotifHolderUIStroke.LineJoinMode = Enum.LineJoinMode.Round
 NotifHolderUIStroke.Thickness = 1
 NotifHolderUIStroke.Transparency = 0
 NotifHolderUIStroke.Enabled = true
 NotifHolderUIStroke.Archivable = true
 
 OkayBtn.Name = "OkayBtn"
 OkayBtn.Parent = NotificationFrame
 OkayBtn.BackgroundColor3 = Color3.fromRGB(190, 190, 190)
 OkayBtn.BorderSizePixel = 1
 OkayBtn.BorderColor3 = _G.SectionColor
 OkayBtn.Position = UDim2.new(0, 125, 0, 190)
 OkayBtn.Size = UDim2.new(0, 150, 0, 30)
 OkayBtn.AutoButtonColor = true
 OkayBtn.Font = Enum.Font.SourceSans
 OkayBtn.Text = ""
 OkayBtn.TextColor3 = _G.SectionTextColor
 OkayBtn.TextSize = 13.000
 
 OkayBtnCorner.CornerRadius = UDim.new(0, 5)
 OkayBtnCorner.Name = "OkayBtnCorner"
 OkayBtnCorner.Parent = OkayBtn
 
 OkayBtnTitle.Name = "OkayBtnTitle"
 OkayBtnTitle.Parent = OkayBtn
 OkayBtnTitle.BackgroundColor3 = _G.SectionColor
 OkayBtnTitle.BackgroundTransparency = 1.000
 OkayBtnTitle.Size = UDim2.new(0, 150, 0, 30)
 OkayBtnTitle.Text = "OK"
 OkayBtnTitle.Font = Enum.Font.Code
 OkayBtnTitle.TextColor3 = Color3.fromRGB(0, 0, 0)
 OkayBtnTitle.TextSize = 22.000
 
 NotificationTitle.Name = "NotificationTitle"
 NotificationTitle.Parent = NotificationFrame
 NotificationTitle.BackgroundColor3 = _G.SectionColor
 NotificationTitle.BackgroundTransparency = 1.000
 NotificationTitle.Position = UDim2.new(0, 0, 0, 10)
 NotificationTitle.Size = UDim2.new(0, 400, 0, 25)
 NotificationTitle.ZIndex = 3
 NotificationTitle.Font = Enum.Font.Code
 NotificationTitle.Text = "Notification"
 NotificationTitle.TextColor3 = Color3.fromRGB(50, 255, 255)
 NotificationTitle.TextSize = 22.000
 
 Line.Name = "Line"
 Line.Parent = NotificationFrame
 Line.BackgroundColor3 = _G.SectionColor
 Line.BorderSizePixel = 0
 Line.Position = UDim2.new(0, 10, 0, 40)
 Line.Size = UDim2.new(0, 380, 0, 1)
 
 NotificationDesc.Name = "NotificationDesc"
 NotificationDesc.Parent = NotificationFrame
 NotificationDesc.BackgroundColor3 = _G.SectionColor
 NotificationDesc.BackgroundTransparency = 1.000
 NotificationDesc.Position = UDim2.new(0, 10, 0, 80)
 NotificationDesc.Size = UDim2.new(0, 380, 0, 200)
 NotificationDesc.Font = Enum.Font.Code
 NotificationDesc.Text = textdesc
NotificationDesc.TextScaled = false
 NotificationDesc.TextColor3 = _G.SectionTextColor
 NotificationDesc.TextSize = 16.000
 NotificationDesc.TextWrapped = true
 NotificationDesc.TextXAlignment = Enum.TextXAlignment.Center
 NotificationDesc.TextYAlignment = Enum.TextYAlignment.Top
 
 OkayBtn.MouseEnter:Connect(function()
TweenService:Create(OkayBtn, TweenInfo.new(.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {BackgroundColor3 = Color3.fromRGB(30, 30, 30)}):Play()
 end)
 
 OkayBtn.MouseLeave:Connect(function()
TweenService:Create(OkayBtn, TweenInfo.new(.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {BackgroundColor3 = Color3.fromRGB(25, 25, 25)}):Play()
 end)
 
 OkayBtn.MouseButton1Click:Connect(function()
NotificationFrame:TweenSize(UDim2.new(0, 0, 0, 0), Enum.EasingDirection.Out, Enum.EasingStyle.Quart, .6, true)
 
wait(0.4)
 
TweenService:Create(NotificationHold, TweenInfo.new(.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {BackgroundTransparency = 1}):Play()
 
wait(.3)
 
NotificationHold:Destroy()
 end)
 end

	local Hub = Instance.new("TextLabel")
	Hub.Name = "Hub"
	Hub.Parent = Top
	Hub.BackgroundColor3 = Color3.fromRGB(51,255,255)
	Hub.BackgroundTransparency = 1.000
	Hub.Position = UDim2.new(0, 80, 0, 0)
	Hub.Size = UDim2.new(0, 50, 0, 27)
	Hub.Font = Enum.Font.Code
	Hub.Text = "HUB"
	Hub.TextColor3 = Color3.fromRGB(50, 255, 255)
	Hub.TextSize = 15.000
	Hub.TextXAlignment = Enum.TextXAlignment.Left
	
local Hub1 = Instance.new("TextLabel")
	Hub1.Name = "Hub"
	Hub1.Parent = Top
	Hub1.BackgroundColor3 = Color3.fromRGB(51,255,255)
	Hub1.BackgroundTransparency = 1.000
	Hub1.Position = UDim2.new(0, 130, 0, 0)
	Hub1.Size = UDim2.new(0, 50, 0, 27)
	Hub1.Font = Enum.Font.Code
	Hub1.Text = "| KAITUN"
	Hub1.TextColor3 = Color3.fromRGB(255,255,255)
	Hub1.TextSize = 15.000

	local BindButton = Instance.new("TextButton")
	BindButton.Name = "BindButton"
	BindButton.Parent = Top
	BindButton.BackgroundColor3 = Color3.fromRGB(51,255,255)
	BindButton.BackgroundTransparency = 1.000
	BindButton.Position = UDim2.new(0.865561002, 0, 0, 0)
	BindButton.Size = UDim2.new(0, 100, 0, 27)
	BindButton.Font = Enum.Font.Code
	BindButton.Text = "[FREE]"
	BindButton.TextColor3 = Color3.fromRGB(51,255,255)
	BindButton.TextSize = 14.000
	BindButton.Visible = true


local Tab = Instance.new("ImageLabel")
local WindowStrokelol = Instance.new("UIStroke")
 Tab.Name = "Tab"
 Tab.Parent = Main
 Tab.BackgroundColor3 = Color3.fromRGB(42, 42, 42)
 Tab.ImageTransparency = 1
 Tab.Position = UDim2.new(0, 5, 0, 35)
 Tab.Size = UDim2.new(0, 160, 0, 310)
 Tab.Image = "rbxassetid://9896553189"
 
 WindowStrokelol.Name = "WindowStroke"
 WindowStrokelol.Parent = Tab
 WindowStrokelol.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
 WindowStrokelol.Color = Color3.fromRGB(51,255,255)
 WindowStrokelol.LineJoinMode = Enum.LineJoinMode.Round
 WindowStrokelol.Thickness = 1
 WindowStrokelol.Transparency = 0
 WindowStrokelol.Enabled = true
 WindowStrokelol.Archivable = true
 
 local TCNR = Instance.new("UICorner")
 TCNR.Name = "TCNR"
 TCNR.Parent = Tab
 
 local ScrollTab = Instance.new("ScrollingFrame")
 ScrollTab.Name = "ScrollTab"
 ScrollTab.Parent = Tab
 ScrollTab.Active = true
 ScrollTab.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
 ScrollTab.BackgroundTransparency = 1
 ScrollTab.Size = UDim2.new(0, 170, 0, 300)
 ScrollTab.CanvasSize = UDim2.new(0, 0, 0, 0)
 ScrollTab.ScrollBarThickness = 0
 
 local PLL = Instance.new("UIListLayout")
 PLL.Name = "PLL"
 PLL.Parent = ScrollTab
 PLL.SortOrder = Enum.SortOrder.LayoutOrder
 PLL.Padding = UDim.new(0, 14)
 
 local PPD = Instance.new("UIPadding")
 PPD.Name = "PPD"
 PPD.Parent = ScrollTab
 PPD.PaddingLeft = UDim.new(0, 10)
 PPD.PaddingTop = UDim.new(0, 10)
 
 local Page = Instance.new("Frame")
 local WindowStrokeshit = Instance.new("UIStroke")
 Page.Name = "Page"
 Page.Parent = Main
 Page.BackgroundColor3 = Color3.fromRGB(42, 42, 42)
 Page.BackgroundTransparency = 0.1
 Page.Position = UDim2.new(0.305426834, 0, 0.100000003, 0)
 Page.Size = UDim2.new(0, 380, 0, 310)
 
 WindowStrokeshit.Name = "WindowStroke"
 WindowStrokeshit.Parent = Page
 WindowStrokeshit.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
 WindowStrokeshit.Color = Color3.fromRGB(51,255,255)
 WindowStrokeshit.LineJoinMode = Enum.LineJoinMode.Round
 WindowStrokeshit.Thickness = 1
 WindowStrokeshit.Transparency = 0
 WindowStrokeshit.Archivable = false
 WindowStrokeshit.Enabled = true
 
 local lolshit = Instance.new("UICorner")
 
 lolshit.Parent = Top1
 
 
 local PCNR = Instance.new("UICorner")
 PCNR.Name = "PCNR"
 PCNR.Parent = Page
 
 local MainPage = Instance.new("Frame")
 MainPage.Name = "MainPage"
 MainPage.Parent = Page
 MainPage.ClipsDescendants = true
 MainPage.BackgroundColor3 = Color3.fromRGB(51,255,255)
 MainPage.BackgroundTransparency = 1.000
 MainPage.Size = UDim2.new(0, 560, 0, 360)
 
 local PageList = Instance.new("Folder")
 PageList.Name = "PageList"
 PageList.Parent = MainPage
 
 local UIPageLayout = Instance.new("UIPageLayout")
 
 UIPageLayout.Parent = PageList
 UIPageLayout.SortOrder = Enum.SortOrder.LayoutOrder
 UIPageLayout.EasingDirection = Enum.EasingDirection.InOut
 UIPageLayout.EasingStyle = Enum.EasingStyle.Quad
 UIPageLayout.FillDirection = Enum.FillDirection.Vertical
 UIPageLayout.Padding = UDim.new(0, 15)
 UIPageLayout.TweenTime = 0.400
 UIPageLayout.GamepadInputEnabled = false
 UIPageLayout.ScrollWheelInputEnabled = false
 UIPageLayout.TouchInputEnabled = false
 
 MakeDraggable(Top,Main)
 
 UserInputService.InputBegan:Connect(function(input)
if input.KeyCode == Enum.KeyCode[yoo] then
if uihide == false then
 uihide = true
 Main:TweenSize(UDim2.new(0, 0, 0, 0),"In","Quad",0.4,true)
else
 uihide = false
 Main:TweenSize(UDim2.new(0, 560, 0, 350),"Out","Quad",0.4,true)
end
end
 end)
	
	local uitab = {}
	
	function uitab:AddTab(text, img)
		local TabButton = Instance.new("TextButton")
		local TabImage = Instance.new("ImageLabel")
		local WindowStroke = Instance.new("UIStroke")
		local Label3 = Instance.new("TextLabel")
		local LabelTitle = Instance.new("TextLabel")
local LabelTitle = Instance.new("TextLabel")

		TabButton.Parent = ScrollTab
		TabButton.Name = text.."Server"
		TabButton.Text = text
		TabButton.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
		TabButton.BackgroundTransparency = 0.1
		TabButton.Size = UDim2.new(0, 138, 0, 30)
		TabButton.Font = Enum.Font.Code
		TabButton.TextColor3 = Color3.fromRGB(255, 225, 225)
		TabButton.TextSize = 12.000
		TabButton.TextTransparency = 0

		Label3.Name = "Label"
			Label3.Parent = TabButton
			Label3.BackgroundColor3 = Color3.fromRGB(51,255,255)
			Label3.BackgroundTransparency = 1.000
			Label3.Position = UDim2.new(0, 27, 0, 7)
			Label3.Size = UDim2.new(0, 20, 0, 20)
			Label3.Font = Enum.Font.ArialBold
			Label3.TextColor3 = Color3.fromRGB(225, 225, 225)
			Label3.TextSize = 10.000
			Label3.Text = "•"
		
local MCNR1 = Instance.new("UICorner")
	MCNR1.Name = "MCNR"
	MCNR1.Parent = TabButton

WindowStroke.Name = "WindowStroke"
 WindowStroke.Parent = TabButton
 WindowStroke.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
 WindowStroke.Color = Color3.fromRGB(51,255,255)
 WindowStroke.LineJoinMode = Enum.LineJoinMode.Round
 WindowStroke.Thickness = 1
 WindowStroke.Transparency = 0
 WindowStroke.Enabled = true
 WindowStroke.Archivable = true

TabImage.Name = text or "TabImage"
 TabImage.Parent = TabButton
 TabImage.BackgroundColor3 = Color3.fromRGB("51,255,255")
 TabImage.BackgroundTransparency = 1.000
 TabImage.Position = UDim2.new(0, 7, 0, 7)
 TabImage.Size = UDim2.new(0, 20, 0, 20)
 TabImage.Image = "rbxassetid://"..tostring(img)
 TabImage.ImageColor3 = Color3.fromRGB(51,255,255)

		local MainFramePage = Instance.new("ScrollingFrame")
		MainFramePage.Name = text.."_Page"
		MainFramePage.Parent = PageList
		MainFramePage.Active = true
		MainFramePage.BackgroundColor3 = Color3.fromRGB(51,255,255)
		MainFramePage.BackgroundTransparency = 1.000
		MainFramePage.BorderSizePixel = 0
		MainFramePage.Size = UDim2.new(0, 390, 0, 300)
		MainFramePage.CanvasSize = UDim2.new(0, 0, 0, 0)
		MainFramePage.ScrollBarThickness = 0
		
		local UIPadding = Instance.new("UIPadding")
		local UIListLayout = Instance.new("UIListLayout")
		
		UIPadding.Parent = MainFramePage
		UIPadding.PaddingLeft = UDim.new(0, 10)
		UIPadding.PaddingTop = UDim.new(0, 10)

		UIListLayout.Padding = UDim.new(0,15)
		UIListLayout.Parent = MainFramePage
		UIListLayout.SortOrder = Enum.SortOrder.LayoutOrder
		
		TabButton.MouseButton1Click:Connect(function()
			for i,v in next, ScrollTab:GetChildren() do
				if v:IsA("TextButton") then
					TweenService:Create(
						v,
						TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
						{TextTransparency = 0.5}
					):Play()
				end
				TweenService:Create(
					TabButton,
					TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
					{TextTransparency = 0}
				):Play()
			end
			for i,v in next, PageList:GetChildren() do
				currentpage = string.gsub(TabButton.Name,"Server","").."_Page"
				if v.Name == currentpage then
					UIPageLayout:JumpTo(v)
				end
			end
		end)

		if abc == false then
			for i,v in next, ScrollTab:GetChildren() do
				if v:IsA("TextButton") then
					TweenService:Create(
						v,
						TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
						{TextTransparency = 0.5}
					):Play()
				end
				TweenService:Create(
					TabButton,
					TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
					{TextTransparency = 0}
				):Play()
			end
			UIPageLayout:JumpToIndex(1)
			abc = true
		end
		
		game:GetService("RunService").Stepped:Connect(function()
			pcall(function()
				MainFramePage.CanvasSize = UDim2.new(0,0,0,UIListLayout.AbsoluteContentSize.Y + 20)
				ScrollTab.CanvasSize = UDim2.new(0,0,0,PLL.AbsoluteContentSize.Y + 20)
			end)
		end)
 
 coroutine.wrap(function()
 while wait() do
 end
 end)()
 
	 
 
 coroutine.wrap(function()
 while wait() do
 end
 end)()
	
		local main = {}
		function main:AddButton(text,callback)
			local Button = Instance.new("Frame")
			local UICorner = Instance.new("UICorner")
			local TextBtn = Instance.new("TextButton")
			local UICorner_2 = Instance.new("UICorner")
			local Black = Instance.new("Frame")
			local UICorner_3 = Instance.new("UICorner")
			
			Button.Name = "Button"
			Button.Parent = MainFramePage
			Button.BackgroundColor3 = _G.Color
			Button.Size = UDim2.new(0, 362, 0, 31)
			
			UICorner.CornerRadius = UDim.new(0, 5)
			UICorner.Parent = Button
			
			TextBtn.Name = "TextBtn"
			TextBtn.Parent = Button
			TextBtn.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
			TextBtn.Position = UDim2.new(0, 1, 0, 1)
			TextBtn.Size = UDim2.new(0, 360, 0, 29)
			TextBtn.AutoButtonColor = false
			TextBtn.Font = Enum.Font.Code
			TextBtn.Text = text
			TextBtn.TextColor3 = Color3.fromRGB(225, 225, 225)
			TextBtn.TextSize = 15.000
			
			UICorner_2.CornerRadius = UDim.new(0, 5)
			UICorner_2.Parent = TextBtn
			
			Black.Name = "Black"
			Black.Parent = Button
			Black.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
			Black.BackgroundTransparency = 1.000
			Black.BorderSizePixel = 0
			Black.Position = UDim2.new(0, 1, 0, 1)
			Black.Size = UDim2.new(0, 360, 0, 29)
			
			UICorner_3.CornerRadius = UDim.new(0, 5)
			UICorner_3.Parent = Black

			TextBtn.MouseEnter:Connect(function()
				TweenService:Create(
					Black,
					TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
					{BackgroundTransparency = 0.7}
				):Play()
			end)
			TextBtn.MouseLeave:Connect(function()
				TweenService:Create(
					Black,
					TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
					{BackgroundTransparency = 1}
				):Play()
			end)
			TextBtn.MouseButton1Click:Connect(function()
				TextBtn.TextSize = 0
				TweenService:Create(
					TextBtn,
					TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
					{TextSize = 15}
				):Play()
				callback()
			end)
		end
		function main:AddToggle(text,config,callback)
			config = config or false
			local toggled = config
			local Toggle = Instance.new("Frame")
			local UICorner = Instance.new("UICorner")
			local Button = Instance.new("TextButton")
			local UICorner_2 = Instance.new("UICorner")
			local Label = Instance.new("TextLabel")
			local ToggleImage = Instance.new("Frame")
			local UICorner_3 = Instance.new("UICorner")
			local Circle = Instance.new("Frame")
			local UICorner_4 = Instance.new("UICorner")
local ImageLabel = Instance.new("ImageLabel")
local Space = Instance.new("TextLabel")

			Toggle.Name = "Toggle"
			Toggle.Parent = MainFramePage
			Toggle.BackgroundColor3 = _G.Color
			Toggle.Size = UDim2.new(0, 362, 0, 31)

			UICorner.CornerRadius = UDim.new(0, 5)
			UICorner.Parent = Toggle

			Button.Name = "Button"
			Button.Parent = Toggle
			Button.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
			Button.Position = UDim2.new(0, 1, 0, 1)
			Button.Size = UDim2.new(0, 360, 0, 29)
			Button.AutoButtonColor = false
			Button.Font = Enum.Font.SourceSans
			Button.Text = ""
			Button.TextColor3 = Color3.fromRGB(0, 0, 0)
			Button.TextSize = 11.000

			UICorner_2.CornerRadius = UDim.new(0, 5)
			UICorner_2.Parent = Button

			Label.Name = "Label"
			Label.Parent = Toggle
			Label.BackgroundColor3 = Color3.fromRGB(51,255,255)
			Label.BackgroundTransparency = 1.000
			Label.Position = UDim2.new(0, 1, 0, 1)
			Label.Size = UDim2.new(0, 360, 0, 29)
			Label.Font = Enum.Font.Code
			Label.Text = text
			Label.TextColor3 = Color3.fromRGB(225, 225, 225)
			Label.TextSize = 15.000
			
ImageLabel.Name = "ImageLabel"
ImageLabel.Parent = Toggle
ImageLabel.BackgroundColor3 = Color3.fromRGB(51,255,255)
ImageLabel.BackgroundTransparency = 1.000
ImageLabel.BorderSizePixel = 0
ImageLabel.Position = UDim2.new(0, 10, 0, 6)
ImageLabel.Size = UDim2.new(0, 18, 0, 18)
ImageLabel.Image = "rbxassetid://8825010231"
ImageLabel.ImageColor3 = Color3.fromRGB(180,180,180)

Space.Name = "Space"
Space.Parent = Toggle
Space.BackgroundColor3 = _G.Color
Space.BackgroundTransparency = 1.000
Space.Position = UDim2.new(0, 30, 0, 0)
Space.Size = UDim2.new(0, 15, 0, 30)
Space.Font = Enum.Font.Code
Space.Text = "|"
Space.TextSize = 13.000
Space.TextColor3 = Color3.fromRGB(180,180,180)
Space.TextXAlignment = Enum.TextXAlignment.Center

			ToggleImage.Name = "ToggleImage"
			ToggleImage.Parent = Toggle
			ToggleImage.BackgroundColor3 = Color3.fromRGB(225, 225, 225)
			ToggleImage.Position = UDim2.new(0, 313, 0, 5)
			ToggleImage.Size = UDim2.new(0, 45, 0, 20)

			UICorner_3.CornerRadius = UDim.new(0, 10)
			UICorner_3.Parent = ToggleImage

			Circle.Name = "Circle"
			Circle.Parent = ToggleImage
			Circle.BackgroundColor3 = Color3.fromRGB(227, 60, 60)
			Circle.Position = UDim2.new(0, 2, 0, 2)
			Circle.Size = UDim2.new(0, 16, 0, 16)

			UICorner_4.CornerRadius = UDim.new(0, 10)
			UICorner_4.Parent = Circle

			Button.MouseButton1Click:Connect(function()
				if toggled == false then
					toggled = true
					Circle:TweenPosition(UDim2.new(0,27,0,2),"Out","Sine",0.2,true)
					TweenService:Create(
						Circle,
						TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
						{BackgroundColor3 = _G.Color1}
					):Play()
				else
					toggled = false
					Circle:TweenPosition(UDim2.new(0,2,0,2),"Out","Sine",0.2,true)
					TweenService:Create(
						Circle,
						TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
						{BackgroundColor3 = Color3.fromRGB(255, 0, 0)}
					):Play()
				end
				pcall(callback,toggled)
			end)

			if config == true then
				toggled = true
				Circle:TweenPosition(UDim2.new(0,27,0,2),"Out","Sine",0.4,true)
				TweenService:Create(
					Circle,
					TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
					{BackgroundColor3 = _G.Color1}
				):Play()
				pcall(callback,toggled)
			end
		end
		

		
		function main:AddDropdown(droptitle, list, callback)
-- Local --
local dropfunc = {}
local list = list or {}
local DropToggled = false
local DropSizeFrame = Instance.new("Frame")
local Frame = Instance.new("Frame")
local UIStroke = Instance.new("UIStroke")
local DropCover = Instance.new("Frame")
local UICorner = Instance.new("UICorner")
local UICorner2 = Instance.new("UICorner")
local ImageLabel = Instance.new("ImageLabel")
local Space = Instance.new("TextLabel")
local Title = Instance.new("TextLabel")
local ImageButton = Instance.new("ImageButton")
local DropStrokeList = Instance.new("UIStroke")
local DropTextList = Instance.new("TextLabel")

-- Prop --
DropSizeFrame.Name = droptitle or "DropSizeFrame"
DropSizeFrame.Parent = MainFramePage
DropSizeFrame.BackgroundColor3 = _G.SectionColor
DropSizeFrame.BackgroundTransparency = 1.000
DropSizeFrame.Size = UDim2.new(0, 360, 0, 60)

Frame.Name = "Frame"
Frame.Parent = DropSizeFrame
Frame.BackgroundColor3 = Color3.fromRGB(30,30,30)
Frame.BorderSizePixel = 0
Frame.Position = UDim2.new(0, 3, 0, 0)
Frame.Size = UDim2.new(0, 360, 0, 60)

UIStroke.Name = "UIStroke"
UIStroke.Parent = Frame
UIStroke.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
UIStroke.Color = Color3.fromRGB(51,255,255)
UIStroke.LineJoinMode = Enum.LineJoinMode.Round
UIStroke.Thickness = 0.5
UIStroke.Transparency = 0
UIStroke.Enabled = true
UIStroke.Archivable = true

UICorner.Parent = Frame
UICorner.CornerRadius = UDim.new(0, 3)

DropCover.Name = "DropCover"
DropCover.Parent = Frame
DropCover.BackgroundColor3 = _G.BackgroundItemColor
DropCover.BackgroundTransparency = 1.000
DropCover.BorderSizePixel = 0
DropCover.Position = UDim2.new(0, 0, 0, 0)
DropCover.Size = UDim2.new(0, 360, 0, 30)

ImageLabel.Name = "ImageLabel"
ImageLabel.Parent = DropCover
ImageLabel.BackgroundColor3 = _G.SectionColor
ImageLabel.BackgroundTransparency = 1.000
ImageLabel.BorderSizePixel = 0
ImageLabel.Position = UDim2.new(0, 5, 0, 6)
ImageLabel.Size = UDim2.new(0, 18, 0, 18)
ImageLabel.Image = "rbxassetid://8825010231"
ImageLabel.ImageColor3 = Color3.fromRGB(51,255,255)

Space.Name = "Space"
Space.Parent = DropCover
Space.BackgroundColor3 = _G.SectionColor
Space.BackgroundTransparency = 1.000
Space.Position = UDim2.new(0, 30, 0, 0)
Space.Size = UDim2.new(0, 15, 0, 30)
Space.Font = Enum.Font.Code
Space.Text = "|"
Space.TextSize = 13.000
Space.TextColor3 = Color3.fromRGB(51,255,255)
Space.TextXAlignment = Enum.TextXAlignment.Center

Title.Name = "Title"
Title.Parent = DropCover
Title.BackgroundColor3 = _G.SectionColor
Title.BackgroundTransparency = 1.000
Title.Position = UDim2.new(0, 50, 0, 0)
Title.Size = UDim2.new(0, 280, 0, 30)
Title.Font = Enum.Font.Code
Title.Text = droptitle or "drop Title"
Title.TextColor3 = Color3.fromRGB(51,255,255)
Title.TextSize = 12.000
Title.TextXAlignment = Enum.TextXAlignment.Left

ImageButton.Name = "ImageButton"
ImageButton.Parent = DropCover
ImageButton.BackgroundColor3 = _G.WindowBackgroundColor
ImageButton.BackgroundTransparency = 1.000
ImageButton.Position = UDim2.new(0, 330, 0, 7)
ImageButton.Size = UDim2.new(0, 23, 0, 18)
ImageButton.Image = "rbxassetid://8825010231"
ImageButton.ImageColor3 = Color3.fromRGB(51,255,255)
ImageButton.Rotation = 180

DropTextList.Name = "DropTextList"
DropTextList.Parent = Frame
DropTextList.BackgroundColor3 = _G.BackgroundItemColor
DropTextList.BackgroundTransparency = 1.000
DropTextList.Position = UDim2.new(0, 3, 0, 30)
DropTextList.Size = UDim2.new(0, 350, 0, 25)
DropTextList.Font = Enum.Font.Code
DropTextList.Text = v or "Select First"
DropTextList.TextColor3 = Color3.fromRGB(51,255,255)
DropTextList.TextSize = 12.000
DropTextList.TextXAlignment = Enum.TextXAlignment.Center

UICorner2.Parent = DropTextList
UICorner2.CornerRadius = UDim.new(0,3)

DropStrokeList.Name = "DropStrokeList"
DropStrokeList.Parent = DropTextList
DropStrokeList.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
DropStrokeList.Color = Color3.fromRGB(51,255,255)
DropStrokeList.LineJoinMode = Enum.LineJoinMode.Round
DropStrokeList.Thickness = 0.2
DropStrokeList.Transparency = 0
DropStrokeList.Enabled = true
DropStrokeList.Archivable = true

-- Adden Local --
local DropItemScroll = Instance.new("ScrollingFrame")
local DropItemLayout = Instance.new("UIListLayout")
local DropItemStroke = Instance.new("UIStroke")

-- Adden Prop --
DropItemScroll.Name = "DropItemScroll"
DropItemScroll.Parent = Frame
DropItemScroll.BackgroundColor3 = _G.SectionColor
DropItemScroll.BackgroundTransparency = 1.000
DropItemScroll.Position = UDim2.new(0, 3, 0, 60)
DropItemScroll.Size = UDim2.new(0, 330, 0, 0)
DropItemScroll.ScrollBarThickness = 0
DropItemScroll.CanvasSize = UDim2.new(0, 0, 0, 0)

DropItemLayout.Name = "DropItemLayout"
DropItemLayout.Parent = DropItemScroll
DropItemLayout.SortOrder = Enum.SortOrder.LayoutOrder
DropItemLayout.Padding = UDim.new(0, 0)

DropItemStroke.Name = "DropItemStroke"
DropItemStroke.Parent = DropItemScroll
DropItemStroke.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
DropItemStroke.Color = Color3.fromRGB(51,255,255)
DropItemStroke.LineJoinMode = Enum.LineJoinMode.Round
DropItemStroke.Thickness = 0
DropItemStroke.Transparency = 0
DropItemStroke.Enabled = true
DropItemStroke.Archivable = true

-- Dropdown Script--
local ItemCount = 0
local FrameSize = 0

ImageButton.MouseButton1Click:Connect(function()
 if DropToggled then
DropToggled = false
DropSizeFrame:TweenSize(UDim2.new(0, 330, 0, 60), 'InOut', 'Linear', 0.08)
Frame:TweenSize(UDim2.new(0, 360, 0, 60), 'InOut', 'Linear', 0.08)
DropItemScroll:TweenSize(UDim2.new(0, 330, 0, 0), 'InOut', 'Linear', 0.08)
game.TweenService:Create(ImageButton, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
{Rotation = 180}
):Play()
game.TweenService:Create(ImageButton, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
{ImageColor3 = Color3.fromRGB(51,255,255)}
):Play()

 else
DropToggled = true
DropSizeFrame:TweenSize(UDim2.new(0, 387, 0, 65 + FrameSize), 'InOut', 'Linear', 0.08)
Frame:TweenSize(UDim2.new(0, 360, 0, 65 + FrameSize), 'InOut', 'Linear', 0.08)
DropItemScroll:TweenSize(UDim2.new(0, 375, 0, FrameSize), 'InOut', 'Linear', 0.08)
game.TweenService:Create(ImageButton, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
{Rotation = 0}
):Play()
game.TweenService:Create(ImageButton, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
{ImageColor3 = Color3.fromRGB(51,255,255)}
):Play()
 end
end)

for i,v in next, list do
 ItemCount = ItemCount + 1
 if ItemCount == 1 then
FrameSize = 30
 elseif ItemCount == 2 then
FrameSize = 60
 elseif ItemCount == 3 then
FrameSize = 90
 elseif ItemCount >= 3 then
FrameSize = 120
 end
 
 local ItemList = Instance.new("TextButton")
 
 ItemList.Name = "ItemList"
 ItemList.Parent = DropItemScroll
 ItemList.BackgroundColor3 = Color3.fromRGB(51,255,255)
 ItemList.BackgroundTransparency = 1.000
 ItemList.Size = UDim2.new(0, 350, 0, 30)
 ItemList.AutoButtonColor = false
 ItemList.Font = Enum.Font.Code
 ItemList.TextColor3 = Color3.fromRGB(51,255,255)
 ItemList.TextSize = 12.000
 ItemList.Text = v or "None..."
 ItemList.TextXAlignment = Enum.TextXAlignment.Center

 ItemList.MouseEnter:Connect(function()
game.TweenService:Create(ItemList, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
{BackgroundTransparency = 0.8}
):Play()
 end)
 ItemList.MouseLeave:Connect(function()
game.TweenService:Create(ItemList, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
{BackgroundTransparency = 1}
):Play()
 end)
 
 ItemList.MouseButton1Click:Connect(function()
DropTextList.Text = v or "None..."
pcall(callback, v)
DropToggled = false
DropSizeFrame:TweenSize(UDim2.new(0, 387, 0, 60), 'InOut', 'Linear', 0.08)
Frame:TweenSize(UDim2.new(0, 360, 0, 60), 'InOut', 'Linear', 0.08)
DropItemScroll:TweenSize(UDim2.new(0, 375, 0), 'InOut', 'Linear', 0.08)
game.TweenService:Create(ImageButton, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
{Rotation = 180}
):Play()
game.TweenService:Create(ImageButton, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
{ImageColor3 = Color3.fromRGB(51,255,255)}
):Play()
 end)
 DropItemScroll.CanvasSize = UDim2.new(0, 0, 0, DropItemLayout.AbsoluteContentSize.Y)
end

function dropfunc:Clear()
                    for _,v  in next, DropItemScroll:GetChildren() do
                        if v:IsA("TextButton") then
                            v:Destroy()
                            FrameSize = 0
                            ItemCount = 0
                        end
                    end
                    DropTextList.Text = "Reset Succesfully..."
                    DropToggled = false
                    DropSizeFrame:TweenSize(UDim2.new(0, 330, 0, 60), 'InOut', 'Linear', 0.08)
                    Frame:TweenSize(UDim2.new(0, 360, 0, 60), 'InOut', 'Linear', 0.08)
                    DropItemScroll:TweenSize(UDim2.new(0, 330, 0), 'InOut', 'Linear', 0.08)
                    game.TweenService:Create(ImageButton, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
                        {Rotation = 180}
                        ):Play()
                    game.TweenService:Create(ImageButton, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
                        {ImageColor3 = Color3.fromRGB(255,255,255)}
                        ):Play()
                end

function dropfunc:Add(newadd)
 newadd = newadd or {}
 ItemCount = ItemCount + 1
 if ItemCount == 1 then
FrameSize = 30
 elseif ItemCount == 2 then
FrameSize = 60
 elseif ItemCount == 3 then
FrameSize = 90
 elseif ItemCount >= 3 then
FrameSize = 120
 end
 
 local ItemList = Instance.new("TextButton")
 ItemList.Name = "ItemList"
 ItemList.Parent = DropItemScroll
 ItemList.BackgroundColor3 = Color3.fromRGB(51,255,255)
 ItemList.BackgroundTransparency = 1.000
 ItemList.Size = UDim2.new(0, 330, 0, 30)
 ItemList.AutoButtonColor = false
 ItemList.Font = Enum.Font.Code
 ItemList.TextColor3 = Color3.fromRGB(51,255,255)
 ItemList.TextSize = 12.000
 ItemList.Text = newadd or "None..."
 ItemList.TextXAlignment = Enum.TextXAlignment.Center

 ItemList.MouseEnter:Connect(function()
game.TweenService:Create(ItemList, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
{BackgroundTransparency = 0.8}
):Play()
 end)
 ItemList.MouseLeave:Connect(function()
game.TweenService:Create(ItemList, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
{BackgroundTransparency = 1}
):Play()
 end)
 
 ItemList.MouseButton1Click:Connect(function()
DropTextList.Text = newadd or "None..."
pcall(callback, newadd)
DropToggled = false
DropSizeFrame:TweenSize(UDim2.new(0, 330, 0, 60), 'InOut', 'Linear', 0.08)
Frame:TweenSize(UDim2.new(0, 360, 0, 60), 'InOut', 'Linear', 0.08)
DropItemScroll:TweenSize(UDim2.new(0, 330, 0), 'InOut', 'Linear', 0.08)
game.TweenService:Create(ImageButton, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
{Rotation = 180}
):Play()
game.TweenService:Create(ImageButton, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
{ImageColor3 = Color3.fromRGB(51,255,255)}
):Play()
 end)
 DropItemScroll.CanvasSize = UDim2.new(0, 0, 0, DropItemLayout.AbsoluteContentSize.Y)
end
return dropfunc
end
function main:AddSlider(slidertitle, min, max, start, callback)
local sliderfunc = {}
local SliderFrame = Instance.new("Frame")
local SliderFrame_2 = Instance.new("Frame")
local UIStroke = Instance.new("UIStroke")
local UICorner = Instance.new("UICorner")
local ImageLabel = Instance.new("ImageLabel")
local Space = Instance.new("TextLabel")
local Title = Instance.new("TextLabel")
local SliderInput = Instance.new("Frame")
local SliderButton = Instance.new("Frame")
local SliderCount = Instance.new("Frame")
local SliderCorner = Instance.new("UICorner")
local SliderCorner2 = Instance.new("UICorner")
local BoxFrame = Instance.new("Frame")
local SliderBox = Instance.new("TextBox")
local SliderStroke = Instance.new("UIStroke")
local Title_2 = Instance.new("TextButton")
local UICorner_2 = Instance.new("UICorner")
local UICorner_3 = Instance.new("UICorner")

-- Prop --
SliderFrame.Name = slidertitle or "SliderFrame"
SliderFrame.Parent = MainFramePage
SliderFrame.BackgroundColor3 = Color3.fromRGB(51,255,255)
SliderFrame.BackgroundTransparency = 1
SliderFrame.BorderSizePixel = 0
SliderFrame.Size = UDim2.new(0, 362, 0, 55)

SliderFrame_2.Name = "SliderFrame_2"
SliderFrame_2.Parent = SliderFrame
SliderFrame_2.BackgroundColor3 = Color3.fromRGB(30,30,30)
SliderFrame_2.BackgroundTransparency = 0
SliderFrame_2.BorderSizePixel = 0
SliderFrame_2.Position = UDim2.new(0, 0.5, 0, 0)
SliderFrame_2.Size = UDim2.new(0, 362, 0, 55)

UIStroke.Name = "UIStroke"
UIStroke.Parent = SliderFrame_2
UIStroke.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
UIStroke.Color = Color3.fromRGB(51,255,255)
UIStroke.LineJoinMode = Enum.LineJoinMode.Round
UIStroke.Thickness = 1
UIStroke.Transparency = 0
UIStroke.Enabled = true
UIStroke.Archivable = true

UICorner.Parent = SliderFrame_2
UICorner.CornerRadius = UDim.new(0, 3)

ImageLabel.Name = "ImageLabel"
ImageLabel.Parent = SliderFrame_2
ImageLabel.BackgroundColor3 = Color3.fromRGB(51,255,255)
ImageLabel.BackgroundTransparency = 1.000
ImageLabel.BorderSizePixel = 0
ImageLabel.Position = UDim2.new(0, 5, 0, 5)
ImageLabel.Size = UDim2.new(0, 18, 0, 18)
ImageLabel.Image = "rbxassetid://8825010231"
ImageLabel.ImageColor3 = Color3.fromRGB(180,180,180)

Space.Name = "Space"
Space.Parent = SliderFrame_2
Space.BackgroundColor3 = Color3.fromRGB(51,255,255)
Space.BackgroundTransparency = 1.000
Space.Position = UDim2.new(0, 30, 0, 0)
Space.Size = UDim2.new(0, 15, 0, 30)
Space.Font = Enum.Font.Code
Space.Text = "|"
Space.TextSize = 13.000
Space.TextColor3 = Color3.fromRGB(180,180,180)
Space.TextXAlignment = Enum.TextXAlignment.Center

Title.Name = "Title"
Title.Parent = SliderFrame_2
Title.BackgroundColor3 = Color3.fromRGB(51,255,255)
Title.BackgroundTransparency = 1.000
Title.Position = UDim2.new(0, 50, 0, 0)
Title.Size = UDim2.new(0, 280, 0, 30)
Title.Font = Enum.Font.Code
Title.Text = slidertitle or "Slider Title"
Title.TextColor3 = Color3.fromRGB(180,180,180)
Title.TextSize = 12.000
Title.TextXAlignment = Enum.TextXAlignment.Left

SliderInput.Name = "SliderInput"
SliderInput.Parent = SliderFrame_2
SliderInput.BackgroundColor3 = Color3.fromRGB(51,255,255)
SliderInput.BackgroundTransparency = 0.7
SliderInput.BorderSizePixel = 0
SliderInput.Position = UDim2.new(0, 8, 0, 37)
SliderInput.Size = UDim2.new(0, 345, 0, 4)

SliderCorner2.CornerRadius = UDim.new(0, 100000)
SliderCorner2.Parent = SliderInput

SliderButton.Name = "SliderButton"
SliderButton.Parent = SliderInput
SliderButton.BackgroundColor3 = Color3.fromRGB(51,255,255)
SliderButton.BackgroundTransparency = 1.000
SliderButton.BorderSizePixel = 0
SliderButton.Position = UDim2.new(0, 0, 0, -7)
SliderButton.Size = UDim2.new(0, 341, 0, 25)

SliderCount.Name = "SliderCount"
SliderCount.Parent = SliderButton
SliderCount.BackgroundColor3 = Color3.fromRGB(51,255,255)
SliderCount.BackgroundTransparency = 0.3
SliderCount.BorderSizePixel = 0
SliderCount.Position = UDim2.new(0,start,0,0)
SliderCount.Size = UDim2.new(0, 18, 0, 18)
 
Title_2.Name = "Title_2"
Title_2.Parent = SliderButton
Title_2.AnchorPoint = Vector2.new(0, 0)
Title_2.BackgroundColor3 = Color3.fromRGB(255,0,0)
Title_2.AutoButtonColor = false
Title_2.BackgroundTransparency = 1.000
Title_2.Position = UDim2.new(0,start,0,0)
Title_2.Size = UDim2.new(0, 18, 0, 18)
Title_2.Font = Enum.Font.Code
Title_2.Text = tostring(start and math.floor((start / max) * (max - min) + min) or 0)
Title_2.TextColor3 = Color3.fromRGB(51,255,255)
Title_2.TextSize = 8.000
Title_2.TextXAlignment = Enum.TextXAlignment.Center

UICorner_2.Parent = Title_2
UICorner_2.CornerRadius = UDim.new(0, 100000)

SliderCorner.CornerRadius = UDim.new(0, 100000)
SliderCorner.Parent = SliderCount

SliderStroke.Name = "SliderStroke"
SliderStroke.Parent = BoxFrame
SliderStroke.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
SliderStroke.Color = Color3.fromRGB(180,180,180)
SliderStroke.LineJoinMode = Enum.LineJoinMode.Round
SliderStroke.Thickness = 1
SliderStroke.Transparency = 0.5
SliderStroke.Enabled = true
SliderStroke.Archivable = true

BoxFrame.Name = "BoxFrame"
BoxFrame.Parent = SliderFrame_2
BoxFrame.BackgroundColor3 = Color3.fromRGB(51,255,255)
BoxFrame.BackgroundTransparency = 1.000
BoxFrame.Size = UDim2.new(0, 50, 0, 15)
BoxFrame.Position = UDim2.new(0, 298, 0, 8)
SliderBox.Name = "SliderBox"
SliderBox.Parent = BoxFrame
SliderBox.BackgroundColor3 = Color3.fromRGB(200, 0, 0)
SliderBox.BackgroundTransparency = 1.000
SliderBox.Position = UDim2.new(0, 0, 0, 1.80)
SliderBox.Size = UDim2.new(0, 50, 0, 15)
SliderBox.ClearTextOnFocus = false
SliderBox.Font = Enum.Font.Code
SliderBox.Text = tostring(start and math.floor((start / max) * (max - min) + min) or 0)
SliderBox.TextColor3 = Color3.fromRGB(200,200,200)
SliderBox.TextSize = 10.000
SliderBox.TextTransparency = 0
SliderBox.TextXAlignment = Enum.TextXAlignment.Center
SliderBox.TextEditable = true

UICorner_3.Parent = BoxFrame
UICorner_3.CornerRadius = UDim.new(0, 2)

-- Slider Script --
local dragging
local SliderButtonStart
local SliderButtonInput
local slide = SliderButton

local function slide(input)
 local slidein = UDim2.new(math.clamp((input.Position.X - SliderButton.AbsolutePosition.X) / SliderButton.AbsoluteSize.X, 0, 1), 0, 0, 0)
 SliderCount:TweenPosition(slidein, Enum.EasingDirection.InOut, Enum.EasingStyle.Linear, 0.08, true)
 Title_2:TweenPosition(slidein, Enum.EasingDirection.InOut, Enum.EasingStyle.Linear, 0.12, true)
 local Value = math.floor(((slidein.X.Scale * max) / max) * (max - min) + min)
 SliderBox.Text = tostring(Value)
 Title_2.Text = tostring(Value)
 pcall(callback, Value, slidein)
end

SliderButton.InputBegan:Connect(function(input)
 if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
dragging = true
SliderButtonInput = input
SliderButtonStart = input.Position.X
slidein = SliderButton.AbsolutePosition.X
game.TweenService:Create(SliderCount, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {BackgroundTransparency = 0, Size = UDim2.new(0, 14, 0, 14)}):Play()
game.TweenService:Create(Title_2, TweenInfo.new(0.12, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {AnchorPoint = Vector2.new(0.22, 0.8), TextSize = 13.000, BackgroundTransparency = 0, Size = UDim2.new(0, 20, 0, 25)}):Play()
game.TweenService:Create(SliderBox, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {TextTransparency = 0}):Play()
game.TweenService:Create(SliderInput, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {BackgroundTransparency = 0.5}):Play()
game.TweenService:Create(SliderStroke, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {Transparency = 0}):Play()
 end
 input.Changed:Connect(function(input)
if input.UserInputType == Enum.UserInputState.End then
dragging = false

end
 end)
end)
SliderButton.InputEnded:Connect(function(input)
 if input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch then
dragging = false
SliderButtonInput = input
game.TweenService:Create(SliderCount, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {BackgroundTransparency = 0.3, Size = UDim2.new(0, 18, 0, 18)}):Play()
game.TweenService:Create(Title_2, TweenInfo.new(0.12, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {AnchorPoint = Vector2.new(0, 0), TextSize = 8.000, BackgroundTransparency = 1.000, Size = UDim2.new(0, 18, 0, 18)}):Play()
game.TweenService:Create(SliderBox, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {TextTransparency = 0.5}):Play()
game.TweenService:Create(SliderInput, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {BackgroundTransparency = 0.7}):Play()
game.TweenService:Create(SliderStroke, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {Transparency = 0.5}):Play()
 end
end)
UserInputService.InputChanged:Connect(function(input)
 if input == SliderButtonInput and dragging then
slide(input)
 end
end)

function set(property)
 if property == "Text" then
if tonumber(SliderBox.Text) then 
if tonumber(SliderBox.Text) <= max then
 Value = SliderBox.Text
 Title_2.Text = SliderBox.Text
 SliderCount:TweenPosition(UDim2.new(((tonumber(SliderBox.Text) or min) - min) / (max - min), 0, 0, 0), "InOut", "Linear", 0.05, true)
 Title_2:TweenPosition(UDim2.new(((tonumber(SliderBox.Text) or min) - min) / (max - min), 0, 0, 0), "InOut", "Linear", 0.8, true)
 pcall(function()
 callback(Value)
 end)
end
if tonumber(SliderBox.Text) > max then
 SliderBox.Text = max
 Title_2.Text = max
 Value = max
 SliderCount:TweenPosition(UDim2.new(((max or min) - min) / (max - min), 0, 0, 0), "InOut", "Linear", 0.08, true)
 Title_2:TweenPosition(UDim2.new(((max or min) - min) / (max - min), 0, 0, 0), "InOut", "Linear", 0.12, true)
 pcall(function()
 callback(Value)
 end)
end
if tonumber(SliderBox.Text) >= min then
 Value = SliderBox.Text
 Title_2.Text = SliderBox.Text
 SliderCount:TweenPosition(UDim2.new(((tonumber(SliderBox.Text) or min) - min) / (max - min), 0, 0, 0), "InOut", "Linear", 0.08, true)
 Title_2:TweenPosition(UDim2.new(((tonumber(SliderBox.Text) or min) - min) / (max - min), 0, 0, 0), "InOut", "Linear", 0.12, true)
 pcall(function()
 callback(Value)
 end)
end
if tonumber(SliderBox.Text) < min then
 Value = min
 Title_2 = min
 SliderCount.Position = UDim2.new(((min or min) - min) / (max - min), 0, 0, 0)
 Title_2.Position = UDim2.new(((min or min) - min) / (max - min), 0, 0, 0)
 pcall(function()
 callback(Value)
 end)
end
else
SliderBox.Text = "" or Value
Title_2.Text = Value
end
 end
end

SliderBox.Focused:Connect(function()
 SliderBox.Changed:Connect(set)
end)

SliderBox.FocusLost:Connect(function(enterP)
 if not enterP then
if SliderBox.Text == "" then
SliderBox.Text = min
Title_2.Text = min
Value = min
SliderCount:TweenPosition(UDim2.new(((min) - min) / (max - min), 0, 0, 0), "InOut", "Linear", 0.08, true)
Title_2:TweenPosition(UDim2.new(((min) - min) / (max - min), 0, 0, 0), "InOut", "Linear", 0.12, true)
pcall(function()
 callback(Value)
end)
end
if tonumber(SliderBox.Text) > tonumber(max) then
Value = max
SliderBox.Text = max
Title_2.Text = max
SliderCount:TweenPosition(UDim2.new(((max or min) - min) / (max - min), 0, 0, 0), "InOut", "Linear", 0.08, true)
Title_2:TweenPosition(UDim2.new(((max or min) - min) / (max - min), 0, 0, 0), "InOut", "Linear", 0.12, true)
pcall(function()
 callback(Value)
end)
else
Value = tonumber(SliderBox.Text)
end
if tonumber(SliderBox.Text) < min then
SliderBox.Text = min
Title_2.Text = min
Value = min
SliderCount:TweenPosition(UDim2.new(((min) - min) / (max - min), 0, 0, 0), "InOut", "Linear", 0.08, true)
Title_2:TweenPosition(UDim2.new(((min) - min) / (max - min), 0, 0, 0), "InOut", "Linear", 0.12, true)
pcall(function()
 callback(Value)
end)
else
Value = tonumber(SliderBox.Text)
end
 end
 if tonumber(SliderBox.Text) > max then
SliderBox.Text = max
Title_2.Text = max
Value = max
SliderCount:TweenPosition(UDim2.new(((max or min) - min) / (max - min), 0, 0, 0), "InOut", "Linear", 0.08, true)
Title_2:TweenPosition(UDim2.new(((max or min) - min) / (max - min), 0, 0, 0), "InOut", "Linear", 0.12, true)
pcall(function()
callback(Value)
end)
 else
Value = tonumber(SliderBox.Text)
 end
 if tonumber(SliderBox.Text) < min then
SliderBox.Text = min
Title_2.Text = min
Value = min
SliderCount.Position = UDim2.new(((min) - min) / (max - min), 0, 0, 0)
Title_2.Position = UDim2.new(((min) - min) / (max - min), 0, 0, 0)
pcall(function()
callback(Value)
end)
 else
Value = tonumber(SliderBox.Text)
 end
 if SliderBox.Text == "" then
SliderBox.Text = min
Title_2.Text = min
Value = min
SliderCount:TweenPosition(UDim2.new(((min) - min) / (max - min), 0, 0, 0), "InOut", "Linear", 0.08, true)
Title_2:TweenPosition(UDim2.new(((min) - min) / (max - min), 0, 0, 0), "InOut", "Linear", 0.12, true)
pcall(function()
callback(Value)
end)
 end
end)
return sliderfunc
end

		function main:AddTextbox(text,disappear,callback)
			local Textbox = Instance.new("Frame")
			local TextboxCorner = Instance.new("UICorner")
			local Textboxx = Instance.new("Frame")
			local TextboxxCorner = Instance.new("UICorner")
			local TextboxLabel = Instance.new("TextLabel")
			local txtbtn = Instance.new("TextButton")
			local RealTextbox = Instance.new("TextBox")
			local UICorner = Instance.new("UICorner")

			Textbox.Name = "Textbox"
			Textbox.Parent = MainFramePage
			Textbox.BackgroundColor3 = _G.Color
			Textbox.BackgroundTransparency = 0
			Textbox.Size = UDim2.new(0, 362, 0, 31)

			TextboxCorner.CornerRadius = UDim.new(0, 5)
			TextboxCorner.Name = "TextboxCorner"
			TextboxCorner.Parent = Textbox

			Textboxx.Name = "Textboxx"
			Textboxx.Parent = Textbox
			Textboxx.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
			Textboxx.Position = UDim2.new(0, 1, 0, 1)
			Textboxx.Size = UDim2.new(0, 360, 0, 29)

			TextboxxCorner.CornerRadius = UDim.new(0, 5)
			TextboxxCorner.Name = "TextboxxCorner"
			TextboxxCorner.Parent = Textboxx

			TextboxLabel.Name = "TextboxLabel"
			TextboxLabel.Parent = Textbox
			TextboxLabel.BackgroundColor3 = Color3.fromRGB(51,255,255)
			TextboxLabel.BackgroundTransparency = 1.000
			TextboxLabel.Position = UDim2.new(0, 15, 0, 0)
			TextboxLabel.Text = text
			TextboxLabel.Size = UDim2.new(0, 145, 0, 31)
			TextboxLabel.Font = Enum.Font.Code
			TextboxLabel.TextColor3 = Color3.fromRGB(225, 225, 225)
			TextboxLabel.TextSize = 16.000
			TextboxLabel.TextTransparency = 0
			TextboxLabel.TextXAlignment = Enum.TextXAlignment.Left

			txtbtn.Name = "txtbtn"
			txtbtn.Parent = Textbox
			txtbtn.BackgroundColor3 = Color3.fromRGB(51,255,255)
			txtbtn.BackgroundTransparency = 1.000
			txtbtn.Position = UDim2.new(0, 1, 0, 1)
			txtbtn.Size = UDim2.new(0, 360, 0, 29)
			txtbtn.Font = Enum.Font.SourceSans
			txtbtn.Text = ""
			txtbtn.TextColor3 = Color3.fromRGB(0, 0, 0)
			txtbtn.TextSize = 14.000

			RealTextbox.Name = "RealTextbox"
			RealTextbox.Parent = Textbox
			RealTextbox.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
			RealTextbox.BackgroundTransparency = 0
			RealTextbox.Position = UDim2.new(0, 255, 0, 4)
			RealTextbox.Size = UDim2.new(0, 100, 0, 24)
			RealTextbox.Font = Enum.Font.Code
			RealTextbox.Text = ""
			RealTextbox.TextColor3 = Color3.fromRGB(225, 225, 225)
			RealTextbox.TextSize = 11.000
			RealTextbox.TextTransparency = 0

			RealTextbox.FocusLost:Connect(function()
				callback(RealTextbox.Text)
				if disappear then
					RealTextbox.Text = ""
				end
			end)

			UICorner.CornerRadius = UDim.new(0, 5)
			UICorner.Parent = RealTextbox
		end
		function main:AddLabel(text)
			local Label = Instance.new("TextLabel")
			local PaddingLabel = Instance.new("UIPadding")
			local labelfunc = {}
	
			Label.Name = "Label"
			Label.Parent = MainFramePage
			Label.BackgroundColor3 = Color3.fromRGB(51,255,255)
			Label.BackgroundTransparency = 1.000
			Label.Size = UDim2.new(0, 360, 0, 20)
			Label.Font = Enum.Font.Code
			Label.TextColor3 = Color3.fromRGB(225, 225, 225)
			Label.TextSize = 14.000
			Label.Text = text
			Label.TextXAlignment = Enum.TextXAlignment.Left

			PaddingLabel.PaddingLeft = UDim.new(0,15)
			PaddingLabel.Parent = Label
			PaddingLabel.Name = "PaddingLabel"
	
			function labelfunc:Set(newtext)
			Label.Text = newtext
		end
		return labelfunc
		end

function main:Label1(text)
			local Label1 = Instance.new("TextLabel")
			local PaddingLabel1 = Instance.new("UIPadding")
			local Label1func = {}
	
			Label1.Name = "Label1"
			Label1.Parent = MainFramePage
			Label1.BackgroundColor3 = Color3.fromRGB(51,255,255)
			Label1.BackgroundTransparency = 1.000
			Label1.Size = UDim2.new(0, 360, 0, 20)
			Label1.Font = Enum.Font.Code
			Label1.TextColor3 = Color3.fromRGB(225, 225, 225)
			Label1.TextSize = 15.000
			Label1.Text = text
			Label1.TextXAlignment = Enum.TextXAlignment.Left

			PaddingLabel1.PaddingLeft = UDim.new(0,15)
			PaddingLabel1.Parent = Label1
			PaddingLabel1.Name = "PaddingLabel1"
function Label1func:Refresh(tochange)
 Label1.Text = tochange
end

return Label1func
end

		function main:AddSeperator(text)
			local Seperator = Instance.new("Frame")
			local Sep1 = Instance.new("Frame")
			local Sep2 = Instance.new("TextLabel")
			local Sep3 = Instance.new("Frame")
			
			Seperator.Name = "Seperator"
			Seperator.Parent = MainFramePage
			Seperator.BackgroundColor3 = Color3.fromRGB(51,255,255)
			Seperator.BackgroundTransparency = 1.000
			Seperator.Size = UDim2.new(0, 350, 0, 20)
			
			Sep1.Name = "Sep1"
			Sep1.Parent = Seperator
			Sep1.BackgroundColor3 = _G.Color
			Sep1.BorderSizePixel = 0
			Sep1.Position = UDim2.new(0, 0, 0, 10)
			Sep1.Size = UDim2.new(0, 90, 0, 1)
			
			Sep2.Name = "Sep2"
			Sep2.Parent = Seperator
			Sep2.BackgroundColor3 = Color3.fromRGB(51,255,255)
			Sep2.BackgroundTransparency = 1.000
			Sep2.Position = UDim2.new(0, 127, 0, 0)
			Sep2.Size = UDim2.new(0, 110, 0, 20)
			Sep2.Font = Enum.Font.Code
			Sep2.Text = text
			Sep2.TextColor3 = Color3.fromRGB(51,255,255)
			Sep2.TextSize = 20.000
			
			Sep3.Name = "Sep3"
			Sep3.Parent = Seperator
			Sep3.BackgroundColor3 = _G.Color
			Sep3.BorderSizePixel = 0
			Sep3.Position = UDim2.new(0, 270, 0, 10)
			Sep3.Size = UDim2.new(0, 90, 0, 1)
		end

		function main:AddLine()
			local Linee = Instance.new("Frame")
			local Line = Instance.new("Frame")
			
			Linee.Name = "Linee"
			Linee.Parent = MainFramePage
			Linee.BackgroundColor3 = Color3.fromRGB(51,255,255)
			Linee.BackgroundTransparency = 1.000
			Linee.Position = UDim2.new(0, 0, 0.119999997, 0)
			Linee.Size = UDim2.new(0, 360, 0, 20)
			
			Line.Name = "Line"
			Line.Parent = Linee
			Line.BackgroundColor3 = _G.Color
			Line.BorderSizePixel = 0
			Line.Position = UDim2.new(0, 0, 0, 10)
			Line.Size = UDim2.new(0, 360, 0, 1)
		end
		return main
	end
	return uitab
end

local RenUi = Update:AddWindow("STEAL",Enum.KeyCode.RightControl)
-- Tabes --
local A = RenUi:AddTab("• Main", "8825667942")
local S = RenUi:AddTab("• Check", nil)
-- Section --


osfunc = A:AddLabel("TimeZone")

local function UpdateOS()
        local date = os.date("*t")
        local hour = (date.hour) % 24
        local ampm = hour < 12 and "AM" or "PM"
        local timezone = string.format("%02i:%02i:%02i %s", ((hour -1) % 12) + 1, date.min, date.sec, ampm)
        local datetime = string.format("%02d/%02d/%04d", date.day, date.month, date.year)
        osfunc:Set("day : "..datetime.." Time : "..timezone)
    end
    spawn(function()
        while true do
            UpdateOS()
            game:GetService("RunService").RenderStepped:Wait()
        end
    end)

Time = A:AddLabel("Server Time")

function UpdateTime()
    local GameTime = math.floor(workspace.DistributedGameTime+0.5)
    local Hour = math.floor(GameTime/(60^2))%24
    local Minute = math.floor(GameTime/(60^1))%60
    local Second = math.floor(GameTime/(60^0))%60
    Time:Set("Hour : "..Hour.." Minute : "..Minute.." Second : "..Second)
end

spawn(function()
    while true do
        UpdateTime()
        wait()
    end
end)

Client = A:AddLabel("Ping Server")

function UpdateClient()
    local Ping = game:GetService("Stats").Network.ServerStatsItem["Data Ping"]:GetValueString()
    Client:Set("Ping : "..Ping)
end

spawn(function()
    while true do wait(.1)
        UpdateClient()
    end
end)

C = A:AddLabel("FPS Server")

function UpdateC()
    local Ping = game:GetService("Stats").Network.ServerStatsItem["Data Ping"]:GetValueString()
    local Fps = workspace:GetRealPhysicsFPS()
    C:Set("Fps : "..Fps)
end

spawn(function()
    while true do wait(.1)
        UpdateC()
    end
end)

pingfunc = A:AddLabel("Memory")

spawn(function()
        while game:GetService("RunService").RenderStepped:wait() do
            pingfunc:Set("Memory : " ..tostring(game:GetService("Stats").PerformanceStats.Memory:GetValueString()).." - "..tostring(game:GetService("Stats").PerformanceStats.NetworkReceived:GetValueString()).." - "..tostring(game:GetService("Stats").PerformanceStats.Ping:GetValueString()))
        end
    end)

A:AddLine()

  if game.PlaceId == 2753915549 then
        World1 = true
    elseif game.PlaceId == 4442272183 then
        World2 = true
    elseif game.PlaceId == 7449423635 then
        World3 = true
    end
    
    function ByPass(Position)
    game.Players.LocalPlayer.Character.Head:Destroy()
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = Position
    wait(.5)
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = Position
    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
   end
    
    function CheckQuest() 
        MyLevel = game:GetService("Players").LocalPlayer.Data.Level.Value
        if World1 then
            if MyLevel == 1 or MyLevel <= 9 then
                Mon = "Bandit [Lv. 5]"
                LevelQuest = 1
                NameQuest = "BanditQuest1"
                NameMon = "Bandit"
                PUK = CFrame.new(1216.779541015625, 56.393497467041016, 1606.126220703125)
                CFrameQuest = CFrame.new(1059.37195, 15.4495068, 1550.4231, 0.939700544, -0, -0.341998369, 0, 1, -0, 0.341998369, 0, 0.939700544)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 10 or MyLevel <= 14 then
                Mon = "Monkey [Lv. 14]"
                LevelQuest = 1
                NameQuest = "JungleQuest"
                NameMon = "Monkey"
                PUK = CFrame.new()
                CFrameQuest = CFrame.new(-1598.08911, 35.5501175, 153.377838, 0, 0, 1, 0, 1, -0, -1, 0, 0)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 15 or MyLevel <= 29 then
                Mon = "Gorilla [Lv. 20]"
                LevelQuest = 2
                NameQuest = "JungleQuest"
                NameMon = "Gorilla"
                PUK = CFrame.new(-1257.61181640625, 65.0517807006836, -499.2301025390625)
                CFrameQuest = CFrame.new(-1598.08911, 35.5501175, 153.377838, 0, 0, 1, 0, 1, -0, -1, 0, 0)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 30 or MyLevel <= 39 then
                Mon = "Pirate [Lv. 35]"
                LevelQuest = 1
                NameQuest = "BuggyQuest1"
                NameMon = "Pirate"
                PUK = CFrame.new(-1178.50244140625, 65.74028778076172, 3889.71630859375)
                CFrameQuest = CFrame.new(-1141.07483, 4.10001802, 3831.5498, 0.965929627, -0, -0.258804798, 0, 1, -0, 0.258804798, 0, 0.965929627)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 40 or MyLevel <= 59 then
                Mon = "Brute [Lv. 45]"
                LevelQuest = 2
                NameQuest = "BuggyQuest1"
                NameMon = "Brute"
                PUK = CFrame.new(-1144.44861, 90.5594559, 4307.25928, -0.998438537, 0, 0.0558618344, 0, 1, 0, -0.0558618344, 0, -0.998438537)
                CFrameQuest = CFrame.new(-1141.07483, 4.10001802, 3831.5498, 0.965929627, -0, -0.258804798, 0, 1, -0, 0.258804798, 0, 0.965929627)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 60 or MyLevel <= 74 then
                Mon = "Desert Bandit [Lv. 60]"
                LevelQuest = 1
                NameQuest = "DesertQuest"
                NameMon = "Desert Bandit"
                PUK = CFrame.new(919.5968017578125, 69.22762298583984, 4487.37109375)
                CFrameQuest = CFrame.new(894.488647, 5.14000702, 4392.43359, 0.819155693, -0, -0.573571265, 0, 1, -0, 0.573571265, 0, 0.819155693)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 75 or MyLevel <= 89 then
                Mon = "Desert Officer [Lv. 70]"
                LevelQuest = 2
                NameQuest = "DesertQuest"
                NameMon = "Desert Officer"
                PUK = CFrame.new(1580.03198, 4.61375761, 4366.86426)
                CFrameQuest = CFrame.new(894.488647, 5.14000702, 4392.43359, 0.819155693, -0, -0.573571265, 0, 1, -0, 0.573571265, 0, 0.819155693)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 90 or MyLevel <= 99 then
                Mon = "Snow Bandit [Lv. 90]"
                LevelQuest = 1
                NameQuest = "SnowQuest"
                NameMon = "Snow Bandit"
                PUK = CFrame.new(1365.15625, 124.89803314208984, -1364.9873046875)
                CFrameQuest = CFrame.new(1389.74451, 88.1519318, -1298.90796, -0.342042685, 0, 0.939684391, 0, 1, 0, -0.939684391, 0, -0.342042685)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 100 or MyLevel <= 119 then
                Mon = "Snowman [Lv. 100]"
                LevelQuest = 2
                NameQuest = "SnowQuest"
                NameMon = "Snowman"
                PUK = CFrame.new(1122.921875, 143.72373962402344, -1539.132080078125)
                CFrameQuest = CFrame.new(1389.74451, 88.1519318, -1298.90796, -0.342042685, 0, 0.939684391, 0, 1, 0, -0.939684391, 0, -0.342042685)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 120 or MyLevel <= 149 then
                Mon = "Chief Petty Officer [Lv. 120]"
                LevelQuest = 1
                NameQuest = "MarineQuest2"
                NameMon = "Chief Petty Officer"
                PUK = CFrame.new(-4882.8623, 22.6520386, 4255.53516)
                CFrameQuest = CFrame.new(-5039.58643, 27.3500385, 4324.68018, 0, 0, -1, 0, 1, 0, 1, 0, 0)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 150 or MyLevel <= 174 then
                Mon = "Sky Bandit [Lv. 150]"
                LevelQuest = 1
                NameQuest = "SkyQuest"
                NameMon = "Sky Bandit"
                PUK = CFrame.new(-4970.74219, 294.544342, -2890.11353)
                CFrameQuest = CFrame.new(-4839.53027, 716.368591, -2619.44165, 0.866007268, 0, 0.500031412, 0, 1, 0, -0.500031412, 0, 0.866007268)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 175 or MyLevel <= 189 then
                Mon = "Dark Master [Lv. 175]"
                LevelQuest = 2
                NameQuest = "SkyQuest"
                NameMon = "Dark Master"
                PUK = CFrame.new(-5220.58594, 430.693298, -2278.17456)
                CFrameQuest = CFrame.new(-4839.53027, 716.368591, -2619.44165, 0.866007268, 0, 0.500031412, 0, 1, 0, -0.500031412, 0, 0.866007268)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 190 or MyLevel <= 209 then
                Mon = "Prisoner [Lv. 190]"
                LevelQuest = 1
                NameQuest = "PrisonerQuest"
                NameMon = "Prisoner"
                PUK = CFrame.new(5308.93115, 1.65517521, 475.120514, -0.0894274712, -5.00292918e-09, -0.995993316, 1.60817859e-09, 1, -5.16744869e-09, 0.995993316, -2.06384709e-09, -0.0894274712)
                CFrameQuest = CFrame.new(5308.93115, 1.65517521, 475.120514, -0.0894274712, -5.00292918e-09, -0.995993316, 1.60817859e-09, 1, -5.16744869e-09, 0.995993316, -2.06384709e-09, -0.0894274712)
          if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
          elseif MyLevel == 210 or MyLevel <= 249 then 
                Mon = "Dangerous Prisoner [Lv. 210]"
                LevelQuest = 2
                NameQuest = "PrisonerQuest"
                NameMon = "Dangerous Prisoner"
                PUK = CFrame.new(5563.1171875, 67.71013641357422, 832.8712158203125)
                CFrameQuest = CFrame.new(5308.93115, 1.65517521, 475.120514, -0.0894274712, -5.00292918e-09, -0.995993316, 1.60817859e-09, 1, -5.16744869e-09, 0.995993316, -2.06384709e-09, -0.0894274712)
           if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
           elseif MyLevel == 250 or MyLevel <= 299 then
                Mon = "Toga Warrior [Lv. 250]"
                LevelQuest = 1
                NameQuest = "ColosseumQuest"
                NameMon = "Toga Warrior"
                PUK = CFrame.new(-1848.348876953125, 42.34652328491211, -2794.3759765625)
                CFrameQuest = CFrame.new(-1580.04663, 6.35000277, -2986.47534, -0.515037298, 0, -0.857167721, 0, 1, 0, 0.857167721, 0, -0.515037298)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 300 or MyLevel <= 324 then
                Mon = "Military Soldier [Lv. 300]"
                LevelQuest = 1
                NameQuest = "MagmaQuest"
                NameMon = "Military Soldier"
                PUK = CFrame.new(-5461.19140625, 44.07990264892578, 8457.443359375)
                CFrameQuest = CFrame.new(-5313.37012, 10.9500084, 8515.29395, -0.499959469, 0, 0.866048813, 0, 1, 0, -0.866048813, 0, -0.499959469)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 325 or MyLevel <= 374 then
                Mon = "Military Spy [Lv. 325]"
                LevelQuest = 2
                NameQuest = "MagmaQuest"
                NameMon = "Military Spy"
                PUK = CFrame.new(-5872.0625, 143.23089599609375, 8790.439453125)
                CFrameQuest = CFrame.new(-5313.37012, 10.9500084, 8515.29395, -0.499959469, 0, 0.866048813, 0, 1, 0, -0.866048813, 0, -0.499959469)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 375 or MyLevel <= 399 then
                Mon = "Fishman Warrior [Lv. 375]"
                LevelQuest = 1
                NameQuest = "FishmanQuest"
                NameMon = "Fishman Warrior"
                PUK = CFrame.new(60875.9921875, 35.35336685180664, 1434.669189453125)
                CFrameQuest = CFrame.new(61122.65234375, 18.497442245483, 1569.3997802734)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 400 or MyLevel <= 449 then
                Mon = "Fishman Commando [Lv. 400]"
                LevelQuest = 2
                NameQuest = "FishmanQuest"
                NameMon = "Fishman Commando"
                PUK = CFrame.new(61914.1484375, 82.76360321044922, 1461.85595703125)
                CFrameQuest = CFrame.new(61122.65234375, 18.497442245483, 1569.3997802734)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 450 or MyLevel <= 474 then
                Mon = "God's Guard [Lv. 450]"
                LevelQuest = 1
                NameQuest = "SkyExp1Quest"
                NameMon = "God's Guard"
                PUK = CFrame.new(-4721.88867, 843.874695, -1949.96643, 0.996191859, -0, -0.0871884301, 0, 1, -0, 0.0871884301, 0, 0.996191859)
                CFrameQuest = CFrame.new(-4721.88867, 843.874695, -1949.96643, 0.996191859, -0, -0.0871884301, 0, 1, -0, 0.0871884301, 0, 0.996191859)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 475 or MyLevel <= 524 then
                Mon = "Shanda [Lv. 475]"
                LevelQuest = 2
                NameQuest = "SkyExp1Quest"
                NameMon = "Shanda"
                PUK = CFrame.new(-7658.7041015625, 5605.01025390625, -529.287353515625)
                CFrameQuest = CFrame.new(-7859.09814, 5544.19043, -381.476196, -0.422592998, 0, 0.906319618, 0, 1, 0, -0.906319618, 0, -0.422592998)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 525 or MyLevel <= 549 then
                Mon = "Royal Squad [Lv. 525]"
                LevelQuest = 1
                NameQuest = "SkyExp2Quest"
                NameMon = "Royal Squad"
                PUK = CFrame.new(-7669.1796875, 5638.10986328125, -1448.95458984375)
                CFrameQuest = CFrame.new(-7906.81592, 5634.6626, -1411.99194, 0, 0, -1, 0, 1, 0, 1, 0, 0)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 550 or MyLevel <= 624 then
                Mon = "Royal Soldier [Lv. 550]"
                LevelQuest = 2
                NameQuest = "SkyExp2Quest"
                NameMon = "Royal Soldier"
                PUK = CFrame.new(-7839.28955078125, 5681.00830078125, -1717.6197509765625)
                CFrameQuest = CFrame.new(-7906.81592, 5634.6626, -1411.99194, 0, 0, -1, 0, 1, 0, 1, 0, 0)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 625 or MyLevel <= 649 then
                Mon = "Galley Pirate [Lv. 625]"
                LevelQuest = 1
                NameQuest = "FountainQuest"
                NameMon = "Galley Pirate"
                PUK = CFrame.new(5566.14453125, 71.22917175292969, 3964.4443359375)
                CFrameQuest = CFrame.new(5259.81982, 37.3500175, 4050.0293, 0.087131381, 0, 0.996196866, 0, 1, 0, -0.996196866, 0, 0.087131381)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel >= 650 then
                Mon = "Galley Captain [Lv. 650]"
                LevelQuest = 2
                NameQuest = "FountainQuest"
                NameMon = "Galley Captain"
                PUK = CFrame.new(5344.2529296875, 104.73433685302734, 4821.6533203125)
                CFrameQuest = CFrame.new(5259.81982, 37.3500175, 4050.0293, 0.087131381, 0, 0.996196866, 0, 1, 0, -0.996196866, 0, 0.087131381)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            end
        elseif World2 then
            if MyLevel == 700 or MyLevel <= 724 then
                Mon = "Raider [Lv. 700]"
                LevelQuest = 1
                NameQuest = "Area1Quest"
                NameMon = "Raider"
                PUK = CFrame.new(-737.026123, 39.1748352, 2392.57959)
                CFrameQuest = CFrame.new(-429.543518, 71.7699966, 1836.18188, -0.22495985, 0, -0.974368095, 0, 1, 0, 0.974368095, 0, -0.22495985)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 725 or MyLevel <= 774 then
                Mon = "Mercenary [Lv. 725]"
                LevelQuest = 2
                NameQuest = "Area1Quest"
                NameMon = "Mercenary"
                PUK = CFrame.new(-1016.576171875, 133.70040893554688, 1433.923095703125)
                CFrameQuest = CFrame.new(-429.543518, 71.7699966, 1836.18188, -0.22495985, 0, -0.974368095, 0, 1, 0, 0.974368095, 0, -0.22495985)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 775 or MyLevel <= 874 then
                Mon = "Swan Pirate [Lv. 775]"
                LevelQuest = 1
                NameQuest = "Area2Quest"
                NameMon = "Swan Pirate"
                PUK = CFrame.new(970.369446, 142.653198, 1217.3667)
                CFrameQuest = CFrame.new(638.43811, 71.769989, 918.282898, 0.139203906, 0, 0.99026376, 0, 1, 0, -0.99026376, 0, 0.139203906)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 875 or MyLevel <= 899 then
                Mon = "Marine Lieutenant [Lv. 875]"
                LevelQuest = 1
                NameQuest = "MarineQuest3"
                NameMon = "Marine Lieutenant"
                PUK = CFrame.new(-2929.03369140625, 163.5143585205078, -3027.66357421875)
                CFrameQuest = CFrame.new(-2440.79639, 71.7140732, -3216.06812, 0.866007268, 0, 0.500031412, 0, 1, 0, -0.500031412, 0, 0.866007268)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 900 or MyLevel <= 949 then
                Mon = "Marine Captain [Lv. 900]"
                LevelQuest = 2
                NameQuest = "MarineQuest3"
                NameMon = "Marine Captain"
                PUK = CFrame.new(-1932.095703125, 131.94061279296875, -3291.61865234375)
                CFrameQuest = CFrame.new(-2440.79639, 71.7140732, -3216.06812, 0.866007268, 0, 0.500031412, 0, 1, 0, -0.500031412, 0, 0.866007268)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 950 or MyLevel <= 999 then
                Mon = "Zombie [Lv. 950]"
                LevelQuest = 1
                NameQuest = "ZombieQuest"
                NameMon = "Zombie"
                PUK = CFrame.new(-5695.2451171875, 124.95378875732422, -775.65478515625)
                CFrameQuest = CFrame.new(-5497.06152, 47.5923004, -795.237061, -0.29242146, 0, -0.95628953, 0, 1, 0, 0.95628953, 0, -0.29242146)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 1000 or MyLevel <= 1049 then
                Mon = "Snow Trooper [Lv. 1000]"
                LevelQuest = 1
                NameQuest = "SnowMountainQuest"
                NameMon = "Snow Trooper"
                PUK = CFrame.new(535.893433, 401.457062, -5329.6958, -0.999524176, 0, 0.0308452044, 0, 1, -0, -0.0308452044, 0, -0.999524176)
                CFrameQuest = CFrame.new(609.858826, 400.119904, -5372.25928, -0.374604106, 0, 0.92718488, 0, 1, 0, -0.92718488, 0, -0.374604106)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 1050 or MyLevel <= 1099 then
                Mon = "Winter Warrior [Lv. 1050]"
                LevelQuest = 2
                NameQuest = "SnowMountainQuest"
                NameMon = "Winter Warrior"
                PUK = CFrame.new(1223.7417, 454.575226, -5170.02148, 0.473996818, 2.56845354e-08, 0.880526543, -5.62456428e-08, 1, 1.10811016e-09, -0.880526543, -5.00510211e-08, 0.473996818)
                CFrameQuest = CFrame.new(609.858826, 400.119904, -5372.25928, -0.374604106, 0, 0.92718488, 0, 1, 0, -0.92718488, 0, -0.374604106)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 1100 or MyLevel <= 1124 then
                Mon = "Lab Subordinate [Lv. 1100]"
                LevelQuest = 1
                NameQuest = "IceSideQuest"
                NameMon = "Lab Subordinate"
                PUK = CFrame.new(-6060.10693, 15.9868021, -4904.7876, -0.411000341, -5.06538868e-07, 0.91163528, 1.26306062e-07, 1, 6.12581289e-07, -0.91163528, 3.66916197e-07, -0.411000341)
                CFrameQuest = CFrame.new(-6064.06885, 15.2422857, -4902.97852, 0.453972578, -0, -0.891015649, 0, 1, -0, 0.891015649, 0, 0.453972578)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 1125 or MyLevel <= 1174 then
                Mon = "Horned Warrior [Lv. 1125]"
                LevelQuest = 2
                NameQuest = "IceSideQuest"
                NameMon = "Horned Warrior"
                PUK = CFrame.new(-6400.85889, 24.7645149, -5818.63574)
                CFrameQuest = CFrame.new(-6064.06885, 15.2422857, -4902.97852, 0.453972578, -0, -0.891015649, 0, 1, -0, 0.891015649, 0, 0.453972578)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 1175 or MyLevel <= 1199 then
                Mon = "Magma Ninja [Lv. 1175]"
                LevelQuest = 1
                NameQuest = "FireSideQuest"
                NameMon = "Magma Ninja"
                PUK = CFrame.new(-5496.65576, 58.6890411, -5929.76855)
                CFrameQuest = CFrame.new(-5428.03174, 15.0622921, -5299.43457, -0.882952213, 0, 0.469463557, 0, 1, 0, -0.469463557, 0, -0.882952213)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 1200 or MyLevel <= 1249 then
                Mon = "Lava Pirate [Lv. 1200]"
                LevelQuest = 2
                NameQuest = "FireSideQuest"
                NameMon = "Lava Pirate"
                PUK = CFrame.new(-5169.71729, 34.1234779, -4669.73633)
                CFrameQuest = CFrame.new(-5428.03174, 15.0622921, -5299.43457, -0.882952213, 0, 0.469463557, 0, 1, 0, -0.469463557, 0, -0.882952213)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 1250 or MyLevel <= 1274 then
                Mon = "Ship Deckhand [Lv. 1250]"
                LevelQuest = 1
                NameQuest = "ShipQuest1"
                NameMon = "Ship Deckhand"
                PUK = CFrame.new(1181.84875, 130.485107, 33005.4961, -0.946877539, -7.47373434e-08, -0.321594298, -7.391602e-08, 1, -1.47637005e-08, 0.321594298, 9.79155601e-09, -0.946877539)
                CFrameQuest = CFrame.new(1037.80127, 125.092171, 32911.6016)         
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 1275 or MyLevel <= 1299 then
                Mon = "Ship Engineer [Lv. 1275]"
                LevelQuest = 2
                NameQuest = "ShipQuest1"
                NameMon = "Ship Engineer"
                PUK = CFrame.new(919.250427, 43.544014, 32781.9922, 0.999619186, 4.03968698e-08, -0.0275939237, -3.75240887e-08, 1, 1.04626984e-07, 0.0275939237, -1.03551706e-07, 0.999619186)
                CFrameQuest = CFrame.new(1037.80127, 125.092171, 32911.6016)   
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end            
            elseif MyLevel == 1300 or MyLevel <= 1324 then
                Mon = "Ship Steward [Lv. 1300]"
                LevelQuest = 1
                NameQuest = "ShipQuest2"
                NameMon = "Ship Steward"
                PUK = CFrame.new(917.478882, 129.556, 33441.2227, -0.999965012, -1.84493896e-08, -0.00836863648, -1.84426696e-08, 1, -8.80260864e-10, 0.00836863648, -7.2589007e-10, -0.999965012)
                CFrameQuest = CFrame.new(968.80957, 125.092171, 33244.125)         
if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 1325 or MyLevel <= 1349 then
                Mon = "Ship Officer [Lv. 1325]"
                LevelQuest = 2
                NameQuest = "ShipQuest2"
                NameMon = "Ship Officer"
                PUK = CFrame.new(1201.18286, 181.149124, 33308.0508, 0.0748318806, -7.14178512e-08, -0.997196138, 2.97970733e-08, 1, -6.93826223e-08, 0.997196138, -2.45214959e-08, 0.0748318806)
                CFrameQuest = CFrame.new(968.80957, 125.092171, 33244.125)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 1350 or MyLevel <= 1374 then
                Mon = "Arctic Warrior [Lv. 1350]"
                LevelQuest = 1
                NameQuest = "FrostQuest"
                NameMon = "Arctic Warrior"
                PUK = CFrame.new(5667.6582, 26.7997818, -6486.08984, -0.933587909, 0, -0.358349502, 0, 1, 0, 0.358349502, 0, -0.933587909)
                CFrameQuest = CFrame.new(5667.6582, 26.7997818, -6486.08984, -0.933587909, 0, -0.358349502, 0, 1, 0, 0.358349502, 0, -0.933587909)
if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 1375 or MyLevel <= 1424 then
                Mon = "Snow Lurker [Lv. 1375]"
                LevelQuest = 2
                NameQuest = "FrostQuest"
                NameMon = "Snow Lurker"
                PUK = CFrame.new(5518.00684, 60.5559731, -6828.80518)
                CFrameQuest = CFrame.new(5667.6582, 26.7997818, -6486.08984, -0.933587909, 0, -0.358349502, 0, 1, 0, 0.358349502, 0, -0.933587909)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 1425 or MyLevel <= 1449 then
                Mon = "Sea Soldier [Lv. 1425]"
                LevelQuest = 1
                NameQuest = "ForgottenQuest"
                NameMon = "Sea Soldier"
                PUK = CFrame.new(-3366.32958984375, 47.21970748901367, -9704.3505859375)
                CFrameQuest = CFrame.new(-3054.44458, 235.544281, -10142.8193, 0.990270376, -0, -0.13915664, 0, 1, -0, 0.13915664, 0, 0.990270376)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel >= 1450 then
                Mon = "Water Fighter [Lv. 1450]"
                LevelQuest = 2
                NameQuest = "ForgottenQuest"
                NameMon = "Water Fighter"
                PUK = CFrame.new(-3436.7727050781, 290.52191162109, -10503.438476563)
                CFrameQuest = CFrame.new(-3054.44458, 235.544281, -10142.8193, 0.990270376, -0, -0.13915664, 0, 1, -0, 0.13915664, 0, 0.990270376)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            end
        elseif World3 then
            if MyLevel == 1500 or MyLevel <= 1524 then
                Mon = "Pirate Millionaire [Lv. 1500]"
                LevelQuest = 1
                NameQuest = "PiratePortQuest"
                NameMon = "Pirate Millionaire"
                PUK = CFrame.new(-290.674988, 34.7821121, 5417.57666, -0.959131062, 7.87279077e-08, 0.282962203, 6.99472977e-08, 1, -4.11336849e-08, -0.282962203, -1.96601544e-08, -0.959131062)
                CFrameQuest = CFrame.new(-290.074677, 42.9034653, 5581.58984, 0.965929627, -0, -0.258804798, 0, 1, -0, 0.258804798, 0, 0.965929627)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 1525 or MyLevel <= 1574 then
                Mon = "Pistol Billionaire [Lv. 1525]"
                LevelQuest = 2
                NameQuest = "PiratePortQuest"
                NameMon = "Pistol Billionaire"
                PUK = CFrame.new(-387.624237, 74.2720413, 5851.84473, -0.990750372, -6.79122536e-08, 0.135697171, -7.2516066e-08, 1, -2.89841076e-08, -0.135697171, -3.85562409e-08, -0.990750372)
                CFrameQuest = CFrame.new(-290.074677, 42.9034653, 5581.58984, 0.965929627, -0, -0.258804798, 0, 1, -0, 0.258804798, 0, 0.965929627)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 1575 or MyLevel <= 1599 then
                Mon = "Dragon Crew Warrior [Lv. 1575]"
                LevelQuest = 1
                NameQuest = "AmazonQuest"
                NameMon = "Dragon Crew Warrior"
                PUK = CFrame.new(6241.9951171875, 51.522083282471, -1243.9771728516)
                CFrameQuest = CFrame.new(5832.83594, 51.6806107, -1101.51563, 0.898790359, -0, -0.438378751, 0, 1, -0, 0.438378751, 0, 0.898790359)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 1600 or MyLevel <= 1624 then 
                Mon = "Dragon Crew Archer [Lv. 1600]"
                NameQuest = "AmazonQuest"
                LevelQuest = 2
                NameMon = "Dragon Crew Archer"
                PUK = CFrame.new(6788.97461, 462.341248, 164.233673, -0.711975694, 1.98202414e-08, 0.702204108, -1.45830699e-08, 1, -4.30117559e-08, -0.702204108, -4.08636183e-08, -0.711975694)
                CFrameQuest = CFrame.new(5833.1147460938, 51.60498046875, -1103.0693359375)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 1625 or MyLevel <= 1649 then
                Mon = "Female Islander [Lv. 1625]"
                NameQuest = "AmazonQuest2"
                LevelQuest = 1
                NameMon = "Female Islander"
                PUK = CFrame.new(5763.98682, 848.118103, 1082.43127, 0.986172736, 2.65753979e-08, 0.165720671, -2.36233451e-08, 1, -1.97844852e-08, -0.165720671, 1.55960436e-08, 0.986172736)
                CFrameQuest = CFrame.new(5446.8793945313, 601.62945556641, 749.45672607422)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 1650 or MyLevel <= 1699 then 
                Mon = "Giant Islander [Lv. 1650]"
                NameQuest = "AmazonQuest2"
                LevelQuest = 2
                NameMon = "Giant Islander"
                PUK = CFrame.new(4784.24561, 708.376465, 466.297485, 0.99801594, 3.11927195e-09, 0.0629619658, -5.34848299e-09, 1, 3.52371394e-08, -0.0629619658, -3.55039766e-08, 0.99801594)
                CFrameQuest = CFrame.new(5446.8793945313, 601.62945556641, 749.45672607422)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 1700 or MyLevel <= 1724 then
                Mon = "Marine Commodore [Lv. 1700]"
                LevelQuest = 1
                NameQuest = "MarineTreeIsland"
                NameMon = "Marine Commodore"
                PUK = CFrame.new(2490.0844726563, 190.4232635498, -7160.0502929688)
                CFrameQuest = CFrame.new(2180.54126, 27.8156815, -6741.5498, -0.965929747, 0, 0.258804798, 0, 1, 0, -0.258804798, 0, -0.965929747)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 1725 or MyLevel <= 1774 then
                Mon = "Marine Rear Admiral [Lv. 1725]"
                NameMon = "Marine Rear Admiral"
                NameQuest = "MarineTreeIsland"
                LevelQuest = 2
                PUK = CFrame.new(3951.3903808594, 229.11549377441, -6912.81640625)
                CFrameQuest = CFrame.new(2179.98828125, 28.731239318848, -6740.0551757813)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 1775 or MyLevel <= 1799 then
                Mon = "Fishman Raider [Lv. 1775]"
                LevelQuest = 1
                NameQuest = "DeepForestIsland3"
                NameMon = "Fishman Raider"
                PUK = CFrame.new(-10322.400390625, 390.94473266602, -8580.0908203125)
                CFrameQuest = CFrame.new(-10581.6563, 330.872955, -8761.18652, -0.882952213, 0, 0.469463557, 0, 1, 0, -0.469463557, 0, -0.882952213)   
                 if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 1800 or MyLevel <= 1824 then
                Mon = "Fishman Captain [Lv. 1800]"
                LevelQuest = 2
                NameQuest = "DeepForestIsland3"
                NameMon = "Fishman Captain"
                PUK = CFrame.new(-11194.541992188, 442.02795410156, -8608.806640625)
                CFrameQuest = CFrame.new(-10581.6563, 330.872955, -8761.18652, -0.882952213, 0, 0.469463557, 0, 1, 0, -0.469463557, 0, -0.882952213)   
                 if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 1825 or MyLevel <= 1849 then
                Mon = "Forest Pirate [Lv. 1825]"
                LevelQuest = 1
                NameQuest = "DeepForestIsland"
                NameMon = "Forest Pirate"
                PUK = CFrame.new(-13225.809570313, 428.19387817383, -7753.1245117188)
                CFrameQuest = CFrame.new(-13234.04, 331.488495, -7625.40137, 0.707134247, -0, -0.707079291, 0, 1, -0, 0.707079291, 0, 0.707134247)
                 if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 1850 or MyLevel <= 1899 then
                Mon = "Mythological Pirate [Lv. 1850]"
                LevelQuest = 2
                NameQuest = "DeepForestIsland"
                NameMon = "Mythological Pirate"
                PUK = CFrame.new(-13869.172851563, 564.95251464844, -7084.4135742188)
                CFrameQuest = CFrame.new(-13234.04, 331.488495, -7625.40137, 0.707134247, -0, -0.707079291, 0, 1, -0, 0.707079291, 0, 0.707134247)   
                 if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 1900 or MyLevel <= 1924 then
                Mon = "Jungle Pirate [Lv. 1900]"
                LevelQuest = 1
                NameQuest = "DeepForestIsland2"
                NameMon = "Jungle Pirate"
                PUK = CFrame.new(-11982.221679688, 376.32522583008, -10451.415039063)
                CFrameQuest = CFrame.new(-12680.3818, 389.971039, -9902.01953, -0.0871315002, 0, 0.996196866, 0, 1, 0, -0.996196866, 0, -0.0871315002)
                 if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 1925 or MyLevel <= 1974 then
                Mon = "Musketeer Pirate [Lv. 1925]"
                LevelQuest = 2
                NameQuest = "DeepForestIsland2"
                NameMon = "Musketeer Pirate"
                PUK = CFrame.new(-13282.3046875, 496.23684692383, -9565.150390625)
                CFrameQuest = CFrame.new(-12680.3818, 389.971039, -9902.01953, -0.0871315002, 0, 0.996196866, 0, 1, 0, -0.996196866, 0, -0.0871315002)
                 if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 1975 or MyLevel <= 1999 then
                Mon = "Reborn Skeleton [Lv. 1975]"
                LevelQuest = 1
                NameQuest = "HauntedQuest1"
                NameMon = "Reborn Skeleton"
                PUK = CFrame.new(-8817.880859375, 191.16761779785, 6298.6557617188)
                CFrameQuest = CFrame.new(-9479.2168, 141.215088, 5566.09277, 0, 0, 1, 0, 1, -0, -1, 0, 0)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 2000 or MyLevel <= 2024 then
                Mon = "Living Zombie [Lv. 2000]"
                LevelQuest = 2
                NameQuest = "HauntedQuest1"
                NameMon = "Living Zombie"
                PUK = CFrame.new(-10125.234375, 183.94705200195, 6242.013671875)
                CFrameQuest = CFrame.new(-9479.2168, 141.215088, 5566.09277, 0, 0, 1, 0, 1, -0, -1, 0, 0)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 2025 or MyLevel <= 2049 then
                Mon = "Demonic Soul [Lv. 2025]"
                LevelQuest = 1
                NameQuest = "HauntedQuest2"
                NameMon = "Demonic Soul"
                PUK = CFrame.new(-9712.03125, 204.69589233398, 6193.322265625)
                CFrameQuest = CFrame.new(-9516.99316, 172.017181, 6078.46533, 0, 0, -1, 0, 1, 0, 1, 0, 0) 
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 2050 or MyLevel <= 2074 then
                Mon = "Posessed Mummy [Lv. 2050]"
                LevelQuest = 2
                NameQuest = "HauntedQuest2"
                NameMon = "Posessed Mummy"
                PUK = CFrame.new(-9545.7763671875, 69.619895935059, 6339.5615234375)
                CFrameQuest = CFrame.new(-9516.99316, 172.017181, 6078.46533, 0, 0, -1, 0, 1, 0, 1, 0, 0)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 2075 or MyLevel <= 2099 then
                Mon = "Peanut Scout [Lv. 2075]"
                LevelQuest = 1
                NameQuest = "NutsIslandQuest"
                NameMon = "Peanut Scout"
                PUK = CFrame.new(-2265.89014, 89.7506104, -10261.2197, -0.809553444, -9.26727282e-08, 0.587046146, -5.44419549e-08, 1, 8.27857534e-08, -0.587046146, 3.50595535e-08, -0.809553444)
                CFrameQuest = CFrame.new(-2104.3908691406, 38.104167938232, -10194.21875, 0, 0, -1, 0, 1, 0, 1, 0, 0)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 2100 or MyLevel <= 2124 then
                Mon = "Peanut President [Lv. 2100]"
                LevelQuest = 2
                NameQuest = "NutsIslandQuest"
                NameMon = "Peanut President"
                PUK = CFrame.new(-2062.11792, 86.0444489, -10481.1445, 0.834163189, -9.79785408e-09, -0.551517665, -2.60617616e-09, 1, -2.17070646e-08, 0.551517665, 1.95445864e-08, 0.834163189)
                CFrameQuest = CFrame.new(-2104.3908691406, 38.104167938232, -10194.21875, 0, 0, -1, 0, 1, 0, 1, 0, 0)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 2125 or MyLevel <= 2149 then
                Mon = "Ice Cream Chef [Lv. 2125]"
                LevelQuest = 1
                NameQuest = "IceCreamIslandQuest"
                NameMon = "Ice Cream Chef"
                PUK = CFrame.new(-875.441345, 107.871437, -11253.3691, 0.630182087, 5.98710486e-08, 0.776447415, -6.03229751e-08, 1, -2.81494827e-08, -0.776447415, -2.90983202e-08, 0.63018208)
                CFrameQuest = CFrame.new(-820.64825439453, 65.819526672363, -10965.795898438, 0, 0, -1, 0, 1, 0, 1, 0, 0)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 2150 or MyLevel <= 2199 then
                Mon = "Ice Cream Commander [Lv. 2150]"
                LevelQuest = 2
                NameQuest = "IceCreamIslandQuest"
                NameMon = "Ice Cream Commander"
                PUK = CFrame.new(-643.3078, 140.913528, -11334.7109, -0.996822715, -9.07818087e-09, 0.0796525627, -1.43212509e-08, 1, -6.52529906e-08, -0.0796525627, -6.61863808e-08, -0.996822715)
                CFrameQuest = CFrame.new(-820.64825439453, 65.819526672363, -10965.795898438, 0, 0, -1, 0, 1, 0, 1, 0, 0)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 2200 or MyLevel <= 2224 then
                Mon = "Cookie Crafter [Lv. 2200]"
                LevelQuest = 1
                NameQuest = "CakeQuest1"
                NameMon = "Cookie Crafter"
                PUK = CFrame.new(-2437.66064, 133.07428, -12122.8721, 0.215197399, 2.05706883e-08, -0.976570547, -6.6551344e-08, 1, 6.39893472e-09, 0.976570547, 6.36150475e-08, 0.215197399)
                CFrameQuest = CFrame.new(-2021.32007, 37.7982254, -12028.7295, 0.957576931, -8.80302053e-08, 0.288177818, 6.9301187e-08, 1, 7.51931211e-08, -0.288177818, -5.2032135e-08, 0.957576931)
            if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 2225 or MyLevel <= 2249 then
                Mon = "Cake Guard [Lv. 2225]"
                LevelQuest = 2
                NameQuest = "CakeQuest1"
                NameMon = "Cake Guard"
                PUK = CFrame.new(-1595.00916, 44.7149811, -12252.0547, -0.998557925, -6.0718726e-08, -0.0536852553, -5.64001539e-08, 1, -8.19574169e-08, 0.0536852553, -7.88113681e-08, -0.998557925)
                CFrameQuest = CFrame.new(-2021.32007, 37.7982254, -12028.7295, 0.957576931, -8.80302053e-08, 0.288177818, 6.9301187e-08, 1, 7.51931211e-08, -0.288177818, -5.2032135e-08, 0.957576931)
            if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 2250 or MyLevel <= 2274 then
                Mon = "Baking Staff [Lv. 2250]"
                LevelQuest = 1
                NameQuest = "CakeQuest2"
                NameMon = "Baking Staff"
                PUK = CFrame.new(-1817.20581, 93.8077316, -12885.6309, -0.696141601, 7.12665269e-08, 0.717904449, 4.05417566e-08, 1, -5.99574506e-08, -0.717904449, -1.26337669e-08, -0.696141601)
                CFrameQuest = CFrame.new(-1927.91602, 37.7981339, -12842.5391, -0.96804446, 4.22142143e-08, 0.250778586, 4.74911062e-08, 1, 1.49904711e-08, -0.250778586, 2.64211941e-08, -0.96804446)
            if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel == 2275 or MyLevel <=2299 then
                Mon = "Head Baker [Lv. 2275]"
                LevelQuest = 2
                NameQuest = "CakeQuest2"
                NameMon = "Head Baker"
                PUK = CFrame.new(-2263.37744, 156.999985, -12776, 0.945995748, 2.16281637e-09, 0.324179053, -1.23387056e-09, 1, -3.0710805e-09, -0.324179053, 2.50523402e-09, 0.945995748)
                CFrameQuest = CFrame.new(-1927.91602, 37.7981339, -12842.5391, -0.96804446, 4.22142143e-08, 0.250778586, 4.74911062e-08, 1, 1.49904711e-08, -0.250778586, 2.64211941e-08, -0.96804446)
         if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
         elseif MyLevel == 2300 or MyLevel <= 2324 then
               Mon = "Cocoa Warrior [Lv. 2300]"
               LevelQuest = 1
               NameQuest = "ChocQuest1"
               NameMon = "Cocoa Warrior"
               PUK = CFrame.new(-103.987442, 141.551514, -12260.2188, 0.589523733, -3.54913752e-08, -0.80775106, 4.28455316e-08, 1, -1.26684059e-08, 0.80775106, -2.71401959e-08, 0.589523733)
               CFrameQuest = CFrame.new(231.742981, 25.3354111, -12199.0537, 0.998278677, -5.16006757e-08, 0.0586484075, 4.79685092e-08, 1, 6.33390442e-08, -0.0586484075, -6.04167383e-08, 0.998278677)
             if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
             elseif MyLevel == 2325 or MyLevel <= 2349 then
               Mon = "Chocolate Bar Battler [Lv. 2325]"
               LevelQuest = 2
               NameQuest = "ChocQuest1"
               NameMon = "Chocolate Bar Battler"
               PUK = CFrame.new(617.304688, 80.6076355, -12580.6494, -0.485228658, 3.42073503e-09, -0.874387324, -4.0368306e-08, 1, 2.63139608e-08, 0.874387324, 4.80658215e-08, -0.485228658)
              CFrameQuest = CFrame.new(231.742981, 25.3354111, -12199.0537, 0.998278677, -5.16006757e-08, 0.0586484075, 4.79685092e-08, 1, 6.33390442e-08, -0.0586484075, -6.04167383e-08, 0.998278677)
              if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
              elseif MyLevel == 2350 or MyLevel <= 2374 then
               Mon = "Sweet Thief [Lv. 2350]"
               LevelQuest = 1
               NameQuest = "ChocQuest2"
               NameMon = "Sweet Thief"
               PUK = CFrame.new(72.062767, 77.630722, -12640.4287, -0.62450999, -9.80953416e-08, 0.781016827, 1.42118917e-09, 1, 1.26735927e-07, -0.781016827, 8.02578199e-08, -0.62450999)
               CFrameQuest = CFrame.new(149.867218, 24.8196201, -12775.5283, -0.0371122323, -7.14229245e-08, -0.99931109, -6.93553162e-08, 1, -6.88964548e-08, 0.99931109, 6.6750637e-08, -0.0371122323)
            if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
            elseif MyLevel >= 2375 then
               Mon = "Candy Rebel [Lv. 2375]"
               LevelQuest = 2
               NameQuest = "ChocQuest2"
               NameMon = "Candy Rebel"  
               PUK = CFrame.new(420.127747, 109.63044, -12989.6035, 0.0957952142, 3.10210027e-08, 0.995401084, -9.46955225e-09, 1, -3.02529948e-08, -0.995401084, -6.52791066e-09, 0.0957952142)
              CFrameQuest = CFrame.new(149.867218, 24.8196201, -12775.5283, -0.0371122323, -7.14229245e-08, -0.99931109, -6.93553162e-08, 1, -6.88964548e-08, 0.99931109, 6.6750637e-08, -0.0371122323)
          if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
                ByPass(CFrameQuest)
            end
          end
        end
    end
    
     
    
     function AutoHaki()
        if not game:GetService("Players").LocalPlayer.Character:FindFirstChild("HasBuso") then
            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Buso")
        end
    end
    
    function UnEquipWeapon(Weapon)
        if game.Players.LocalPlayer.Character:FindFirstChild(Weapon) then
            _G.NotAutoEquip = true
            wait(.5)
            game.Players.LocalPlayer.Character:FindFirstChild(Weapon).Parent = game.Players.LocalPlayer.Backpack
            wait(.1)
            _G.NotAutoEquip = false
        end
    end
    
    function EquipWeapon(ToolSe)
        if not _G.NotAutoEquip then
            if game.Players.LocalPlayer.Backpack:FindFirstChild(ToolSe) then
                Tool = game.Players.LocalPlayer.Backpack:FindFirstChild(ToolSe)
                wait(.1)
                game.Players.LocalPlayer.Character.Humanoid:EquipTool(Tool)
            end
        end
    end
    
    function topos(Pos)
        Distance = (Pos.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude
        if game.Players.LocalPlayer.Character.Humanoid.Sit == true then game.Players.LocalPlayer.Character.Humanoid.Sit = false end
        pcall(function() tween = game:GetService("TweenService"):Create(game.Players.LocalPlayer.Character.HumanoidRootPart,TweenInfo.new(Distance/210, Enum.EasingStyle.Linear),{CFrame = Pos}) end)
        tween:Play()
        if Distance <= 250 then
            tween:Cancel()
            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = Pos
        end
        if _G.StopTween == true then
            tween:Cancel()
            _G.Clip = false
        end
    end
    
    spawn(function()
        pcall(function()
            while wait() do
                if _G.AutoAdvanceDungeon or _G.Chest or _G.AutoSaw or _G.Sea1 or _G.Sea or _G.Magma or _G.Fish or _G.My or _G.God or _G.combo or _G.Auto_Bone2 or _G.AutoDoughtBoss or _G.Auto_DungeonMobAura or _G.AutoFarmChest or _G.AutoFarmBossHallow or _G.AutoFarmSwanGlasses or _G.AutoLongSword or _G.AutoBlackSpikeycoat or _G.AutoElectricClaw or _G.AutoFarmGunMastery or _G.AutoHolyTorch or _G.AutoLawRaid or _G.AutoFarmBoss or _G.AutoTwinHooks or _G.AutoOpenSwanDoor or _G.AutoDragon_Trident or _G.AutoSaber or _G.AutoFarmFruitMastery or _G.AutoFarmGunMastery or _G.TeleportIsland or _G.Auto_EvoRace or _G.AutoFarmAllMsBypassType or _G.AutoObservationv2 or _G.AutoMusketeerHat or _G.AutoEctoplasm or _G.AutoRengoku or _G.Auto_Rainbow_Haki or _G.AutoObservation or _G.AutoDarkDagger or _G.Safe_Mode or _G.MasteryFruit or _G.AutoBudySword or _G.AutoBounty or _G.AutoAllBoss or _G.Auto_Bounty or _G.AutoSharkman or _G.Auto_Mastery_Fruit or _G.Auto_Mastery_Gun or _G.Auto_Dungeon or _G.Auto_Cavender or _G.Auto_Pole or _G.Auto_Kill_Ply or _G.Auto_Factory or _G.AutoSecondSea or _G.TeleportPly or _G.AutoBartilo or _G.Auto_DarkBoss or _G.GrabChest or _G.AutoFarmBounty or _G.Holy_Torch or _G.AutoFarm or _G.Clip or FarmBoss or _G.AutoElitehunter or _G.AutoThirdSea or _G.Auto_Bone == true then
                    if not game:GetService("Players").LocalPlayer.Character.HumanoidRootPart:FindFirstChild("BodyClip") then
                        local Noclip = Instance.new("BodyVelocity")
                        Noclip.Name = "BodyClip"
                        Noclip.Parent = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart
                        Noclip.MaxForce = Vector3.new(100000,100000,100000)
                        Noclip.Velocity = Vector3.new(0,0,0)
                    end
                end
            end
        end)
    end)
    
    spawn(function()
        pcall(function()
            game:GetService("RunService").Stepped:Connect(function()
                if _G.AutoAdvanceDungeon or _G.Chest1 or _G.AutoSaw or _G.Chest or _G.Sea1 or _G.Sea or _G.Magma or _G.Fish or _G.My or _G.God or _G.combo or _G.Auto_Bone2 or _G.AutoDoughtBoss or _G.Auto_DungeonMobAura or _G.AutoFarmChest or _G.AutoFarmBossHallow or _G.AutoFarmSwanGlasses or _G.AutoLongSword or _G.AutoBlackSpikeycoat or _G.AutoElectricClaw or _G.AutoFarmGunMastery or _G.AutoHolyTorch or _G.AutoLawRaid or _G.AutoFarmBoss or _G.AutoTwinHooks or _G.AutoOpenSwanDoor or _G.AutoDragon_Trident or _G.AutoSaber or _G.NOCLIP or _G.AutoFarmFruitMastery or _G.AutoFarmGunMastery or _G.TeleportIsland or _G.Auto_EvoRace or _G.AutoFarmAllMsBypassType or _G.AutoObservationv2 or _G.AutoMusketeerHat or _G.AutoEctoplasm or _G.AutoRengoku or _G.Auto_Rainbow_Haki or _G.AutoObservation or _G.AutoDarkDagger or _G.Safe_Mode or _G.MasteryFruit or _G.AutoBudySword or _G.AutoBounty or _G.AutoAllBoss or _G.Auto_Bounty or _G.AutoSharkman or _G.Auto_Mastery_Fruit or _G.Auto_Mastery_Gun or _G.Auto_Dungeon or _G.Auto_Cavender or _G.Auto_Pole or _G.Auto_Kill_Ply or _G.Auto_Factory or _G.AutoSecondSea or _G.TeleportPly or _G.AutoBartilo or _G.Auto_DarkBoss or _G.GrabChest or _G.AutoFarmBounty or _G.Holy_Torch or _G.AutoFarm or _G.Clip or _G.AutoElitehunter or _G.AutoThirdSea or _G.Auto_Bone == true then
                    for _, v in pairs(game:GetService("Players").LocalPlayer.Character:GetDescendants()) do
                        if v:IsA("BasePart") then
                            v.CanCollide = false    
                        end
                    end
                end
            end)
        end)
    end)
    
    spawn(function()
        while wait() do
            if _G.AutoDoughtBoss or _G.Chest1 or _G.AutoSaw or _G.Chest or _G.Sea1 or _G.Sea or _G.Magma or _G.Fish or _G.My or _G.God or _G.combo or _G.Auto_Bone2 or _G.Auto_DungeonMobAura or _G.AutoFarmChest or _G.AutoFarmBossHallow or _G.AutoFarmSwanGlasses or _G.AutoLongSword or _G.AutoBlackSpikeycoat or _G.AutoElectricClaw or _G.AutoFarmGunMastery or _G.AutoHolyTorch or _G.AutoLawRaid or _G.AutoFarmBoss or _G.AutoTwinHooks or _G.AutoOpenSwanDoor or _G.AutoDragon_Trident or _G.AutoSaber or _G.NOCLIP or _G.AutoFarmFruitMastery or _G.AutoFarmGunMastery or _G.TeleportIsland or _G.Auto_EvoRace or _G.AutoFarmAllMsBypassType or _G.AutoObservationv2 or _G.AutoMusketeerHat or _G.AutoEctoplasm or _G.AutoRengoku or _G.Auto_Rainbow_Haki or _G.AutoObservation or _G.AutoDarkDagger or _G.Safe_Mode or _G.MasteryFruit or _G.AutoBudySword or _G.AutoAllBoss or _G.Auto_Bounty or _G.AutoSharkman or _G.Auto_Mastery_Fruit or _G.Auto_Mastery_Gun or _G.Auto_Dungeon or _G.Auto_Cavender or _G.Auto_Pole or _G.Auto_Kill_Ply or _G.Auto_Factory or _G.AutoSecondSea or _G.TeleportPly or _G.AutoBartilo or _G.Auto_DarkBoss or _G.AutoFarm or _G.Clip or _G.AutoElitehunter or _G.AutoThirdSea or _G.Auto_Bone == true then
                pcall(function()
                    game:GetService("ReplicatedStorage").Remotes.CommE:FireServer("Ken",true)
                end)
            end    
        end
    end)
    
    function StopTween(target)
        if not target then
            _G.StopTween = true
            wait()
            topos(game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame)
            wait()
            if game:GetService("Players").LocalPlayer.Character.HumanoidRootPart:FindFirstChild("BodyClip") then
                game:GetService("Players").LocalPlayer.Character.HumanoidRootPart:FindFirstChild("BodyClip"):Destroy()
            end
            _G.StopTween = false
            _G.Clip = false
        end
    end
    
    spawn(function()
        pcall(function()
            while wait() do
                for i,v in pairs(game:GetService("Players").LocalPlayer.Backpack:GetChildren()) do  
                    if v:IsA("Tool") then
                        if v:FindFirstChild("RemoteFunctionShoot") then 
                            SelectWeaponGun = v.Name
                        end
                    end
                end
            end
        end)
    end)
    
     WeaponList = {}
    
    for i,v in pairs(game:GetService("Players").LocalPlayer.Backpack:GetChildren()) do  
        if v:IsA("Tool") then
            table.insert(WeaponList ,v.Name)
        end
    end
    
    local SelectWeapona = A:AddDropdown("Select Weapon",WeaponList,function(value)
        _G.SelectWeapon = value
    end)
    
    A:AddButton("Refresh Weapon",function()
        SelectWeapona:Clear()
        for i,v in pairs(game:GetService("Players").LocalPlayer.Backpack:GetChildren()) do  
            SelectWeapona:Add(v.Name)
        end
    end)

local AutoFarm = A:AddToggle("Auto Farm Level",true,function(value)
        _G.AutoFarm = value
        StopTween(_G.AutoFarm)
    end)

spawn(function()
        while wait() do
            if _G.AutoFarm then
                pcall(function()
                    local QuestTitle = game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text
                    if not string.find(QuestTitle, NameMon) then
                        StartMagnet = false
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
                    end
                    if game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false then
                        StartMagnet = false
                        CheckQuest()
                        repeat wait() topos(CFrameQuest) until (CFrameQuest.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 3 or not _G.AutoFarm
                        if (CFrameQuest.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 3 then
                            wait(1.2)
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StartQuest",NameQuest,LevelQuest)
                            wait(0.5)
                        end
                    elseif game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == true then
                        CheckQuest()
                        if game:GetService("Workspace").Enemies:FindFirstChild(Mon) then
                            for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                                if v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
                                    if v.Name == Mon then
                                        if string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, NameMon) then
                                            repeat task.wait()
                                                EquipWeapon(_G.SelectWeapon)
                                                AutoHaki()                                            
                                                PosMon = v.HumanoidRootPart.CFrame
                                                topos(v.HumanoidRootPart.CFrame * CFrame.new(0,45,0))
                                                v.HumanoidRootPart.CanCollide = false
                                                v.Humanoid.WalkSpeed = 0
                                                v.Head.CanCollide = false
                                                v.HumanoidRootPart.Size = Vector3.new(50,50,50)
                                                StartMagnet = true
                                                game:GetService'VirtualUser':CaptureController()
                                                game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
                                            until not _G.AutoFarm or v.Humanoid.Health <= 0 or not v.Parent or game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false
                                        else
                                            StartMagnet = false
                                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
                                        end
                                    end
                                end
                            end
                        else
                            StartMagnet = false
                            if game:GetService("ReplicatedStorage"):FindFirstChild(Mon) then
                                topos(game:GetService("ReplicatedStorage"):FindFirstChild(Mon).HumanoidRootPart.CFrame * CFrame.new(0,45,0))
                            else
                                if (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 200 then
                                    if PUK ~= nil then
                                        topos(PUK * CFrame.new(0,0,0))
                                    else
                                        if OldPos ~= nil then
                                            topos(OldPos.Position)
                                            end 
                                            end 
                                            else 
                                              StartMagnet = false 
                                              topos(PUK)
                                            end 
                                            end
                                            end
                                            end
                                            end)
                                            end
                                            end
                                            end)
           A:AddLine()
           
 statsfarm = A:AddLabel("AutoFarm : ❌")          
           
           spawn(function()
        pcall(function()
            while wait() do
            if _G.AutoFarm == false then
             statsfarm:Refresh("AutoFarm : ❌")
             elseif _G.AutoFarm == true then
             statsfarm:Set("AutoFarm : ✅")
              end
              end
              end)
              end)
           
                        QuestStatus = A:AddLabel("")

spawn(function()
    while wait() do
        CheckQuest(NameQuest)
        QuestStatus:Set("Quest : "..NameQuest)
end
end)

 Questlv = A:AddLabel("")

spawn(function()
    while wait() do
        CheckQuest(LevelQuest)
        Questlv:Set("LevelQuest : "..LevelQuest)
end
end)

 NamemonStatus = A:AddLabel("")

spawn(function()
    while wait() do
        CheckQuest(Mon)
        NamemonStatus:Set("Mon & Level Mon : "..Mon)
end
end)

    spawn(function()
        pcall(function()
            while wait() do
                if _G.AutoFarm then
                    if game:GetService("Players").LocalPlayer.Character.Humanoid.Health > 0 then
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
                    end
                end
            end
        end)
    end)
    
    spawn(function()
      while wait() do
      if _G.WhiteScreen then
        for i, v in pairs(game.Workspace["_WorldOrigin"]:GetChildren()) do
            if v.Name == "CurvedRing" or v.Name == "SlashHit" or v.Name == "DamageCounter" or v.Name == "SwordSlash" or v.Name == "SlashTail" or v.Name == "Sounds" then
                v:Destroy() 
            end
        end
    end
    end
end) 
    
        S:AddToggle("White Screen [ Booster FPS ]",_G.WhiteScreen,function(value)
    _G.WhiteScreen = value
if _G.WhiteScreen == true then
    game:GetService("RunService"):Set3dRenderingEnabled(false)
elseif _G.WhiteScreen == false then
    game:GetService("RunService"):Set3dRenderingEnabled(true)
end
end)
    
    
    local CameraShaker = require(game.ReplicatedStorage.Util.CameraShaker)
CombatFrameworkR = require(game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework)
y = debug.getupvalues(CombatFrameworkR)[2]
spawn(function()
    game:GetService("RunService").RenderStepped:Connect(function()
        if _G.AutoFarm then
            if typeof(y) == "table" then
                pcall(function()
                    CameraShaker:Stop()
                    y.activeController.timeToNextAttack = (math.huge^math.huge^math.huge)
                    y.activeController.timeToNextAttack = 0
                    y.activeController.hitboxMagnitude = 9999
                    y.activeController.active = false
                    y.activeController.timeToNextBlock = 0
                    y.activeController.focusStart = 0
                    y.activeController.increment = 1
                    y.activeController.blocking = false
                    y.activeController.attacking = false
                    y.activeController.humanoid.AutoRotate = true
                end)
            end
        end
    end)
end)
    
    spawn(function()
    while true do wait()
       rejoin = game:GetService("CoreGui").RobloxPromptGui.promptOverlay.ChildAdded:Connect(function(Kick)
            if not _G.AutoFarm then
                if Kick.Name == 'ErrorPrompt' and Kick:FindFirstChild('MessageArea') and Kick.MessageArea:FindFirstChild("ErrorFrame") then
                    game:GetService("TeleportService"):Teleport(game.PlaceId)
                    wait(50)
                end
            end
        end)
    end
end)  

 task.spawn(function()
        while task.wait() do
            pcall(function()
                if _G.AutoFarm then
                    CheckQuest()
                    for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                        if _G.AutoFarm and StartMagnet and v.Name == Mon and (Mon == "Factory Staff [Lv. 800]" or Mon == "Monkey [Lv. 14]" or Mon == "Dragon Crew Warrior [Lv. 1575]" or Mon == "Dragon Crew Archer [Lv. 1600]") and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 and (v.HumanoidRootPart.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 220 then
                            v.HumanoidRootPart.Size = Vector3.new(50,50,50)
                            v.HumanoidRootPart.CFrame = PosMon
                            v.Humanoid:ChangeState(1)
                            v.HumanoidRootPart.CanCollide = false
                            v.Head.CanCollide = false
                            if v.Humanoid:FindFirstChild("Animator") then
                                v.Humanoid.Animator:Destroy()
                            end
                            sethiddenproperty(game:GetService("Players").LocalPlayer,"SimulationRadius",math.huge)
                        elseif _G.AutoFarm and StartMagnet and v.Name == Mon and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 and (v.HumanoidRootPart.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 275 then
                            v.HumanoidRootPart.Size = Vector3.new(50,50,50)
                            v.HumanoidRootPart.CFrame = PosMon
                            v.Humanoid:ChangeState(1)
                            v.HumanoidRootPart.CanCollide = false
                            v.Head.CanCollide = false
                            if v.Humanoid:FindFirstChild("Animator") then
                                v.Humanoid.Animator:Destroy()
                            end
                            sethiddenproperty(game:GetService("Players").LocalPlayer,"SimulationRadius",math.huge)
                        end
                        if _G.AutoEctoplasm and StartEctoplasmMagnet then
                            if string.find(v.Name, "Ship") and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 and (v.HumanoidRootPart.Position - EctoplasmMon.Position).Magnitude <= 250 then
                                v.HumanoidRootPart.Size = Vector3.new(50,50,50)
                                v.HumanoidRootPart.CFrame = EctoplasmMon
                                v.Humanoid:ChangeState(14)
                                v.HumanoidRootPart.CanCollide = false
                                v.Head.CanCollide = false
                                if v.Humanoid:FindFirstChild("Animator") then
                                    v.Humanoid.Animator:Destroy()
                                end
                                sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                            end
                        end
                        if _G.AutoRengoku and StartRengokuMagnet then
                            if (v.Name == "Snow Lurker [Lv. 1375]" or v.Name == "Arctic Warrior [Lv. 1350]") and (v.HumanoidRootPart.Position - RengokuMon.Position).Magnitude <= 250 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                v.HumanoidRootPart.Size = Vector3.new(50,50,50)
                                v.Humanoid:ChangeState(14)
                                v.HumanoidRootPart.CanCollide = false
                                v.Head.CanCollide = false
                                v.HumanoidRootPart.CFrame = RengokuMon
                                if v.Humanoid:FindFirstChild("Animator") then
                                    v.Humanoid.Animator:Destroy()
                                end
                                sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                            end
                        end
                        if _G.AutoMusketeerHat and StartMagnetMusketeerhat then
                            if v.Name == "Forest Pirate [Lv. 1825]" and (v.HumanoidRootPart.Position - MusketeerHatMon.Position).Magnitude <= 250 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                v.HumanoidRootPart.Size = Vector3.new(50,50,50)
                                v.Humanoid:ChangeState(14)
                                v.HumanoidRootPart.CanCollide = false
                                v.Head.CanCollide = false
                                v.HumanoidRootPart.CFrame = MusketeerHatMon
                                if v.Humanoid:FindFirstChild("Animator") then
                                    v.Humanoid.Animator:Destroy()
                                end
                                sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                            end
                        end
                        if _G.Auto_EvoRace and StartEvoMagnet then
                            if v.Name == "Zombie [Lv. 950]" and (v.HumanoidRootPart.Position - PosMonEvo.Position).Magnitude <= 250 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                v.HumanoidRootPart.Size = Vector3.new(50,50,50)
                                v.Humanoid:ChangeState(14)
                                v.HumanoidRootPart.CanCollide = false
                                v.Head.CanCollide = false
                                v.HumanoidRootPart.CFrame = PosMonEvo
                                if v.Humanoid:FindFirstChild("Animator") then
                                    v.Humanoid.Animator:Destroy()
                                end
                                sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                            end
                        end
                        if _G.AutoBartilo and AutoBartiloBring then
                            if v.Name == "Swan Pirate [Lv. 775]" and (v.HumanoidRootPart.Position - PosMonBarto.Position).Magnitude <= 250 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                v.HumanoidRootPart.Size = Vector3.new(50,50,50)
                                v.Humanoid:ChangeState(14)
                                v.HumanoidRootPart.CanCollide = false
                                v.Head.CanCollide = false
                                v.HumanoidRootPart.CFrame = PosMonBarto
                                if v.Humanoid:FindFirstChild("Animator") then
                                    v.Humanoid.Animator:Destroy()
                                end
                                sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                            end
                        end
                        if _G.AutoFarmFruitMastery and StartMasteryFruitMagnet then
                            if v.Name == "Monkey [Lv. 14]" then
                                if (v.HumanoidRootPart.Position - PosMonMasteryFruit.Position).Magnitude <= 250 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                    v.HumanoidRootPart.Size = Vector3.new(50,50,50)
                                    v.Humanoid:ChangeState(14)
                                    v.HumanoidRootPart.CanCollide = false
                                    v.Head.CanCollide = false
                                    v.HumanoidRootPart.CFrame = PosMonMasteryFruit
                                    if v.Humanoid:FindFirstChild("Animator") then
                                        v.Humanoid.Animator:Destroy()
                                    end
                                    sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                                end
                            elseif v.Name == "Factory Staff [Lv. 800]" then
                                if (v.HumanoidRootPart.Position - PosMonMasteryFruit.Position).Magnitude <= 250 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                    v.HumanoidRootPart.Size = Vector3.new(50,50,50)
                                    v.Humanoid:ChangeState(14)
                                    v.HumanoidRootPart.CanCollide = false
                                    v.Head.CanCollide = false
                                    v.HumanoidRootPart.CFrame = PosMonMasteryFruit
                                    if v.Humanoid:FindFirstChild("Animator") then
                                        v.Humanoid.Animator:Destroy()
                                    end
                                    sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                                end
                            elseif v.Name == Mon then
                                if (v.HumanoidRootPart.Position - PosMonMasteryFruit.Position).Magnitude <= 250 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                    v.HumanoidRootPart.Size = Vector3.new(50,50,50)
                                    v.Humanoid:ChangeState(14)
                                    v.HumanoidRootPart.CanCollide = false
                                    v.Head.CanCollide = false
                                    v.HumanoidRootPart.CFrame = PosMonMasteryFruit
                                    if v.Humanoid:FindFirstChild("Animator") then
                                        v.Humanoid.Animator:Destroy()
                                    end
                                    sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                                end
                            end
                        end
                        if _G.AutoFarmGunMastery and StartMasteryGunMagnet then
                            if v.Name == "Monkey [Lv. 14]" then
                                if (v.HumanoidRootPart.Position - PosMonMasteryGun.Position).Magnitude <= 250 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                    v.HumanoidRootPart.Size = Vector3.new(50,50,50)
                                    v.Humanoid:ChangeState(14)
                                    v.HumanoidRootPart.CanCollide = false
                                    v.Head.CanCollide = false
                                    v.HumanoidRootPart.CFrame = PosMonMasteryGun
                                    if v.Humanoid:FindFirstChild("Animator") then
                                        v.Humanoid.Animator:Destroy()
                                    end
                                    sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                                end
                            elseif v.Name == "Factory Staff [Lv. 800]" then
                                if (v.HumanoidRootPart.Position - PosMonMasteryGun.Position).Magnitude <= 250 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                    v.HumanoidRootPart.Size = Vector3.new(50,50,50)
                                    v.Humanoid:ChangeState(14)
                                    v.HumanoidRootPart.CanCollide = false
                                    v.Head.CanCollide = false
                                    v.HumanoidRootPart.CFrame = PosMonMasteryGun
                                    if v.Humanoid:FindFirstChild("Animator") then
                                        v.Humanoid.Animator:Destroy()
                                    end
                                    sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                                end
                            elseif v.Name == Mon then
                                if (v.HumanoidRootPart.Position - PosMonMasteryGun.Position).Magnitude <= 250 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                    v.HumanoidRootPart.Size = Vector3.new(50,50,50)
                                    v.Humanoid:ChangeState(14)
                                    v.HumanoidRootPart.CanCollide = false
                                    v.Head.CanCollide = false
                                    v.HumanoidRootPart.CFrame = PosMonMasteryGun
                                    if v.Humanoid:FindFirstChild("Animator") then
                                        v.Humanoid.Animator:Destroy()
                                    end
                                    sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                                end
                            end
                        end
                        if _G.Auto_Bone and StartMagnetBoneMon then
                            if (v.Name == "Reborn Skeleton [Lv. 1975]" or v.Name == "Living Zombie [Lv. 2000]" or v.Name == "Demonic Soul [Lv. 2025]" or v.Name == "Posessed Mummy [Lv. 2050]") and (v.HumanoidRootPart.Position - PosMonBone.Position).Magnitude <= 250 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                v.HumanoidRootPart.Size = Vector3.new(50,50,50)
                                v.Humanoid:ChangeState(14)
                                v.HumanoidRootPart.CanCollide = false
                                v.Head.CanCollide = false
                                v.HumanoidRootPart.CFrame = PosMonBone
                                if v.Humanoid:FindFirstChild("Animator") then
                                    v.Humanoid.Animator:Destroy()
                                end
                                sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                            end
                        end
                        if _G.Auto_Bone2 and StartMagnetBoneMon2 then
                            if (v.HumanoidRootPart.Position - PosMonBone2.Position).Magnitude <= 250 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                v.HumanoidRootPart.Size = Vector3.new(50,50,50)
                                v.Humanoid:ChangeState(1)
                                v.HumanoidRootPart.CanCollide = false
                                v.Head.CanCollide = false
                                v.HumanoidRootPart.CFrame = PosMonBone2
                                if v.Humanoid:FindFirstChild("Animator") then
                                    v.Humanoid.Animator:Destroy()
                                end
                                sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                            end
                        end
                        if _G.AutoDoughtBoss and MagnetDought then
                            if (v.HumanoidRootPart.Position - PosMonDoughtOpenDoor.Position).Magnitude <= 250 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                v.HumanoidRootPart.Size = Vector3.new(50,50,50)
                                v.Humanoid:ChangeState(1)
                                v.HumanoidRootPart.CanCollide = false
                                v.Head.CanCollide = false
                                v.HumanoidRootPart.CFrame = PosMonDoughtOpenDoor
                                if v.Humanoid:FindFirstChild("Animator") then
                                    v.Humanoid.Animator:Destroy()
                                end
                                sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                            end
                        end
                        if _G.God and StartMagnetdragon then
                            if (v.HumanoidRootPart.Position - PosMondragon.Position).Magnitude <= 250 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                v.HumanoidRootPart.Size = Vector3.new(50,50,50)
                                v.Humanoid:ChangeState(14)
                                v.HumanoidRootPart.CanCollide = false
                                v.Head.CanCollide = false
                                v.HumanoidRootPart.CFrame = PosMondragon
                                if v.Humanoid:FindFirstChild("Animator") then
                                    v.Humanoid.Animator:Destroy()
                                end
                                sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                            end
                        end
                        if _G.My and StartMagnetMy then
                            if (v.HumanoidRootPart.Position - PosMonMy.Position).Magnitude <= 250 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                v.HumanoidRootPart.Size = Vector3.new(50,50,50)
                                v.Humanoid:ChangeState(1)
                                v.HumanoidRootPart.CanCollide = false
                                v.Head.CanCollide = false
                                v.HumanoidRootPart.CFrame = PosMonMy
                                if v.Humanoid:FindFirstChild("Animator") then
                                    v.Humanoid.Animator:Destroy()
                                end
                                sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                            end
                        end
                        if _G.Fish and StartMagnetFish then
                            if (v.HumanoidRootPart.Position - PosMonFish.Position).Magnitude <= 250 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                v.HumanoidRootPart.Size = Vector3.new(50,50,50)
                                v.Humanoid:ChangeState(1)
                                v.HumanoidRootPart.CanCollide = false
                                v.Head.CanCollide = false
                                v.HumanoidRootPart.CFrame = PosMonFish
                                if v.Humanoid:FindFirstChild("Animator") then
                                    v.Humanoid.Animator:Destroy()
                                end
                                sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                            end
                        end
                         if _G.Magma and StartMagnetMagma then
                            if (v.HumanoidRootPart.Position - PosMonMagma.Position).Magnitude <= 250 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                v.HumanoidRootPart.Size = Vector3.new(50,50,50)
                                v.Humanoid:ChangeState(1)
                                v.HumanoidRootPart.CanCollide = false
                                v.Head.CanCollide = false
                                v.HumanoidRootPart.CFrame = PosMonMagma
                                if v.Humanoid:FindFirstChild("Animator") then
                                    v.Humanoid.Animator:Destroy()
                                end
                                sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                            end
                        end
                        if _G.AutoCandy and StartMagnetCandy then
                            if (v.HumanoidRootPart.Position - PosMonCandy.Position).Magnitude <= 250 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                v.HumanoidRootPart.Size = Vector3.new(50,50,50)
                                v.Humanoid:ChangeState(14)
                                v.HumanoidRootPart.CanCollide = false
                                v.Head.CanCollide = false
                                v.HumanoidRootPart.CFrame = PosMonCandy
                                if v.Humanoid:FindFirstChild("Animator") then
                                    v.Humanoid.Animator:Destroy()
                                end
                                sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                            end
                        end
                    end
                end
            end)
        end
    end)

task.spawn(function()
        while wait() do
            pcall(function()
                if _G.AutoFarm then
                    if World1 then
                       game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AddPoint","Melee",_G.PointStats)
                    elseif World2 then
                       game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AddPoint","Melee",_G.PointStats)
                       game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AddPoint","Defense",_G.PointStats)
                    end
                end
            end)
        end
    end)
    
    spawn(function()
        pcall(function()
            while wait() do 
                if _G.AutoFarm then
                    if game.Players.LocalPlayer.Backpack:FindFirstChild("Combat") or game.Players.LocalPlayer.Character:FindFirstChild("Combat") and game:GetService("Players")["LocalPlayer"].Data.Beli.Value >= 150000 then
                      _G.SelectWeapon = "Combat"
                      wait(.1)
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyBlackLeg")
                    end   
                    if game.Players.LocalPlayer.Character:FindFirstChild("Superhuman") or game.Players.LocalPlayer.Backpack:FindFirstChild("Superhuman") then
                        _G.SelectWeapon = "Superhuman"
                    end  
                    if game.Players.LocalPlayer.Backpack:FindFirstChild("Black Leg") or game.Players.LocalPlayer.Character:FindFirstChild("Black Leg") or game.Players.LocalPlayer.Backpack:FindFirstChild("Electro") or game.Players.LocalPlayer.Character:FindFirstChild("Electro") or game.Players.LocalPlayer.Backpack:FindFirstChild("Fishman Karate") or game.Players.LocalPlayer.Character:FindFirstChild("Fishman Karate") or game.Players.LocalPlayer.Backpack:FindFirstChild("Dragon Claw") or game.Players.LocalPlayer.Character:FindFirstChild("Dragon Claw") then
                        if game.Players.LocalPlayer.Backpack:FindFirstChild("Black Leg") and game.Players.LocalPlayer.Backpack:FindFirstChild("Black Leg").Level.Value <= 299 then
                            _G.SelectWeapon = "Black Leg"
                        end
                        if game.Players.LocalPlayer.Backpack:FindFirstChild("Electro") and game.Players.LocalPlayer.Backpack:FindFirstChild("Electro").Level.Value <= 299 then
                            _G.SelectWeapon = "Electro"
                        end
                        if game.Players.LocalPlayer.Backpack:FindFirstChild("Fishman Karate") and game.Players.LocalPlayer.Backpack:FindFirstChild("Fishman Karate").Level.Value <= 299 then
                            _G.SelectWeapon = "Fishman Karate"
                        end
                        if game.Players.LocalPlayer.Backpack:FindFirstChild("Dragon Claw") and game.Players.LocalPlayer.Backpack:FindFirstChild("Dragon Claw").Level.Value <= 299 then
                            _G.SelectWeapon = "Dragon Claw"
                        end
                        if game.Players.LocalPlayer.Backpack:FindFirstChild("Black Leg") and game.Players.LocalPlayer.Backpack:FindFirstChild("Black Leg").Level.Value >= 300 and game:GetService("Players")["LocalPlayer"].Data.Beli.Value >= 300000 then
                            UnEquipWeapon("Black Leg")
                            wait(.1)
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyElectro")
                        end
                        if game.Players.LocalPlayer.Character:FindFirstChild("Black Leg") and game.Players.LocalPlayer.Character:FindFirstChild("Black Leg").Level.Value >= 300 and game:GetService("Players")["LocalPlayer"].Data.Beli.Value >= 300000 then
                            UnEquipWeapon("Black Leg")
                            wait(.1)
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyElectro")
                        end
                        if game.Players.LocalPlayer.Backpack:FindFirstChild("Electro") and game.Players.LocalPlayer.Backpack:FindFirstChild("Electro").Level.Value >= 300 and game:GetService("Players")["LocalPlayer"].Data.Beli.Value >= 750000 then
                            UnEquipWeapon("Electro")
                            wait(.1)
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyFishmanKarate")
                        end
                        if game.Players.LocalPlayer.Character:FindFirstChild("Electro") and game.Players.LocalPlayer.Character:FindFirstChild("Electro").Level.Value >= 300 and game:GetService("Players")["LocalPlayer"].Data.Beli.Value >= 750000 then
                            UnEquipWeapon("Electro")
                            wait(.1)
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyFishmanKarate")
                        end
                        if game.Players.LocalPlayer.Backpack:FindFirstChild("Fishman Karate") and game.Players.LocalPlayer.Backpack:FindFirstChild("Fishman Karate").Level.Value >= 300 and game:GetService("Players")["Localplayer"].Data.Fragments.Value >= 1500 then
                            UnEquipWeapon("Fishman Karate")
                            wait(.1)
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BlackbeardReward","DragonClaw","1")
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BlackbeardReward","DragonClaw","2") 
                        end
                        if game.Players.LocalPlayer.Character:FindFirstChild("Fishman Karate") and game.Players.LocalPlayer.Character:FindFirstChild("Fishman Karate").Level.Value >= 300 and game:GetService("Players")["Localplayer"].Data.Fragments.Value >= 1500 then
                            UnEquipWeapon("Fishman Karate")
                            wait(.1)
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BlackbeardReward","DragonClaw","1")
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BlackbeardReward","DragonClaw","2") 
                        end
                        if game.Players.LocalPlayer.Backpack:FindFirstChild("Dragon Claw") and game.Players.LocalPlayer.Backpack:FindFirstChild("Dragon Claw").Level.Value >= 300 and game:GetService("Players")["LocalPlayer"].Data.Beli.Value >= 3000000 then
                            UnEquipWeapon("Dragon Claw")
                            wait(.1)
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySuperhuman")
                        end
                        if game.Players.LocalPlayer.Character:FindFirstChild("Dragon Claw") and game.Players.LocalPlayer.Character:FindFirstChild("Dragon Claw").Level.Value >= 300 and game:GetService("Players")["LocalPlayer"].Data.Beli.Value >= 3000000 then
                            UnEquipWeapon("Dragon Claw")
                            wait(.1)
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySuperhuman")
                        end 
                    end
                end
            end
        end)
    end)
    
    S:AddLine()
    
  PlayerName = S:AddLabel("")
  
  spawn(
    function()
        pcall(
            function()
                while wait() do
                    PlayerName:Set("PlayerName : " .. game.Players.localPlayer.Name)
                end
            end
        )
    end
)
    
    local locallv = S:AddLabel("Level")
    
   
    spawn(function()
        while wait() do
            pcall(function()
                locallv:Set("Level :".." "..game:GetService("Players").LocalPlayer.Data.Level.Value)
            end)
        end
    end)
    
    local localrace = S:AddLabel("Race")
    
    spawn(function()
        while wait() do
            pcall(function()
                localrace:Set("Race :".." "..game:GetService("Players").LocalPlayer.Data.Race.Value)
            end)
        end
    end)
    
    local localbeli = S:AddLabel("Beli")
    
    spawn(function()
        while wait() do
            pcall(function()
                localbeli:Set("Beli :".." "..game:GetService("Players").LocalPlayer.Data.Beli.Value)
            end)
        end
    end)
    
    local localfrag = S:AddLabel("Fragment")
    
    spawn(function()
        while wait() do
            pcall(function()
                localfrag:Set("Fragments :".." "..game:GetService("Players").LocalPlayer.Data.Fragments.Value)
            end)
        end
    end)
    
    
    local localexp = S:AddLabel("ExP")
    
    spawn(function()
        while wait() do
            pcall(function()
                localexp:Set("ExP Points :".." "..game:GetService("Players").LocalPlayer.Data.Exp.Value)
            end)
        end
    end)
    
    local localstat = S:AddLabel("Stats Points")
    
    spawn(function()
        while wait() do
            pcall(function()
                localstat:Set("Stats Points :".." "..game:GetService("Players").LocalPlayer.Data.Points.Value)
            end)
        end
    end)
    
    local localbountyhornor = S:AddLabel("Bounty")
    
    spawn(function()
        while wait() do
            pcall(function()
                localbountyhornor:Set("Bounty / Honor :".." "..game:GetService("Players").LocalPlayer.leaderstats["Bounty/Honor"].Value)
            end)
        end
    end)
    
    local localDevil = S:AddLabel("Devil Fruit")
    
    spawn(function()
        while wait() do
            pcall(function()
                if game:GetService("Players").LocalPlayer.Character:FindFirstChild(game:GetService("Players").LocalPlayer.Data.DevilFruit.Value) or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild(game:GetService("Players").LocalPlayer.Data.DevilFruit.Value) then
                    localDevil:Set("Devil Fruit :".." "..game:GetService("Players").LocalPlayer.Data.DevilFruit.Value)
                else
                    localDevil:Set("Not Have Devil Fruit")
                end
            end)
        end
    end)
    
    Health = S:AddLabel("")
    
    task.spawn(
    function()
        pcall(
            function()
                while wait() do
                    Health:Set("Health : " .. game.Players.LocalPlayer.Character.Humanoid.Health)
                end
            end
        )
    end
)
Energy = S:AddLabel("")
task.spawn(
    function()
        pcall(
            function()
                while wait() do
                    Energy:Set("Stamina : " .. game.Players.LocalPlayer.Character.Energy.Value)
                end
            end
        )
    end
)
    
S:AddLine(eee)
S:AddLabel("Wolrd")
WolrdSet3 = S:AddLabel("Wolrd : 1 ❌")
WolrdSet = S:AddLabel("Wolrd : 2 ❌")
WolrdSet1 = S:AddLabel("Wolrd : 3 ❌")

S:AddLine()
S:AddLabel("Mellee")
Superhuman = S:AddLabel("❌ : Superhuman")
DeathStep = S:AddLabel("❌ : Death Step")
SharkmanKarate = S:AddLabel("❌ : Sharkman Karate")
ElectricClaw = S:AddLabel("❌ : Electric Claw")
DragonTalon = S:AddLabel("❌ : Dragon Talon")
GodHuman = S:AddLabel("❌ : God Human")
S:AddLine()
S:AddLabel("Legendary Sword")
Shisui = S:AddLabel("❌ : Shisui")
Saddi = S:AddLabel("❌ : Saddi")
Wando = S:AddLabel("❌ : Wando")
TrueTripleKatana = S:AddLabel("❌ : True Triple Katana")

S:AddLine()
S:AddLabel("Sword")
Saber = S:AddLabel("❌ : Saber")
Rengoku = S:AddLabel("❌ : Rengoku")
MidnightBlade = S:AddLabel("❌ : Midnight Blade")
DragonTrident = S:AddLabel("❌ : DragonTrident")
Yama = S:AddLabel("❌ : Yama")
BuddySword = S:AddLabel("❌ : Buddy Sword")
Canvander = S:AddLabel("❌ : Canvander")
TwinHooks = S:AddLabel("❌ : Twin Hooks")
SpikeyTrident = S:AddLabel("❌ : Spikey Trident")
HallowScythe = S:AddLabel("❌ : Hallow Scythe")
DarkDagger = S:AddLabel("❌ : Dark Dagger")
Tushita = S:AddLabel("❌ : Tushita")
S:AddLine()
S:AddLabel("Gun")
Kabucha = S:AddLabel("❌ : Kabucha")
AcidumRifle = S:AddLabel("❌ : Acidum Rifle")
BizarreRifle = S:AddLabel("❌ : Bizarre Rifle")
S:AddLine()
S:AddLabel("Quest")
BartiloQuest = S:AddLabel("❌ : Bartilo Quest")
DonSwanQuest = S:AddLabel("❌ : Don Swan Quest")
KillDonSwan = S:AddLabel("❌ : Kill Don Swan")
    
    task.spawn(
    function()
        while task.wait() do
            if game.Players.LocalPlayer.Team == nil then
                pcall(
                    function()
                        if _G.Team == "Pirate" then
                            game:GetService("Players").LocalPlayer.PlayerGui.Main.ChooseTeam.Container.Pirates.Frame.ViewportFrame.TextButton.Size =
                                UDim2.new(10000, 1000, 10000, 1000)
                            game:GetService("Players").LocalPlayer.PlayerGui.Main.ChooseTeam.Container.Pirates.Frame.ViewportFrame.TextButton.Position =
                                UDim2.new(-4, 0, -5, 0)
                            wait(.5)
                            game:GetService("VirtualInputManager"):SendMouseButtonEvent(
                                605,
                                394,
                                0,
                                true,
                                game:GetService("Players").LocalPlayer.PlayerGui.Main.ChooseTeam.Container.Pirates.Frame.ViewportFrame.TextButton,
                                0
                            )
                            game:GetService("VirtualInputManager"):SendMouseButtonEvent(
                                605,
                                394,
                                0,
                                false,
                                game:GetService("Players").LocalPlayer.PlayerGui.Main.ChooseTeam.Container.Pirates.Frame.ViewportFrame.TextButton,
                                0
                            )
                        end
                    end
                )
            end
        end
    end
)

 spawn(function()
        pcall(function()
            while wait(.1) do
                if _G.AutoFarm then
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Cousin","Buy")
                end 
            end
        end)
    end)
    
    spawn(function()
        while wait() do
            if _G.AutoFarm or World2 then
                pcall(function()
                    local args = {
                        [1] = "LegendarySwordDealer",
                        [2] = "1"
                    }
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                    local args = {
                        [1] = "LegendarySwordDealer",
                        [2] = "2"
                    }
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                    local args = {
                        [1] = "LegendarySwordDealer",
                        [2] = "3"
                    }
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                    if _G.AutoBuyLegendarySword_Hop and _G.AutoBuyLegendarySword and World2 then
                        wait(10)
                        Hop()
                    end
                end)
            end 
        end
    end)

FruitList = {
        "Bomb-Bomb",
        "Spike-Spike",
        "Chop-Chop",
        "Spring-Spring",
        "Kilo-Kilo",
        "Spin-Spin",
        "Bird: Falcon",
        "Smoke-Smoke",
        "Flame-Flame",
        "Ice-Ice",
        "Sand-Sand",
        "Dark-Dark",
        "Revive-Revive",
        "Diamond-Diamond",
        "Light-Light",
        "Love-Love",
        "Rubber-Rubber",
        "Barrier-Barrier",
        "Magma-Magma",
        "Door-Door",
        "Quake-Quake",
        "Human-Human: Buddha",
        "String-String",
        "Bird-Bird: Phoenix",
        "Rumble-Rumble",
        "Paw-Paw",
        "Gravity-Gravity",
        "Dough-Dough",
        "Venom-Venom",
        "Shadow-Shadow",
        "Control-Control",
        "Soul-Soul",
        "Dragon-Dragon",
        "Leopard-Leopard",
    }

spawn(function()
    while task.wait(0.1) do
        if _G.AutoFarm then
            pcall(function()
                for i,v in pairs(FruitList) do
                for x,y in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
                    if string.find(y.Name, "Fruit") then
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StoreFruit",v,game.Players.LocalPlayer.Backpack[y.Name])
                    end
                end
                end
            end)
        end
    end
end)

spawn(function()
      while wait() do 
        pcall(function() 
          if _G.AutoFarm then 
  			  for i,v in pairs(game:GetService("Workspace"):GetChildren()) do if v:IsA("Tool") then if string.find(v.Name, "Fruit") then
   				 repeat wait() 
   					 wait(.1) 
    					v.Handle.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame * CFrame.new(0, 10, 0)
   				 wait(.1) 
   				 v.Handle.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame * CFrame.new(0, 2, 0)
   					 wait(1) 
   					 firetouchinterest(game:GetService("Players").LocalPlayer.Character.HumanoidRootPart,v.Handle,0)
   					 wait(.1) 
   					 until not _G.AutoFarm or v.Parent == game.Players.LocalPlayer.Character 
    end
    end
    end
    end
    end)
    end
    end)

spawn(function()
     pcall(function()
    while wait() do
    if _G.AutoFarm then
     game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyHaki","Geppo")
     wait(1)
     game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyHaki","Buso")
     wait(1)
     game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyHaki","Soru")
     wait(1)
     game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("KenTalk","Buy")
              end 
            end
        end)
    end)

function toTarget(targetPos, targetCFrame)
        local tweenfunc = {}
        local tween_s = game:service"TweenService"
        local info = TweenInfo.new((targetPos - game:GetService("Players").LocalPlayer.Character:WaitForChild("HumanoidRootPart").Position).Magnitude/300, Enum.EasingStyle.Linear)
        local tween = tween_s:Create(game:GetService("Players").LocalPlayer.Character["HumanoidRootPart"], info, {CFrame = targetCFrame * CFrame.fromAxisAngle(Vector3.new(1,0,0), math.rad(0))})
        tween:Play()
    
        function tweenfunc:Stop()
            tween:Cancel()
            return tween
        end
    
        if not tween then return tween end
        return tweenfunc
    end

spawn(function()
            while wait() do
                if _G.AutoFarm or World1 then
                    if game.Players.localPlayer.Data.Level.Value < 200 then
        stop(_G.AutoFarm)
                    else
                        if game.Workspace.Map.Jungle.Final.Part.CanCollide == true then
                            if _G.AutoFarm and game.ReplicatedStorage:FindFirstChild("Saber Expert [Lv. 200] [Boss]") or game.Workspace.Enemies:FindFirstChild("Saber Expert [Lv. 200] [Boss]") then
                                if game.Workspace.Enemies:FindFirstChild("Saber Expert [Lv. 200] [Boss]") then
                                    for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
                                        if v.Name == "Saber Expert [Lv. 200] [Boss]" and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
                                            repeat wait()
                                                if (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude > 300 then
                                                    Farmtween = toTarget(v.HumanoidRootPart.Position,v.HumanoidRootPart.CFrame)
                                                elseif (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 300 then
                                                    if Farmtween then
                                                        Farmtween:Stop()
                                                    end
                                                    AutoHaki()
                                                    EquipWeapon(_G.Select_Weapon)
                                                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * CFrame.new(0, 30, 0)
                                                    game:GetService'VirtualUser':CaptureController()
                                                    game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
                                                end
                                            until not _G.AutoFarm or not v.Parent or v.Humanoid.Health <= 0
                                        end
                                    end
                                else
                                    Questtween = toTarget(CFrame.new(-1405.41956, 29.8519993, 5.62435055).Position,CFrame.new(-1405.41956, 29.8519993, 5.62435055))
                                    if (CFrame.new(-1405.41956, 29.8519993, 5.62435055).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 300 then
                                        if Questtween then
                                            Questtween:Stop()
                                        end
                                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-1405.41956, 29.8519993, 5.62435055, 0.885240912, 3.52892613e-08, 0.465132833, -6.60881128e-09, 1, -6.32913171e-08, -0.465132833, 5.29540891e-08, 0.885240912)
                                    end
                                end
                            else
                                if _G.Auto_Saber_Hop then
                                    Hop()
                                end
                            end
                        elseif game.Players.LocalPlayer.Backpack:FindFirstChild("Relic") or game.Players.LocalPlayer.Character:FindFirstChild("Relic") and game.Players.localPlayer.Data.Level.Value >= 200 then
                            EquipWeapon("Relic")
                            wait(0.5)
                            Questtween = toTarget(CFrame.new(-1405.41956, 29.8519993, 5.62435055).Position,CFrame.new(-1405.41956, 29.8519993, 5.62435055))
                            if (CFrame.new(-1405.41956, 29.8519993, 5.62435055).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 300 then
                                if Questtween then
                                    Questtween:Stop()
                                end
                                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-1405.41956, 29.8519993, 5.62435055, 0.885240912, 3.52892613e-08, 0.465132833, -6.60881128e-09, 1, -6.32913171e-08, -0.465132833, 5.29540891e-08, 0.885240912)
                            end
                        else
                            if Workspace.Map.Jungle.QuestPlates.Door.CanCollide == false then
                                if game.Workspace.Map.Desert.Burn.Part.CanCollide == false then
                                    if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ProQuestProgress","SickMan") == 0 then
                                        if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ProQuestProgress","RichSon") == 0 then
                                            if game.Workspace.Enemies:FindFirstChild("Mob Leader [Lv. 120] [Boss]") then
                                                for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
                                                    if _G.AutoFarm and v:IsA("Model") and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 and v.Name == "Mob Leader [Lv. 120] [Boss]" then
                                                        repeat wait()
                                                            pcall(function() wait() 
                                                                if (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude > 300 then
                                                                    Farmtween = toTarget(v.HumanoidRootPart.Position,v.HumanoidRootPart.CFrame)
                                                                elseif (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 300 then
                                                                    if Farmtween then
                                                                        Farmtween:Stop()
                                                                    end
                                                                    AutoHaki()
                                                                    EquipWeapon(_G.Select_Weapon)
                                                                    if not game.Players.LocalPlayer.Character:FindFirstChild("HasBuso") then
                                                                        local args = {
                                                                            [1] = "Buso"
                                                                        }
                                                                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                                                                    end
                                                                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * CFrame.new(0, 30, 0)
                                                                    game:GetService'VirtualUser':CaptureController()
                                                                    game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
                                                                end
                                                            end)
                                                        until not _G.AutoFarm or not v.Parent or v.Humanoid.Health <= 0
                                                    end
                                                end
                                            else
                                                Questtween = toTarget(CFrame.new(-2848.59399, 7.4272871, 5342.44043).Position,CFrame.new(-2848.59399, 7.4272871, 5342.44043))
                                                if (CFrame.new(-2848.59399, 7.4272871, 5342.44043).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 300 then
                                                    if Questtween then
                                                        Questtween:Stop()
                                                    end
                                                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-2848.59399, 7.4272871, 5342.44043, -0.928248107, -8.7248246e-08, 0.371961564, -7.61816636e-08, 1, 4.44474857e-08, -0.371961564, 1.29216433e-08, -0.928248107)
                                                end
                                            end
                                        elseif game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ProQuestProgress","RichSon") == 1 then
                                            if game.Players.LocalPlayer.Backpack:FindFirstChild("Relic") or game.Players.LocalPlayer.Character:FindFirstChild("Relic") then
                                                EquipWeapon("Relic")
                                                wait(0.5)
                                                Questtween = toTarget(CFrame.new(-1405.41956, 29.8519993, 5.62435055).Position,CFrame.new(-1405.41956, 29.8519993, 5.62435055))
                                                if (CFrame.new(-1405.41956, 29.8519993, 5.62435055).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 300 then
                                                    if Questtween then
                                                        Questtween:Stop()
                                                    end
                                                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-1405.41956, 29.8519993, 5.62435055)
                                                end
                                            else
                                                Questtween = toTarget(CFrame.new(-910.979736, 13.7520342, 4078.14624).Position,CFrame.new(-910.979736, 13.7520342, 4078.14624))
                                                if (CFrame.new(-910.979736, 13.7520342, 4078.14624).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 300 then
                                                    if Questtween then
                                                        Questtween:Stop()
                                                    end
                                                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-910.979736, 13.7520342, 4078.14624, 0.00685182028, -1.53155766e-09, -0.999976516, 9.15205245e-09, 1, -1.46888401e-09, 0.999976516, -9.14177267e-09, 0.00685182028)
                                                    wait(.5)
                                                    local args = {
                                                        [1] = "ProQuestProgress",
                                                        [2] = "RichSon"
                                                    }
                                                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                                                end
                                            end
                                        else
                                            Questtween = toTarget(CFrame.new(-910.979736, 13.7520342, 4078.14624).Position,CFrame.new(-910.979736, 13.7520342, 4078.14624))
                                            if (CFrame.new(-910.979736, 13.7520342, 4078.14624).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 300 then
                                                if Questtween then
                                                    Questtween:Stop()
                                                end
                                                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-910.979736, 13.7520342, 4078.14624)
                                                local args = {
                                                    [1] = "ProQuestProgress",
                                                    [2] = "RichSon"
                                                }
                                                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                                            end
                                        end
                                    else
                                        if game.Players.LocalPlayer.Backpack:FindFirstChild("Cup") or game.Players.LocalPlayer.Character:FindFirstChild("Cup") then
                                            EquipWeapon("Cup")
                                            if game.Players.LocalPlayer.Character.Cup.Handle:FindFirstChild("TouchInterest") then
                                                Questtween = toTarget(CFrame.new(1397.229, 37.3480148, -1320.85217).Position,CFrame.new(1397.229, 37.3480148, -1320.85217))
                                                if (CFrame.new(1397.229, 37.3480148, -1320.85217).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 300 then
                                                    if Questtween then
                                                        Questtween:Stop()
                                                    end
                                                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(1397.229, 37.3480148, -1320.85217, -0.11285457, 2.01368788e-08, 0.993611455, 1.91641178e-07, 1, 1.50028845e-09, -0.993611455, 1.90586206e-07, -0.11285457)
                                                end
                                            else
                                                wait(0.5)
                                                if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ProQuestProgress","SickMan") ~= 0 then
                                                    local args = {
                                                        [1] = "ProQuestProgress",
                                                        [2] = "SickMan"
                                                    }
                                                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                                                end
                                            end
                                        else
                                            Questtween = toTarget(game.Workspace.Map.Desert.Cup.Position,game.Workspace.Map.Desert.Cup.CFrame)
                                            if (game.Workspace.Map.Desert.Cup.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 300 then
                                                if Questtween then
                                                    Questtween:Stop()
                                                end
                                                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.Workspace.Map.Desert.Cup.CFrame
                                            end
                                            -- firetouchinterest(game.Workspace.Map.Desert.Cup.TouchInterest,game.Players.LocalPlayer.Character.Head, 1)
                                        end
                                    end
                                else
                                    if game.Players.LocalPlayer.Backpack:FindFirstChild("Torch") or game.Players.LocalPlayer.Character:FindFirstChild("Torch") then
                                        EquipWeapon("Torch")
                                        Questtween = toTarget(CFrame.new(1114.87708, 4.9214654, 4349.8501).Position,CFrame.new(1114.87708, 4.9214654, 4349.8501))
                                        if (CFrame.new(1114.87708, 4.9214654, 4349.8501).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 300 then
                                            if Questtween then
                                                Questtween:Stop()
                                            end
                                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(1114.87708, 4.9214654, 4349.8501, -0.612586915, -9.68697833e-08, 0.790403247, -1.2634203e-07, 1, 2.4638446e-08, -0.790403247, -8.47679615e-08, -0.612586915)
                                        end
                                    else
                                        Questtween = toTarget(CFrame.new(-1610.00757, 11.5049858, 164.001587).Position,CFrame.new(-1610.00757, 11.5049858, 164.001587))
                                        if (CFrame.new(-1610.00757, 11.5049858, 164.001587).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 300 then
                                            if Questtween then
                                                Questtween:Stop()
                                            end
                                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-1610.00757, 11.5049858, 164.001587, 0.984807551, -0.167722285, -0.0449818149, 0.17364943, 0.951244235, 0.254912198, 3.42372805e-05, -0.258850515, 0.965917408)
                                        end
                                    end
                                end
                            else
                                for i,v in pairs(Workspace.Map.Jungle.QuestPlates:GetChildren()) do
                                    if v:IsA("Model") then wait()
                                        if v.Button.BrickColor ~= BrickColor.new("Camo") then
                                            repeat wait()
                                                Questtween = toTarget(v.Button.Position,v.Button.CFrame)
                                                if (v.Button.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 150 then
                                                    if Questtween then
                                                        Questtween:Stop()
                                                    end
                                                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.Button.CFrame
                                                end
                                            until not _G.AutoFarm or v.Button.BrickColor == BrickColor.new("Camo")
                                        end
                                    end
                                end    
                            end
                        end
                    end 
                end
            end
            end)


task.spawn(
    function()
        pcall(
            function()
                while wait() do
                    if game.PlaceId == 2753915549 then
                        WolrdSet3:Set("Wolrd : 1 " .. "✅")
                    end
                end
            end
        )
    end
)
task.spawn(
    function()
        pcall(
            function()
                while wait() do
                    if game.PlaceId == 4442272183 then
                        WolrdSet:Set("Wolrd : 2 " .. "✅")
                    end
                end
            end
        )
    end
)
task.spawn(
    function()
        pcall(
            function()
                while wait() do
                    if game.PlaceId == 7449423635 then
                        WolrdSet1:Set("Wolrd : 3 " .. "✅")
                    end
                end
            end
        )
    end
)


task.spawn(
    function()
        while task.wait() do
            pcall(
                function()
                    for i, v in pairs(
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("getInventoryWeapons")
                    ) do
                        if v.Name == "Saber" then
                            Saber:Set("✅ : Saber")
                        end
                        if v.Name == "Rengoku" then
                            Rengoku:Set("✅ : Rengoku")
                        end
                        if v.Name == "Midnight Blade" then
                            MidnightBlade:Set("✅ : Midnight Blade")
                        end
                        if v.Name == "Dragon Trident" then
                            DragonTrident:Set("✅ : Dragon Trident")
                        end
                        if v.Name == "Yama" then
                            Yama:Set("✅ : Yama")
                        end
                        if v.Name == "Buddy Sword" then
                            BuddySword:Set("✅ : Buddy Sword")
                        end
                        if v.Name == "Canvander" then
                            Canvander:Set("✅ : Canvander")
                        end
                        if v.Name == "Twin Hooks" then
                            TwinHooks:Set("✅ : Twin Hooks")
                        end
                        if v.Name == "Spikey Trident" then
                            SpikeyTrident:Set("✅ : Spikey Trident")
                        end
                        if v.Name == "Hallow Scythe" then
                            HallowScythe:Set("✅ : Hallow Scythe")
                        end
                        if v.Name == "Dark Dagger" then
                            DarkDagger:Set("✅ : Dark Dagger")
                        end
                        if v.Name == "Tushita" then
                            Tushita:Set("✅ : Tushita")
                        end
                    end
                end
            )
        end
    end
)

task.spawn(
    function()
        while task.wait() do
            pcall(
                function()
                    for i, v in pairs(
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("getInventoryWeapons")
                    ) do
                        if v.Name == "Kabucha" then
                            Kabucha:Set("✅ : Kabucha")
                        end
                        if v.Name == "Acidum Rifle" then
                            AcidumRifle:Set("✅ : Acidum Rifle")
                        end
                        if v.Name == "Bizarre Rifle" then
                            BizarreRifle:Set("✅ : Bizarre Rifle")
                        end
                    end
                end
            )
        end
    end
)

task.spawn(
    function()
        while task.wait() do
            if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BartiloQuestProgress", "Bartilo") == 3 then
                BartiloQuest:Set("✅ : Bartilo Quest")
            end
            if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("GetUnlockables").FlamingoAccess == nil then
            else
                DonSwanQuest:Set("✅ : Don Swan Quest")
            end
            if game:GetService("ReplicatedStorage").Remotes["CommF_"]:InvokeServer("ZQuestProgress", "Check") == 1 then
                KillDonSwan:Set("✅ : Kill Don Swan")
            end
        end
    end
)

task.spawn(
    function()
        while task.wait() do
            pcall(
                function()
                    for i, v in pairs(
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("getInventoryWeapons")
                    ) do
                        if v.Name == "Shisui" then
                            Shisui:Set("✅ : Shisui")
                        end
                        if v.Name == "Saddi" then
                            Saddi:Set("✅ : Saddi")
                        end
                        if v.Name == "Wando" then
                            Wando:Set("✅ : Wando")
                        end
                        if v.Name == "True Triple Katana" then
                            TrueTripleKatana:Set("✅ : True Triple Katana")
                        end
                    end
                end
            )
        end
    end
)

task.spawn(
    function()
        while task.wait() do
            if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySuperhuman", true) == 1 then
                Superhuman:Set("✅ : Superhuman")
            end
            if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDeathStep", true) == 1 then
                DeathStep:Set("✅ : Death Step")
            end
            if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySharkmanKarate", true) == 1 then
                SharkmanKarate:Set("✅ : Sharkman Karate")
            end
            if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyElectricClaw", true) == 1 then
                ElectricClaw:Set("✅ : Electric Claw")
            end
            if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDragonTalon", true) == 1 then
                DragonTalon:Set("✅ : Dragon Talon")
            end
            if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyGodhuman", true) == 1 then
                GodHuman:Set("✅ : God Human")
            end
        end
    end
)

_G.Team = 'Marine'

 if game:GetService("Players").LocalPlayer.PlayerGui.Main:FindFirstChild("ChooseTeam") then
	repeat wait()
		if game:GetService("Players").LocalPlayer.PlayerGui:WaitForChild("Main").ChooseTeam.Visible == true then
			if _G.Team == "Pirate" then
				for i, v in pairs(getconnections(game:GetService("Players").LocalPlayer.PlayerGui.Main.ChooseTeam.Container.Pirates.Frame.ViewportFrame.TextButton.Activated)) do                                                                                                
					v.Function()
				end
			elseif _G.Team == "Marine" then
				for i, v in pairs(getconnections(game:GetService("Players").LocalPlayer.PlayerGui.Main.ChooseTeam.Container.Marines.Frame.ViewportFrame.TextButton.Activated)) do                                                                                                
					v.Function()
				end
			else
				for i, v in pairs(getconnections(game:GetService("Players").LocalPlayer.PlayerGui.Main.ChooseTeam.Container.Pirates.Frame.ViewportFrame.TextButton.Activated)) do                                                                                                
					v.Function()
				end
			end
		end
	until game.Players.LocalPlayer.Team ~= nil and game:IsLoaded()
end
