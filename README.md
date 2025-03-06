local ScreenGui = Instance.new("ScreenGui") -- Cria a interface principal
local Frame = Instance.new("Frame") -- Janela para o executor
local TextBox = Instance.new("TextBox") -- Campo para digitar o código
local ExecuteButton = Instance.new("TextButton") -- Botão para executar
local OutputText = Instance.new("TextLabel") -- Caixa para mostrar saída
local TitleLabel = Instance.new("TextLabel") -- Título na parte superior

-- Configuração da UI
ScreenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")

Frame.Parent = ScreenGui
Frame.Size = UDim2.new(0, 400, 0, 300)
Frame.Position = UDim2.new(0.5, -200, 0.5, -150)
Frame.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
Frame.BorderSizePixel = 2
Frame.BorderColor3 = Color3.fromRGB(255, 255, 255)

-- Título da UI
TitleLabel.Parent = Frame
TitleLabel.Size = UDim2.new(1, 0, 0, 30)
TitleLabel.Position = UDim2.new(0, 0, 0, 0)
TitleLabel.Text = "15M Leaks Scripts"
TitleLabel.TextColor3 = Color3.fromRGB(255, 0, 255) -- Cor roxa
TitleLabel.TextSize = 20
TitleLabel.TextScaled = true
TitleLabel.BackgroundTransparency = 1

-- Caixa de texto para digitar o código
TextBox.Parent = Frame
TextBox.Size = UDim2.new(1, -20, 0.6, -10)
TextBox.Position = UDim2.new(0, 10, 0, 40)
TextBox.Text = "Digite seu código Lua aqui..."
TextBox.ClearTextOnFocus = false
TextBox.MultiLine = true
TextBox.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
TextBox.TextColor3 = Color3.fromRGB(255, 255, 255)

-- Botão para executar o código
ExecuteButton.Parent = Frame
ExecuteButton.Size = UDim2.new(0, 380, 0, 50)
ExecuteButton.Position = UDim2.new(0, 10, 0.7, 0)
ExecuteButton.Text = "Executar"
ExecuteButton.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
ExecuteButton.TextColor3 = Color3.fromRGB(255, 255, 255)

-- Caixa para mostrar a saída do código
OutputText.Parent = Frame
OutputText.Size = UDim2.new(1, -20, 0.2, -10)
OutputText.Position = UDim2.new(0, 10, 0.8, 0)
OutputText.Text = "Saída: Aguarde..."
OutputText.TextColor3 = Color3.fromRGB(255, 255, 255)
OutputText.TextScaled = true
OutputText.BackgroundTransparency = 1

-- Função para enviar mensagem no chat com tempo limite
local function SendChatMessage(message)
    local chatEvents = game:GetService("ReplicatedStorage"):WaitForChild("DefaultChatSystemChatEvents", 5) -- 5 segundos de timeout
    if chatEvents then
        chatEvents:WaitForChild("SayMessageRequest"):FireServer(message, "All")
    else
        warn("Não foi possível encontrar 'DefaultChatSystemChatEvents' dentro do ReplicatedStorage.")
    end
end

-- Função para executar o código digitado
ExecuteButton.MouseButton1Click:Connect(function()
    local codigo = TextBox.Text
    local func, erro = loadstring(codigo)

    -- Envia a mensagem "15M Leaks 💜" para o chat antes de executar
    SendChatMessage("15M Leaks 💜")

    if func then
        local sucesso, resultado = pcall(func)
        
        -- Envia a mensagem "15M Leaks Scripts 📝" para o chat depois de executar
        SendChatMessage("15M Leaks Scripts 📝")

        if sucesso then
            OutputText.Text = "Saída: " .. (resultado or "Executado com sucesso!")
        else
            OutputText.Text = "Erro: " .. resultado
        end

    else
        OutputText.Text = "Erro de compilação: " .. erro
    end
end)
