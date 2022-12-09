


if game.CoreGui:FindFirstChild("BlackTrap") then
    game.CoreGui:FindFirstChild("BlackTrap"):Destroy()
end

local Blacklib = {}
local UserInputService = game:GetService("UserInputService")
local TweenService = game:GetService("TweenService")
local RunService = game:GetService("RunService")
local LocalizationService = game:GetService("LocalizationService")
local LocalPlayer = game:GetService("Players").LocalPlayer
local Mouse = LocalPlayer:GetMouse()
local NameID = LocalPlayer.Name


_G.WindowBackgroundColor = Color3.fromRGB(12,12,12)
_G.BackgroundItemColor = Color3.fromRGB(20, 20, 20)
_G.TabWindowColor = Color3.fromRGB(30, 30, 30)
_G.ContainerColor = Color3.fromRGB(30, 30, 30)
_G.TitleTextColor = Color3.fromRGB(150, 150, 150)
_G.ImageColor = Color3.fromRGB(150, 150, 150)
_G.LineThemeColor = Color3.fromRGB(150, 150, 150)
_G.TabTextColor = Color3.fromRGB(150, 150, 150)
_G.TabImageColor = Color3.fromRGB(150, 150, 150)
_G.TabThemeColor = Color3.fromRGB(250, 0, 0)
_G.SectionColor = Color3.fromRGB(150, 150, 150)
_G.SectionImageColor = Color3.fromRGB(150, 150, 150)
_G.SectionTextColor = Color3.fromRGB(150, 150, 150)
_G.SectionOn = Color3.fromRGB(0, 250, 0)


