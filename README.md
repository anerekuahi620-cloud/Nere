-- [[ NERE GOAT 0.1 - SISTEMA COMPLETO ]] --

local Players = game:GetService("Players")
local RunService = game:GetService("RunService")
local UserInputService = game:GetService("UserInputService")
local LocalPlayer = Players.LocalPlayer
local Mouse = LocalPlayer:GetMouse()
local Camera = workspace.CurrentCamera

-- === CONFIGURAÃ‡Ã•ES ===
local CorrectKey = "Kuahi11@"
local Settings = {
    AimbotEnabled = false,
    ESPEnabled = false,
    FOVRadius = 150,
    Smoothness = 0.1,
    MenuKey = Enum.KeyCode.Insert,
    CurrentColor = Color3.fromRGB(255, 0, 0)
}

-- === INTERFACE PRINCIPAL ===
local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "NereGoatHub"
ScreenGui.Parent = LocalPlayer:WaitForChild("PlayerGui")
ScreenGui.ResetOnSpawn = false

-- --- TELA DE LOGIN (KEY) ---
local KeyFrame = Instance.new("Frame")
KeyFrame.Name = "KeyFrame"
KeyFrame.Size = UDim2.new(0, 250, 0, 160)
KeyFrame.Position = UDim2.new(0.5, -125, 0.5, -80)
KeyFrame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
KeyFrame.BorderSizePixel = 0
KeyFrame.Active = true
KeyFrame.Parent = ScreenGui

local KeyTitle = Instance.new("TextLabel")
KeyTitle.Size = UDim2.new(1, 0, 0, 40)
KeyTitle.Text = "NERE GOAT 0.1 - LOGIN"
KeyTitle.TextColor3 = Color3.fromRGB(255, 255, 255)
KeyTitle.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
KeyTitle.Font = Enum.Font.GothamBold
KeyTitle.Parent = KeyFrame

local KeyInput = Instance.new("TextBox")
KeyInput.Size = UDim2.new(0.8, 0, 0, 35)
KeyInput.Position = UDim2.new(0.1, 0, 0.35, 0)
KeyInput.PlaceholderText = "Digite a Key..."
KeyInput.Text = ""
KeyInput.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
KeyInput.TextColor3 = Color3.fromRGB(255, 255, 255)
KeyInput.Parent = KeyFrame

local KeyBtn = Instance.new("TextButton")
KeyBtn.Size = UDim2.new(0.8, 0, 0, 35)
KeyBtn.Position = UDim2.new(0.1, 0, 0.7, 0)
KeyBtn.Text = "ENTRAR"
KeyBtn.BackgroundColor3 = Color3.fromRGB(0, 120, 0)
KeyBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
KeyBtn.Parent = KeyFrame

-- --- PAINEL DO HUB ---
local MainFrame = Instance.new("Frame")
MainFrame.Name = "MainFrame"
MainFrame.Size = UDim2.new(0, 220, 0, 260)
MainFrame.Position = UDim2.new(0.5, -110, 0.1, 0)
MainFrame.BackgroundColor3 = Color3.fromRGB(25, 25, 25)
MainFrame.Visible = false
MainFrame.Draggable = true
MainFrame.Active = true
MainFrame.Parent = ScreenGui

local Title = Instance.new("TextLabel")
Title.Size = UDim2.new(1, 0, 0, 40)
Title.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
Title.Text = "NERE GOAT 0.1"
Title.TextColor3 = Settings.CurrentColor
Title.Font = Enum.Font.GothamBold
Title.Parent = MainFrame

-- --- PÃGINAS ---
local MainMenu = Instance.new("Frame")
MainMenu.Size = UDim2.new(1, 0, 1, -40)
MainMenu.Position = UDim2.new(0, 0, 0, 40)
MainMenu.BackgroundTransparency = 1
MainMenu.Parent = MainFrame

local ConfigMenu = Instance.new("Frame")
ConfigMenu.Size = UDim2.new(1, 0, 1, -40)
ConfigMenu.Position = UDim2.new(0, 0, 0, 40)
ConfigMenu.BackgroundTransparency = 1
ConfigMenu.Visible = false
ConfigMenu.Parent = MainFrame

-- --- BOTÃ•ES ---
local AimBtn = Instance.new("TextButton")
AimBtn.Size = UDim2.new(0.9, 0, 0, 40)
AimBtn.Position = UDim2.new(0.05, 0, 0.1, 0)
AimBtn.Text = "AIMBOT: OFF"
AimBtn.Parent = MainMenu

local EspBtn = Instance.new("TextButton")
EspBtn.Size = UDim2.new(0.9, 0, 0, 40)
EspBtn.Position = UDim2.new(0.05, 0, 0.35, 0)
EspBtn.Text = "ESP: OFF"
EspBtn.Parent = MainMenu

local GoConfigBtn = Instance.new("TextButton")
GoConfigBtn.Size = UDim2.new(0.9, 0, 0, 40)
GoConfigBtn.Position = UDim2.new(0.05, 0, 0.65, 0)
GoConfigBtn.Text = "CONFIGURAÃ‡Ã•ES"
GoConfigBtn.BackgroundColor3 = Color3.fromRGB(60, 45, 45)
GoConfigBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
GoConfigBtn.Parent = MainMenu

