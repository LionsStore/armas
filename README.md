# Sistema de Combate BDR - Guia Rápido

## Como funciona?
Este sistema permite criar armas de combate corpo a corpo (melee) e armas arremessáveis para Roblox, com sons, animações, efeitos e lógica de dano. O sistema é modular: basta criar a Tool, adicionar os valores obrigatórios e ela funcionará automaticamente.

---

## Como criar uma arma Melee

### Passo a passo
```lua
local tool = Instance.new("Tool")
tool.Name = "Espada"
tool.Parent = game.StarterPack

local handle = Instance.new("Part")
handle.Name = "Handle"
handle.Parent = tool

-- Valores obrigatórios
local danoNormal = Instance.new("NumberValue")
danoNormal.Name = "DanoNormal"
danoNormal.Value = 10
danoNormal.Parent = tool

local danoEspecial = Instance.new("NumberValue")
danoEspecial.Name = "DanoEspecial"
danoEspecial.Value = 20
danoEspecial.Parent = tool

local cooldown = Instance.new("NumberValue")
cooldown.Name = "Cooldown"
cooldown.Value = 1.2
cooldown.Parent = tool

-- Animações
local slashAnim = Instance.new("StringValue")
slashAnim.Name = "slashAnimation"
slashAnim.Value = "rbxassetid://ID_ANIMACAO_NORMAL"
slashAnim.Parent = tool

local specialAnim = Instance.new("StringValue")
specialAnim.Name = "specialAnimation"
specialAnim.Value = "rbxassetid://ID_ANIMACAO_ESPECIAL"
specialAnim.Parent = tool

-- Sons
local sonoroEquipar = Instance.new("Sound")
sonoroEquipar.Name = "SonoroEquipar"
sonoroEquipar.SoundId = "rbxassetid://ID_SOM_EQUIPAR"
sonoroEquipar.Parent = tool

local sonoroDesequipar = Instance.new("Sound")
sonoroDesequipar.Name = "SonoroDesequipar"
sonoroDesequipar.SoundId = "rbxassetid://ID_SOM_DESEQUIPAR"
sonoroDesequipar.Parent = tool

local sonoroNormal = Instance.new("Sound")
sonoroNormal.Name = "SonoroNormal"
sonoroNormal.SoundId = "rbxassetid://ID_SOM_NORMAL"
sonoroNormal.Parent = tool

local sonoroEspecial = Instance.new("Sound")
sonoroEspecial.Name = "SonoroEspecial"
sonoroEspecial.SoundId = "rbxassetid://ID_SOM_ESPECIAL"
sonoroEspecial.Parent = tool

local sonoroErrouAlvo = Instance.new("Sound")
sonoroErrouAlvo.Name = "SonoroErrouAlvo"
sonoroErrouAlvo.SoundId = "rbxassetid://ID_SOM_ERROU"
sonoroErrouAlvo.Parent = tool
```

### Resumo dos valores
| Nome              | Tipo         | Função                                 |
|-------------------|--------------|----------------------------------------|
| DanoNormal        | NumberValue  | Dano do ataque normal (clique)         |
| DanoEspecial      | NumberValue  | Dano do ataque especial (tecla E)      |
| Cooldown          | NumberValue  | Tempo entre ataques (segundos)         |
| slashAnimation    | StringValue  | ID da animação do ataque normal        |
| specialAnimation  | StringValue  | ID da animação do ataque especial      |
| SonoroEquipar     | Sound        | Som ao equipar                         |
| SonoroDesequipar  | Sound        | Som ao desequipar                      |
| SonoroNormal      | Sound        | Som ao acertar ataque normal           |
| SonoroEspecial    | Sound        | Som ao acertar ataque especial         |
| SonoroErrouAlvo   | Sound        | Som ao errar o ataque                  |

---

## Como criar uma arma Arremessável

