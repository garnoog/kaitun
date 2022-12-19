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

do  local ui =  game:GetService("CoreGui"):FindFirstChild("Ui Native Hub")  if ui then ui:Destroy() end end

local UserInputService = game:GetService("UserInputService")
local TweenService = game:GetService("TweenService")
local RunService = game:GetService("RunService")
local LocalPlayer = game:GetService("Players").LocalPlayer
local Mouse = LocalPlayer:GetMouse()



local function Tween(instance, properties,style,wa)
	if style == nil or "" then
		return Back
	end
	tween:Create(instance,TweenInfo.new(wa,Enum.EasingStyle[style]),{properties}):Play()
end

local ActualTypes = {
	RoundFrame = "ImageLabel",
	Shadow = "ImageLabel",
	Circle = "ImageLabel",
	CircleButton = "ImageButton",
	Frame = "Frame",
	Label = "TextLabel",
	Button = "TextButton",
	SmoothButton = "ImageButton",
	Box = "TextBox",
	ScrollingFrame = "ScrollingFrame",
	Menu = "ImageButton",
	NavBar = "ImageButton"
}

local Properties = {
	RoundFrame = {
		BackgroundTransparency = 1,
		Image = "http://www.roblox.com/asset/?id=5554237731",
		ScaleType = Enum.ScaleType.Slice,
		SliceCenter = Rect.new(3,3,297,297)
	},
	SmoothButton = {
		AutoButtonColor = false,
		BackgroundTransparency = 1,
		Image = "http://www.roblox.com/asset/?id=5554237731",
		ScaleType = Enum.ScaleType.Slice,
		SliceCenter = Rect.new(3,3,297,297)
	},
	Shadow = {
		Name = "Shadow",
		BackgroundTransparency = 1,
		Image = "http://www.roblox.com/asset/?id=5554236805",
		ScaleType = Enum.ScaleType.Slice,
		SliceCenter = Rect.new(23,23,277,277),
		Size = UDim2.fromScale(1,1) + UDim2.fromOffset(30,30),
		Position = UDim2.fromOffset(-15,-15)
	},
	Circle = {
		BackgroundTransparency = 1,
		Image = "http://www.roblox.com/asset/?id=5554831670"
	},
	CircleButton = {
		BackgroundTransparency = 1,
		AutoButtonColor = false,
		Image = "http://www.roblox.com/asset/?id=5554831670"
	},
	Frame = {
		BackgroundTransparency = 1,
		BorderSizePixel = 0,
		Size = UDim2.fromScale(1,1)
	},
	Label = {
		BackgroundTransparency = 1,
		Position = UDim2.fromOffset(5,0),
		Size = UDim2.fromScale(1,1) - UDim2.fromOffset(5,0),
		TextSize = 14,
		TextXAlignment = Enum.TextXAlignment.Left
	},
	Button = {
		BackgroundTransparency = 1,
		Position = UDim2.fromOffset(5,0),
		Size = UDim2.fromScale(1,1) - UDim2.fromOffset(5,0),
		TextSize = 14,
		TextXAlignment = Enum.TextXAlignment.Left
	},
	Box = {
		BackgroundTransparency = 1,
		Position = UDim2.fromOffset(5,0),
		Size = UDim2.fromScale(1,1) - UDim2.fromOffset(5,0),
		TextSize = 14,
		TextXAlignment = Enum.TextXAlignment.Left
	},
	ScrollingFrame = {
		BackgroundTransparency = 1,
		ScrollBarThickness = 0,
		CanvasSize = UDim2.fromScale(0,0),
		Size = UDim2.fromScale(1,1)
	},
	Menu = {
		Name = "More",
		AutoButtonColor = false,
		BackgroundTransparency = 1,
		Image = "http://www.roblox.com/asset/?id=5555108481",
		Size = UDim2.fromOffset(20,20),
		Position = UDim2.fromScale(1,0.5) - UDim2.fromOffset(25,10)
	},
	NavBar = {
		Name = "SheetToggle",
		Image = "http://www.roblox.com/asset/?id=5576439039",
		BackgroundTransparency = 1,
		Size = UDim2.fromOffset(20,20),
		Position = UDim2.fromOffset(5,5),
		AutoButtonColor = false
	}
}

local Types = {
	"RoundFrame",
	"Shadow",
	"Circle",
	"CircleButton",
	"Frame",
	"Label",
	"Button",
	"SmoothButton",
	"Box",
	"ScrollingFrame",
	"Menu",
	"NavBar"
}