function Blacklib:Window()
    local osfunc = {}
    local titlefunc = {}
    local pingfunc = {}
    local timefunc = {}
    local Points = Instance.new("Frame")
    local BlackTrap = Instance.new("ScreenGui")
    local PlayTime = Instance.new("TextLabel")
    local PlayTimeCorner = Instance.new("UICorner")
    local WindowFrame = Instance.new("Frame")
    local WindowCorner = Instance.new("UICorner")
    local WindowStroke = Instance.new("UIStroke")
    local BlackImage = Instance.new("ImageLabel")
    local Space = Instance.new("TextLabel")
    local Space2 = Instance.new("TextLabel")
    local BlackTitle = Instance.new("TextLabel")
    local ServerTime = Instance.new("TextLabel")
    local Pinged = Instance.new("TextLabel")
    local CloseButton = Instance.new("TextButton")
    
    -- Propertiers --
    BlackTrap.Name = "BlackTrap"
    BlackTrap.Parent = game.CoreGui
    BlackTrap.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
    
    Points.Name = "Points"
    Points.Parent = BlackTrap
    Points.BackgroundColor3 = _G.WindowBackgroundColor
    Points.BackgroundTransparency = 1.000
    Points.Size = UDim2.new(0, 800, 0, 600)
    Points.Position = UDim2.new(0, 0, 0, 0)
    
    WindowFrame.Name = "WindowFrame"
    WindowFrame.Parent = Points
    WindowFrame.BackgroundColor3 = _G.WindowBackgroundColor
    WindowFrame.Position = UDim2.new(0, 220, 0, 30)
    WindowFrame.BorderSizePixel = 0
    WindowFrame.Size = UDim2.new(0, 550, 0, 0)
    WindowFrame.ClipsDescendants = true
    
    WindowFrame:TweenSize(UDim2.new(0, 550, 0, 350), Enum.EasingDirection.InOut, Enum.EasingStyle.Linear, .6, true)
    
    WindowCorner.Name = "WindowCorner"
    WindowCorner.Parent = WindowFrame
    WindowCorner.CornerRadius = UDim.new(0, 7)
    
    WindowStroke.Name = "WindowStroke"
    WindowStroke.Parent = WindowFrame
    WindowStroke.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
    WindowStroke.Color = Color3.fromRGB(120,120,120)
    WindowStroke.LineJoinMode = Enum.LineJoinMode.Round
    WindowStroke.Thickness = 1
    WindowStroke.Transparency = 0
    WindowStroke.Enabled = true
    WindowStroke.Archivable = true
    
    PlayTime.Name = "PlayTime"
    PlayTime.Parent = WindowFrame
    PlayTime.BackgroundColor3 = Color3.fromRGB(12,12,12)
    PlayTime.BackgroundTransparency = 1.000
    PlayTime.Position = UDim2.new(0, 3, 0, 324)
    PlayTime.Size = UDim2.new(0, 150, 0, 25)
    PlayTime.Font = Enum.Font.Code
    PlayTime.Text = ""
    PlayTime.TextSize = 13.000
    PlayTime.TextColor3 = Color3.fromRGB(180,180,180)
    PlayTime.TextXAlignment = Enum.TextXAlignment.Center
    
    PlayTimeCorner.Name = "PlayTimeCorner"
    PlayTimeCorner.Parent = PlayTime
    PlayTimeCorner.CornerRadius = UDim.new(0, 2)
    
    BlackImage.Name = "BlackImage"
    BlackImage.Parent = WindowFrame
    BlackImage.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
    BlackImage.BackgroundTransparency = 1.000
    BlackImage.Position = UDim2.new(0, 3, 0, 3)
    BlackImage.Size = UDim2.new(0, 25, 0, 25)
    BlackImage.Image = "rbxassetid://8666601749"
    BlackImage.ImageColor3 = Color3.fromRGB(0,220,0)
    
    BlackTitle.Name = "BlackTitle"
    BlackTitle.Parent = WindowFrame
    BlackTitle.BackgroundColor3 = _G.WindowBackgroundColor
    BlackTitle.BackgroundTransparency = 1.000
    BlackTitle.Position = UDim2.new(0, 33, 0, 3)
    BlackTitle.Size = UDim2.new(0, 50, 0, 25)
    BlackTitle.Font = Enum.Font.GothamBold
    BlackTitle.Text = ""
    BlackTitle.TextColor3 = Color3.fromRGB(180,180,180)
    BlackTitle.TextSize = 13.000
    BlackTitle.TextXAlignment = Enum.TextXAlignment.Left
    
    Space.Name = "Space"
    Space.Parent = WindowFrame
    Space.BackgroundColor3 = _G.WindowBackgroundColor
    Space.BackgroundTransparency = 1.000
    Space.Position = UDim2.new(0, 98, 0, 3)
    Space.Size = UDim2.new(0, 10, 0, 25)
    Space.Font = Enum.Font.GothamBold
    Space.Text = "|"
    Space.TextColor3 = Color3.fromRGB(0,150,0)
    Space.TextSize = 18.000
    
    ServerTime.Name = "ServerTime"
    ServerTime.Parent = WindowFrame
    ServerTime.BackgroundColor3 = _G.WindowBackgroundColor
    ServerTime.BackgroundTransparency = 1.000
    ServerTime.Position = UDim2.new(0, 115, 0, 3)
    ServerTime.Size = UDim2.new(0, 225, 0, 25)
    ServerTime.Font = Enum.Font.Code
    ServerTime.Text = ""
    ServerTime.TextSize = 13.000
    ServerTime.TextColor3 = Color3.fromRGB(180,180,180)
    ServerTime.TextXAlignment = Enum.TextXAlignment.Left
    
    Space2.Name = "Space2"
    Space2.Parent = WindowFrame
    Space2.BackgroundColor3 = _G.WindowBackgroundColor
    Space2.BackgroundTransparency = 1.000
    Space2.Position = UDim2.new(0, 276, 0, 3)
    Space2.Size = UDim2.new(0, 10, 0, 25)
    Space2.Font = Enum.Font.GothamBold
    Space2.Text = "|"
    Space2.TextColor3 = Color3.fromRGB(0,150,0)
    Space2.TextSize = 18.000
    
    Pinged.Name = "Pinged"
    Pinged.Parent = WindowFrame
    Pinged.BackgroundColor3 = _G.WindowBackgroundColor
    Pinged.BackgroundTransparency = 1.000
    Pinged.Position = UDim2.new(0, 295, 0, 3)
    Pinged.Size = UDim2.new(0, 225, 0, 25)
    Pinged.Font = Enum.Font.Code
    Pinged.Text = ""
    Pinged.TextSize = 13.000
    Pinged.TextColor3 = Color3.fromRGB(180,180,180)
    Pinged.TextXAlignment = Enum.TextXAlignment.Left
    
    CloseButton.Name = "CloseButton"
    CloseButton.Parent = WindowFrame
    CloseButton.BackgroundColor3 = _G.WindowBackgroundColor
    CloseButton.BackgroundTransparency = 1.000
    CloseButton.AutoButtonColor = false
    CloseButton.Position = UDim2.new(0, 525, 0, 3)
    CloseButton.Size = UDim2.new(0, 25, 0, 25)
    CloseButton.Font = Enum.Font.Gotham
    CloseButton.TextColor3 = Color3.fromRGB(0, 200, 0)
    CloseButton.Text = "×"
    CloseButton.Rotation = 0
    CloseButton.TextSize = 25.000
    
    -- Tab & Container --
    local LineWindow = Instance.new("Frame")
    local SpaceWindow = Instance.new("Frame")
    local TabWindow = Instance.new("ScrollingFrame")
    local TabWindowList = Instance.new("UIListLayout")
    local ContainerHold = Instance.new("Frame")
    local ContainerItem = Instance.new("Folder")
    local ContainerHoldCorner = Instance.new("UICorner")
    
    LineWindow.Name = "LineWindow"
    LineWindow.Parent = WindowFrame
    LineWindow.BackgroundColor3 = Color3.fromRGB(120,120,120)
    LineWindow.BorderSizePixel = 0
    LineWindow.Position = UDim2.new(0, 5, 0, 31)
    LineWindow.Size = UDim2.new(0, 540, 0, 1)
    
    SpaceWindow.Name = "SpaceWindow"
    SpaceWindow.Parent = WindowFrame
    SpaceWindow.BackgroundColor3 = Color3.fromRGB(120,120,120)
    SpaceWindow.BorderSizePixel = 0
    SpaceWindow.Position = UDim2.new(0, 156, 0, 41)
    SpaceWindow.Size = UDim2.new(0, 1, 0, 300)
    
    TabWindow.Name = "TabWindow"
    TabWindow.Parent = WindowFrame
    TabWindow.BackgroundColor3 = _G.TabWindowColor
    TabWindow.BackgroundTransparency = 1.000
    TabWindow.BorderSizePixel = 0
    TabWindow.Position = UDim2.new(0, 3, 0, 40)
    TabWindow.Size = UDim2.new(0, 150, 0, 0)
    TabWindow.ScrollBarThickness = 0
    TabWindow.ClipsDescendants = true
    
    TabWindow:TweenSize(UDim2.new(0, 150, 0, 275), Enum.EasingDirection.InOut, Enum.EasingStyle.Linear, 10.0, true)
    
    TabWindowList.Name = "TabWindowList"
    TabWindowList.Parent = TabWindow
    TabWindowList.FillDirection = Enum.FillDirection.Vertical
    TabWindowList.SortOrder = Enum.SortOrder.LayoutOrder
    TabWindowList.Padding = UDim.new(0, 2)
    TabWindowList.VerticalAlignment = Enum.VerticalAlignment.Top
    
    ContainerHold.Name = "ContainerHold"
    ContainerHold.Parent = WindowFrame
    ContainerHold.BackgroundColor3 = _G.ContainerColor
    ContainerHold.BackgroundTransparency = 1.000
    ContainerHold.BorderSizePixel = 0
    ContainerHold.Position = UDim2.new(0, 160, 0, 40)
    ContainerHold.Size = UDim2.new(0, 387, 0, 304)
    
    ContainerHoldCorner.Name = "ContainerHoldCorner"
    ContainerHoldCorner.Parent = ContainerHold
    ContainerHoldCorner.CornerRadius = UDim.new(0, 5)
    
    ContainerItem.Name = "ContainerItem"
    ContainerItem.Parent = ContainerHold
    
    TabWindow.CanvasSize = UDim2.new(0, 0, 0, 0 + TabWindowList.AbsoluteContentSize.Y)
    TabWindowList:GetPropertyChangedSignal("AbsoluteContentSize"):Connect(function()
        TabWindow.CanvasSize = UDim2.new(0, 0, 0, 0 + TabWindowList.AbsoluteContentSize.Y)
    end)
    
    -- Window Script --
    local gui = WindowFrame
    local dragging
    local dragInput
    local dragStart
    local startPos
    local function update(input)
        local delta = input.Position - dragStart
        gui.Position = UDim2.new(startPos.X.Scale, startPos.X.Offset + delta.X, startPos.Y.Scale, startPos.Y.Offset + delta.Y)
    end
    gui.InputBegan:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
            dragging = true
            dragStart = input.Position
            startPos = gui.Position
            
            input.Changed:Connect(function()
                if input.UserInputState == Enum.UserInputState.End then
                    dragging = false
                end
            end)
        end
    end)
    gui.InputChanged:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch then
            dragInput = input
        end
    end)
    UserInputService.InputChanged:Connect(function(input)
        if input == dragInput and dragging then
            update(input)
        end
    end)
    
    -- Script --
    local closetog = false
    CloseButton.MouseButton1Click:Connect(function()
        if closetog == true then
            game.TweenService:Create(WindowFrame, TweenInfo.new(0.4, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
                {Size = UDim2.new(0, 550, 0, 350)}
                ):Play()
            game.TweenService:Create(CloseButton, TweenInfo.new(0.12, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
                {Rotation = 0}
                ):Play()
        else
            game.TweenService:Create(WindowFrame, TweenInfo.new(0.4, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
                {Size = UDim2.new(0, 550, 0, 30)}
                ):Play()
            game.TweenService:Create(CloseButton, TweenInfo.new(0.12, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
                {Rotation = 45}
                ):Play()
        end
        closetog = not closetog
    end)
    
    function osfunc:Refresh(textadd)
        ServerTime.Text = textadd
    end
    function titlefunc:Refresh(text)
        BlackTitle.Text = text
    end
    function pingfunc:Refresh(newtext)
        Pinged.Text = newtext
    end
    function timefunc:Refresh(newtime)
        PlayTime.Text = newtime
    end
    
    local function UpdateTime()
        local GameTime = math.floor(workspace.DistributedGameTime+0.5)
        local Day = math.floor(GameTime/(60^3))%24
        local Hour = math.floor(GameTime/(60^2))%24
        local Minute = math.floor(GameTime/(60^1))%60
        local Second = math.floor(GameTime/(60^0))%60
        
        timefunc:Refresh("Timer = "..Day.."."..Hour.. "."..Minute.. "."..Second)
    end
    spawn(function()
        while true do
            UpdateTime()
            game:GetService("RunService").RenderStepped:Wait()
        end
    end)
    
    spawn(function()
        while game:GetService("RunService").RenderStepped:wait() do
            pingfunc:Refresh(tostring(game:GetService("Stats").PerformanceStats.Memory:GetValueString()).." - "..tostring(game:GetService("Stats").PerformanceStats.NetworkReceived:GetValueString()).." - "..tostring(game:GetService("Stats").PerformanceStats.Ping:GetValueString()))
        end
    end)
    
    local function UpdateOS()
        local date = os.date("*t")
        local hour = (date.hour) % 24
        local ampm = hour < 12 and "AM" or "PM"
        local timezone = string.format("%02i:%02i:%02i %s", ((hour -1) % 12) + 1, date.min, date.sec, ampm)
        local datetime = string.format("%02d/%02d/%04d", date.day, date.month, date.year)
        osfunc:Refresh(datetime.." - "..timezone)
    end
    spawn(function()
        while true do
            UpdateOS()
            game:GetService("RunService").RenderStepped:Wait()
        end
    end)
    spawn(function()
        while task.wait() do
            titlefunc:Refresh("") wait(.2) titlefunc:Refresh("S") wait(.2) titlefunc:Refresh("ST") wait(.2) titlefunc:Refresh("STE") wait(.2) titlefunc:Refresh("STEA") wait(.2) titlefunc:Refresh("STEAL") wait(.9) titlefunc:Refresh("STEA") wait(.2) titlefunc:Refresh("STE") wait(.2) titlefunc:Refresh("ST") wait(.2) titlefunc:Refresh("S") wait(.2) wait(.3)
        end
    end)
    -- End Windows --
    
    -- Notification --
    function Blacklib:Notification(titledesc, textdesc)
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
        
        -- Prop --
        NotificationHold.Name = "NotificationHold"
        NotificationHold.Parent = WindowFrame
        NotificationHold.BackgroundColor3 = _G.WindowBackgroundColor
        NotificationHold.BackgroundTransparency = 0.4
        NotificationHold.BorderSizePixel = 0
        NotificationHold.Size = UDim2.new(0, 550, 0, 350)
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
        NotificationFrame.BackgroundColor3 = Color3.fromRGB(30,30,30)
        NotificationFrame.BorderColor3 = _G.SectionColor
        NotificationFrame.BorderSizePixel = 0
        NotificationFrame.ClipsDescendants = true
        NotificationFrame.Position = UDim2.new(0, 275, 0, 175)
        NotificationFrame.Size = UDim2.new(0, 0, 0, 0)		
 
        NotificationFrame:TweenSize(UDim2.new(0, 400, 0, 250), Enum.EasingDirection.Out, Enum.EasingStyle.Quart, .6, true)
        
        NotifCorner.Name = "NotifCorner"
        NotifCorner.Parent = NotificationFrame
        NotifCorner.CornerRadius = UDim.new(0, 5)
        
        NotifHolderUIStroke.Name = "NotifHolderUIStroke"
        NotifHolderUIStroke.Parent = NotificationFrame
        NotifHolderUIStroke.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
        NotifHolderUIStroke.Color = Color3.fromRGB(180,180,180)
        NotifHolderUIStroke.LineJoinMode = Enum.LineJoinMode.Round
        NotifHolderUIStroke.Thickness = 0.5
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
        OkayBtn.Font = Enum.Font.Code
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
        NotificationTitle.Text = titledesc or "Notification"
        NotificationTitle.TextColor3 = Color3.fromRGB(180,180,180)
        NotificationTitle.TextSize = 20.000
        
        Line.Name = "Line"
        Line.Parent = NotificationFrame
        Line.BackgroundColor3 = Color3.fromRGB(180,180,180)
        Line.BorderSizePixel = 0
        Line.Position = UDim2.new(0, 5, 0, 43)
        Line.Size = UDim2.new(0, 390, 0, 1)
        
        NotificationDesc.Name = "NotificationDesc"
        NotificationDesc.Parent = NotificationFrame
        NotificationDesc.BackgroundColor3 = _G.SectionColor
        NotificationDesc.BackgroundTransparency = 1.000
        NotificationDesc.Position = UDim2.new(0, 10, 0, 70)
        NotificationDesc.Size = UDim2.new(0, 380, 0, 100)
        NotificationDesc.Font = Enum.Font.Code
        NotificationDesc.Text = textdesc
        NotificationDesc.TextColor3 = Color3.fromRGB(180,180,180)
        NotificationDesc.TextSize = 16.000
        NotificationDesc.TextWrapped = true
        NotificationDesc.TextXAlignment = Enum.TextXAlignment.Center
        NotificationDesc.TextYAlignment = Enum.TextYAlignment.Top
        
        -- Notification Script--
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
    
    coroutine.wrap(function()
        while wait() do
        end
    end)()
    -- End Notification --
    
    -- Tabs --
    local Tabs = {}
    function Tabs:Tab(tabtitle, img)
        local TabFrame = Instance.new("TextButton")
        local TabCorner = Instance.new("UICorner")
        local TabTitle = Instance.new("TextLabel")
        local TabImage = Instance.new("ImageLabel")
        
        -- Prop --
        TabFrame.Name = tabtitle or "TabFrame"
        TabFrame.Parent = TabWindow
        TabFrame.BackgroundColor3 = Color3.fromRGB(30,30,30)
        TabFrame.BackgroundTransparency = 0
        TabFrame.BorderSizePixel = 0
        TabFrame.AutoButtonColor = false
        TabFrame.Size = UDim2.new(0, 150, 0, 30)
        TabFrame.Font = Enum.Font.Code
        TabFrame.Text = ""
        TabFrame.TextColor3 = Color3.fromRGB(180,180,180)
        TabFrame.TextSize = 15.000
        
        TabCorner.Name = tabtitle or "TabCorner"
        TabCorner.Parent = TabFrame
        TabCorner.CornerRadius = UDim.new(0, 5)
        
        TabImage.Name = tabtitle or "TabImage"
        TabImage.Parent = TabFrame
        TabImage.BackgroundColor3 = _G.TabWindowColor
        TabImage.BackgroundTransparency = 1.000
        TabImage.Position = UDim2.new(0, 3, 0, 4)
        TabImage.Size = UDim2.new(0, 20, 0, 20)
        TabImage.Image = img or "rbxassetid://8666601749"
        TabImage.ImageColor3 = Color3.fromRGB(200,200,200)
        
        TabTitle.Name = tabtitle or "TabTitle"
        TabTitle.Parent = TabFrame
        TabTitle.BackgroundColor3 = _G.TabWindowColor
        TabTitle.BackgroundTransparency = 1.000
        TabTitle.BorderSizePixel = 0
        TabTitle.Position = UDim2.new(0, 30, 0, 2.5)
        TabTitle.Size = UDim2.new(0, 150, 0, 25)
        TabTitle.Font = Enum.Font.Code
        TabTitle.Text = tabtitle or "Put Tab Title"
        TabTitle.TextColor3 = Color3.fromRGB(180,180,180)
        TabTitle.TextSize = 13.000
        TabTitle.TextXAlignment = Enum.TextXAlignment.Left
        
        -- Container --
        local Container = Instance.new("ScrollingFrame")
        local ContainerLayout = Instance.new("UIListLayout")
        
        -- Prop --
        Container.Name = "Container"
        Container.Parent = ContainerItem
        Container.Active = true
        Container.AnchorPoint = Vector2.new(0, 0)
        Container.BackgroundColor3 = _G.ContainerColor
        Container.BackgroundTransparency = 1.000
        Container.Position = UDim2.new(0, 0, 0, 0)
        Container.Size = UDim2.new(0, 387, 0, 0)
        Container.ScrollBarThickness = 0
        Container.Visible = true
        
        ContainerLayout.Name = "ContainerLayout"
        ContainerLayout.Parent = Container
        ContainerLayout.SortOrder = Enum.SortOrder.LayoutOrder
        ContainerLayout.Padding = UDim.new(0, 10)
        
        local function UpdateSize()
            local cLt = ContainerLayout.AbsoluteContentSize

            game.TweenService:Create(Container, TweenInfo.new(.3, Enum.EasingStyle.Linear, Enum.EasingDirection.In), {
                CanvasSize = UDim2.new(0, 0, 0, cLt.Y)
            }):Play()
        end
        UpdateSize()
        Container.ChildAdded:Connect(UpdateSize)
        Container.ChildRemoved:Connect(UpdateSize)
        
        -- function --
        TabFrame.MouseButton1Click:Connect(function()
            for i,v in next, TabWindow:GetChildren() do
                if v:IsA('TextButton') then
                    game.TweenService:Create(v, TweenInfo.new(.1, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
                        {BackgroundColor3 = Color3.fromRGB(30,30,30)}
                        ):Play()
                    game.TweenService:Create(v, TweenInfo.new(.1, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
                        {BackgroundTransparency = 0}
                        ):Play()
                    UpdateSize()
                end
            end
            game.TweenService:Create(TabFrame, TweenInfo.new(.1, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), 
                {BackgroundColor3 = Color3.fromRGB(0,200,0)}
                ):Play()
            game.TweenService:Create(TabFrame, TweenInfo.new(.1, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
                {BackgroundTransparency = 0.9}
                ):Play()
            
            for i,v in next, ContainerItem:GetChildren() do
                v:TweenSize(UDim2.new(0, 387, 0, 0), Enum.EasingDirection.In, Enum.EasingStyle.Linear, .3, true)
                UpdateSize()
            end
            wait(0.1)
            Container:TweenSize(UDim2.new(0, 387, 0, 304), Enum.EasingDirection.In, Enum.EasingStyle.Linear, .3, true)
            UpdateSize()
            
        end)
        -- End Tabs Container --
        
        -- Section --
        local Section = {}
        function Section:NewSection(seclabel)
            local sectionFrame = Instance.new("Frame")
            local UICorner = Instance.new("UICorner")
            local sectionListLayout = Instance.new("UIListLayout")
            local sectionFrameHead = Instance.new("Frame")
            local UICorner_2 = Instance.new("UICorner")
            local sectionCircle = Instance.new("Frame")
            local UICorner_3 = Instance.new("UICorner")
            local TextLabel = Instance.new("TextLabel")
            local closeSection = Instance.new("TextButton")
            
            -- Prop --
            sectionFrame.Name = seclabel or "sectionFrame"
            sectionFrame.Parent = Container
            sectionFrame.BackgroundColor3 = Color3.fromRGB(30,30,30)
            sectionFrame.BackgroundTransparency = 1.000
            sectionFrame.Position = UDim2.new(0, 0, 0, 0)
            sectionFrame.Size = UDim2.new(0, 387, 0, 25)
            sectionFrame.ClipsDescendants = true

            UICorner.Parent = sectionFrame
            UICorner.CornerRadius = UDim.new(0, 5)

            sectionListLayout.Parent = sectionFrame
            sectionListLayout.SortOrder = Enum.SortOrder.LayoutOrder
            sectionListLayout.Padding = UDim.new(0, 7)
            sectionListLayout.HorizontalAlignment = Enum.HorizontalAlignment.Center

            sectionFrameHead.Name = seclabel or "sectionFrameHead"
            sectionFrameHead.Parent = sectionFrame
            sectionFrameHead.BackgroundColor3 = Color3.fromRGB(30,30,30)
            sectionFrameHead.BackgroundTransparency = 1.000
            sectionFrameHead.Position = UDim2.new(0, 0, 0, 0)
            sectionFrameHead.Size = UDim2.new(0, 387, 0, 25)

            UICorner_2.Parent = sectionFrameHead
            UICorner_2.CornerRadius = UDim.new(0, 5)
            
            TextLabel.Name = seclabel or "TextLabel"
            TextLabel.Parent = sectionFrameHead
            TextLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
            TextLabel.BackgroundTransparency = 1.000
            TextLabel.Position = UDim2.new(0, 0, 0, 0)
            TextLabel.Size = UDim2.new(0, 387, 0, 25)
            TextLabel.Font = Enum.Font.Code
            TextLabel.Text = seclabel
            TextLabel.TextColor3 = Color3.fromRGB(255,255,255)
            TextLabel.TextSize = 13.000
            TextLabel.TextXAlignment = Enum.TextXAlignment.Center
            
            sectionFrame.Size = UDim2.new(0, 387, 0, 5 + sectionListLayout.AbsoluteContentSize.Y + sectionListLayout.Padding.Offset)
            
            sectionListLayout:GetPropertyChangedSignal("AbsoluteContentSize"):Connect(function()
                sectionFrame.Size = UDim2.new(0, 387, 0, 5 + sectionListLayout.AbsoluteContentSize.Y + sectionListLayout.Padding.Offset)
                UpdateSize()
            end)
            
            -- Button --
            local ItemHand = {}
            function ItemHand:Button(buttontitle, callback)
                local ButtonFrame = Instance.new("Frame")
                local Button = Instance.new("TextButton")
                local UIStroke = Instance.new("UIStroke")
                local UICorner = Instance.new("UICorner")
                local UIListLayout = Instance.new("UIListLayout")
                
                -- Prop --
                ButtonFrame.Name = buttontitle or "ButtonFrame"
                ButtonFrame.Parent = sectionFrame
                ButtonFrame.BackgroundColor3 = _G.SectionColor
                ButtonFrame.BackgroundTransparency = 1.000
                ButtonFrame.BorderSizePixel = 0
                ButtonFrame.Size = UDim2.new(0, 387, 0, 25)
            
                Button.Name = buttontitle or "Button"
                Button.Parent = ButtonFrame
                Button.AutoButtonColor = false
                Button.BackgroundColor3 = Color3.fromRGB(30,30,30)
                Button.BackgroundTransparency = 0
                Button.BorderSizePixel = 0
                Button.Position = UDim2.new(0, 50, 0, 2)
                Button.Size = UDim2.new(0, 305, 0, 25)
                Button.Font = Enum.Font.Code
                Button.Text = buttontitle
                Button.TextColor3 = Color3.fromRGB(180,180,180)
                Button.TextSize = 12.000
                
                UIStroke.Name = "UIStroke"
                UIStroke.Parent = Button
                UIStroke.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
                UIStroke.Color = Color3.fromRGB(180,180,180)
                UIStroke.LineJoinMode = Enum.LineJoinMode.Round
                UIStroke.Thickness = 0.5
                UIStroke.Transparency = 0
                UIStroke.Enabled = true
                UIStroke.Archivable = true
                
                UICorner.CornerRadius = UDim.new(0, 3)
                UICorner.Parent = Button
                
                UIListLayout.Parent = ButtonFrame
                UIListLayout.HorizontalAlignment = Enum.HorizontalAlignment.Center
                UIListLayout.SortOrder = Enum.SortOrder.LayoutOrder
                UIListLayout.VerticalAlignment = Enum.VerticalAlignment.Center
                
                -- Button Script --
                local clickDebounce = false
                local callBackDebounce = false
                local mouseleft
                
                Button.MouseButton1Click:Connect(function()
                    if not callBackDebounce then
                        callBackDebounce = true	
                        callback()
                        wait(0.5)
                        callBackDebounce = false
                    end
                end)
                Button.MouseButton1Down:Connect(function()
                    if not clickDebounce then
                        clickDebounce = true
                        game.TweenService:Create(Button, TweenInfo.new(0.1, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),{
                            Size = UDim2.new(0, 295,0, 23),
                            TextSize = 10
                        }):Play()
                        wait(0.5)
                        clickDebounce = false
                    end
                end)
                Button.MouseButton1Up:Connect(function()
                    if mouseleft then
                        game.TweenService:Create(Button, TweenInfo.new(0.1, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),{
                            Size = UDim2.new(0, 305, 0, 25),
                            TextSize = 11
                        }):Play()
                    else
                        game.TweenService:Create(Button, TweenInfo.new(0.1, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),{
                            Size = UDim2.new(0, 305, 0, 25),
                            TextSize = 11
                        }):Play()
                    end
                end)
                Button.MouseEnter:Connect(function()
                    if callBackDebounce then
                        mouseleft = false
                        game.TweenService:Create(UIStroke, TweenInfo.new(0.1, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),{
                            Color = Color3.fromRGB(70,70,70)
                        }):Play()
                    else
                        mouseleft = false
                        game.TweenService:Create(UIStroke, TweenInfo.new(0.1, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),{
                            Color = Color3.fromRGB(90,90,90)
                        }):Play()
                    end
                end)
                Button.MouseLeave:Connect(function()
                    if callBackDebounce then
                        mouseleft = true
                        game.TweenService:Create(Button, TweenInfo.new(0.1, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),{
                            Size = UDim2.new(0, 305,0, 25),
                            TextSize = 12
                        }):Play()
                        game.TweenService:Create(UIStroke, TweenInfo.new(0.1, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),{
                            Color = Color3.fromRGB(180,180,180)
                        }):Play()
                    else
                        mouseleft = true
                        game.TweenService:Create(Button, TweenInfo.new(0.1, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),{
                            Size = UDim2.new(0, 305,0, 25),
                            TextSize = 12
                        }):Play()
                        game.TweenService:Create(UIStroke, TweenInfo.new(0.1, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),{
                            Color = Color3.fromRGB(180,180,180)
                        }):Play()
                    end
                end)
            end
            -- End Button --
            
            -- Toggled --
            function ItemHand:Toggle(TogInfo, default, callback)
                local toggle = false
                local CheckFrame = Instance.new("Frame")
                local CheckFrame2 = Instance.new("Frame")
                local UIStroke = Instance.new("UIStroke")
                local UIListLayout = Instance.new("UIListLayout")
                local UICorner = Instance.new("UICorner")
                local ImageLabel = Instance.new("ImageLabel")
                local Space = Instance.new("TextLabel")
                local Title = Instance.new("TextLabel")
                local ImageButton = Instance.new("ImageButton")
                
                -- Prop --
                CheckFrame.Name = TogInfo or "CheckFrame"
                CheckFrame.Parent = sectionFrame
                CheckFrame.BackgroundColor3 = _G.BackgroundItemColor
                CheckFrame.BackgroundTransparency = 1.000
                CheckFrame.BorderSizePixel = 0
                CheckFrame.Size = UDim2.new(0, 387, 0, 30)
            
                CheckFrame2.Name = "CheckFrame2"
                CheckFrame2.Parent = CheckFrame
                CheckFrame2.BackgroundColor3 = Color3.fromRGB(30,30,30)
                CheckFrame2.BorderSizePixel = 0
                CheckFrame2.Position = UDim2.new(0, 3, 0, 0)
                CheckFrame2.Size = UDim2.new(0, 381, 0, 30)
                
                UIStroke.Name = "UIStroke"
                UIStroke.Parent = CheckFrame2
                UIStroke.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
                UIStroke.Color = Color3.fromRGB(180,180,180)
                UIStroke.LineJoinMode = Enum.LineJoinMode.Round
                UIStroke.Thickness = 0.5
                UIStroke.Transparency = 0
                UIStroke.Enabled = true
                UIStroke.Archivable = true
                
                UICorner.Parent = CheckFrame2
                UICorner.CornerRadius = UDim.new(0, 3)
                
                ImageLabel.Name = "ImageLabel"
                ImageLabel.Parent = CheckFrame2
                ImageLabel.BackgroundColor3 = _G.SectionColor
                ImageLabel.BackgroundTransparency = 1.000
                ImageLabel.BorderSizePixel = 0
                ImageLabel.Position = UDim2.new(0, 5, 0, 6)
                ImageLabel.Size = UDim2.new(0, 18, 0, 18)
                ImageLabel.Image = "rbxassetid://8825010231"
                ImageLabel.ImageColor3 = Color3.fromRGB(180,180,180)
                
                Space.Name = "Space"
                Space.Parent = CheckFrame2
                Space.BackgroundColor3 = _G.SectionColor
                Space.BackgroundTransparency = 1.000
                Space.Position = UDim2.new(0, 30, 0, 0)
                Space.Size = UDim2.new(0, 15, 0, 30)
                Space.Font = Enum.Font.GothamSemibold
                Space.Text = "|"
                Space.TextSize = 13.000
                Space.TextColor3 = Color3.fromRGB(180,180,180)
                Space.TextXAlignment = Enum.TextXAlignment.Center
            
                Title.Name = "Title"
                Title.Parent = CheckFrame2
                Title.BackgroundColor3 = _G.SectionColor
                Title.BackgroundTransparency = 1.000
                Title.Position = UDim2.new(0, 50, 0, 0)
                Title.Size = UDim2.new(0, 280, 0, 30)
                Title.Font = Enum.Font.Code
                Title.Text = TogInfo or "checkBox Title"
                Title.TextColor3 = Color3.fromRGB(180,180,180)
                Title.TextSize = 12.000
                Title.TextXAlignment = Enum.TextXAlignment.Left
            
                ImageButton.Name = "ImageButton"
                ImageButton.Parent = CheckFrame2
                ImageButton.BackgroundColor3 = _G.WindowBackgroundColor
                ImageButton.BackgroundTransparency = 1.000
                ImageButton.Position = UDim2.new(0, 352, 0, 4)
                ImageButton.Size = UDim2.new(0, 23, 0, 23)
                ImageButton.ZIndex = 2
                ImageButton.Image = "rbxassetid://3926311105"
                ImageButton.ImageColor3 = Color3.fromRGB(180,180,180)
                ImageButton.ImageRectOffset = Vector2.new(940, 784)
                ImageButton.ImageRectSize = Vector2.new(48, 48)
                
                -- Toggle Script --
                if default == true then
                    ImageButton.ImageRectOffset = Vector2.new(4, 836)
                    game.TweenService:Create(ImageButton, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
                        {ImageColor3 = Color3.fromRGB(0,255,0)}
                        ):Play()
                    toggle = not toggle
                    pcall(callback, toggle)
                end
                
                ImageButton.MouseButton1Click:Connect(function()
                    if toggle == false then
                        game.TweenService:Create(ImageButton, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
                            {ImageColor3 = Color3.fromRGB(0,255,0)}
                            ):Play()
                        ImageButton.ImageRectOffset = Vector2.new(4, 836)
                    else
                        game.TweenService:Create(ImageButton, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
                            {ImageColor3 = Color3.fromRGB(180,180,180)}
                            ):Play()
                        ImageButton.ImageRectOffset = Vector2.new(940, 784)
                    end
                    toggle = not toggle
                    pcall(callback, toggle)
                end)
            end
            -- End Toggle --
            
            -- Dropdown --
            function ItemHand:Dropdown(droptitle, list, callback)
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
                DropSizeFrame.Parent = sectionFrame
                DropSizeFrame.BackgroundColor3 = _G.SectionColor
                DropSizeFrame.BackgroundTransparency = 1.000
                DropSizeFrame.Size = UDim2.new(0, 387, 0, 60)
                
                Frame.Name = "Frame"
                Frame.Parent = DropSizeFrame
                Frame.BackgroundColor3 = Color3.fromRGB(30,30,30)
                Frame.BorderSizePixel = 0
                Frame.Position = UDim2.new(0, 3, 0, 0)
                Frame.Size = UDim2.new(0, 381, 0, 60)
                
                UIStroke.Name = "UIStroke"
                UIStroke.Parent = Frame
                UIStroke.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
                UIStroke.Color = Color3.fromRGB(180,180,180)
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
                DropCover.Size = UDim2.new(0, 381, 0, 30)
                
                ImageLabel.Name = "ImageLabel"
                ImageLabel.Parent = DropCover
                ImageLabel.BackgroundColor3 = _G.SectionColor
                ImageLabel.BackgroundTransparency = 1.000
                ImageLabel.BorderSizePixel = 0
                ImageLabel.Position = UDim2.new(0, 5, 0, 6)
                ImageLabel.Size = UDim2.new(0, 18, 0, 18)
                ImageLabel.Image = "rbxassetid://8825005073"
                ImageLabel.ImageColor3 = Color3.fromRGB(180,180,180)
                
                Space.Name = "Space"
                Space.Parent = DropCover
                Space.BackgroundColor3 = _G.SectionColor
                Space.BackgroundTransparency = 1.000
                Space.Position = UDim2.new(0, 30, 0, 0)
                Space.Size = UDim2.new(0, 15, 0, 30)
                Space.Font = Enum.Font.GothamSemibold
                Space.Text = "|"
                Space.TextSize = 13.000
                Space.TextColor3 = Color3.fromRGB(180,180,180)
                Space.TextXAlignment = Enum.TextXAlignment.Center
            
                Title.Name = "Title"
                Title.Parent = DropCover
                Title.BackgroundColor3 = _G.SectionColor
                Title.BackgroundTransparency = 1.000
                Title.Position = UDim2.new(0, 50, 0, 0)
                Title.Size = UDim2.new(0, 280, 0, 30)
                Title.Font = Enum.Font.Code
                Title.Text = droptitle or "drop Title"
                Title.TextColor3 = Color3.fromRGB(180,180,180)
                Title.TextSize = 12.000
                Title.TextXAlignment = Enum.TextXAlignment.Left
            
                ImageButton.Name = "ImageButton"
                ImageButton.Parent = DropCover
                ImageButton.BackgroundColor3 = _G.WindowBackgroundColor
                ImageButton.BackgroundTransparency = 1.000
                ImageButton.Position = UDim2.new(0, 352, 0, 7)
                ImageButton.Size = UDim2.new(0, 23, 0, 18)
                ImageButton.Image = "rbxassetid://8530745436"
                ImageButton.ImageColor3 = Color3.fromRGB(180,180,180)
                ImageButton.Rotation = 180
                
                DropTextList.Name = "DropTextList"
                DropTextList.Parent = Frame
                DropTextList.BackgroundColor3 = _G.BackgroundItemColor
                DropTextList.BackgroundTransparency = 1.000
                DropTextList.Position = UDim2.new(0, 3, 0, 30)
                DropTextList.Size = UDim2.new(0, 375, 0, 25)
                DropTextList.Font = Enum.Font.Code
                DropTextList.Text = v or "None..."
                DropTextList.TextColor3 = Color3.fromRGB(180,180,180)
                DropTextList.TextSize = 12.000
                DropTextList.TextXAlignment = Enum.TextXAlignment.Center
                
                UICorner2.Parent = DropTextList
                UICorner2.CornerRadius = UDim.new(0,3)
                
                DropStrokeList.Name = "DropStrokeList"
                DropStrokeList.Parent = DropTextList
                DropStrokeList.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
                DropStrokeList.Color = Color3.fromRGB(180,180,180)
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
                DropItemScroll.Size = UDim2.new(0, 375, 0, 0)
                DropItemScroll.ScrollBarThickness = 0
                DropItemScroll.CanvasSize = UDim2.new(0, 0, 0, 0)
                
                DropItemLayout.Name = "DropItemLayout"
                DropItemLayout.Parent = DropItemScroll
                DropItemLayout.SortOrder = Enum.SortOrder.LayoutOrder
                DropItemLayout.Padding = UDim.new(0, 0)
                
                DropItemStroke.Name = "DropItemStroke"
                DropItemStroke.Parent = DropItemScroll
                DropItemStroke.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
                DropItemStroke.Color = Color3.fromRGB(180,180,180)
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
                        DropSizeFrame:TweenSize(UDim2.new(0, 387, 0, 60), 'InOut', 'Linear', 0.08)
                        Frame:TweenSize(UDim2.new(0, 381, 0, 60), 'InOut', 'Linear', 0.08)
                        DropItemScroll:TweenSize(UDim2.new(0, 375, 0, 0), 'InOut', 'Linear', 0.08)
                        game.TweenService:Create(ImageButton, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
                            {Rotation = 180}
                            ):Play()
                        game.TweenService:Create(ImageButton, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
                            {ImageColor3 = Color3.fromRGB(180,180,180)}
                            ):Play()
                        
                    else
                        DropToggled = true
                        DropSizeFrame:TweenSize(UDim2.new(0, 387, 0, 65 + FrameSize), 'InOut', 'Linear', 0.08)
                        Frame:TweenSize(UDim2.new(0, 381, 0, 65 + FrameSize), 'InOut', 'Linear', 0.08)
                        DropItemScroll:TweenSize(UDim2.new(0, 375, 0, FrameSize), 'InOut', 'Linear', 0.08)
                        game.TweenService:Create(ImageButton, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
                            {Rotation = 0}
                            ):Play()
                        game.TweenService:Create(ImageButton, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
                            {ImageColor3 = Color3.fromRGB(0,255,0)}
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
                    ItemList.BackgroundColor3 = Color3.fromRGB(0,255,0)
                    ItemList.BackgroundTransparency = 1.000
                    ItemList.Size = UDim2.new(0, 375, 0, 30)
                    ItemList.AutoButtonColor = false
                    ItemList.Font = Enum.Font.Code
                    ItemList.TextColor3 = Color3.fromRGB(180,180,180)
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
                        Frame:TweenSize(UDim2.new(0, 381, 0, 60), 'InOut', 'Linear', 0.08)
                        DropItemScroll:TweenSize(UDim2.new(0, 375, 0), 'InOut', 'Linear', 0.08)
                        game.TweenService:Create(ImageButton, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
                            {Rotation = 180}
                            ):Play()
                        game.TweenService:Create(ImageButton, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
                            {ImageColor3 = Color3.fromRGB(180,180,180)}
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
                    DropSizeFrame:TweenSize(UDim2.new(0, 387, 0, 60), 'InOut', 'Linear', 0.08)
                    Frame:TweenSize(UDim2.new(0, 381, 0, 60), 'InOut', 'Linear', 0.08)
                    DropItemScroll:TweenSize(UDim2.new(0, 375, 0), 'InOut', 'Linear', 0.08)
                    game.TweenService:Create(ImageButton, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
                        {Rotation = 180}
                        ):Play()
                    game.TweenService:Create(ImageButton, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
                        {ImageColor3 = Color3.fromRGB(180,180,180)}
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
                    ItemList.BackgroundColor3 = Color3.fromRGB(0,255,0)
                    ItemList.BackgroundTransparency = 1.000
                    ItemList.Size = UDim2.new(0, 375, 0, 30)
                    ItemList.AutoButtonColor = false
                    ItemList.Font = Enum.Font.Code
                    ItemList.TextColor3 = Color3.fromRGB(255,0,0)
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
                        DropSizeFrame:TweenSize(UDim2.new(0, 387, 0, 60), 'InOut', 'Linear', 0.08)
                        Frame:TweenSize(UDim2.new(0, 381, 0, 60), 'InOut', 'Linear', 0.08)
                        DropItemScroll:TweenSize(UDim2.new(0, 375, 0), 'InOut', 'Linear', 0.08)
                        game.TweenService:Create(ImageButton, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
                            {Rotation = 180}
                            ):Play()
                        game.TweenService:Create(ImageButton, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
                            {ImageColor3 = Color3.fromRGB(180,180,180)}
                            ):Play()
                    end)
                    DropItemScroll.CanvasSize = UDim2.new(0, 0, 0, DropItemLayout.AbsoluteContentSize.Y)
                end
                return dropfunc
            end
            -- End Dropdown --
            
            -- Slider --
            function ItemHand:Slider(slidertitle, min, max, start, callback)
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
                SliderFrame.Parent = sectionFrame
                SliderFrame.BackgroundColor3 = _G.BackgroundItemColor
                SliderFrame.BackgroundTransparency = 1.000
                SliderFrame.BorderSizePixel = 0
                SliderFrame.Size = UDim2.new(0, 387, 0, 55)
            
                SliderFrame_2.Name = "SliderFrame_2"
                SliderFrame_2.Parent = SliderFrame
                SliderFrame_2.BackgroundColor3 = Color3.fromRGB(30,30,30)
                SliderFrame_2.BackgroundTransparency = 0
                SliderFrame_2.BorderSizePixel = 0
                SliderFrame_2.Position = UDim2.new(0, 3, 0, 0)
                SliderFrame_2.Size = UDim2.new(0, 381, 0, 55)
                
                UIStroke.Name = "UIStroke"
                UIStroke.Parent = SliderFrame_2
                UIStroke.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
                UIStroke.Color = Color3.fromRGB(180,180,180)
                UIStroke.LineJoinMode = Enum.LineJoinMode.Round
                UIStroke.Thickness = 0.5
                UIStroke.Transparency = 0
                UIStroke.Enabled = true
                UIStroke.Archivable = true
                
                UICorner.Parent = SliderFrame_2
                UICorner.CornerRadius = UDim.new(0, 3)
                
                ImageLabel.Name = "ImageLabel"
                ImageLabel.Parent = SliderFrame_2
                ImageLabel.BackgroundColor3 = _G.SectionColor
                ImageLabel.BackgroundTransparency = 1.000
                ImageLabel.BorderSizePixel = 0
                ImageLabel.Position = UDim2.new(0, 5, 0, 5)
                ImageLabel.Size = UDim2.new(0, 18, 0, 18)
                ImageLabel.Image = "rbxassetid://6034509993"
                ImageLabel.ImageColor3 = Color3.fromRGB(180,180,180)
                
                Space.Name = "Space"
                Space.Parent = SliderFrame_2
                Space.BackgroundColor3 = _G.SectionColor
                Space.BackgroundTransparency = 1.000
                Space.Position = UDim2.new(0, 30, 0, 0)
                Space.Size = UDim2.new(0, 15, 0, 30)
                Space.Font = Enum.Font.GothamSemibold
                Space.Text = "|"
                Space.TextSize = 13.000
                Space.TextColor3 = Color3.fromRGB(180,180,180)
                Space.TextXAlignment = Enum.TextXAlignment.Center
            
                Title.Name = "Title"
                Title.Parent = SliderFrame_2
                Title.BackgroundColor3 = _G.SectionColor
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
                SliderInput.BackgroundColor3 = Color3.fromRGB(0, 200, 0)
                SliderInput.BackgroundTransparency = 0.7
                SliderInput.BorderSizePixel = 0
                SliderInput.Position = UDim2.new(0, 8, 0, 37)
                SliderInput.Size = UDim2.new(0, 365, 0, 4)
                
                SliderCorner2.CornerRadius = UDim.new(0, 100000)
                SliderCorner2.Parent = SliderInput
                
                SliderButton.Name = "SliderButton"
                SliderButton.Parent = SliderInput
                SliderButton.BackgroundColor3 = _G.SectionColor
                SliderButton.BackgroundTransparency = 1.000
                SliderButton.BorderSizePixel = 0
                SliderButton.Position = UDim2.new(0, 0, 0, -7)
                SliderButton.Size = UDim2.new(0, 346, 0, 25)
            
                SliderCount.Name = "SliderCount"
                SliderCount.Parent = SliderButton
                SliderCount.BackgroundColor3 = Color3.fromRGB(0,200,0)
                SliderCount.BackgroundTransparency = 0.3
                SliderCount.BorderSizePixel = 0
                SliderCount.Position = UDim2.new(0,start,0,0)
                SliderCount.Size = UDim2.new(0, 18, 0, 18)
               
                Title_2.Name = "Title_2"
                Title_2.Parent = SliderButton
                Title_2.AnchorPoint = Vector2.new(0, 0)
                Title_2.BackgroundColor3 = Color3.fromRGB(0,200,0)
                Title_2.AutoButtonColor = false
                Title_2.BackgroundTransparency = 1.000
                Title_2.Position = UDim2.new(0,start,0,0)
                Title_2.Size = UDim2.new(0, 18, 0, 18)
                Title_2.Font = Enum.Font.GothamBold
                Title_2.Text = tostring(start and math.floor((start / max) * (max - min) + min) or 0)
                Title_2.TextColor3 = Color3.fromRGB(255, 255, 255)
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
                BoxFrame.BackgroundColor3 = _G.BackgroundItemColor
                BoxFrame.BackgroundTransparency = 1.000
                BoxFrame.Size = UDim2.new(0, 50, 0, 15)
                BoxFrame.Position = UDim2.new(0, 323, 0, 8)
            
                SliderBox.Name = "SliderBox"
                SliderBox.Parent = BoxFrame
                SliderBox.BackgroundColor3 = Color3.fromRGB(200, 0, 0)
                SliderBox.BackgroundTransparency = 1.000
                SliderBox.Position = UDim2.new(0, 0, 0, 1.65)
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
                        game.TweenService:Create(Title_2, TweenInfo.new(0.12, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {AnchorPoint = Vector2.new(0.22, 0.8), TextSize = 13.000, BackgroundTransparency = 0, Size = UDim2.new(0, 25, 0, 25)}):Play()
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
                                SliderCount:TweenPosition(UDim2.new(((tonumber(SliderBox.Text) or min) - min) / (max - min), 0, 0, 0), "InOut", "Linear", 0.08, true)
                                Title_2:TweenPosition(UDim2.new(((tonumber(SliderBox.Text) or min) - min) / (max - min), 0, 0, 0), "InOut", "Linear", 0.12, true)
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
            -- End Slider --
            -- Text Box --
            function ItemHand:TextBox(boxtitle, textbox, callback)
                textbox = textbox or "Type Here"
                callback = callback or function() end
                local BoxFrame = Instance.new("Frame")
                local BoxCover = Instance.new("Frame")
                local UICorner = Instance.new("UICorner")
                local ImageLabel = Instance.new("ImageLabel")
                local Space = Instance.new("TextLabel")
                local Title = Instance.new("TextLabel")
                local TextBox = Instance.new("TextBox")
                local UICorner_2 = Instance.new("UICorner")
                local UIStroke = Instance.new("UIStroke")
                local UIStroke2 = Instance.new("UIStroke")
                
                -- Prop --
                BoxFrame.Name = boxtitle or "BoxFrame"
                BoxFrame.Parent = sectionFrame
                BoxFrame.BackgroundColor3 = _G.BackgroundItemColor
                BoxFrame.BackgroundTransparency = 1.000
                BoxFrame.BorderSizePixel = 0
                BoxFrame.Size = UDim2.new(0, 387, 0, 40)
            
                BoxCover.Name = "BoxCover"
                BoxCover.Parent = BoxFrame
                BoxCover.BackgroundColor3 = Color3.fromRGB(30,30,30)
                BoxCover.BackgroundTransparency = 0
                BoxCover.BorderSizePixel = 0
                BoxCover.Position = UDim2.new(0, 3, 0, 0)
                BoxCover.Size = UDim2.new(0, 381, 0, 40)
                
                UIStroke2.Parent = BoxCover
                UIStroke2.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
                UIStroke2.Color = Color3.fromRGB(180,180,180)
                UIStroke2.LineJoinMode = Enum.LineJoinMode.Round
                UIStroke2.Thickness = 0.5
                UIStroke2.Transparency = 0
                UIStroke2.Enabled = true
                UIStroke2.Archivable = true
                
                UICorner.Parent = BoxCover
                UICorner.CornerRadius = UDim.new(0, 3)
                
                ImageLabel.Name = "ImageLabel"
                ImageLabel.Parent = BoxCover
                ImageLabel.BackgroundColor3 = _G.SectionColor
                ImageLabel.BackgroundTransparency = 1.000
                ImageLabel.BorderSizePixel = 0
                ImageLabel.Position = UDim2.new(0, 5, 0, 12)
                ImageLabel.Size = UDim2.new(0, 18, 0, 18)
                ImageLabel.Image = "rbxassetid://8825051254"
                ImageLabel.ImageColor3 = Color3.fromRGB(180,180,180)
                
                Space.Name = "Space"
                Space.Parent = BoxCover
                Space.BackgroundColor3 = _G.SectionColor
                Space.BackgroundTransparency = 1.000
                Space.Position = UDim2.new(0, 30, 0, 0)
                Space.Size = UDim2.new(0, 15, 0, 40)
                Space.Font = Enum.Font.GothamSemibold
                Space.Text = "|"
                Space.TextSize = 13.000
                Space.TextColor3 = Color3.fromRGB(180,180,180)
                Space.TextXAlignment = Enum.TextXAlignment.Center
            
                Title.Name = "Title"
                Title.Parent = BoxCover
                Title.BackgroundColor3 = _G.SectionColor
                Title.BackgroundTransparency = 1.000
                Title.Position = UDim2.new(0, 50, 0, 0)
                Title.Size = UDim2.new(0, 280, 0, 40)
                Title.Font = Enum.Font.Code
                Title.Text = boxtitle or "box Title"
                Title.TextColor3 = Color3.fromRGB(180,180,180)
                Title.TextSize = 12.000
                Title.TextXAlignment = Enum.TextXAlignment.Left
                
                TextBox.Name = "TextBox"
                TextBox.Parent = BoxCover
                TextBox.BackgroundColor3 = Color3.fromRGB(190, 190, 180)
                TextBox.BackgroundTransparency = 1.000
                TextBox.Position = UDim2.new(0, 293, 0, 10)
                TextBox.Size = UDim2.new(0, 80, 0, 20)
                TextBox.Font = Enum.Font.Code
                TextBox.PlaceholderText = textbox or "Type Here"
                TextBox.Text = ""
                TextBox.TextColor3 = Color3.fromRGB(180,180,180)
                TextBox.TextWrapped = true
                TextBox.TextScaled = false
                TextBox.TextTransparency = 0.5
                TextBox.PlaceholderColor3 = Color3.fromRGB(180,180,180)
                TextBox.TextSize = 12.000
            
                UICorner_2.Parent = TextBox
                UICorner_2.CornerRadius = UDim.new(0, 2)
            
                UIStroke.Parent = TextBox
                UIStroke.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
                UIStroke.Color = Color3.fromRGB(180,180,180)
                UIStroke.LineJoinMode = Enum.LineJoinMode.Round
                UIStroke.Thickness = 1
                UIStroke.Transparency = 0.5
                UIStroke.Enabled = true
                UIStroke.Archivable = true
                
                -- TextBox Script --
                function anim(property)
                    if property == "Text" then
                        TextBox:TweenSize(UDim2.new(0, 70, 0, 18), "InOut", "Linear", 0.08, true)
                        wait(0.15)
                        TextBox:TweenSize(UDim2.new(0, 80, 0, 20), "InOut", "Linear", 0.08, true)
                    end
                end
            
                TextBox.FocusLost:Connect(function()
                    if not EnterPressed then
                        callback(TextBox.Text)
                        TextBox:TweenSize(UDim2.new(0, 70, 0, 18), "InOut", "Linear", 0.08, true)
                        game.TweenService:Create(UIStroke, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {Transparency = 0}):Play()
                        game.TweenService:Create(TextBox, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {TextTransparency = 0}):Play()
                        wait(0.15)
                        TextBox:TweenSize(UDim2.new(0, 80, 0, 20), "InOut", "Linear", 0.08, true)
                        game.TweenService:Create(UIStroke, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {Transparency = 0.5}):Play()
                        game.TweenService:Create(TextBox, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {TextTransparency = 0.5}):Play()
                        return
                    end
                    TextBox.Text = textbox
                end)
            end
            -- End TextBox --
            
            -- KeyBind --
            function ItemHand:Bind(textbind, preset, callback)
                local Key = preset.Name
                local BindFrame = Instance.new("Frame")
                local BindFrame_2 = Instance.new("Frame")
                local UICorner = Instance.new("UICorner")
                local ImageLabel = Instance.new("ImageLabel")
                local Space = Instance.new("TextLabel")
                local Title = Instance.new("TextLabel")
                local KeyBindButton = Instance.new("TextButton")
                local UICorner_2 = Instance.new("UICorner")
                local UIStroke = Instance.new("UIStroke")
                local UIStroke2 = Instance.new("UIStroke")
                
                -- Prop --
                BindFrame.Name = textbind or "BindFrame"
                BindFrame.Parent = sectionFrame
                BindFrame.BackgroundColor3 = _G.BackgroundItemColor
                BindFrame.BackgroundTransparency = 1.000
                BindFrame.BorderSizePixel = 0
                BindFrame.Size = UDim2.new(0, 387, 0, 40)
            
                BindFrame_2.Name = "BindFrame_2"
                BindFrame_2.Parent = BindFrame
                BindFrame_2.BackgroundColor3 = Color3.fromRGB(30,30,30)
                BindFrame_2.BackgroundTransparency = 0
                BindFrame_2.BorderSizePixel = 0
                BindFrame_2.Position = UDim2.new(0, 3, 0, 0)
                BindFrame_2.Size = UDim2.new(0, 381, 0, 40)
                
                UIStroke2.Parent = BindFrame_2
                UIStroke2.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
                UIStroke2.Color = Color3.fromRGB(180,180,180)
                UIStroke2.LineJoinMode = Enum.LineJoinMode.Round
                UIStroke2.Thickness = 0.5
                UIStroke2.Transparency = 0
                UIStroke2.Enabled = true
                UIStroke2.Archivable = true
                
                UICorner.Parent = BindFrame_2
                UICorner.CornerRadius = UDim.new(0, 3)
                
                ImageLabel.Name = "ImageLabel"
                ImageLabel.Parent = BindFrame_2
                ImageLabel.BackgroundColor3 = _G.SectionColor
                ImageLabel.BackgroundTransparency = 1.000
                ImageLabel.BorderSizePixel = 0
                ImageLabel.Position = UDim2.new(0, 5, 0, 12)
                ImageLabel.Size = UDim2.new(0, 18, 0, 18)
                ImageLabel.Image = "rbxassetid://8930945601"
                ImageLabel.ImageColor3 = Color3.fromRGB(180,180,180)
                
                Space.Name = "Space"
                Space.Parent = BindFrame_2
                Space.BackgroundColor3 = _G.SectionColor
                Space.BackgroundTransparency = 1.000
                Space.Position = UDim2.new(0, 30, 0, 0)
                Space.Size = UDim2.new(0, 15, 0, 40)
                Space.Font = Enum.Font.GothamSemibold
                Space.Text = "|"
                Space.TextSize = 13.000
                Space.TextColor3 = Color3.fromRGB(180,180,180)
                Space.TextXAlignment = Enum.TextXAlignment.Center
            
                Title.Name = "Title"
                Title.Parent = BindFrame_2
                Title.BackgroundColor3 = _G.SectionColor
                Title.BackgroundTransparency = 1.000
                Title.Position = UDim2.new(0, 50, 0, 0)
                Title.Size = UDim2.new(0, 280, 0, 40)
                Title.Font = Enum.Font.Code
                Title.Text = textbind or "bind Title"
                Title.TextColor3 = Color3.fromRGB(180,180,180)
                Title.TextSize = 12.000
                Title.TextXAlignment = Enum.TextXAlignment.Left
                
                KeyBindButton.Name = textbind or "KeyBindButton"
                KeyBindButton.Parent = BindFrame_2
                KeyBindButton.BackgroundColor3 = Color3.fromRGB(190, 190, 180)
                KeyBindButton.BackgroundTransparency = 1.000
                KeyBindButton.AutoButtonColor = false
                KeyBindButton.Position = UDim2.new(0, 297, 0, 10)
                KeyBindButton.Size = UDim2.new(0, 80, 0, 20)
                KeyBindButton.Font = Enum.Font.Code
                KeyBindButton.Text = preset.Name
                KeyBindButton.TextColor3 = Color3.fromRGB(180,180,180)
                KeyBindButton.TextSize = 12.000
                KeyBindButton.TextXAlignment = Enum.TextXAlignment.Center
                
                UICorner_2.Parent = KeyBindButton
                UICorner_2.CornerRadius = UDim.new(0, 2)
            
                UIStroke.Parent = KeyBindButton
                UIStroke.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
                UIStroke.Color = Color3.fromRGB(180,180,180)
                UIStroke.LineJoinMode = Enum.LineJoinMode.Round
                UIStroke.Thickness = 0.5
                UIStroke.Transparency = 0
                UIStroke.Enabled = true
                UIStroke.Archivable = true
                
                
                -- Keybind Script --
                KeyBindButton.MouseButton1Click:Connect(function()
					KeyBindButton.Text = ". . ."
					local inputwait = game:GetService("UserInputService").InputBegan:wait()
					if inputwait.KeyCode.Name ~= "Unknown" then
						KeyBindButton.Text = inputwait.KeyCode.Name
						Key = inputwait.KeyCode.Name
					end
				end)
				UserInputService.InputBegan:Connect(function(current, pressed)
					if not pressed then
						if current.KeyCode.Name == Key then
							pcall(callback)
						end
					end
				end)
				
            end
            -- End Keybind --
            
            -- Label --
            function ItemHand:Label(textlabel)
                local labelfunc = {}
                local Frame = Instance.new("Frame")
                local TextButton = Instance.new("TextButton")
                
                -- Prop --
                Frame.Name = textlabel or "Frame"
                Frame.Parent = sectionFrame
                Frame.BackgroundColor3 = _G.BackgroundItemColor
                Frame.BackgroundTransparency = 1.000
                Frame.BorderSizePixel = 0
                Frame.Size = UDim2.new(0, 387, 0, 15)
                
                TextButton.Name = "TextButton"
                TextButton.Parent = Frame
                TextButton.BackgroundColor3 = _G.SectionColor
                TextButton.BackgroundTransparency = 1.000
                TextButton.AutoButtonColor = false
                TextButton.Position = UDim2.new(0, 3, 0, 0)
                TextButton.Size = UDim2.new(0, 381, 0, 15)
                TextButton.Font = Enum.Font.Code
                TextButton.Text = textlabel or ""
                TextButton.TextColor3 = Color3.fromRGB(255,255,255)
                TextButton.TextSize = 12.000
                TextButton.TextXAlignment = Enum.TextXAlignment.Left
                
                -- Label Script --
                function labelfunc:Refresh(newtext)
                    TextButton.Text = newtext
                end
                return labelfunc
            end
            
            -- Line --
            function ItemHand:Line()
                local Frame = Instance.new("Frame")
                local Frame2 = Instance.new("Frame")
                
                -- Prop --
                Frame.Name = "Frame Line"
                Frame.Parent = sectionFrame
                Frame.BackgroundColor3 = _G.BackgroundItemColor
                Frame.BackgroundTransparency = 1.000
                Frame.BorderSizePixel = 0
                Frame.Size = UDim2.new(0, 387, 0, 2)
                
                Frame2.Name = "Line"
                Frame2.Parent = sectionFrame
                Frame2.BackgroundColor3 = Color3.fromRGB(200,200,200)
                Frame2.BorderSizePixel = 0
                Frame2.Position = UDim2.new(0, 8, 0, 1)
                Frame2.Size = UDim2.new(0, 371, 0, 1)
            -- End Label --
            end
            return ItemHand
        end
        return Section
    end
    return Tabs
end

local Win = Blacklib:Window("Gui")
-- Tabes --
local Main = Win:Tab("• Main", "rbxassetid://8825667942")
local Home = Win:Tab("• Setting", nil)
-- Section --
local A = Main:NewSection("HElP For SC")
local S = Home:NewSection("Setting")

Time = A:Label("Server Time")

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

Client = A:Label("Ping Server")

function UpdateClient()
    local Ping = game:GetService("Stats").Network.ServerStatsItem["Data Ping"]:GetValueString()
    Client:Refresh("Ping : "..Ping)
end

spawn(function()
    while true do wait(.1)
        UpdateClient()
    end
end)

C = A:Label("FPS Server")

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

A:Line()

  if game.PlaceId == 2753915549 then
        World1 = true
    elseif game.PlaceId == 4442272183 then
        World2 = true
    elseif game.PlaceId == 7449423635 then
        World3 = true
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
            elseif MyLevel == 10 or MyLevel <= 14 then
                Mon = "Monkey [Lv. 14]"
                LevelQuest = 1
                NameQuest = "JungleQuest"
                NameMon = "Monkey"
                PUK = CFrame.new()
                CFrameQuest = CFrame.new(-1598.08911, 35.5501175, 153.377838, 0, 0, 1, 0, 1, -0, -1, 0, 0)
            elseif MyLevel == 15 or MyLevel <= 29 then
                Mon = "Gorilla [Lv. 20]"
                LevelQuest = 2
                NameQuest = "JungleQuest"
                NameMon = "Gorilla"
                PUK = CFrame.new(-1257.61181640625, 65.0517807006836, -499.2301025390625)
                CFrameQuest = CFrame.new(-1598.08911, 35.5501175, 153.377838, 0, 0, 1, 0, 1, -0, -1, 0, 0)
            elseif MyLevel == 30 or MyLevel <= 39 then
                Mon = "Pirate [Lv. 35]"
                LevelQuest = 1
                NameQuest = "BuggyQuest1"
                NameMon = "Pirate"
                PUK = CFrame.new(-1178.50244140625, 65.74028778076172, 3889.71630859375)
                CFrameQuest = CFrame.new(-1141.07483, 4.10001802, 3831.5498, 0.965929627, -0, -0.258804798, 0, 1, -0, 0.258804798, 0, 0.965929627)
            elseif MyLevel == 40 or MyLevel <= 59 then
                Mon = "Brute [Lv. 45]"
                LevelQuest = 2
                NameQuest = "BuggyQuest1"
                NameMon = "Brute"
                PUK = CFrame.new(-1144.44861, 90.5594559, 4307.25928, -0.998438537, 0, 0.0558618344, 0, 1, 0, -0.0558618344, 0, -0.998438537)
                CFrameQuest = CFrame.new(-1141.07483, 4.10001802, 3831.5498, 0.965929627, -0, -0.258804798, 0, 1, -0, 0.258804798, 0, 0.965929627)
            elseif MyLevel == 60 or MyLevel <= 74 then
                Mon = "Desert Bandit [Lv. 60]"
                LevelQuest = 1
                NameQuest = "DesertQuest"
                NameMon = "Desert Bandit"
                PUK = CFrame.new(919.5968017578125, 69.22762298583984, 4487.37109375)
                CFrameQuest = CFrame.new(894.488647, 5.14000702, 4392.43359, 0.819155693, -0, -0.573571265, 0, 1, -0, 0.573571265, 0, 0.819155693)
            elseif MyLevel == 75 or MyLevel <= 89 then
                Mon = "Desert Officer [Lv. 70]"
                LevelQuest = 2
                NameQuest = "DesertQuest"
                NameMon = "Desert Officer"
                PUK = CFrame.new(1580.03198, 4.61375761, 4366.86426)
                CFrameQuest = CFrame.new(894.488647, 5.14000702, 4392.43359, 0.819155693, -0, -0.573571265, 0, 1, -0, 0.573571265, 0, 0.819155693)
            elseif MyLevel == 90 or MyLevel <= 99 then
                Mon = "Snow Bandit [Lv. 90]"
                LevelQuest = 1
                NameQuest = "SnowQuest"
                NameMon = "Snow Bandit"
                PUK = CFrame.new(1365.15625, 124.89803314208984, -1364.9873046875)
                CFrameQuest = CFrame.new(1389.74451, 88.1519318, -1298.90796, -0.342042685, 0, 0.939684391, 0, 1, 0, -0.939684391, 0, -0.342042685)
            elseif MyLevel == 100 or MyLevel <= 119 then
                Mon = "Snowman [Lv. 100]"
                LevelQuest = 2
                NameQuest = "SnowQuest"
                NameMon = "Snowman"
                PUK = CFrame.new(1122.921875, 143.72373962402344, -1539.132080078125)
                CFrameQuest = CFrame.new(1389.74451, 88.1519318, -1298.90796, -0.342042685, 0, 0.939684391, 0, 1, 0, -0.939684391, 0, -0.342042685)
            elseif MyLevel == 120 or MyLevel <= 149 then
                Mon = "Chief Petty Officer [Lv. 120]"
                LevelQuest = 1
                NameQuest = "MarineQuest2"
                NameMon = "Chief Petty Officer"
                PUK = CFrame.new(-4882.8623, 22.6520386, 4255.53516)
                CFrameQuest = CFrame.new(-5039.58643, 27.3500385, 4324.68018, 0, 0, -1, 0, 1, 0, 1, 0, 0)
            elseif MyLevel == 150 or MyLevel <= 174 then
                Mon = "Sky Bandit [Lv. 150]"
                LevelQuest = 1
                NameQuest = "SkyQuest"
                NameMon = "Sky Bandit"
                PUK = CFrame.new(-4970.74219, 294.544342, -2890.11353)
                CFrameQuest = CFrame.new(-4839.53027, 716.368591, -2619.44165, 0.866007268, 0, 0.500031412, 0, 1, 0, -0.500031412, 0, 0.866007268)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-4607.82275, 872.54248, -1667.55688))
                end
            elseif MyLevel == 175 or MyLevel <= 189 then
                Mon = "Dark Master [Lv. 175]"
                LevelQuest = 2
                NameQuest = "SkyQuest"
                NameMon = "Dark Master"
                PUK = CFrame.new(-5220.58594, 430.693298, -2278.17456)
                CFrameQuest = CFrame.new(-4839.53027, 716.368591, -2619.44165, 0.866007268, 0, 0.500031412, 0, 1, 0, -0.500031412, 0, 0.866007268)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
               game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-4607.82275, 872.54248, -1667.55688))
               end
            elseif MyLevel == 190 or MyLevel <= 209 then
                Mon = "Prisoner [Lv. 190]"
                LevelQuest = 1
                NameQuest = "PrisonerQuest"
                NameMon = "Prisoner"
                PUK = CFrame.new(5308.93115, 1.65517521, 475.120514, -0.0894274712, -5.00292918e-09, -0.995993316, 1.60817859e-09, 1, -5.16744869e-09, 0.995993316, -2.06384709e-09, -0.0894274712)
                CFrameQuest = CFrame.new(5308.93115, 1.65517521, 475.120514, -0.0894274712, -5.00292918e-09, -0.995993316, 1.60817859e-09, 1, -5.16744869e-09, 0.995993316, -2.06384709e-09, -0.0894274712)
           elseif MyLevel == 210 or MyLevel <= 249 then 
                Mon = "Dangerous Prisoner [Lv. 210]"
                LevelQuest = 2
                NameQuest = "PrisonerQuest"
                NameMon = "Dangerous Prisoner"
                PUK = CFrame.new(5563.1171875, 67.71013641357422, 832.8712158203125)
                CFrameQuest = CFrame.new(5308.93115, 1.65517521, 475.120514, -0.0894274712, -5.00292918e-09, -0.995993316, 1.60817859e-09, 1, -5.16744869e-09, 0.995993316, -2.06384709e-09, -0.0894274712)
           elseif MyLevel == 250 or MyLevel <= 299 then
                Mon = "Toga Warrior [Lv. 250]"
                LevelQuest = 1
                NameQuest = "ColosseumQuest"
                NameMon = "Toga Warrior"
                PUK = CFrame.new(-1848.348876953125, 42.34652328491211, -2794.3759765625)
                CFrameQuest = CFrame.new(-1580.04663, 6.35000277, -2986.47534, -0.515037298, 0, -0.857167721, 0, 1, 0, 0.857167721, 0, -0.515037298)
            elseif MyLevel == 300 or MyLevel <= 324 then
                Mon = "Military Soldier [Lv. 300]"
                LevelQuest = 1
                NameQuest = "MagmaQuest"
                NameMon = "Military Soldier"
                PUK = CFrame.new(-5461.19140625, 44.07990264892578, 8457.443359375)
                CFrameQuest = CFrame.new(-5313.37012, 10.9500084, 8515.29395, -0.499959469, 0, 0.866048813, 0, 1, 0, -0.866048813, 0, -0.499959469)
            elseif MyLevel == 325 or MyLevel <= 374 then
                Mon = "Military Spy [Lv. 325]"
                LevelQuest = 2
                NameQuest = "MagmaQuest"
                NameMon = "Military Spy"
                PUK = CFrame.new(-5872.0625, 143.23089599609375, 8790.439453125)
                CFrameQuest = CFrame.new(-5313.37012, 10.9500084, 8515.29395, -0.499959469, 0, 0.866048813, 0, 1, 0, -0.866048813, 0, -0.499959469)
            elseif MyLevel == 375 or MyLevel <= 399 then
                Mon = "Fishman Warrior [Lv. 375]"
                LevelQuest = 1
                NameQuest = "FishmanQuest"
                NameMon = "Fishman Warrior"
                PUK = CFrame.new(60875.9921875, 35.35336685180664, 1434.669189453125)
                CFrameQuest = CFrame.new(61122.65234375, 18.497442245483, 1569.3997802734)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(61163.8515625, 11.6796875, 1819.7841796875))
                end
            elseif MyLevel == 400 or MyLevel <= 449 then
                Mon = "Fishman Commando [Lv. 400]"
                LevelQuest = 2
                NameQuest = "FishmanQuest"
                NameMon = "Fishman Commando"
                PUK = CFrame.new(61914.1484375, 82.76360321044922, 1461.85595703125)
                CFrameQuest = CFrame.new(61122.65234375, 18.497442245483, 1569.3997802734)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(61163.8515625, 11.6796875, 1819.7841796875))
                end
            elseif MyLevel == 450 or MyLevel <= 474 then
                Mon = "God's Guard [Lv. 450]"
                LevelQuest = 1
                NameQuest = "SkyExp1Quest"
                NameMon = "God's Guard"
                PUK = CFrame.new(-4721.88867, 843.874695, -1949.96643, 0.996191859, -0, -0.0871884301, 0, 1, -0, 0.0871884301, 0, 0.996191859)
                CFrameQuest = CFrame.new(-4721.88867, 843.874695, -1949.96643, 0.996191859, -0, -0.0871884301, 0, 1, -0, 0.0871884301, 0, 0.996191859)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-4607.82275, 872.54248, -1667.55688))
                end
            elseif MyLevel == 475 or MyLevel <= 524 then
                Mon = "Shanda [Lv. 475]"
                LevelQuest = 2
                NameQuest = "SkyExp1Quest"
                NameMon = "Shanda"
                PUK = CFrame.new(-7658.7041015625, 5605.01025390625, -529.287353515625)
                CFrameQuest = CFrame.new(-7859.09814, 5544.19043, -381.476196, -0.422592998, 0, 0.906319618, 0, 1, 0, -0.906319618, 0, -0.422592998)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-7894.6176757813, 5547.1416015625, -380.29119873047))
                end
            elseif MyLevel == 525 or MyLevel <= 549 then
                Mon = "Royal Squad [Lv. 525]"
                LevelQuest = 1
                NameQuest = "SkyExp2Quest"
                NameMon = "Royal Squad"
                PUK = CFrame.new(-7669.1796875, 5638.10986328125, -1448.95458984375)
                CFrameQuest = CFrame.new(-7906.81592, 5634.6626, -1411.99194, 0, 0, -1, 0, 1, 0, 1, 0, 0)
            elseif MyLevel == 550 or MyLevel <= 624 then
                Mon = "Royal Soldier [Lv. 550]"
                LevelQuest = 2
                NameQuest = "SkyExp2Quest"
                NameMon = "Royal Soldier"
                PUK = CFrame.new(-7839.28955078125, 5681.00830078125, -1717.6197509765625)
                CFrameQuest = CFrame.new(-7906.81592, 5634.6626, -1411.99194, 0, 0, -1, 0, 1, 0, 1, 0, 0)
            elseif MyLevel == 625 or MyLevel <= 649 then
                Mon = "Galley Pirate [Lv. 625]"
                LevelQuest = 1
                NameQuest = "FountainQuest"
                NameMon = "Galley Pirate"
                PUK = CFrame.new(5566.14453125, 71.22917175292969, 3964.4443359375)
                CFrameQuest = CFrame.new(5259.81982, 37.3500175, 4050.0293, 0.087131381, 0, 0.996196866, 0, 1, 0, -0.996196866, 0, 0.087131381)
            elseif MyLevel >= 650 then
                Mon = "Galley Captain [Lv. 650]"
                LevelQuest = 2
                NameQuest = "FountainQuest"
                NameMon = "Galley Captain"
                PUK = CFrame.new(5344.2529296875, 104.73433685302734, 4821.6533203125)
                CFrameQuest = CFrame.new(5259.81982, 37.3500175, 4050.0293, 0.087131381, 0, 0.996196866, 0, 1, 0, -0.996196866, 0, 0.087131381)
            end
        elseif World2 then
            if MyLevel == 700 or MyLevel <= 724 then
                Mon = "Raider [Lv. 700]"
                LevelQuest = 1
                NameQuest = "Area1Quest"
                NameMon = "Raider"
                PUK = CFrame.new(-737.026123, 39.1748352, 2392.57959)
                CFrameQuest = CFrame.new(-429.543518, 71.7699966, 1836.18188, -0.22495985, 0, -0.974368095, 0, 1, 0, 0.974368095, 0, -0.22495985)
            elseif MyLevel == 725 or MyLevel <= 774 then
                Mon = "Mercenary [Lv. 725]"
                LevelQuest = 2
                NameQuest = "Area1Quest"
                NameMon = "Mercenary"
                PUK = CFrame.new(-1016.576171875, 133.70040893554688, 1433.923095703125)
                CFrameQuest = CFrame.new(-429.543518, 71.7699966, 1836.18188, -0.22495985, 0, -0.974368095, 0, 1, 0, 0.974368095, 0, -0.22495985)
            elseif MyLevel == 775 or MyLevel <= 874 then
                Mon = "Swan Pirate [Lv. 775]"
                LevelQuest = 1
                NameQuest = "Area2Quest"
                NameMon = "Swan Pirate"
                PUK = CFrame.new(970.369446, 142.653198, 1217.3667)
                CFrameQuest = CFrame.new(638.43811, 71.769989, 918.282898, 0.139203906, 0, 0.99026376, 0, 1, 0, -0.99026376, 0, 0.139203906)
            elseif MyLevel == 875 or MyLevel <= 899 then
                Mon = "Marine Lieutenant [Lv. 875]"
                LevelQuest = 1
                NameQuest = "MarineQuest3"
                NameMon = "Marine Lieutenant"
                PUK = CFrame.new(-2929.03369140625, 163.5143585205078, -3027.66357421875)
                CFrameQuest = CFrame.new(-2440.79639, 71.7140732, -3216.06812, 0.866007268, 0, 0.500031412, 0, 1, 0, -0.500031412, 0, 0.866007268)
            elseif MyLevel == 900 or MyLevel <= 949 then
                Mon = "Marine Captain [Lv. 900]"
                LevelQuest = 2
                NameQuest = "MarineQuest3"
                NameMon = "Marine Captain"
                PUK = CFrame.new(-1932.095703125, 131.94061279296875, -3291.61865234375)
                CFrameQuest = CFrame.new(-2440.79639, 71.7140732, -3216.06812, 0.866007268, 0, 0.500031412, 0, 1, 0, -0.500031412, 0, 0.866007268)
            elseif MyLevel == 950 or MyLevel <= 999 then
                Mon = "Zombie [Lv. 950]"
                LevelQuest = 1
                NameQuest = "ZombieQuest"
                NameMon = "Zombie"
                PUK = CFrame.new(-5695.2451171875, 124.95378875732422, -775.65478515625)
                CFrameQuest = CFrame.new(-5497.06152, 47.5923004, -795.237061, -0.29242146, 0, -0.95628953, 0, 1, 0, 0.95628953, 0, -0.29242146)
            elseif MyLevel == 1000 or MyLevel <= 1049 then
                Mon = "Snow Trooper [Lv. 1000]"
                LevelQuest = 1
                NameQuest = "SnowMountainQuest"
                NameMon = "Snow Trooper"
                PUK = CFrame.new(535.893433, 401.457062, -5329.6958, -0.999524176, 0, 0.0308452044, 0, 1, -0, -0.0308452044, 0, -0.999524176)
                CFrameQuest = CFrame.new(609.858826, 400.119904, -5372.25928, -0.374604106, 0, 0.92718488, 0, 1, 0, -0.92718488, 0, -0.374604106)
            elseif MyLevel == 1050 or MyLevel <= 1099 then
                Mon = "Winter Warrior [Lv. 1050]"
                LevelQuest = 2
                NameQuest = "SnowMountainQuest"
                NameMon = "Winter Warrior"
                PUK = CFrame.new(1223.7417, 454.575226, -5170.02148, 0.473996818, 2.56845354e-08, 0.880526543, -5.62456428e-08, 1, 1.10811016e-09, -0.880526543, -5.00510211e-08, 0.473996818)
                CFrameQuest = CFrame.new(609.858826, 400.119904, -5372.25928, -0.374604106, 0, 0.92718488, 0, 1, 0, -0.92718488, 0, -0.374604106)
            elseif MyLevel == 1100 or MyLevel <= 1124 then
                Mon = "Lab Subordinate [Lv. 1100]"
                LevelQuest = 1
                NameQuest = "IceSideQuest"
                NameMon = "Lab Subordinate"
                PUK = CFrame.new(-6060.10693, 15.9868021, -4904.7876, -0.411000341, -5.06538868e-07, 0.91163528, 1.26306062e-07, 1, 6.12581289e-07, -0.91163528, 3.66916197e-07, -0.411000341)
                CFrameQuest = CFrame.new(-6064.06885, 15.2422857, -4902.97852, 0.453972578, -0, -0.891015649, 0, 1, -0, 0.891015649, 0, 0.453972578)
            elseif MyLevel == 1125 or MyLevel <= 1174 then
                Mon = "Horned Warrior [Lv. 1125]"
                LevelQuest = 2
                NameQuest = "IceSideQuest"
                NameMon = "Horned Warrior"
                PUK = CFrame.new(-6400.85889, 24.7645149, -5818.63574)
                CFrameQuest = CFrame.new(-6064.06885, 15.2422857, -4902.97852, 0.453972578, -0, -0.891015649, 0, 1, -0, 0.891015649, 0, 0.453972578)
            elseif MyLevel == 1175 or MyLevel <= 1199 then
                Mon = "Magma Ninja [Lv. 1175]"
                LevelQuest = 1
                NameQuest = "FireSideQuest"
                NameMon = "Magma Ninja"
                PUK = CFrame.new(-5496.65576, 58.6890411, -5929.76855)
                CFrameQuest = CFrame.new(-5428.03174, 15.0622921, -5299.43457, -0.882952213, 0, 0.469463557, 0, 1, 0, -0.469463557, 0, -0.882952213)
            elseif MyLevel == 1200 or MyLevel <= 1249 then
                Mon = "Lava Pirate [Lv. 1200]"
                LevelQuest = 2
                NameQuest = "FireSideQuest"
                NameMon = "Lava Pirate"
                PUK = CFrame.new(-5169.71729, 34.1234779, -4669.73633)
                CFrameQuest = CFrame.new(-5428.03174, 15.0622921, -5299.43457, -0.882952213, 0, 0.469463557, 0, 1, 0, -0.469463557, 0, -0.882952213)
            elseif MyLevel == 1250 or MyLevel <= 1274 then
                Mon = "Ship Deckhand [Lv. 1250]"
                LevelQuest = 1
                NameQuest = "ShipQuest1"
                NameMon = "Ship Deckhand"
                PUK = CFrame.new(1181.84875, 130.485107, 33005.4961, -0.946877539, -7.47373434e-08, -0.321594298, -7.391602e-08, 1, -1.47637005e-08, 0.321594298, 9.79155601e-09, -0.946877539)
                CFrameQuest = CFrame.new(1037.80127, 125.092171, 32911.6016)         
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(923.21252441406, 126.9760055542, 32852.83203125))
                end
            elseif MyLevel == 1275 or MyLevel <= 1299 then
                Mon = "Ship Engineer [Lv. 1275]"
                LevelQuest = 2
                NameQuest = "ShipQuest1"
                NameMon = "Ship Engineer"
                PUK = CFrame.new(919.250427, 43.544014, 32781.9922, 0.999619186, 4.03968698e-08, -0.0275939237, -3.75240887e-08, 1, 1.04626984e-07, 0.0275939237, -1.03551706e-07, 0.999619186)
                CFrameQuest = CFrame.new(1037.80127, 125.092171, 32911.6016)   
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(923.21252441406, 126.9760055542, 32852.83203125))
                end             
            elseif MyLevel == 1300 or MyLevel <= 1324 then
                Mon = "Ship Steward [Lv. 1300]"
                LevelQuest = 1
                NameQuest = "ShipQuest2"
                NameMon = "Ship Steward"
                PUK = CFrame.new(917.478882, 129.556, 33441.2227, -0.999965012, -1.84493896e-08, -0.00836863648, -1.84426696e-08, 1, -8.80260864e-10, 0.00836863648, -7.2589007e-10, -0.999965012)
                CFrameQuest = CFrame.new(968.80957, 125.092171, 33244.125)         
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(923.21252441406, 126.9760055542, 32852.83203125))
                end
            elseif MyLevel == 1325 or MyLevel <= 1349 then
                Mon = "Ship Officer [Lv. 1325]"
                LevelQuest = 2
                NameQuest = "ShipQuest2"
                NameMon = "Ship Officer"
                PUK = CFrame.new(1201.18286, 181.149124, 33308.0508, 0.0748318806, -7.14178512e-08, -0.997196138, 2.97970733e-08, 1, -6.93826223e-08, 0.997196138, -2.45214959e-08, 0.0748318806)
                CFrameQuest = CFrame.new(968.80957, 125.092171, 33244.125)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(923.21252441406, 126.9760055542, 32852.83203125))
                end
            elseif MyLevel == 1350 or MyLevel <= 1374 then
                Mon = "Arctic Warrior [Lv. 1350]"
                LevelQuest = 1
                NameQuest = "FrostQuest"
                NameMon = "Arctic Warrior"
                PUK = CFrame.new(5667.6582, 26.7997818, -6486.08984, -0.933587909, 0, -0.358349502, 0, 1, 0, 0.358349502, 0, -0.933587909)
                CFrameQuest = CFrame.new(5667.6582, 26.7997818, -6486.08984, -0.933587909, 0, -0.358349502, 0, 1, 0, 0.358349502, 0, -0.933587909)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-6508.5581054688, 5000.034996032715, -132.83953857422))
                end
            elseif MyLevel == 1375 or MyLevel <= 1424 then
                Mon = "Snow Lurker [Lv. 1375]"
                LevelQuest = 2
                NameQuest = "FrostQuest"
                NameMon = "Snow Lurker"
                PUK = CFrame.new(5518.00684, 60.5559731, -6828.80518)
                CFrameQuest = CFrame.new(5667.6582, 26.7997818, -6486.08984, -0.933587909, 0, -0.358349502, 0, 1, 0, 0.358349502, 0, -0.933587909)
            elseif MyLevel == 1425 or MyLevel <= 1449 then
                Mon = "Sea Soldier [Lv. 1425]"
                LevelQuest = 1
                NameQuest = "ForgottenQuest"
                NameMon = "Sea Soldier"
                PUK = CFrame.new(-3366.32958984375, 47.21970748901367, -9704.3505859375)
                CFrameQuest = CFrame.new(-3054.44458, 235.544281, -10142.8193, 0.990270376, -0, -0.13915664, 0, 1, -0, 0.13915664, 0, 0.990270376)
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
            elseif MyLevel == 1600 or MyLevel <= 1624 then 
                Mon = "Dragon Crew Archer [Lv. 1600]"
                NameQuest = "AmazonQuest"
                LevelQuest = 2
                NameMon = "Dragon Crew Archer"
                PUK = CFrame.new(6788.97461, 462.341248, 164.233673, -0.711975694, 1.98202414e-08, 0.702204108, -1.45830699e-08, 1, -4.30117559e-08, -0.702204108, -4.08636183e-08, -0.711975694)
                CFrameQuest = CFrame.new(5833.1147460938, 51.60498046875, -1103.0693359375)
            elseif MyLevel == 1625 or MyLevel <= 1649 then
                Mon = "Female Islander [Lv. 1625]"
                NameQuest = "AmazonQuest2"
                LevelQuest = 1
                NameMon = "Female Islander"
                PUK = CFrame.new(5763.98682, 848.118103, 1082.43127, 0.986172736, 2.65753979e-08, 0.165720671, -2.36233451e-08, 1, -1.97844852e-08, -0.165720671, 1.55960436e-08, 0.986172736)
                CFrameQuest = CFrame.new(5446.8793945313, 601.62945556641, 749.45672607422)
            elseif MyLevel == 1650 or MyLevel <= 1699 then 
                Mon = "Giant Islander [Lv. 1650]"
                NameQuest = "AmazonQuest2"
                LevelQuest = 2
                NameMon = "Giant Islander"
                PUK = CFrame.new(4784.24561, 708.376465, 466.297485, 0.99801594, 3.11927195e-09, 0.0629619658, -5.34848299e-09, 1, 3.52371394e-08, -0.0629619658, -3.55039766e-08, 0.99801594)
                CFrameQuest = CFrame.new(5446.8793945313, 601.62945556641, 749.45672607422)
            elseif MyLevel == 1700 or MyLevel <= 1724 then
                Mon = "Marine Commodore [Lv. 1700]"
                LevelQuest = 1
                NameQuest = "MarineTreeIsland"
                NameMon = "Marine Commodore"
                PUK = CFrame.new(2490.0844726563, 190.4232635498, -7160.0502929688)
                CFrameQuest = CFrame.new(2180.54126, 27.8156815, -6741.5498, -0.965929747, 0, 0.258804798, 0, 1, 0, -0.258804798, 0, -0.965929747)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-12471.169921875, 374.94024658203, -7551.677734375))
               end
            elseif MyLevel == 1725 or MyLevel <= 1774 then
                Mon = "Marine Rear Admiral [Lv. 1725]"
                NameMon = "Marine Rear Admiral"
                NameQuest = "MarineTreeIsland"
                LevelQuest = 2
                PUK = CFrame.new(3951.3903808594, 229.11549377441, -6912.81640625)
                CFrameQuest = CFrame.new(2179.98828125, 28.731239318848, -6740.0551757813)
                 if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-12471.169921875, 374.94024658203, -7551.677734375))
               end
            elseif MyLevel == 1775 or MyLevel <= 1799 then
                Mon = "Fishman Raider [Lv. 1775]"
                LevelQuest = 1
                NameQuest = "DeepForestIsland3"
                NameMon = "Fishman Raider"
                PUK = CFrame.new(-10322.400390625, 390.94473266602, -8580.0908203125)
                CFrameQuest = CFrame.new(-10581.6563, 330.872955, -8761.18652, -0.882952213, 0, 0.469463557, 0, 1, 0, -0.469463557, 0, -0.882952213)   
                 if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-12471.169921875, 374.94024658203, -7551.677734375))
               end
            elseif MyLevel == 1800 or MyLevel <= 1824 then
                Mon = "Fishman Captain [Lv. 1800]"
                LevelQuest = 2
                NameQuest = "DeepForestIsland3"
                NameMon = "Fishman Captain"
                PUK = CFrame.new(-11194.541992188, 442.02795410156, -8608.806640625)
                CFrameQuest = CFrame.new(-10581.6563, 330.872955, -8761.18652, -0.882952213, 0, 0.469463557, 0, 1, 0, -0.469463557, 0, -0.882952213)   
                 if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-12471.169921875, 374.94024658203, -7551.677734375))
               end
            elseif MyLevel == 1825 or MyLevel <= 1849 then
                Mon = "Forest Pirate [Lv. 1825]"
                LevelQuest = 1
                NameQuest = "DeepForestIsland"
                NameMon = "Forest Pirate"
                PUK = CFrame.new(-13225.809570313, 428.19387817383, -7753.1245117188)
                CFrameQuest = CFrame.new(-13234.04, 331.488495, -7625.40137, 0.707134247, -0, -0.707079291, 0, 1, -0, 0.707079291, 0, 0.707134247)
                 if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-12471.169921875, 374.94024658203, -7551.677734375))
               end
            elseif MyLevel == 1850 or MyLevel <= 1899 then
                Mon = "Mythological Pirate [Lv. 1850]"
                LevelQuest = 2
                NameQuest = "DeepForestIsland"
                NameMon = "Mythological Pirate"
                PUK = CFrame.new(-13869.172851563, 564.95251464844, -7084.4135742188)
                CFrameQuest = CFrame.new(-13234.04, 331.488495, -7625.40137, 0.707134247, -0, -0.707079291, 0, 1, -0, 0.707079291, 0, 0.707134247)   
                 if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-12471.169921875, 374.94024658203, -7551.677734375))
               end
            elseif MyLevel == 1900 or MyLevel <= 1924 then
                Mon = "Jungle Pirate [Lv. 1900]"
                LevelQuest = 1
                NameQuest = "DeepForestIsland2"
                NameMon = "Jungle Pirate"
                PUK = CFrame.new(-11982.221679688, 376.32522583008, -10451.415039063)
                CFrameQuest = CFrame.new(-12680.3818, 389.971039, -9902.01953, -0.0871315002, 0, 0.996196866, 0, 1, 0, -0.996196866, 0, -0.0871315002)
                 if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-12471.169921875, 374.94024658203, -7551.677734375))
               end
            elseif MyLevel == 1925 or MyLevel <= 1974 then
                Mon = "Musketeer Pirate [Lv. 1925]"
                LevelQuest = 2
                NameQuest = "DeepForestIsland2"
                NameMon = "Musketeer Pirate"
                PUK = CFrame.new(-13282.3046875, 496.23684692383, -9565.150390625)
                CFrameQuest = CFrame.new(-12680.3818, 389.971039, -9902.01953, -0.0871315002, 0, 0.996196866, 0, 1, 0, -0.996196866, 0, -0.0871315002)
                 if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-12471.169921875, 374.94024658203, -7551.677734375))
               end
            elseif MyLevel == 1975 or MyLevel <= 1999 then
                Mon = "Reborn Skeleton [Lv. 1975]"
                LevelQuest = 1
                NameQuest = "HauntedQuest1"
                NameMon = "Reborn Skeleton"
                PUK = CFrame.new(-8817.880859375, 191.16761779785, 6298.6557617188)
                CFrameQuest = CFrame.new(-9479.2168, 141.215088, 5566.09277, 0, 0, 1, 0, 1, -0, -1, 0, 0)
            elseif MyLevel == 2000 or MyLevel <= 2024 then
                Mon = "Living Zombie [Lv. 2000]"
                LevelQuest = 2
                NameQuest = "HauntedQuest1"
                NameMon = "Living Zombie"
                PUK = CFrame.new(-10125.234375, 183.94705200195, 6242.013671875)
                CFrameQuest = CFrame.new(-9479.2168, 141.215088, 5566.09277, 0, 0, 1, 0, 1, -0, -1, 0, 0)
            elseif MyLevel == 2025 or MyLevel <= 2049 then
                Mon = "Demonic Soul [Lv. 2025]"
                LevelQuest = 1
                NameQuest = "HauntedQuest2"
                NameMon = "Demonic Soul"
                PUK = CFrame.new(-9712.03125, 204.69589233398, 6193.322265625)
                CFrameQuest = CFrame.new(-9516.99316, 172.017181, 6078.46533, 0, 0, -1, 0, 1, 0, 1, 0, 0) 
            elseif MyLevel == 2050 or MyLevel <= 2074 then
                Mon = "Posessed Mummy [Lv. 2050]"
                LevelQuest = 2
                NameQuest = "HauntedQuest2"
                NameMon = "Posessed Mummy"
                PUK = CFrame.new(-9545.7763671875, 69.619895935059, 6339.5615234375)
                CFrameQuest = CFrame.new(-9516.99316, 172.017181, 6078.46533, 0, 0, -1, 0, 1, 0, 1, 0, 0)
            elseif MyLevel == 2075 or MyLevel <= 2099 then
                Mon = "Peanut Scout [Lv. 2075]"
                LevelQuest = 1
                NameQuest = "NutsIslandQuest"
                NameMon = "Peanut Scout"
                PUK = CFrame.new(-2265.89014, 89.7506104, -10261.2197, -0.809553444, -9.26727282e-08, 0.587046146, -5.44419549e-08, 1, 8.27857534e-08, -0.587046146, 3.50595535e-08, -0.809553444)
                CFrameQuest = CFrame.new(-2104.3908691406, 38.104167938232, -10194.21875, 0, 0, -1, 0, 1, 0, 1, 0, 0)
            elseif MyLevel == 2100 or MyLevel <= 2124 then
                Mon = "Peanut President [Lv. 2100]"
                LevelQuest = 2
                NameQuest = "NutsIslandQuest"
                NameMon = "Peanut President"
                PUK = CFrame.new(-2062.11792, 86.0444489, -10481.1445, 0.834163189, -9.79785408e-09, -0.551517665, -2.60617616e-09, 1, -2.17070646e-08, 0.551517665, 1.95445864e-08, 0.834163189)
                CFrameQuest = CFrame.new(-2104.3908691406, 38.104167938232, -10194.21875, 0, 0, -1, 0, 1, 0, 1, 0, 0)
            elseif MyLevel == 2125 or MyLevel <= 2149 then
                Mon = "Ice Cream Chef [Lv. 2125]"
                LevelQuest = 1
                NameQuest = "IceCreamIslandQuest"
                NameMon = "Ice Cream Chef"
                PUK = CFrame.new(-875.441345, 107.871437, -11253.3691, 0.630182087, 5.98710486e-08, 0.776447415, -6.03229751e-08, 1, -2.81494827e-08, -0.776447415, -2.90983202e-08, 0.63018208)
                CFrameQuest = CFrame.new(-820.64825439453, 65.819526672363, -10965.795898438, 0, 0, -1, 0, 1, 0, 1, 0, 0)
            elseif MyLevel == 2150 or MyLevel <= 2199 then
                Mon = "Ice Cream Commander [Lv. 2150]"
                LevelQuest = 2
                NameQuest = "IceCreamIslandQuest"
                NameMon = "Ice Cream Commander"
                PUK = CFrame.new(-643.3078, 140.913528, -11334.7109, -0.996822715, -9.07818087e-09, 0.0796525627, -1.43212509e-08, 1, -6.52529906e-08, -0.0796525627, -6.61863808e-08, -0.996822715)
                CFrameQuest = CFrame.new(-820.64825439453, 65.819526672363, -10965.795898438, 0, 0, -1, 0, 1, 0, 1, 0, 0)
            elseif MyLevel == 2200 or MyLevel <= 2224 then
                Mon = "Cookie Crafter [Lv. 2200]"
                LevelQuest = 1
                NameQuest = "CakeQuest1"
                NameMon = "Cookie Crafter"
                PUK = CFrame.new(-2437.66064, 133.07428, -12122.8721, 0.215197399, 2.05706883e-08, -0.976570547, -6.6551344e-08, 1, 6.39893472e-09, 0.976570547, 6.36150475e-08, 0.215197399)
                CFrameQuest = CFrame.new(-2021.32007, 37.7982254, -12028.7295, 0.957576931, -8.80302053e-08, 0.288177818, 6.9301187e-08, 1, 7.51931211e-08, -0.288177818, -5.2032135e-08, 0.957576931)
            elseif MyLevel == 2225 or MyLevel <= 2249 then
                Mon = "Cake Guard [Lv. 2225]"
                LevelQuest = 2
                NameQuest = "CakeQuest1"
                NameMon = "Cake Guard"
                PUK = CFrame.new(-1595.00916, 44.7149811, -12252.0547, -0.998557925, -6.0718726e-08, -0.0536852553, -5.64001539e-08, 1, -8.19574169e-08, 0.0536852553, -7.88113681e-08, -0.998557925)
                CFrameQuest = CFrame.new(-2021.32007, 37.7982254, -12028.7295, 0.957576931, -8.80302053e-08, 0.288177818, 6.9301187e-08, 1, 7.51931211e-08, -0.288177818, -5.2032135e-08, 0.957576931)
            elseif MyLevel == 2250 or MyLevel <= 2274 then
                Mon = "Baking Staff [Lv. 2250]"
                LevelQuest = 1
                NameQuest = "CakeQuest2"
                NameMon = "Baking Staff"
                PUK = CFrame.new(-1817.20581, 93.8077316, -12885.6309, -0.696141601, 7.12665269e-08, 0.717904449, 4.05417566e-08, 1, -5.99574506e-08, -0.717904449, -1.26337669e-08, -0.696141601)
                CFrameQuest = CFrame.new(-1927.91602, 37.7981339, -12842.5391, -0.96804446, 4.22142143e-08, 0.250778586, 4.74911062e-08, 1, 1.49904711e-08, -0.250778586, 2.64211941e-08, -0.96804446)
            elseif MyLevel == 2275 or MyLevel <=2299 then
                Mon = "Head Baker [Lv. 2275]"
                LevelQuest = 2
                NameQuest = "CakeQuest2"
                NameMon = "Head Baker"
                PUK = CFrame.new(-2263.37744, 156.999985, -12776, 0.945995748, 2.16281637e-09, 0.324179053, -1.23387056e-09, 1, -3.0710805e-09, -0.324179053, 2.50523402e-09, 0.945995748)
                CFrameQuest = CFrame.new(-1927.91602, 37.7981339, -12842.5391, -0.96804446, 4.22142143e-08, 0.250778586, 4.74911062e-08, 1, 1.49904711e-08, -0.250778586, 2.64211941e-08, -0.96804446)
         elseif MyLevel == 2300 or MyLevel <= 2324 then
               Mon = "Cocoa Warrior [Lv. 2300]"
               LevelQuest = 1
               NameQuest = "ChocQuest1"
               NameMon = "Cocoa Warrior"
               PUK = CFrame.new(-103.987442, 141.551514, -12260.2188, 0.589523733, -3.54913752e-08, -0.80775106, 4.28455316e-08, 1, -1.26684059e-08, 0.80775106, -2.71401959e-08, 0.589523733)
               CFrameQuest = CFrame.new(231.742981, 25.3354111, -12199.0537, 0.998278677, -5.16006757e-08, 0.0586484075, 4.79685092e-08, 1, 6.33390442e-08, -0.0586484075, -6.04167383e-08, 0.998278677)
             elseif MyLevel == 2325 or MyLevel <= 2349 then
               Mon = "Chocolate Bar Battler [Lv. 2325]"
               LevelQuest = 2
               NameQuest = "ChocQuest1"
               NameMon = "Chocolate Bar Battler"
               PUK = CFrame.new(617.304688, 80.6076355, -12580.6494, -0.485228658, 3.42073503e-09, -0.874387324, -4.0368306e-08, 1, 2.63139608e-08, 0.874387324, 4.80658215e-08, -0.485228658)
              CFrameQuest = CFrame.new(231.742981, 25.3354111, -12199.0537, 0.998278677, -5.16006757e-08, 0.0586484075, 4.79685092e-08, 1, 6.33390442e-08, -0.0586484075, -6.04167383e-08, 0.998278677)
              elseif MyLevel == 2350 or MyLevel <= 2374 then
               Mon = "Sweet Thief [Lv. 2350]"
               LevelQuest = 1
               NameQuest = "ChocQuest2"
               NameMon = "Sweet Thief"
               PUK = CFrame.new(72.062767, 77.630722, -12640.4287, -0.62450999, -9.80953416e-08, 0.781016827, 1.42118917e-09, 1, 1.26735927e-07, -0.781016827, 8.02578199e-08, -0.62450999)
               CFrameQuest = CFrame.new(149.867218, 24.8196201, -12775.5283, -0.0371122323, -7.14229245e-08, -0.99931109, -6.93553162e-08, 1, -6.88964548e-08, 0.99931109, 6.6750637e-08, -0.0371122323)
             elseif MyLevel >= 2375 then
               Mon = "Candy Rebel [Lv. 2375]"
               LevelQuest = 2
               NameQuest = "ChocQuest2"
               NameMon = "Candy Rebel"  
               PUK = CFrame.new(420.127747, 109.63044, -12989.6035, 0.0957952142, 3.10210027e-08, 0.995401084, -9.46955225e-09, 1, -3.02529948e-08, -0.995401084, -6.52791066e-09, 0.0957952142)
              CFrameQuest = CFrame.new(149.867218, 24.8196201, -12775.5283, -0.0371122323, -7.14229245e-08, -0.99931109, -6.93553162e-08, 1, -6.88964548e-08, 0.99931109, 6.6750637e-08, -0.0371122323)
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
    
    local SelectWeapona = A:Dropdown("Select Weapon",WeaponList,function(value)
        _G.SelectWeapon = value
    end)
    
    A:Button("Refresh Weapon",function()
        SelectWeapona:Clear()
        for i,v in pairs(game:GetService("Players").LocalPlayer.Backpack:GetChildren()) do  
            SelectWeapona:Add(v.Name)
        end
    end)

local AutoFarm = A:Toggle("Auto Farm Level",_G.AutoFarm,function(value)
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
                                                topos(v.HumanoidRootPart.CFrame * CFrame.new(0,20,0))
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
                                topos(game:GetService("ReplicatedStorage"):FindFirstChild(Mon).HumanoidRootPart.CFrame * CFrame.new(0,0,0))
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
    
        S:Toggle("White Screen [ Booster FPS ]",_G.WhiteScreen,function(value)
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
                    y.activeController.increment = 4
                    y.activeController.blocking = false
                    y.activeController.attacking = false
                    y.activeController.humanoid.AutoRotate = true
                end)
            end
        end
    end)
end)
    
    S:Toggle("Bring Mob",true,function(value)
        _G.BringMonster = value
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
        "Leopard-Leopard"
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
   					 until not _G.Bring  or v.Parent == game.Players.LocalPlayer.Character 
    end
    end
    end
    end
    end)
    end
    end)

return Blacklib
