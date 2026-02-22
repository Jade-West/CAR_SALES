-- Create the ScreenGui
local screenGui = Instance.new("ScreenGui")
screenGui.Name = "KeyGuiSystem"
screenGui.Parent = game:GetService("Players").LocalPlayer:WaitForChild("PlayerGui")
screenGui.ResetOnSpawn = false

-- Main Frame
local frame = Instance.new("Frame")
frame.Name = "MainFrame"
frame.Size = UDim2.new(0, 350, 0, 240) -- Made slightly taller to fit the warning text
frame.Position = UDim2.new(0.85, 0, 0.5, 0) 
frame.AnchorPoint = Vector2.new(0.5, 0.5)
frame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
frame.BorderSizePixel = 0
frame.Active = true
frame.Draggable = true 
frame.Parent = screenGui

local uiCorner = Instance.new("UICorner")
uiCorner.CornerRadius = UDim.new(0, 10)
uiCorner.Parent = frame

-- Title Label
local title = Instance.new("TextLabel")
title.Name = "Title"
title.Size = UDim2.new(1, 0, 0, 40)
title.BackgroundTransparency = 1
title.Text = "COPY THE KEY"
title.TextColor3 = Color3.fromRGB(255, 255, 255)
title.TextSize = 22
title.Font = Enum.Font.GothamBold
title.Parent = frame

-- The Key Display (Big Text)
local keyDisplay = Instance.new("TextLabel")
keyDisplay.Name = "KeyDisplay"
keyDisplay.Size = UDim2.new(0.8, 0, 0, 50)
keyDisplay.Position = UDim2.new(0.1, 0, 0.25, 0)
keyDisplay.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
keyDisplay.Text = "HappyScript123"
keyDisplay.TextColor3 = Color3.fromRGB(0, 255, 127) 
keyDisplay.TextSize = 28
keyDisplay.Font = Enum.Font.GothamBlack
keyDisplay.Parent = frame

local keyCorner = Instance.new("UICorner")
keyCorner.Parent = keyDisplay

-- Copy Button
local copyBtn = Instance.new("TextButton")
copyBtn.Name = "CopyButton"
copyBtn.Size = UDim2.new(0.6, 0, 0, 40)
copyBtn.Position = UDim2.new(0.2, 0, 0.55, 0)
copyBtn.BackgroundColor3 = Color3.fromRGB(0, 120, 215)
copyBtn.Text = "Copy Key"
copyBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
copyBtn.TextSize = 18
copyBtn.Font = Enum.Font.GothamSemibold
copyBtn.Parent = frame

local btnCorner = Instance.new("UICorner")
btnCorner.Parent = copyBtn

-- NEW WARNING LABEL --
local warningLabel = Instance.new("TextLabel")
warningLabel.Name = "WarningLabel"
warningLabel.Size = UDim2.new(0.9, 0, 0, 30)
warningLabel.Position = UDim2.new(0.05, 0, 0.8, 0)
warningLabel.BackgroundTransparency = 1
warningLabel.Text = "Dont click on the copy in the keysystem"
warningLabel.TextColor3 = Color3.fromRGB(255, 80, 80) -- Red warning color
warningLabel.TextSize = 14
warningLabel.Font = Enum.Font.GothamBold
warningLabel.TextWrapped = true
warningLabel.Parent = frame

-- Close Button (X)
local closeBtn = Instance.new("TextButton")
closeBtn.Name = "CloseButton"
closeBtn.Size = UDim2.new(0, 30, 0, 30)
closeBtn.Position = UDim2.new(1, -35, 0, 5)
closeBtn.BackgroundColor3 = Color3.fromRGB(200, 50, 50)
closeBtn.Text = "X"
closeBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
closeBtn.Font = Enum.Font.GothamBold
closeBtn.Parent = frame

local closeCorner = Instance.new("UICorner")
closeCorner.CornerRadius = UDim.new(1, 0)
closeCorner.Parent = closeBtn

--- Logic ---

closeBtn.MouseButton1Click:Connect(function()
	screenGui:Destroy()
end)

copyBtn.MouseButton1Click:Connect(function()
	if setclipboard then
		setclipboard("HappyScript123")
		copyBtn.Text = "Copied!"
		copyBtn.BackgroundColor3 = Color3.fromRGB(50, 180, 50)
		task.wait(2)
		copyBtn.Text = "Copy Key"
		copyBtn.BackgroundColor3 = Color3.fromRGB(0, 120, 215)
	else
		copyBtn.Text = "Not Supported"
		task.wait(2)
		copyBtn.Text = "Copy Key"
	end
end)
