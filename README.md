local player = game.Players.LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")
local screenGui = Instance.new("ScreenGui")
screenGui.Parent = playerGui

local blurEffect = Instance.new("BlurEffect")
blurEffect.Parent = game.Lighting
blurEffect.Size = 25 

local welcomeLabel = Instance.new("TextLabel")
welcomeLabel.Parent = screenGui
welcomeLabel.Size = UDim2.new(0, 600, 0, 100)
welcomeLabel.Position = UDim2.new(0.5, -300, 0.4, -50) 
welcomeLabel.Text = "Welcome to the CUCUMBER HUB!🥒"
welcomeLabel.TextSize = 36
welcomeLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
welcomeLabel.BackgroundTransparency = 1
welcomeLabel.TextStrokeTransparency = 0.8  
welcomeLabel.TextStrokeColor3 = Color3.fromRGB(0, 0, 0)
welcomeLabel.Font = Enum.Font.Garamond

local tweenService = game:GetService("TweenService")

local welcomeTweenInfo = TweenInfo.new(3, Enum.EasingStyle.Bounce, Enum.EasingDirection.Out, 0, false)
local welcomeTweenGoalIn = {TextTransparency = 0} 
local welcomeTweenGoalOut = {TextTransparency = 1}  

local welcomeTweenIn = tweenService:Create(welcomeLabel, welcomeTweenInfo, welcomeTweenGoalIn)
local welcomeTweenOut = tweenService:Create(welcomeLabel, welcomeTweenInfo, welcomeTweenGoalOut)

welcomeLabel.TextTransparency = 1
welcomeTweenIn:Play()

local blurTweenInfo = TweenInfo.new(3, Enum.EasingStyle.Linear, Enum.EasingDirection.Out)
local blurTweenGoalIn = {Size = 0}
local blurTweenGoalOut = {Size = 25}

local blurTweenIn = tweenService:Create(blurEffect, blurTweenInfo, blurTweenGoalIn)
local blurTweenOut = tweenService:Create(blurEffect, blurTweenInfo, blurTweenGoalOut)

blurTweenOut:Play()

wait(3)

welcomeTweenOut:Play()

wait(3) 
blurTweenIn:Play()

local badgeLabel = Instance.new("TextLabel")
badgeLabel.Parent = screenGui
badgeLabel.Size = UDim2.new(0, 200, 0, 50)
badgeLabel.Position = UDim2.new(1, -210, 1, -60)
badgeLabel.Text = "Executed!"
badgeLabel.TextSize = 24
badgeLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
badgeLabel.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
badgeLabel.BackgroundTransparency = 0.5
badgeLabel.BorderSizePixel = 0
badgeLabel.TextStrokeTransparency = 0.5 

local badgeTweenInfo = TweenInfo.new(3, Enum.EasingStyle.Linear, Enum.EasingDirection.Out)
local badgeTweenGoal = {TextTransparency = 1, BackgroundTransparency = 1}

local badgeTween = tweenService:Create(badgeLabel, badgeTweenInfo, badgeTweenGoal)

wait(1) 
badgeTween:Play()

wait(3)
screenGui:Destroy()