### Passo a passo
```lua
local tool = Instance.new("Tool")
tool.Name = "FacaArremessavel"
tool.Parent = game.StarterPack

local handle = Instance.new("Part")
handle.Name = "Handle"
handle.CanCollide = true -- Importante!
handle.Parent = tool

-- Valores obrigatórios
local danoNormal = Instance.new("NumberValue")
danoNormal.Name = "DanoNormal"
danoNormal.Value = 8
danoNormal.Parent = tool

local arremessoDano = Instance.new("NumberValue")
arremessoDano.Name = "ArremessoDano"
arremessoDano.Value = 18
arremessoDano.Parent = tool

local arremessoSpeed = Instance.new("NumberValue")
arremessoSpeed.Name = "ArremessoSpeed"
arremessoSpeed.Value = 60
arremessoSpeed.Parent = tool

local cooldown = Instance.new("NumberValue")
cooldown.Name = "Cooldown"
cooldown.Value = 1.1
cooldown.Parent = tool

-- Animações
local slashAnim = Instance.new("StringValue")
slashAnim.Name = "slashAnimation"
slashAnim.Value = "rbxassetid://ID_ANIMACAO_NORMAL"
slashAnim.Parent = tool

local specialAnim = Instance.new("StringValue")
specialAnim.Name = "specialAnimation"
specialAnim.Value = "rbxassetid://ID_ANIMACAO_ARREMESSO"
specialAnim.Parent = tool

-- Tipo da arma
local tipoArma = Instance.new("StringValue")
tipoArma.Name = "TipoArma"
tipoArma.Value = "arremessavel"
tipoArma.Parent = tool

-- Sons
local sonoroEquipar = Instance.new("Sound")
sonoroEquipar.Name = "SonoroEquipar"
sonoroEquipar.SoundId = "rbxassetid://ID_SOM_EQUIPAR"
sonoroEquipar.Parent = tool

local sonoroDesequipar = Instance.new("Sound")
sonoroDesequipar.Name = "SonoroDesequipar"
sonoroDesequipar.SoundId = "rbxassetid://ID_SOM_DESEQUIPAR"
sonoroDesequipar.Parent = tool

local sonoroArremesso = Instance.new("Sound")
sonoroArremesso.Name = "SonoroArremesso"
sonoroArremesso.SoundId = "rbxassetid://ID_SOM_ARREMESSO"
sonoroArremesso.Parent = tool

local sonoroNormal = Instance.new("Sound")
sonoroNormal.Name = "SonoroNormal"
sonoroNormal.SoundId = "rbxassetid://ID_SOM_IMPACTO"
sonoroNormal.Parent = tool

local sonoroEspecial = Instance.new("Sound")
sonoroEspecial.Name = "SonoroEspecial"
sonoroEspecial.SoundId = "rbxassetid://ID_SOM_ESPECIAL"
sonoroEspecial.Parent = tool

local sonoroErrouAlvo = Instance.new("Sound")
sonoroErrouAlvo.Name = "SonoroErrouAlvo"
sonoroErrouAlvo.SoundId = "rbxassetid://ID_SOM_ERROU"
sonoroErrouAlvo.Parent = tool
```

### Resumo dos valores
| Nome              | Tipo         | Função                                         |
|-------------------|--------------|------------------------------------------------|
| DanoNormal        | NumberValue  | Dano do ataque normal (tecla E)                |
| ArremessoDano     | NumberValue  | Dano do arremesso (clique)                     |
| ArremessoSpeed    | NumberValue  | Velocidade do arremesso                        |
| Cooldown          | NumberValue  | Tempo entre arremessos (segundos)              |
| slashAnimation    | StringValue  | ID da animação do ataque normal (tecla E)      |
| specialAnimation  | StringValue  | ID da animação do arremesso (clique)           |
| TipoArma          | StringValue  | "arremessavel" para ativar o modo arremesso    |
| SonoroEquipar     | Sound        | Som ao equipar                                 |
| SonoroDesequipar  | Sound        | Som ao desequipar                              |
| SonoroArremesso   | Sound        | Som ao arremessar                              |
| SonoroNormal      | Sound        | Som ao acertar personagem                      |
| SonoroEspecial    | Sound        | Som ao acertar especial (tecla E)              |
| SonoroErrouAlvo   | Sound        | Som ao errar o alvo                            |

---

## Observações importantes
- O cooldown define a duração da animação. Para armas arremessáveis, o arremesso e o som acontecem 0.2 segundos antes do fim da animação.
- Para armas arremessáveis, o Handle deve ter `CanCollide = true`.
- Os nomes dos valores e sons devem ser exatamente os listados.
- Se faltar algum valor, a arma pode não funcionar corretamente.

---

Pronto! Agora o README está limpo, direto e pronto para consulta rápida.
