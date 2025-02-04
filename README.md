local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/GhostDuckyy/UI-Libraries/main/Neverlose/source.lua"))()
-- Toggle UI: Library:Toggle()

local AriHUB = Library:AriHUB({
    text = "AriHUB"
})

local ARI = AriHUB:ARI({
    text = "ARI."
})

-- Primeira Tab: Universal
local TabUniversal = ARI:Universal({
    text = "Universal",
    icon = "🌐",
})

local SectionUniversal = TabUniversal:Section({
    text = "Section"
})

SectionUniversal:Button({
    text = "Button",
    callback = function()
        print("Clicked button")
    end,
})

-- Variável para controlar o InfJump
local infJumpEnabled = false

SectionUniversal:InfJump({
    text = "InfJump",
    state = false, -- Default boolean
    callback = function(state)
        infJumpEnabled = state
        if state then
            print("InfJump Ativado")
        else
            print("InfJump Desativado")
        end
    end
})

-- Criando a lógica para pulo infinito
local UserInputService = game:GetService("UserInputService")
local Players = game:GetService("Players")
local player = Players.LocalPlayer

UserInputService.JumpRequest:Connect(function()
    if infJumpEnabled and player.Character then
        local humanoid = player.Character:FindFirstChildOfClass("Humanoid")
        if humanoid then
            humanoid:ChangeState(Enum.HumanoidStateType.Jumping)
        end
    end
end)

-- Ajustando a velocidade do jogador
SectionUniversal:WalkSpeed({
    text = "WalkSpeed",
    min = 10,
    max = 1000,
    callback = function(speed)
        if player.Character then
            local humanoid = player.Character:FindFirstChildOfClass("Humanoid")
            if humanoid then
                humanoid.WalkSpeed = speed
                print("Velocidade alterada para:", speed)
            end
        end
    end
})

SectionUniversal:Keybind({
    text = "Keybind",
    default = Enum.KeyCode.L,
    callback = function(defaultBind)
        print("Triggered keybind:", defaultBind)
    end
})

-- Segunda Tab: Universal Scripts
local TabUniversalScripts = ARI:Universal({
    text = "Universal Scripts",
    icon = "🌐",
})

local SectionUniversalScripts = TabUniversalScripts:Section({
    text = "Universal Scripts Section"
})

-- Mudança do nome da Section para "GhostHUB" e execução do script
SectionUniversalScripts:Button({
    text = "GhostHUB",
    callback = function()
        -- Executar o script quando clicado
        loadstring(game:HttpGet('https://raw.githubusercontent.com/GhostPlayer352/Test4/main/GhostHub'))()
        print("GhostHUB executado!")
    end,
})

-- Mudança da section "Volume" para "SystemBroken"
SectionUniversalScripts:Slider({
    text = "SystemBroken",
    min = 0,
    max = 100,
    default = 50,
    callback = function(volume)
        -- Defina a lógica para ajustar o volume ou outro comportamento, se necessário.
        print("SystemBroken ajustado para:", volume)
    end
})

-- Mudança da section "SystemBroken" para executar o script ao ser clicado
SectionUniversalScripts:Button({
    text = "SystemBroken",
    callback = function()
        -- Executar o script quando clicado
        loadstring(game:HttpGet("https://raw.githubusercontent.com/H20CalibreYT/SystemBroken/main/script"))()
        print("SystemBroken executado!")
    end,
})

-- Novo botão "Infinite yield" na section "Universal Scripts Section"
SectionUniversalScripts:Button({
    text = "Infinite yield",
    callback = function()
        -- Executar o script quando clicado
        loadstring(game:HttpGet("https://raw.githubusercontent.com/EdgeIY/infiniteyield/master/source"))()
        print("Infinite Yield executado!")
    end,
})

-- Nova Tab: Aim
local TabAim = ARI:Universal({
    text = "Aim",
    icon = "🏹",
})

-- Adicionar uma section na nova tab "Aim"
local SectionAim = TabAim:Section({
    text = "Aim Section"
})

-- Variável para controlar o AimLock
local aimLockEnabled = false

-- Botão AimLock ativado/desativado
SectionAim:Button({
    text = "AimLock",
    callback = function()
        aimLockEnabled = not aimLockEnabled
        if aimLockEnabled then
            print("AimLock Ativado")
            -- Executar o script de AimLock quando ativado
            loadstring(game:HttpGet("https://raw.githubusercontent.com/testinglolll/lock/refs/heads/main/README.md"))()
        else
            print("AimLock Desativado")
            -- Aqui você pode adicionar a lógica para desativar o AimLock, se necessário
        end
    end,
})

-- Mudança do nome da seção para "AimBot+ESP" e execução do script ao ser clicado
SectionAim:Button({
    text = "AimBot+ESP",
    callback = function()
        print("AimBot+ESP ativado!")
        -- Executar o script quando clicado
        loadstring(game:HttpGet("https://raw.githubusercontent.com/testinglolll/Aim/refs/heads/main/README.md"))()
    end,
})