function FindType(String)
	for _, Type in next, Types do
		if Type:sub(1, #String):lower() == String:lower() then
			return Type
		end
	end
	return false
end

local Objects = {}

function Objects.new(Type)
	local TargetType = FindType(Type)
	if TargetType then
		local NewImage = Instance.new(ActualTypes[TargetType])
		if Properties[TargetType] then
			for Property, Value in next, Properties[TargetType] do
				NewImage[Property] = Value
			end
		end
		return NewImage
	else
		return Instance.new(Type)
	end
end

local function GetXY(GuiObject)
	local Max, May = GuiObject.AbsoluteSize.X, GuiObject.AbsoluteSize.Y
	local Px, Py = math.clamp(Mouse.X - GuiObject.AbsolutePosition.X, 0, Max), math.clamp(Mouse.Y - GuiObject.AbsolutePosition.Y, 0, May)
	return Px/Max, Py/May
end

local function CircleAnim(GuiObject, EndColour, StartColour)
	local PX, PY = GetXY(GuiObject)
	local Circle = Objects.new("Circle")
	Circle.Size = UDim2.fromScale(0,0)
	Circle.Position = UDim2.fromScale(PX,PY)
	Circle.ImageColor3 = StartColour or GuiObject.ImageColor3
	Circle.ZIndex = 200
	Circle.Parent = GuiObject
	local Size = GuiObject.AbsoluteSize.X
	TweenService:Create(Circle, TweenInfo.new(0.4), {Position = UDim2.fromScale(PX,PY) - UDim2.fromOffset(Size/2,Size/2), ImageTransparency = 1, ImageColor3 = EndColour, Size = UDim2.fromOffset(Size,Size)}):Play()
	spawn(function()
		wait(0.4)
		Circle:Destroy()
	end)
end


local function MakeDraggable(topbarobject, object)
    local Dragging = nil
    local DragInput = nil	
    local DragStart = nil
    local StartPosition = nil

    local function Update(input)
        local Delta = input.Position - DragStart
        local pos =
            UDim2.new(
                StartPosition.X.Scale,
                StartPosition.X.Offset + Delta.X,
                StartPosition.Y.Scale,
                StartPosition.Y.Offset + Delta.Y
            )
        local Tween = TweenService:Create(object, TweenInfo.new(0.2), {Position = pos})
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


local Lib = {}

function Lib:Window(text)
    local UiNativeHub = Instance.new("ScreenGui")
    local Main = Instance.new("Frame")
    local UICornerMain = Instance.new("UICorner")
    local Top = Instance.new("Frame")
    local UICornerTop = Instance.new("UICorner")
    local logo = Instance.new("ImageLabel")
    local Tab = Instance.new("Frame")
    local ScrollingTab = Instance.new("ScrollingFrame")
    local TabList = Instance.new("UIListLayout")
    local UIPadding = Instance.new("UIPadding")
    local NameReal = Instance.new("TextLabel")
    local ImageTab = Instance.new("ImageLabel")
    local MainPage = Instance.new("Frame")
    local UICornerPage = Instance.new("UICorner")
    local PageFolder = Instance.new("Folder")
    local UIPageLayout = Instance.new("UIPageLayout")
    local Tabtoggle = false
    local abc = false

    UiNativeHub.Name = "Ui Native Hub"
    UiNativeHub.Parent = game.CoreGui
    UiNativeHub.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
    
    Main.Name = "Main"
    Main.Parent = UiNativeHub
    Main.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
    Main.BorderSizePixel = 0
    Main.ClipsDescendants = true
    Main.Position = UDim2.new(0.240740746, 0, 0.286585361, 0)
    Main.Size = UDim2.new(0, 0, 0, 0)

    pcall(Main:TweenSize(UDim2.new(0, 700, 0, 380),"Out","Back",0.4,true))

    UICornerMain.CornerRadius = UDim.new(0, 4)
    UICornerMain.Name = "UICornerMain"
    UICornerMain.Parent = Main
    
    Top.Name = "Top"
    Top.Parent = Main
    Top.BackgroundColor3 = Color3.fromRGB(25, 25, 25)
    Top.BorderSizePixel = 0
    Top.Size = UDim2.new(0, 700, 0, 38)
    
    UICornerTop.CornerRadius = UDim.new(0, 4)
    UICornerTop.Name = "UICornerTop"
    UICornerTop.Parent = Top
    
    logo.Name = "logo"
    logo.Parent = Top
    logo.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
    logo.BackgroundTransparency = 1.000
    logo.Position = UDim2.new(0.0157142859, 0, 0, 0)
    logo.Size = UDim2.new(0, 40, 0, 40)
    logo.Image = "rbxassetid://11862785327"
    
    NameReal.Name = "NameReal"
    NameReal.Parent = Top
    NameReal.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
    NameReal.BackgroundTransparency = 1.000
    NameReal.Position = UDim2.new(0.0900000036, 0, 0, 0)
    NameReal.Size = UDim2.new(0, 170, 0, 38)
    NameReal.Font = Enum.Font.GothamBold
    NameReal.Text = text
    NameReal.TextColor3 = Color3.fromRGB(255,255,255)
    NameReal.TextSize = 16.000
    NameReal.TextXAlignment = Enum.TextXAlignment.Left
    
    ImageTab.Name = "ImageTab"
    ImageTab.Parent = Top
    ImageTab.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
    ImageTab.BackgroundTransparency = 1.000
    ImageTab.Position = UDim2.new(0.940000057, 0, 0.105263151, 0)
    ImageTab.Size = UDim2.new(0, 30, 0, 30)
    ImageTab.Image = "http://www.roblox.com/asset/?id=11271966220"
    
    local TabButtonnnn = Instance.new("TextButton")
    TabButtonnnn.Parent = ImageTab
    TabButtonnnn.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
    TabButtonnnn.BackgroundTransparency = 1.000
    TabButtonnnn.Size = UDim2.new(0, 30, 0, 30)
    TabButtonnnn.Font = Enum.Font.SourceSans
    TabButtonnnn.Text = ""
    TabButtonnnn.TextColor3 = Color3.fromRGB(0, 0, 0)
    TabButtonnnn.TextSize = 14.000
    
    Tab.Name = "Tab"
    Tab.Parent = Main
    Tab.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
    Tab.BorderSizePixel = 0
    Tab.ClipsDescendants = true
    Tab.Position = UDim2.new(0, 0, 0.100000001, 0)
    Tab.Size = UDim2.new(0, 0, 0, 342)
    Tab.ZIndex = 2

    ScrollingTab.Name = "ScrollingTab"
    ScrollingTab.Parent = Tab
    ScrollingTab.Active = true
    ScrollingTab.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
    ScrollingTab.BackgroundTransparency = 1.000
    ScrollingTab.BorderSizePixel = 0
    ScrollingTab.Size = UDim2.new(0, 247, 0, 342)
    ScrollingTab.ScrollBarThickness = 4
    ScrollingTab.CanvasSize = UDim2.new(0, 0, 0, 0)
    ScrollingTab.ClipsDescendants = true

    TabList.Name = "TabList"
    TabList.Parent = ScrollingTab
    TabList.SortOrder = Enum.SortOrder.LayoutOrder
    TabList.Padding = UDim.new(0, 3)



    UIPadding.Parent = ScrollingTab
    UIPadding.PaddingTop = UDim.new(0, 5)
    
    MainPage.Name = "MainPage"
    MainPage.Parent = Main
    MainPage.BackgroundColor3 = Color3.fromRGB(25, 25, 25)
    MainPage.BorderSizePixel = 0
    MainPage.Position = UDim2.new(0.0157142859, 0, 0.126315787, 0)
    MainPage.Size = UDim2.new(0, 677, 0, 318)
    MainPage.ClipsDescendants = true
    
    UICornerPage.CornerRadius = UDim.new(0, 4)
    UICornerPage.Name = "UICornerPage"
    UICornerPage.Parent = MainPage
    
    PageFolder.Name = "PageFolder"
    PageFolder.Parent = MainPage
    
    UIPageLayout.Parent = PageFolder
    UIPageLayout.SortOrder = Enum.SortOrder.LayoutOrder
    UIPageLayout.EasingDirection = Enum.EasingDirection.InOut
    UIPageLayout.EasingStyle = Enum.EasingStyle.Quad
    UIPageLayout.GamepadInputEnabled = false
    UIPageLayout.ScrollWheelInputEnabled = false
    UIPageLayout.TouchInputEnabled = false
    UIPageLayout.TweenTime = 0.300



    local Black = Instance.new("Frame")
    Black.Name = "Black"
    Black.Parent = Main
    Black.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
    Black.BackgroundTransparency = .3
    Black.BorderSizePixel = 0
    Black.Position = UDim2.new(0, 0, 0.086585361, 0)
    Black.Size = UDim2.new(0, 0, 0, 342)
    
    
    UserInputService.InputBegan:Connect(function(input)
		if input.KeyCode == Enum.KeyCode.RightControl then
			if uihide == false then
				uihide = true
                pcall(Main:TweenSize(UDim2.new(0, 0, 0, 0),"In","Quad",0.4,true))
			else
				uihide = false
				pcall(Main:TweenSize(UDim2.new(0, 700, 0, 380),"Out","Back",0.4,true))
			end
		end
	end)
    
    TabButtonnnn.MouseButton1Click:Connect(function()
        if Tabtoggle == false then
            Tabtoggle = true
            TweenService:Create(
                Tab,
                TweenInfo.new(0.2,Enum.EasingStyle.Back,Enum.EasingDirection.Out),
                {Size = UDim2.new(0, 247, 0, 342)}
            ):Play()
            TweenService:Create(
                Black,
                TweenInfo.new(0.1,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                {Size = UDim2.new(0, 700, 0, 342)}
            ):Play()
            TweenService:Create(
                ImageTab,
                TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                {ImageColor3 = Color3.fromRGB(32,143,252)}
            ):Play()
        else
            Tabtoggle = false
            TweenService:Create(
                Tab,
                TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                {Size = UDim2.new(0, 0, 0, 342)}
            ):Play()
            TweenService:Create(
                Black,
                TweenInfo.new(0,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                {Size = UDim2.new(0, 0, 0, 342)}
            ):Play()
            TweenService:Create(
                ImageTab,
                TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                {ImageColor3 = Color3.fromRGB(255, 255, 255)}
            ):Play()
        end
    end)

    local Ui = {}

    function Ui:Tab(text)
        local TabFrame = Instance.new("Frame")
        local Tabb = Instance.new("Frame")
        local UICornerTabb = Instance.new("UICorner")
        local UIGradientTabb = Instance.new("UIGradient")
        local TextTab = Instance.new("TextLabel")
        local TextButton = Instance.new("TextButton")
        local MainFramePage = Instance.new("Frame")
        local UICornerMainFramePage = Instance.new("UICorner")

        TabFrame.Name = "TabFrame"
        TabFrame.Parent = ScrollingTab
        TabFrame.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
        TabFrame.BackgroundTransparency = 1.000
        TabFrame.Size = UDim2.new(0, 247, 0, 40)
        
        Tabb.Name = "Tabb"
        Tabb.Parent = TabFrame
        Tabb.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
        Tabb.ClipsDescendants = true
        Tabb.Position = UDim2.new(0.0445344113, 0, 0.125, 0)
        Tabb.Size = UDim2.new(0, 222, 0, 30)
        
        UICornerTabb.CornerRadius = UDim.new(0, 4)
        UICornerTabb.Name = "UICornerTabb"
        UICornerTabb.Parent = Tabb
        
        UIGradientTabb.Color = ColorSequence.new{ColorSequenceKeypoint.new(0.00, Color3.fromRGB(32,143,252)), ColorSequenceKeypoint.new(1.00, Color3.fromRGB(160, 212, 255))}
        UIGradientTabb.Name = "UIGradientTabb"
        UIGradientTabb.Parent = Tabb
        
        TextTab.Name = "TextTab"
        TextTab.Parent = Tabb
        TextTab.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
        TextTab.BackgroundTransparency = 1.000
        TextTab.Size = UDim2.new(0, 222, 0, 30)
        TextTab.Font = Enum.Font.GothamBold
        TextTab.Text = text
        TextTab.TextColor3 = Color3.fromRGB(255, 255, 255)
        TextTab.TextSize = 15.000
        
        TextButton.Parent = TabFrame
        TextButton.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
        TextButton.BackgroundTransparency = 1.000
        TextButton.Size = UDim2.new(0, 247, 0, 40)
        TextButton.Font = Enum.Font.SourceSans
        TextButton.Text = ""
        TextButton.TextColor3 = Color3.fromRGB(0, 0, 0)
        TextButton.TextSize = 14.000
        
        MainFramePage.Name = "MainFramePage"
        MainFramePage.Parent = PageFolder
        MainFramePage.BackgroundColor3 = Color3.fromRGB(25, 25, 25)
        MainFramePage.BorderSizePixel = 0
        MainFramePage.Position = UDim2.new(0.0925237387, 0, 0.132605091, 0)
        MainFramePage.Size = UDim2.new(0, 677, 0, 318)
        MainFramePage.ClipsDescendants = true
        
        UICornerMainFramePage.CornerRadius = UDim.new(0, 4)
        UICornerMainFramePage.Name = "UICornerMainFramePage"
        UICornerMainFramePage.Parent = MainFramePage

        local ScrollMainPage = Instance.new("ScrollingFrame")
        local UIListLayoutPage = Instance.new("UIListLayout")
        
        ScrollMainPage.Name = "ScrollMainPage"
        ScrollMainPage.Parent = MainFramePage
        ScrollMainPage.Active = true
        ScrollMainPage.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
        ScrollMainPage.BackgroundTransparency = 1.000
        ScrollMainPage.BorderSizePixel = 0
        ScrollMainPage.Size = UDim2.new(0, 677, 0, 318)
        ScrollMainPage.CanvasSize = UDim2.new(0, 0, 0, 0)
        ScrollMainPage.ScrollBarThickness = 0
        
        UIListLayoutPage.Name = "UIListLayoutPage"
        UIListLayoutPage.Parent = ScrollMainPage
        UIListLayoutPage.FillDirection = Enum.FillDirection.Horizontal
        UIListLayoutPage.SortOrder = Enum.SortOrder.LayoutOrder
        UIListLayoutPage.Padding = UDim.new(0, 7)

        local UIPaddingPage = Instance.new("UIPadding")
        
        UIPaddingPage.Name = "UIPaddingPage"
        UIPaddingPage.Parent = ScrollMainPage
        UIPaddingPage.PaddingLeft = UDim.new(0, 7)
        UIPaddingPage.PaddingTop = UDim.new(0, 12)

        MakeDraggable(Top,Main)


        TextButton.MouseButton1Click:Connect(function()
            CircleAnim(Tabb, Color3.fromRGB(255,255,255), Color3.fromRGB(255,255,255))
            TextTab.TextSize = 0
            TweenService:Create(
                TextTab,
                TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                {TextSize = 15}
            ):Play()
            for i,v in next, PageFolder:GetChildren() do 
                if v.Name == "MainFramePage" then
                    currenttab = v.Name
                end
                UIPageLayout:JumpTo(MainFramePage)
                
            end
		end)

		if abc == false then
            UIPageLayout:JumpToIndex(1)
			abc = true
		end

        local Tab = {}

        function Tab:Page()

            local MainFramePage_2 = Instance.new("Frame")
            local UICornerMainFramePage_2 = Instance.new("UICorner")
            local ScrollingMainFramePage = Instance.new("ScrollingFrame")
            local UIListLayoutMainFramePage = Instance.new("UIListLayout")



            MainFramePage_2.Name = "MainFramePage"
            MainFramePage_2.Parent = ScrollMainPage
            MainFramePage_2.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
            MainFramePage_2.BorderSizePixel = 0
            MainFramePage_2.ClipsDescendants = true
            MainFramePage_2.Position = UDim2.new(-0.010447761, 0, -0.00326797389, 0)
            MainFramePage_2.Size = UDim2.new(0, 328, 0, 296)

            UICornerMainFramePage_2.CornerRadius = UDim.new(0, 4)
            UICornerMainFramePage_2.Name = "UICornerMainFramePage"
            UICornerMainFramePage_2.Parent = MainFramePage_2

            ScrollingMainFramePage.Name = "ScrollingMainFramePage"
            ScrollingMainFramePage.Parent = MainFramePage_2
            ScrollingMainFramePage.Active = true
            ScrollingMainFramePage.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
            ScrollingMainFramePage.BackgroundTransparency = 1.000
            ScrollingMainFramePage.BorderSizePixel = 0
            ScrollingMainFramePage.Size = UDim2.new(0, 328, 0, 296)
            ScrollingMainFramePage.CanvasSize = UDim2.new(0, 0, 0, 0)
            ScrollingMainFramePage.ScrollBarThickness = 0

            UIListLayoutMainFramePage.Name = "UIListLayoutMainFramePage"
            UIListLayoutMainFramePage.Parent = ScrollingMainFramePage
            UIListLayoutMainFramePage.SortOrder = Enum.SortOrder.LayoutOrder
            UIListLayoutMainFramePage.Padding = UDim.new(0, 8)


            local UIPaddingMainFramePage = Instance.new("UIPadding")

            UIPaddingMainFramePage.Name = "UIPaddingMainFramePage"
            UIPaddingMainFramePage.Parent = ScrollingMainFramePage
            UIPaddingMainFramePage.PaddingTop = UDim.new(0, 9)
            
            
            game:GetService("RunService").Stepped:Connect(function()
                pcall(function()
                    ScrollingMainFramePage.CanvasSize = UDim2.new(0,0,0,UIListLayoutMainFramePage.AbsoluteContentSize.Y + 26)
                    ScrollingTab.CanvasSize = UDim2.new(0,0,0,TabList.AbsoluteContentSize.Y + 10)
                end)
            end)

            local main = {}
            function main:Toggle2(text,default,callback)
                local ToggleFrame2 = Instance.new("Frame")
                local TextToggle2 = Instance.new("TextLabel")
                local Toggle_2 = Instance.new("Frame")
                local UICornerToggle2 = Instance.new("UICorner")
                local Tgle2 = Instance.new("ImageLabel")
                local ButtonTgle2 = Instance.new("TextButton")
                local toggle2 = false
                local lock2 = false

                ToggleFrame2.Name = "ToggleFrame2"
                ToggleFrame2.Parent = ScrollingMainFramePage
                ToggleFrame2.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                ToggleFrame2.BackgroundTransparency = 1.000
                ToggleFrame2.ClipsDescendants = true
                ToggleFrame2.Size = UDim2.new(0, 328, 0, 32)

                TextToggle2.Name = "TextToggle2"
                TextToggle2.Parent = ToggleFrame2
                TextToggle2.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                TextToggle2.BackgroundTransparency = 1.000
                TextToggle2.Position = UDim2.new(0.23780489, 0, 0, 0)
                TextToggle2.Size = UDim2.new(0, 192, 0, 32)
                TextToggle2.Font = Enum.Font.GothamBold
                TextToggle2.Text = "Auto Farm Level"
                TextToggle2.TextColor3 = Color3.fromRGB(255, 255, 255)
                TextToggle2.TextSize = 14.000
                TextToggle2.TextXAlignment = Enum.TextXAlignment.Left

                Toggle_2.Name = "Toggle"
                Toggle_2.Parent = ToggleFrame2
                Toggle_2.BackgroundColor3 = Color3.fromRGB(39, 39, 39)
                Toggle_2.BorderSizePixel = 0
                Toggle_2.Position = UDim2.new(0.103658535, 0, 0.0625, 0)
                Toggle_2.Size = UDim2.new(0, 28, 0, 28)

                UICornerToggle2.CornerRadius = UDim.new(0, 4)
                UICornerToggle2.Name = "UICornerToggle2"
                UICornerToggle2.Parent = Toggle_2

                Tgle2.Name = "Tgle2"
                Tgle2.Parent = Toggle_2
                Tgle2.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                Tgle2.BackgroundTransparency = 1.000
                Tgle2.Position = UDim2.new(0.0357142873, 0, 0.0357142873, 0)
                Tgle2.Size = UDim2.new(0, 26, 0, 26)
                Tgle2.Image = "rbxassetid://6031068421"
                Tgle2.ImageColor3 = Color3.fromRGB(32,143,252)

                ButtonTgle2.Name = "ButtonTgle2"
                ButtonTgle2.Parent = ToggleFrame2
                ButtonTgle2.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                ButtonTgle2.BackgroundTransparency = 1.000
                ButtonTgle2.Size = UDim2.new(0, 328, 0, 32)
                ButtonTgle2.Font = Enum.Font.SourceSans
                ButtonTgle2.Text = ""
                ButtonTgle2.TextColor3 = Color3.fromRGB(0, 0, 0)
                ButtonTgle2.TextSize = 14.000

                
                if default == false then
                    toggle_lol = false
                    TweenService:Create(
                        Tgle2,
                        TweenInfo.new(0.2,Enum.EasingStyle.Back,Enum.EasingDirection.Out),
                        {ImageTransparency = 1}
                    ):Play()
                    callback(toggle_lol)
                end
                if default == true then
                    toggle_lol = true
                    TweenService:Create(
                        Tgle2,
                        TweenInfo.new(0.2,Enum.EasingStyle.Back,Enum.EasingDirection.Out),
                        {ImageTransparency = 0}
                    ):Play()
                    callback(toggle_lol)
                end
                ButtonTgle2.MouseButton1Click:Connect(function()
                    if Tabtoggle == false then
                        if toggle_lol == false and lock2 == false then
                            toggle_lol = true
                            TweenService:Create(
                                Tgle2,
                                TweenInfo.new(0.2,Enum.EasingStyle.Back,Enum.EasingDirection.Out),
                                {ImageTransparency = 0}
                            ):Play()
                            callback(toggle_lol)
                        elseif toggle_lol == true and lock2 == false then
                            toggle_lol = false
                            TweenService:Create(
                                Tgle2,
                                TweenInfo.new(0.2,Enum.EasingStyle.Back,Enum.EasingDirection.Out),
                                {ImageTransparency = 1}
                            ):Play()
                            callback(toggle_lol)
                        end
                    end
                end
                )
            end

            function main:AddButton(text,callback)
                local FrameButton = Instance.new("Frame")
                local Btn = Instance.new("Frame")
                local UICornerBtn = Instance.new("UICorner")
                local UIGradientBtn = Instance.new("UIGradient")
                
                local TextLabelBtn = Instance.new("TextLabel")
                local ButtonBtn = Instance.new("TextButton")

                FrameButton.Name = "FrameButton"
                FrameButton.Parent = ScrollingMainFramePage
                FrameButton.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                FrameButton.BackgroundTransparency = 1.000
                FrameButton.Size = UDim2.new(0, 328, 0, 32)
                
                Btn.Name = "Btn"
                Btn.Parent = FrameButton
                Btn.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                Btn.BorderSizePixel = 0
                Btn.Position = UDim2.new(0.0487804897, 0, 0.03125, 0)
                Btn.Size = UDim2.new(0, 296, 0, 30)
                Btn.ClipsDescendants = true

                UICornerBtn.CornerRadius = UDim.new(0, 4)
                UICornerBtn.Name = "UICornerBtn"
                UICornerBtn.Parent = Btn
                



                UIGradientBtn.Color = ColorSequence.new{ColorSequenceKeypoint.new(0.00, Color3.fromRGB(32,143,252)), ColorSequenceKeypoint.new(0.50, Color3.fromRGB(101, 185, 255)), ColorSequenceKeypoint.new(1.00, Color3.fromRGB(32,143,252))}
                UIGradientBtn.Name = "UIGradientBtn"
                UIGradientBtn.Parent = Btn
                
                TextLabelBtn.Name = "TextLabelBtn"
                TextLabelBtn.Parent = Btn
                TextLabelBtn.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                TextLabelBtn.BackgroundTransparency = 1.000
                TextLabelBtn.Size = UDim2.new(0, 296, 0, 30)
                TextLabelBtn.Font = Enum.Font.GothamBold
                TextLabelBtn.Text = text
                TextLabelBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
                TextLabelBtn.TextSize = 14.000
                
                ButtonBtn.Name = "ButtonBtn"
                ButtonBtn.Parent = FrameButton
                ButtonBtn.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                ButtonBtn.BackgroundTransparency = 1.000
                ButtonBtn.Size = UDim2.new(0, 328, 0, 31)
                ButtonBtn.Font = Enum.Font.SourceSans
                ButtonBtn.Text = ""
                ButtonBtn.TextColor3 = Color3.fromRGB(0, 0, 0)
                ButtonBtn.TextSize = 14.000
                
                ButtonBtn.MouseButton1Click:Connect(function()
                    if Tabtoggle == false then
                        CircleAnim(Btn, Color3.fromRGB(255,255,255), Color3.fromRGB(255,255,255))
                        TextLabelBtn.TextSize = 0
                        TweenService:Create(
                            TextLabelBtn,
                            TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {TextSize = 14}
                        ):Play()
                        callback()
                    end
                end)
            end
            function main:AddLine()
                local LineFrame = Instance.new("Frame")
				local Line = Instance.new("Frame")
				local LineUIGradient = Instance.new("UIGradient")

				LineFrame.Name = "LineFrame"
				LineFrame.Parent = ScrollingMainFramePage
				LineFrame.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				LineFrame.BackgroundTransparency = 1.000
				LineFrame.Size = UDim2.new(0, 328, 0, 21)

				Line.Name = "LineMain"
				Line.Parent = LineFrame
				Line.AnchorPoint = Vector2.new(0.5, 0.5)
				Line.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				Line.BorderSizePixel = 0
				Line.Position = UDim2.new(0.5, 0, 0.428571433, 0)
				Line.Size = UDim2.new(0, 296, 0, 2)

				LineUIGradient.Color = ColorSequence.new{ColorSequenceKeypoint.new(0.00, Color3.fromRGB(15, 15, 15)), ColorSequenceKeypoint.new(0.16, Color3.fromRGB(0,90,165)), ColorSequenceKeypoint.new(0.51, Color3.fromRGB(32,143,252)), ColorSequenceKeypoint.new(0.85, Color3.fromRGB(0,90,165)), ColorSequenceKeypoint.new(1.00, Color3.fromRGB(15, 15, 15))}
				LineUIGradient.Name = "LineUIGradient"
				LineUIGradient.Parent = Line
            end
            function main:AddLabel(text)
                local LabelFrame = Instance.new("Frame")
                local textlabel = Instance.new("TextLabel")
                local labelfunc = {}


                LabelFrame.Name = "LabelFrame"
                LabelFrame.Parent = ScrollingMainFramePage
                LabelFrame.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                LabelFrame.BackgroundTransparency = 1.000
                LabelFrame.ClipsDescendants = true
                LabelFrame.Size = UDim2.new(0, 328, 0, 32)

                textlabel.Name = "TextToggle"
                textlabel.Parent = LabelFrame
                textlabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                textlabel.BackgroundTransparency = 1.000
                textlabel.Position = UDim2.new(0.090, 0, 0, 0)
                textlabel.Size = UDim2.new(0, 192, 0, 32)
                textlabel.Font = Enum.Font.GothamBold
                textlabel.Text = text
                textlabel.TextColor3 = Color3.fromRGB(255, 255, 255)
                textlabel.TextSize = 14.000
                textlabel.TextXAlignment = Enum.TextXAlignment.Left

                function labelfunc:Refresh(newtext)
                    textlabel.Text = newtext
                end

                return labelfunc
            end
            function main:AddToggle(text,default,callback)
                local ToggleFrame = Instance.new("Frame")
                local TextToggle = Instance.new("TextLabel")
                local Toggle = Instance.new("Frame")
                local UICornerToggle = Instance.new("UICorner")
                local Tgle = Instance.new("Frame")
                local UICornerTgle = Instance.new("UICorner")
                local ButtonToggle = Instance.new("TextButton")
                default = default or false
                local toggle = default
                local RetrunStatsToggle = {}
                local lock = false

                ToggleFrame.Name = "ToggleFrame"
                ToggleFrame.Parent = ScrollingMainFramePage
                ToggleFrame.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                ToggleFrame.BackgroundTransparency = 1.000
                ToggleFrame.ClipsDescendants = true
                ToggleFrame.Size = UDim2.new(0, 328, 0, 32)

                TextToggle.Name = "TextToggle"
                TextToggle.Parent = ToggleFrame
                TextToggle.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                TextToggle.BackgroundTransparency = 1.000
                TextToggle.Position = UDim2.new(0.104, 0, 0, 0)
                TextToggle.Size = UDim2.new(0, 192, 0, 32)
                TextToggle.Font = Enum.Font.GothamBold
                TextToggle.Text = text
                TextToggle.TextColor3 = Color3.fromRGB(255, 255, 255)
                TextToggle.TextSize = 14.000
                TextToggle.TextXAlignment = Enum.TextXAlignment.Left

                Toggle.Name = "Toggle"
                Toggle.Parent = ToggleFrame
                Toggle.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
                Toggle.BorderSizePixel = 0
                Toggle.Position = UDim2.new(0.713414609, 0, 0.09375, 0)
                Toggle.Size = UDim2.new(0, 56, 0, 25)

                UICornerToggle.CornerRadius = UDim.new(0, 9999)
                UICornerToggle.Name = "UICornerToggle"
                UICornerToggle.Parent = Toggle

                Tgle.Name = "Tgle"
                Tgle.Parent = Toggle
                Tgle.BackgroundColor3 = Color3.fromRGB(32,143,252)
                Tgle.Position = UDim2.new(0, 1, 0, 2)
                Tgle.Size = UDim2.new(0, 22, 0, 22)

                UICornerTgle.CornerRadius = UDim.new(0, 9999)
                UICornerTgle.Name = "UICornerTgle"
                UICornerTgle.Parent = Tgle

                ButtonToggle.Name = "ButtonToggle"
                ButtonToggle.Parent = ToggleFrame
                ButtonToggle.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                ButtonToggle.BackgroundTransparency = 1.000
                ButtonToggle.Size = UDim2.new(0, 328, 0, 32)
                ButtonToggle.Font = Enum.Font.SourceSans
                ButtonToggle.Text = ""
                ButtonToggle.TextColor3 = Color3.fromRGB(0, 0, 0)
                ButtonToggle.TextSize = 14.000


                if default == false then
                    toggle = false
                    TweenService:Create(
                        Tgle,
                        TweenInfo.new(0.2,Enum.EasingStyle.Back,Enum.EasingDirection.Out),
                        {Position = UDim2.new(0, 1.5, 0, 2)}
                    ):Play()
                    wait()
                    TweenService:Create(
                        Tgle,
                        TweenInfo.new(0.2,Enum.EasingStyle.Back,Enum.EasingDirection.Out),
                        {Size = UDim2.new(0, 32, 0, 22)}
                    ):Play()
                    wait()
                    TweenService:Create(
                        Tgle,
                        TweenInfo.new(0.2,Enum.EasingStyle.Back,Enum.EasingDirection.Out),
                        {Size = UDim2.new(0, 22, 0, 22)}
                    ):Play()
                    wait()
                    TweenService:Create(
                        Tgle,
                        TweenInfo.new(0.2,Enum.EasingStyle.Back,Enum.EasingDirection.Out),
                        {Position = UDim2.new(0, 1, 0, 2)}
                    ):Play()
                    callback(toggle)
                end
                if default == true then
                    toggle = true
                    TweenService:Create(
                        Tgle,
                        TweenInfo.new(0.2,Enum.EasingStyle.Back,Enum.EasingDirection.Out),
                        {Size = UDim2.new(0, 32, 0, 22)}
                    ):Play()
                    wait()
                    TweenService:Create(
                        Tgle,
                        TweenInfo.new(0.2,Enum.EasingStyle.Back,Enum.EasingDirection.Out),
                        {Position = UDim2.new(0, 30, 0, 2)}
                    ):Play()
                    wait()
                    TweenService:Create(
                        Tgle,
                        TweenInfo.new(0.2,Enum.EasingStyle.Back,Enum.EasingDirection.Out),
                        {Size = UDim2.new(0, 22, 0, 22)}
                    ):Play()
                    wait()
                    TweenService:Create(
                        Tgle,
                        TweenInfo.new(0.2,Enum.EasingStyle.Back,Enum.EasingDirection.Out),
                        {Position = UDim2.new(0, 33, 0, 2)}
                    ):Play()
                    callback(toggle)
                end

                ButtonToggle.MouseButton1Click:Connect(function()
                    if Tabtoggle == false then
                        if toggle == false and lock == false then
                            toggle = true
                            TweenService:Create(
                                Tgle,
                                TweenInfo.new(0.2,Enum.EasingStyle.Back,Enum.EasingDirection.Out),
                                {Size = UDim2.new(0, 32, 0, 22)}
                            ):Play()
                            wait()
                            TweenService:Create(
                                Tgle,
                                TweenInfo.new(0.2,Enum.EasingStyle.Back,Enum.EasingDirection.Out),
                                {Position = UDim2.new(0, 30, 0, 2)}
                            ):Play()
                            wait()
                            TweenService:Create(
                                Tgle,
                                TweenInfo.new(0.2,Enum.EasingStyle.Back,Enum.EasingDirection.Out),
                                {Size = UDim2.new(0, 22, 0, 22)}
                            ):Play()
                            wait()
                            TweenService:Create(
                                Tgle,
                                TweenInfo.new(0.2,Enum.EasingStyle.Back,Enum.EasingDirection.Out),
                                {Position = UDim2.new(0, 33, 0, 2)}
                            ):Play()
                            callback(toggle)
                        elseif toggle == true and lock == false then
                            toggle = false
                            TweenService:Create(
                                Tgle,
                                TweenInfo.new(0.2,Enum.EasingStyle.Back,Enum.EasingDirection.Out),
                                {Position = UDim2.new(0, 1.5, 0, 2)}
                            ):Play()
                            wait()
                            TweenService:Create(
                                Tgle,
                                TweenInfo.new(0.2,Enum.EasingStyle.Back,Enum.EasingDirection.Out),
                                {Size = UDim2.new(0, 32, 0, 22)}
                            ):Play()
                            wait()
                            TweenService:Create(
                                Tgle,
                                TweenInfo.new(0.2,Enum.EasingStyle.Back,Enum.EasingDirection.Out),
                                {Size = UDim2.new(0, 22, 0, 22)}
                            ):Play()
                            wait()
                            TweenService:Create(
                                Tgle,
                                TweenInfo.new(0.2,Enum.EasingStyle.Back,Enum.EasingDirection.Out),
                                {Position = UDim2.new(0, 1, 0, 2)}
                            ):Play()
                            callback(toggle)
                        end
                    end
                end
                )

                local lockerframe = Instance.new("Frame")

                lockerframe.Name = "lockerframe"
                lockerframe.Parent = ToggleFrame
                lockerframe.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
                lockerframe.BackgroundTransparency = 1
                lockerframe.BorderSizePixel = 0
                lockerframe.Size = UDim2.new(0, 300, 0, 32)
                lockerframe.Position = UDim2.new(0.5, 0, 0.5, 0)
                lockerframe.AnchorPoint = Vector2.new(0.5, 0.5)
    
                local LockerImageLabel = Instance.new("ImageLabel")
    
                LockerImageLabel.Parent = lockerframe
                LockerImageLabel.BackgroundTransparency = 1.000
                LockerImageLabel.BorderSizePixel = 0
                LockerImageLabel.Position = UDim2.new(0.5, 0, 0.5, 0)
                LockerImageLabel.AnchorPoint = Vector2.new(0.5, 0.5)
                LockerImageLabel.Size = UDim2.new(0, 0, 0, 0)
                LockerImageLabel.Image = "http://www.roblox.com/asset/?id=3926305904"
                LockerImageLabel.ImageRectOffset = Vector2.new(404, 364)
                LockerImageLabel.ImageRectSize = Vector2.new(36, 36)
                LockerImageLabel.ImageColor3 = Color3.fromRGB(255,25,25)

                function RetrunStatsToggle:Lock()
                    TweenService:Create(
                        lockerframe,
                        TweenInfo.new(.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out,0.1),
                        {BackgroundTransparency = 0.7}
                    ):Play()
                    TweenService:Create(
                        LockerImageLabel,
                        TweenInfo.new(.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out,0.1),
                        {Size = UDim2.new(0, 30, 0, 30)}
                    ):Play()
                    lock = true
                end

                function RetrunStatsToggle:ChangeStateTrue()
                    if toggle == false and lock == false then
                        toggle = true
                        TweenService:Create(
                            Tgle,
                            TweenInfo.new(0.2,Enum.EasingStyle.Back,Enum.EasingDirection.Out),
                            {Size = UDim2.new(0, 32, 0, 22)}
                        ):Play()
                        wait()
                        TweenService:Create(
                            Tgle,
                            TweenInfo.new(0.2,Enum.EasingStyle.Back,Enum.EasingDirection.Out),
                            {Position = UDim2.new(0, 30, 0, 2)}
                        ):Play()
                        wait()
                        TweenService:Create(
                            Tgle,
                            TweenInfo.new(0.2,Enum.EasingStyle.Back,Enum.EasingDirection.Out),
                            {Size = UDim2.new(0, 22, 0, 22)}
                        ):Play()
                        wait()
                        TweenService:Create(
                            Tgle,
                            TweenInfo.new(0.2,Enum.EasingStyle.Back,Enum.EasingDirection.Out),
                            {Position = UDim2.new(0, 33, 0, 2)}
                        ):Play()
                        callback(toggle)
                    end
                end

                function RetrunStatsToggle:ChangeStateFalse()
                    if toggle == true and lock == false then
                        toggle = false
                        TweenService:Create(
                            Tgle,
                            TweenInfo.new(0.2,Enum.EasingStyle.Back,Enum.EasingDirection.Out),
                            {Position = UDim2.new(0, 1.5, 0, 2)}
                        ):Play()
                        wait()
                        TweenService:Create(
                            Tgle,
                            TweenInfo.new(0.2,Enum.EasingStyle.Back,Enum.EasingDirection.Out),
                            {Size = UDim2.new(0, 32, 0, 22)}
                        ):Play()
                        wait()
                        TweenService:Create(
                            Tgle,
                            TweenInfo.new(0.2,Enum.EasingStyle.Back,Enum.EasingDirection.Out),
                            {Size = UDim2.new(0, 22, 0, 22)}
                        ):Play()
                        wait()
                        TweenService:Create(
                            Tgle,
                            TweenInfo.new(0.2,Enum.EasingStyle.Back,Enum.EasingDirection.Out),
                            {Position = UDim2.new(0, 1, 0, 2)}
                        ):Play()
                        callback(toggle)
                    end
                end
                function RetrunStatsToggle:Unlock()
                    TweenService:Create(
                        lockerframe,
                        TweenInfo.new(.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out,0.1),
                        {BackgroundTransparency = 1}
                    ):Play()
                    TweenService:Create(
                        LockerImageLabel,
                        TweenInfo.new(.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out,0.1),
                        {Size = UDim2.new(0, 0, 0, 0)}
                    ):Play()
                    lock = false
                end
                return RetrunStatsToggle
            end
            function main:AddSlider(text,min,max,set,callback)
                local sliderfunc = {}
                local SliderFrame = Instance.new("Frame")
                local ClickHere = Instance.new("TextButton")
                local Bar = Instance.new("Frame")
                local UICornerBar = Instance.new("UICorner")
                local BarValue = Instance.new("Frame")
                local UICornerBarValue = Instance.new("UICorner")
                local TextSlider = Instance.new("TextLabel")

                
                SliderFrame.Name = "SliderFrame"
                SliderFrame.Parent = ScrollingMainFramePage
                SliderFrame.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                SliderFrame.BackgroundTransparency = 1.000
                SliderFrame.Position = UDim2.new(0, 0, 0.292682916, 0)
                SliderFrame.Size = UDim2.new(0, 328, 0, 56)

                ClickHere.Name = "ClickHere"
                ClickHere.Parent = SliderFrame
                ClickHere.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                ClickHere.BackgroundTransparency = 1.000
                ClickHere.ClipsDescendants = true
                ClickHere.Position = UDim2.new(0.0853658542, 0, 0.642857134, 0)
                ClickHere.Size = UDim2.new(0, 271, 0, 5)
                ClickHere.Font = Enum.Font.SourceSans
                ClickHere.Text = ""
                ClickHere.TextColor3 = Color3.fromRGB(0, 0, 0)
                ClickHere.TextSize = 14.000

                Bar.Name = "Bar"
                Bar.Parent = ClickHere
                Bar.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                Bar.ClipsDescendants = true
                Bar.Size = UDim2.new(0, 271, 0, 5)

                UICornerBar.CornerRadius = UDim.new(0, 99)
                UICornerBar.Name = "UICornerBar"
                UICornerBar.Parent = Bar

                BarValue.Name = "BarValue"
                BarValue.Parent = ClickHere
                BarValue.BackgroundColor3 = Color3.fromRGB(32,143,252)
                BarValue.Size = UDim2.new((set or 0) / max, 0, 0, 5)

                UICornerBarValue.CornerRadius = UDim.new(0, 99)
                UICornerBarValue.Name = "UICornerBarValue"
                UICornerBarValue.Parent = BarValue

                TextSlider.Name = "TextSlider"
                TextSlider.Parent = SliderFrame
                TextSlider.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                TextSlider.BackgroundTransparency = 1.000
                TextSlider.Position = UDim2.new(0.0792682916, 0, 0.196428567, 0)
                TextSlider.Size = UDim2.new(0, 200, 0, 21)
                TextSlider.Font = Enum.Font.GothamBold
                TextSlider.Text = text.." : "..tostring(set and math.floor( (set / max) * (max - min) + min) or 0)
                TextSlider.TextColor3 = Color3.fromRGB(255, 255, 255)
                TextSlider.TextSize = 14.000
                TextSlider.TextXAlignment = Enum.TextXAlignment.Left


                
                local mouse = game.Players.LocalPlayer:GetMouse()
                local uis = game:GetService("UserInputService")


                if Value == nil then
                    Value = set
                    pcall(function()
                        callback(Value)
                    end)
                end

                
                ClickHere.MouseButton1Down:Connect(function()
                    if Tabtoggle == false then
                        Value = math.floor((((tonumber(max) - tonumber(min)) / 271) * BarValue.AbsoluteSize.X) + tonumber(min)) or 0
                        TweenService:Create(
                            BarValue,
                            TweenInfo.new(0.1,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {Size = UDim2.new(0, math.clamp(mouse.X - BarValue.AbsolutePosition.X, 0, 271), 0, 5)}
                        ):Play()
                        moveconnection = mouse.Move:Connect(function()
                            TextSlider.Text = text.." : "..Value
                            Value = math.floor((((tonumber(max) - tonumber(min)) / 271) * BarValue.AbsoluteSize.X) + tonumber(min))
                            TweenService:Create(
                                BarValue,
                                TweenInfo.new(0.1,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                                {Size = UDim2.new(0, math.clamp(mouse.X - BarValue.AbsolutePosition.X, 0, 271), 0, 5)}
                            ):Play()
                        end)
                        releaseconnection = uis.InputEnded:Connect(function(Mouse)
                            if Mouse.UserInputType == Enum.UserInputType.MouseButton1 then
                                Value = math.floor((((tonumber(max) - tonumber(min)) / 271) * BarValue.AbsoluteSize.X) + tonumber(min))
                                pcall(function()
                                    callback(Value)
                                    TextSlider.Text = text.." : "..Value
                                end)
                                TweenService:Create(
                                    BarValue,
                                    TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                                    {Size = UDim2.new(0, math.clamp(mouse.X - BarValue.AbsolutePosition.X, 0, 271), 0, 5)}
                                ):Play()
                                moveconnection:Disconnect()
                                releaseconnection:Disconnect()
                            end
                        end)
                    end
                end)

                function sliderfunc:Update(value)
                    TextSlider.Text = text.." : "..value
                    BarValue:TweenSize(UDim2.new((value or 0) / max, 0, 0, 5), "Out", "Sine", 0.2, true)
                    pcall(function()
                        callback(value)
                    end)
                end
                return sliderfunc
            end  
            function main:AddDropdown(text,option,callback)
                local DropFrame = Instance.new("Frame")
                
                local DropImage = Instance.new("ImageLabel")
                local DownFrame = Instance.new("Frame")
                local ScrollingDown = Instance.new("ScrollingFrame")
                local ItemList = Instance.new("UIListLayout")
                local Frame = Instance.new("Frame")
                local CornerFrae = Instance.new("UICorner")
                local ButtonDrop = Instance.new("TextButton")
                local DropToggle = false
                local RetrunDrop = {}

                DropFrame.Name = "DropFrame"
                DropFrame.Parent = ScrollingMainFramePage
                DropFrame.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                DropFrame.BackgroundTransparency = 1.000
                DropFrame.Position = UDim2.new(0, 0, 0.522648096, 0)
                DropFrame.Size = UDim2.new(0, 328, 0, 35)
                
                Frame.Parent = DropFrame
                Frame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
                Frame.BorderSizePixel = 0
                Frame.Position = UDim2.new(0.0457317084, 0, 0.0285714287, 0)
                Frame.Size = UDim2.new(0, 296, 0, 32)
                Frame.ClipsDescendants = true

                DropImage.Name = "DropImage"
                DropImage.Parent = Frame
                DropImage.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                DropImage.BackgroundTransparency = 1.000
                DropImage.Position = UDim2.new(0.871374369, 0, -0.012, 0)
                DropImage.Rotation = 180.000
                DropImage.Size = UDim2.new(0, 32, 0, 32)
                DropImage.Image = "rbxassetid://6031094670"
                
                
                
                CornerFrae.CornerRadius = UDim.new(0, 4)
                CornerFrae.Name = "CornerFrae"
                CornerFrae.Parent = Frame

                ButtonDrop.Name = "ButtonToggle"
                ButtonDrop.Parent = DropFrame
                ButtonDrop.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                ButtonDrop.BackgroundTransparency = 1.000
                ButtonDrop.Size = UDim2.new(0, 328, 0, 40)
                ButtonDrop.Font = Enum.Font.SourceSans
                ButtonDrop.Text = ""
                ButtonDrop.TextColor3 = Color3.fromRGB(0, 0, 0)
                ButtonDrop.TextSize = 14.000


                DownFrame.Name = "DownFrame"
                DownFrame.Parent = ScrollingMainFramePage
                DownFrame.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                DownFrame.BackgroundTransparency = 1.000
                DownFrame.BorderColor3 = Color3.fromRGB(27, 42, 53)
                DownFrame.ClipsDescendants = true
                DownFrame.Position = UDim2.new(0, 0, 0.1, 0)
                DownFrame.Size = UDim2.new(0, 328, 0, 0)

                ScrollingDown.Name = "ScrollingDown"
                ScrollingDown.Parent = DownFrame
                ScrollingDown.Active = true
                ScrollingDown.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                ScrollingDown.BackgroundTransparency = 1.000
                ScrollingDown.BorderSizePixel = 0
                ScrollingDown.Size = UDim2.new(0, 328, 0, 98)
                ScrollingDown.CanvasSize = UDim2.new(0, 0, 0, 0)
                ScrollingDown.ScrollBarThickness = 0
                ScrollingDown.BottomImage = ""
                ScrollingDown.TopImage = ""

                ItemList.Name = "ItemList"
                ItemList.Parent = ScrollingDown
                ItemList.SortOrder = Enum.SortOrder.LayoutOrder
                ItemList.Padding = UDim.new(0, 3)

                local SelectionScrollingUIPadding = Instance.new("UIPadding")
                SelectionScrollingUIPadding.Name = "SelectionScrollingUIPadding"
                SelectionScrollingUIPadding.Parent = ScrollingDown

                if set ~= nil then
                    callback(set)
                end

                for i,v in pairs(option) do
                    local ItemFrame = Instance.new("Frame")
                    local ItemButton = Instance.new("TextButton")
                    local UICorner = Instance.new("UICorner")


                    ItemFrame.Name = "ItemFrame"
                    ItemFrame.Parent = ScrollingDown
                    ItemFrame.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                    ItemFrame.BackgroundTransparency = 1.000
                    ItemFrame.Size = UDim2.new(0, 328, 0, 24)
    
                    ItemButton.Name = "ItemButton"
                    ItemButton.Parent = ItemFrame
                    ItemButton.BackgroundColor3 = Color3.fromRGB(32,143,252)
                    ItemButton.BorderSizePixel = 0
                    ItemButton.Position = UDim2.new(0.0701219514, 0, 0, 0)
                    ItemButton.Size = UDim2.new(0, 282, 0, 24)
                    ItemButton.AutoButtonColor = false
                    ItemButton.Font = Enum.Font.GothamBold
                    ItemButton.Text = tostring(v)
                    ItemButton.ClipsDescendants = true
                    ItemButton.TextColor3 = Color3.fromRGB(255, 255, 255)
                    ItemButton.TextSize = 14.000
    
                    UICorner.CornerRadius = UDim.new(0, 4)
                    UICorner.Parent = ItemButton

                    ItemButton.MouseButton1Down:Connect(function()
                        if Tabtoggle == false then
                            ItemButton.TextSize = 0
                            TweenService:Create(
                                ItemButton,
                                TweenInfo.new(.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out,0.1),
                                {TextSize = 12}
                            ):Play()
                            Text.Text = tostring(text.." : "..v)
                            CircleAnim(ItemButton,Color3.fromRGB(255,255,255),Color3.fromRGB(255,255,255))
                            
                            callback(v)
                            DropToggle = false
                            TweenService:Create(
                                DownFrame,
                                TweenInfo.new(0.2,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                                {Size = UDim2.new(0, 328, 0, 0)}
                            ):Play()
                            TweenService:Create(
                                DropImage,
                                TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                                {Rotation = 180}
                            ):Play()
                        end         
                    end)
                end 

                ScrollingDown.CanvasSize = UDim2.new(0,0,0,ItemList.AbsoluteContentSize.Y + 10)
                ButtonDrop.MouseButton1Click:Connect(function()
                    if Tabtoggle == false then
                        if DropToggle == false then
                            DropToggle = true
                            TweenService:Create(
                                DownFrame,
                                TweenInfo.new(0.2,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                                {Size = UDim2.new(0, 328, 0, 98)}
                            ):Play()
                            TweenService:Create(
                                DropImage,
                                TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                                {Rotation = 270}
                            ):Play()
                            CircleAnim(Frame,Color3.fromRGB(255,255,255),Color3.fromRGB(255,255,255))
                        elseif DropToggle == true then
                            DropToggle = false
                            TweenService:Create(
                                DownFrame,
                                TweenInfo.new(0.2,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                                {Size = UDim2.new(0, 328, 0, 0)}
                            ):Play()
                            TweenService:Create(
                                DropImage,
                                TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                                {Rotation = 180}
                            ):Play()
                            CircleAnim(Frame,Color3.fromRGB(255,255,255),Color3.fromRGB(255,255,255))
                        end
                    end
                end
                )

                function RetrunDrop:Add(newtext)
                    local ItemFrame = Instance.new("Frame")
                    local ItemButton = Instance.new("TextButton")
                    local UICorner = Instance.new("UICorner")


                    ItemFrame.Name = "ItemFrame"
                    ItemFrame.Parent = ScrollingDown
                    ItemFrame.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                    ItemFrame.BackgroundTransparency = 1.000
                    ItemFrame.Size = UDim2.new(0, 328, 0, 24)
    
                    ItemButton.Name = "ItemButton"
                    ItemButton.Parent = ItemFrame
                    ItemButton.BackgroundColor3 = Color3.fromRGB(32,143,252)
                    ItemButton.BorderSizePixel = 0
                    ItemButton.Position = UDim2.new(0.0701219514, 0, 0, 0)
                    ItemButton.Size = UDim2.new(0, 282, 0, 24)
                    ItemButton.AutoButtonColor = false
                    ItemButton.Font = Enum.Font.GothamBold
                    ItemButton.Text = tostring(newtext)
                    ItemButton.ClipsDescendants = true
                    ItemButton.TextColor3 = Color3.fromRGB(255, 255, 255)
                    ItemButton.TextSize = 14.000
    
                    UICorner.CornerRadius = UDim.new(0, 4)
                    UICorner.Parent = ItemButton

                    ItemButton.MouseButton1Down:Connect(function()
                        if Tabtoggle == false then
                            ItemButton.TextSize = 0
                            TweenService:Create(
                                ItemButton,
                                TweenInfo.new(.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out,0.1),
                                {TextSize = 12}
                            ):Play()
                            Text.Text = tostring(text.." : "..newtext)
                            CircleAnim(ItemButton,Color3.fromRGB(255,255,255),Color3.fromRGB(255,255,255))
                            
                            callback(newtext)
                            DropToggle = false
                            TweenService:Create(
                                DownFrame,
                                TweenInfo.new(0.2,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                                {Size = UDim2.new(0, 328, 0, 0)}
                            ):Play()
                            TweenService:Create(
                                DropImage,
                                TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                                {Rotation = 180}
                            ):Play()
                        end
                    end)

                    ScrollingDown.CanvasSize = UDim2.new(0,0,0,ItemList.AbsoluteContentSize.Y + 10)
                end

                function RetrunDrop:Clear()
                    Text.Text = tostring(text).." : "
                    DropToggle = false
                    TweenService:Create(
                        DownFrame,
                        TweenInfo.new(0.2,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                        {Size = UDim2.new(0, 328, 0, 0)}
                    ):Play()
                    TweenService:Create(
                        DropImage,
                        TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                        {Rotation = 180}
                    ):Play()
                    for i, v in next, ScrollingDown:GetChildren() do
                        if v:IsA("Frame") then
                            v:Destroy()
                        end
                    end
                    ScrollingDown.CanvasSize = UDim2.new(0,0,0,ItemList.AbsoluteContentSize.Y + 10)
                end
                return RetrunDrop
            end
            return main
        end
        return Tab
    end
    return Ui
end

-------------------------------------------------------------------------

local ScreenGui = Instance.new("ScreenGui")
local ImageButton = Instance.new("ImageButton")


ScreenGui.Parent = game.CoreGui
ScreenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

ImageButton.Parent = ScreenGui
ImageButton.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
ImageButton.BorderSizePixel = 0
ImageButton.Position = UDim2.new(0.120833337, 0, 0.0952890813, 0)
ImageButton.Size = UDim2.new(0, 30, 0, 30)
ImageButton.Draggable = true
ImageButton.Image = "http://www.roblox.com/asset/?id=11538629932"
ImageButton.MouseButton1Down:connect(function()
game:GetService("VirtualInputManager"):SendKeyEvent(true,305,false,game)
 game:GetService("VirtualInputManager"):SendKeyEvent(false,305,false,game)
end)

-----------------------------------------------------------------------------

local Win = Lib:Window("STEAL Hub")
local Main = Win:Tab("Main")
local A = Main:Page("")
local S = Main:Page("")


osfunc = A:AddLabel("TimeZone")

local function UpdateOS()
        local date = os.date("*t")
        local hour = (date.hour) % 24
        local ampm = hour < 12 and "AM" or "PM"
        local timezone = string.format("%02i:%02i:%02i %s", ((hour -1) % 12) + 1, date.min, date.sec, ampm)
        local datetime = string.format("%02d/%02d/%04d", date.day, date.month, date.year)
        osfunc:Refresh("day : "..datetime.." Time : "..timezone)
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
    Time:Refresh("Hour : "..Hour.." Minute : "..Minute.." Second : "..Second)
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
    Client:Refresh("Ping : "..Ping)
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
    C:Refresh("Fps : "..Fps)
end

spawn(function()
    while true do wait(.1)
        UpdateC()
    end
end)

pingfunc = A:AddLabel("Memory")

spawn(function()
        while game:GetService("RunService").RenderStepped:wait() do
            pingfunc:Refresh("Memory : " ..tostring(game:GetService("Stats").PerformanceStats.Memory:GetValueString()).." - "..tostring(game:GetService("Stats").PerformanceStats.NetworkReceived:GetValueString()).." - "..tostring(game:GetService("Stats").PerformanceStats.Ping:GetValueString()))
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
            end
        elseif World3 then
            if MyLevel == 1500 or MyLevel <= 1524 then
                Mon = "Pirate Millionaire [Lv. 1500]"
                LevelQuest = 1
                NameQuest = "PiratePortQuest"
                NameMon = "Pirate Millionaire"
                PUK = CFrame.new(-290.674988, 34.7821121, 5417.57666, -0.959131062, 7.87279077e-08, 0.282962203, 6.99472977e-08, 1, -4.11336849e-08, -0.282962203, -1.96601544e-08, -0.959131062)
                CFrameQuest = CFrame.new(-290.074677, 42.9034653, 5581.58984, 0.965929627, -0, -0.258804798, 0, 1, -0, 0.258804798, 0, 0.965929627)
            elseif MyLevel == 1525 or MyLevel <= 1574 then
                Mon = "Pistol Billionaire [Lv. 1525]"
                LevelQuest = 2
                NameQuest = "PiratePortQuest"
                NameMon = "Pistol Billionaire"
                PUK = CFrame.new(-387.624237, 74.2720413, 5851.84473, -0.990750372, -6.79122536e-08, 0.135697171, -7.2516066e-08, 1, -2.89841076e-08, -0.135697171, -3.85562409e-08, -0.990750372)
                CFrameQuest = CFrame.new(-290.074677, 42.9034653, 5581.58984, 0.965929627, -0, -0.258804798, 0, 1, -0, 0.258804798, 0, 0.965929627)
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
             statsfarm:Refresh("AutoFarm : ✅")
              end
              end
              end)
              end)
           
                        QuestStatus = A:AddLabel("")

spawn(function()
    while wait() do
        CheckQuest(NameQuest)
        QuestStatus:Refresh("Quest : "..NameQuest)
end
end)

 Questlv = A:AddLabel("")

spawn(function()
    while wait() do
        CheckQuest(LevelQuest)
        Questlv:Refresh("LevelQuest : "..LevelQuest)
end
end)

 NamemonStatus = A:AddLabel("")

spawn(function()
    while wait() do
        CheckQuest(Mon)
        NamemonStatus:Refresh("Mon & Level Mon : "..Mon)
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
    
    S:AddToggle("Black Screen",nil,function(a)
    _G.Bl = a
    if _G.Bl == true then
    game:GetService("Players").LocalPlayer.PlayerGui.Main.Blackscreen.Size = UDim2.new(500, 0, 500, 500)
elseif _G.Bl == false then
    game:GetService("Players").LocalPlayer.PlayerGui.Main.Blackscreen.Size = UDim2.new(0, 0, 500, 500)
end
end)

    spawn(function()
      while wait() do
      if _G.Bl then
        for i, v in pairs(game.Workspace["_WorldOrigin"]:GetChildren()) do
            if v.Name == "CurvedRing" or v.Name == "SlashHit" or v.Name == "DamageCounter" or v.Name == "SwordSlash" or v.Name == "SlashTail" or v.Name == "Sounds" then
                v:Destroy() 
            end
        end
    end
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
                    PlayerName:Refresh("PlayerName : " .. game.Players.localPlayer.Name)
                end
            end
        )
    end
)
    
    local locallv = S:AddLabel("Level")
    
   
    spawn(function()
        while wait() do
            pcall(function()
                locallv:Refresh("Level :".." "..game:GetService("Players").LocalPlayer.Data.Level.Value)
            end)
        end
    end)
    
    local localrace = S:AddLabel("Race")
    
    spawn(function()
        while wait() do
            pcall(function()
                localrace:Refresh("Race :".." "..game:GetService("Players").LocalPlayer.Data.Race.Value)
            end)
        end
    end)
    
    local localbeli = S:AddLabel("Beli")
    
    spawn(function()
        while wait() do
            pcall(function()
                localbeli:Refresh("Beli :".." "..game:GetService("Players").LocalPlayer.Data.Beli.Value)
            end)
        end
    end)
    
    local localfrag = S:AddLabel("Fragment")
    
    spawn(function()
        while wait() do
            pcall(function()
                localfrag:Refresh("Fragments :".." "..game:GetService("Players").LocalPlayer.Data.Fragments.Value)
            end)
        end
    end)
    
    
    local localexp = S:AddLabel("ExP")
    
    spawn(function()
        while wait() do
            pcall(function()
                localexp:Refresh("ExP Points :".." "..game:GetService("Players").LocalPlayer.Data.Exp.Value)
            end)
        end
    end)
    
    local localstat = S:AddLabel("Stats Points")
    
    spawn(function()
        while wait() do
            pcall(function()
                localstat:Refresh("Stats Points :".." "..game:GetService("Players").LocalPlayer.Data.Points.Value)
            end)
        end
    end)
    
    local localbountyhornor = S:AddLabel("Bounty")
    
    spawn(function()
        while wait() do
            pcall(function()
                localbountyhornor:Refresh("Bounty / Honor :".." "..game:GetService("Players").LocalPlayer.leaderstats["Bounty/Honor"].Value)
            end)
        end
    end)
    
    local localDevil = S:AddLabel("Devil Fruit")
    
    spawn(function()
        while wait() do
            pcall(function()
                if game:GetService("Players").LocalPlayer.Character:FindFirstChild(game:GetService("Players").LocalPlayer.Data.DevilFruit.Value) or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild(game:GetService("Players").LocalPlayer.Data.DevilFruit.Value) then
                    localDevil:Refresh("Devil Fruit :".." "..game:GetService("Players").LocalPlayer.Data.DevilFruit.Value)
                else
                    localDevil:Refresh("Not Have Devil Fruit")
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
                    Health:Refresh("Health : " .. game.Players.LocalPlayer.Character.Humanoid.Health)
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
                    Energy:Refresh("Stamina : " .. game.Players.LocalPlayer.Character.Energy.Value)
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
      If _G.Aa then 
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
                        WolrdSet3:Refresh("Wolrd : 1 " .. "✅")
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
                        WolrdSet:Refresh("Wolrd : 2 " .. "✅")
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
                        WolrdSet1:Refresh("Wolrd : 3 " .. "✅")
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
                            Saber:Refresh("✅ : Saber")
                        end
                        if v.Name == "Rengoku" then
                            Rengoku:Refresh("✅ : Rengoku")
                        end
                        if v.Name == "Midnight Blade" then
                            MidnightBlade:Refresh("✅ : Midnight Blade")
                        end
                        if v.Name == "Dragon Trident" then
                            DragonTrident:Refresh("✅ : Dragon Trident")
                        end
                        if v.Name == "Yama" then
                            Yama:Refresh("✅ : Yama")
                        end
                        if v.Name == "Buddy Sword" then
                            BuddySword:Refresh("✅ : Buddy Sword")
                        end
                        if v.Name == "Canvander" then
                            Canvander:Refresh("✅ : Canvander")
                        end
                        if v.Name == "Twin Hooks" then
                            TwinHooks:Refresh("✅ : Twin Hooks")
                        end
                        if v.Name == "Spikey Trident" then
                            SpikeyTrident:Refresh("✅ : Spikey Trident")
                        end
                        if v.Name == "Hallow Scythe" then
                            HallowScythe:Refresh("✅ : Hallow Scythe")
                        end
                        if v.Name == "Dark Dagger" then
                            DarkDagger:Refresh("✅ : Dark Dagger")
                        end
                        if v.Name == "Tushita" then
                            Tushita:Refresh("✅ : Tushita")
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
                            Kabucha:Refresh("✅ : Kabucha")
                        end
                        if v.Name == "Acidum Rifle" then
                            AcidumRifle:Refresh("✅ : Acidum Rifle")
                        end
                        if v.Name == "Bizarre Rifle" then
                            BizarreRifle:Refresh("✅ : Bizarre Rifle")
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
                BartiloQuest:Refresh("✅ : Bartilo Quest")
            end
            if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("GetUnlockables").FlamingoAccess == nil then
            else
                DonSwanQuest:Refresh("✅ : Don Swan Quest")
            end
            if game:GetService("ReplicatedStorage").Remotes["CommF_"]:InvokeServer("ZQuestProgress", "Check") == 1 then
                KillDonSwan:Refresh("✅ : Kill Don Swan")
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
                            Shisui:Refresh("✅ : Shisui")
                        end
                        if v.Name == "Saddi" then
                            Saddi:Refresh("✅ : Saddi")
                        end
                        if v.Name == "Wando" then
                            Wando:Refresh("✅ : Wando")
                        end
                        if v.Name == "True Triple Katana" then
                            TrueTripleKatana:Refresh("✅ : True Triple Katana")
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
                Superhuman:Refresh("✅ : Superhuman")
            end
            if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDeathStep", true) == 1 then
                DeathStep:Refresh("✅ : Death Step")
            end
            if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySharkmanKarate", true) == 1 then
                SharkmanKarate:Refresh("✅ : Sharkman Karate")
            end
            if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyElectricClaw", true) == 1 then
                ElectricClaw:Refresh("✅ : Electric Claw")
            end
            if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDragonTalon", true) == 1 then
                DragonTalon:Refresh("✅ : Dragon Talon")
            end
            if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyGodhuman", true) == 1 then
                GodHuman:Refresh("✅ : God Human")
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