local ColorInput = Instance.new("TextBox")
ColorInput.Size = UDim2.new(0.9, 0, 0, 35)
ColorInput.Position = UDim2.new(0.05, 0, 0.1, 0)
ColorInput.PlaceholderText = "Cor (Ex: Blue)"
ColorInput.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
ColorInput.TextColor3 = Color3.fromRGB(255, 255, 255)
ColorInput.Parent = ConfigMenu

local ApplyColorBtn = Instance.new("TextButton")
ApplyColorBtn.Size = UDim2.new(0.9, 0, 0, 35)
ApplyColorBtn.Position = UDim2.new(0.05, 0, 0.35, 0)
ApplyColorBtn.Text = "APLICAR COR"
ApplyColorBtn.BackgroundColor3 = Color3.fromRGB(0, 100, 0)
ApplyColorBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
ApplyColorBtn.Parent = ConfigMenu

local BackBtn = Instance.new("TextButton")
BackBtn.Size = UDim2.new(0.9, 0, 0, 35)
BackBtn.Position = UDim2.new(0.05, 0, 0.7, 0)
BackBtn.Text = "VOLTAR"
BackBtn.Parent = ConfigMenu

local FOVFrame = Instance.new("Frame")
FOVFrame.Size = UDim2.new(0, Settings.FOVRadius * 2, 0, Settings.FOVRadius * 2)
FOVFrame.BackgroundTransparency = 1
FOVFrame.Position = UDim2.new(0.5, -Settings.FOVRadius, 0.5, -Settings.FOVRadius)
FOVFrame.Visible = false
FOVFrame.Parent = ScreenGui

local UIStroke = Instance.new("UIStroke")
UIStroke.Thickness = 2
UIStroke.Color = Settings.CurrentColor
UIStroke.Parent = FOVFrame
Instance.new("UICorner", FOVFrame).CornerRadius = UDim.new(1, 0)

-- === LÃ“GICA ===
KeyBtn.MouseButton1Click:Connect(function()
    if KeyInput.Text == CorrectKey then
        KeyFrame.Visible = false
        MainFrame.Visible = true
        FOVFrame.Visible = true
    else
        KeyBtn.Text = "KEY INVÃLIDA"
        task.wait(1)
        KeyBtn.Text = "ENTRAR"
    end
end)

GoConfigBtn.MouseButton1Click:Connect(function()
    MainMenu.Visible = false
    ConfigMenu.Visible = true
end)

BackBtn.MouseButton1Click:Connect(function()
    ConfigMenu.Visible = false
    MainMenu.Visible = true
end)

ApplyColorBtn.MouseButton1Click:Connect(function()
    local success, result = pcall(function() return BrickColor.new(ColorInput.Text).Color end)
    if success and result then
        Settings.CurrentColor = result
        UIStroke.Color = result
        Title.TextColor3 = result
        ApplyColorBtn.Text = "SUCESSO!"
        task.wait(1)
        ApplyColorBtn.Text = "APLICAR COR"
    end
end)

local function GetClosest()
    local target = nil
    local dist = Settings.FOVRadius
    local center = Vector2.new(Camera.ViewportSize.X / 2, Camera.ViewportSize.Y / 2)
    for _, p in pairs(Players:GetPlayers()) do
        if p ~= LocalPlayer and p.Character and p.Character:FindFirstChild("Head") then
            local hum = p.Character:FindFirstChild("Humanoid")
            if hum and hum.Health > 0 then
                local pos, onScreen = Camera:WorldToViewportPoint(p.Character.Head.Position)
                if onScreen then
                    local mDist = (center - Vector2.new(pos.X, pos.Y)).Magnitude
                    if mDist < dist then
                        target = p.Character.Head
                        dist = mDist
                    end
                end
            end
        end
    end
    return target
end

AimBtn.MouseButton1Click:Connect(function()
    Settings.AimbotEnabled = not Settings.AimbotEnabled
    AimBtn.Text = "AIMBOT: " .. (Settings.AimbotEnabled and "ON" or "OFF")
end)

EspBtn.MouseButton1Click:Connect(function()
    Settings.ESPEnabled = not Settings.ESPEnabled
    EspBtn.Text = "ESP: " .. (Settings.ESPEnabled and "ON" or "OFF")
end)

UserInputService.InputBegan:Connect(function(i, p)
    if not p and i.KeyCode == Settings.MenuKey and not KeyFrame.Visible then
        MainFrame.Visible = not MainFrame.Visible
        FOVFrame.Visible = MainFrame.Visible
    end
end)

RunService.RenderStepped:Connect(function()
    if MainFrame.Visible or Settings.ESPEnabled or Settings.AimbotEnabled then
        if Settings.AimbotEnabled then
            local t = GetClosest()
            if t then Camera.CFrame = Camera.CFrame:Lerp(CFrame.new(Camera.CFrame.Position, t.Position), Settings.Smoothness) end
        end
        if Settings.ESPEnabled then
            for _, p in pairs(Players:GetPlayers()) do
                if p ~= LocalPlayer and p.Character then
                    local h = p.Character:FindFirstChild("NextESP") or Instance.new("Highlight", p.Character)
                    h.Name = "NextESP"
                    h.FillColor = Settings.CurrentColor
                    h.DepthMode = Enum.HighlightDepthMode.AlwaysOnTop
                end
            end
        else
            for _, p in pairs(Players:GetPlayers()) do
                if p.Character and p.Character:FindFirstChild("NextESP") then p.Character.NextESP:Destroy() end
            end
        end
    end
end)
