local Lib = loadstring(game:HttpGet("https://raw.githubusercontent.com/7yhx/kwargs_Ui_Library/main/source.lua"))()

local UI = Lib:Create{
    Theme = "Dark", -- ou qualquer outro tema
    Size = UDim2.new(0, 555, 0, 400) -- padrão
}

local Main = UI:Tab{
    Name = "Inicia"
}

local Divider = Main:Divider{
    Name = "Itens do Jogo"
}

local QuitDivider = Main:Divider{
    Name = "Sair"
}

-- Função para obter todos os itens no Workspace
local function getAllItems()
    local items = {}
    
    -- Varre o Workspace para pegar todos os itens (objetos)
    for _, item in pairs(game.Workspace:GetChildren()) do
        table.insert(items, item.Name) -- Insere o nome do item na lista
    end
    
    return items
end

-- Adicionando um Dropdown para mostrar os itens no jogo
local ItemsDropdown = Divider:Dropdown{
    Name = "Itens no Jogo",
    Options = getAllItems(), -- Preenche com a lista de itens
    Callback = function(Value)
        print("Item selecionado: " .. Value)
    end
}

-- Escolher a cor do ESP (Aqui você pode definir a cor desejada para o ESP)
Divider:ColorPicker{
    Name = "Cor do ESP",
    Default = Color3.fromRGB(255, 0, 0), -- Definindo a cor vermelha como padrão
    Callback = function(Value)
        print("Cor do ESP escolhida: ", Value)
    end
}

local Quit = QuitDivider:Button{
    Name = "Fechar a biblioteca UI.",
    Callback = function()
        UI:Quit{
            Message = "Saindo...", -- mensagem ao fechar
            Length = 1 -- segundos que a mensagem fica visível
        }
    end
}
