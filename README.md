local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Parent = game.Players.LocalPlayer.PlayerGui

-- Criando um Frame para a interface
local MainFrame = Instance.new("Frame")
MainFrame.Parent = ScreenGui
MainFrame.Size = UDim2.new(0, 400, 0, 300)
MainFrame.Position = UDim2.new(0.5, -200, 0.5, -150)
MainFrame.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
MainFrame.BorderSizePixel = 0
MainFrame.UICornerRadius = UDim.new(0, 12)
MainFrame.UIStroke.Color = Color3.fromRGB(0, 255, 0)
MainFrame.UIStroke.Thickness = 2

-- Criar um texto para o título
local Title = Instance.new("TextLabel")
Title.Parent = MainFrame
Title.Size = UDim2.new(1, 0, 0, 40)
Title.Text = "Fz4 Executor Require 🤝 15 Leaks"
Title.TextColor3 = Color3.fromRGB(255, 255, 255)
Title.BackgroundColor3 = Color3.fromRGB(0, 150, 0)
Title.TextScaled = true
Title.Font = Enum.Font.SourceSans
Title.TextStrokeTransparency = 0.8
Title.TextStrokeColor3 = Color3.fromRGB(0, 0, 0)

-- Divisão de cores no fundo (verde e roxo)
local LeftSide = Instance.new("Frame")
LeftSide.Parent = MainFrame
LeftSide.Size = UDim2.new(0.5, 0, 1, 0)
LeftSide.BackgroundColor3 = Color3.fromRGB(0, 255, 0)
LeftSide.BorderSizePixel = 0
LeftSide.UICornerRadius = UDim.new(0, 12)

local RightSide = Instance.new("Frame")
RightSide.Parent = MainFrame
RightSide.Size = UDim2.new(0.5, 0, 1, 0)
RightSide.Position = UDim2.new(0.5, 0, 0, 0)
RightSide.BackgroundColor3 = Color3.fromRGB(128, 0, 128)
RightSide.BorderSizePixel = 0
RightSide.UICornerRadius = UDim.new(0, 12)

-- Caixa de texto para o código
local CodeBox = Instance.new("TextBox")
CodeBox.Parent = MainFrame
CodeBox.Size = UDim2.new(1, -20, 0, 150)
CodeBox.Position = UDim2.new(0, 10, 0, 50)
CodeBox.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
CodeBox.TextColor3 = Color3.fromRGB(0, 0, 0)
CodeBox.Text = "Digite o código Lua aqui..."
CodeBox.ClearTextOnFocus = true
CodeBox.TextWrapped = true
CodeBox.Font = Enum.Font.SourceSans
CodeBox.TextScaled = true
CodeBox.UICornerRadius = UDim.new(0, 8)
CodeBox.UIStroke.Color = Color3.fromRGB(0, 150, 0)
CodeBox.UIStroke.Thickness = 2

-- Botão para executar o código
local ExecuteButton = Instance.new("TextButton")
ExecuteButton.Parent = MainFrame
ExecuteButton.Size = UDim2.new(1, -20, 0, 40)
ExecuteButton.Position = UDim2.new(0, 10, 0, 210)
ExecuteButton.Text = "Executar Código"
ExecuteButton.BackgroundColor3 = Color3.fromRGB(0, 150, 0)
ExecuteButton.TextColor3 = Color3.fromRGB(255, 255, 255)
ExecuteButton.TextScaled = true
ExecuteButton.Font = Enum.Font.SourceSans
ExecuteButton.UICornerRadius = UDim.new(0, 8)
ExecuteButton.UIStroke.Color = Color3.fromRGB(0, 255, 0)
ExecuteButton.UIStroke.Thickness = 2

-- Função para executar o código Lua quando pressionado o botão
ExecuteButton.MouseButton1Click:Connect(function()
    local code = CodeBox.Text
    local success, result = pcall(function()
        return loadstring(code)() -- Executa o código Lua digitado
    end)

    if success then
        print("Código Executado com Sucesso!")
    else
        print("Erro ao executar o código: " .. result)
    end
end)
