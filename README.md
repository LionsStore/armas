# Sistema de Armas - Instruções

## Tipos de Armas

### 1. Arma Normal
- Clique normal: Ataque normal
- Tecla E: Ataque especial

### 2. Arma Arremessável
- Clique normal: Arremessa a arma
- Tecla E: Ataque normal (igual uma arma normal)

## Como Criar uma Arma Normal

1. Crie uma Tool no StarterPack
2. Adicione um Handle (Part) à Tool
3. Adicione os seguintes valores:

```lua
-- Tipo da arma (StringValue)
local tipoArma = Instance.new("StringValue")
tipoArma.Name = "TipoArma"
tipoArma.Value = "melee"
tipoArma.Parent = tool

-- Dano (NumberValue)
local danoNormal = Instance.new("NumberValue")
danoNormal.Name = "DanoNormal"
danoNormal.Value = 10
danoNormal.Parent = tool

local danoCritico = Instance.new("NumberValue")
danoCritico.Name = "DanoCritico"
danoCritico.Value = 20
danoCritico.Parent = tool

-- Cooldown (NumberValue)
local cooldown = Instance.new("NumberValue")
cooldown.Name = "Cooldown"
cooldown.Value = 1
cooldown.Parent = tool

-- Animações (StringValue)
local slashAnim = Instance.new("StringValue")
slashAnim.Name = "slashAnimation"
slashAnim.Value = "rbxassetid://SEU_ID_AQUI"
slashAnim.Parent = tool

local specialAnim = Instance.new("StringValue")
specialAnim.Name = "specialAnimation"
specialAnim.Value = "rbxassetid://SEU_ID_AQUI"
specialAnim.Parent = tool
```

## Como Criar uma Arma Arremessável

1. Crie uma Tool no StarterPack
2. Adicione um Handle (Part) à Tool
3. Adicione os seguintes valores:

```lua
-- Tipo da arma (StringValue)
local tipoArma = Instance.new("StringValue")
tipoArma.Name = "TipoArma"
tipoArma.Value = "arremessavel"
tipoArma.Parent = tool

-- Dano normal (para o ataque da tecla E)
local danoNormal = Instance.new("NumberValue")
danoNormal.Name = "DanoNormal"
danoNormal.Value = 10
danoNormal.Parent = tool

local danoCritico = Instance.new("NumberValue")
danoCritico.Name = "DanoCritico"
danoCritico.Value = 20
danoCritico.Parent = tool

-- Dano e velocidade do arremesso
local arremessoSpeed = Instance.new("NumberValue")
arremessoSpeed.Name = "ArremessoSpeed"
arremessoSpeed.Value = 50
arremessoSpeed.Parent = tool

local arremessoDano = Instance.new("NumberValue")
arremessoDano.Name = "ArremessoDano"
arremessoDano.Value = 25
arremessoDano.Parent = tool

-- Cooldown
local cooldown = Instance.new("NumberValue")
cooldown.Name = "Cooldown"
cooldown.Value = 1
cooldown.Parent = tool

-- Animações
local slashAnim = Instance.new("StringValue")
slashAnim.Name = "slashAnimation"
slashAnim.Value = "rbxassetid://SEU_ID_AQUI" -- Animação do ataque normal (tecla E)
slashAnim.Parent = tool

local specialAnim = Instance.new("StringValue")
specialAnim.Name = "specialAnimation"
specialAnim.Value = "rbxassetid://SEU_ID_AQUI" -- Animação do arremesso
specialAnim.Parent = tool
```

## Como Modificar Valores

### Arma Normal
- `DanoNormal`: Dano do ataque normal (clique)
- `DanoCritico`: Dano crítico do ataque normal
- `Cooldown`: Tempo entre ataques
- `slashAnimation`: ID da animação do ataque normal
- `specialAnimation`: ID da animação do ataque especial

### Arma Arremessável
- `DanoNormal`: Dano do ataque normal (tecla E)
- `DanoCritico`: Dano crítico do ataque normal
- `ArremessoSpeed`: Velocidade do arremesso
- `ArremessoDano`: Dano causado pelo arremesso
- `Cooldown`: Tempo entre ataques
- `slashAnimation`: ID da animação do ataque normal
- `specialAnimation`: ID da animação do arremesso

## Configuração de Arma Arremessável

### Valores Específicos
- `ArremessoSpeed` - Velocidade do arremesso
- `ArremessoDano` - Dano do arremesso

### Comportamento
- Clique normal: Arremessa a arma
- Tecla E: Ataque especial corpo a corpo

### Exemplo de Configuração
```lua
local tool = Instance.new("Tool")
tool.Name = "ArmaArremessavel"

-- Valores básicos
local danoNormal = Instance.new("NumberValue")
danoNormal.Name = "DanoNormal"
danoNormal.Value = 10
danoNormal.Parent = tool

local danoCritico = Instance.new("NumberValue")
danoCritico.Name = "DanoCritico"
danoCritico.Value = 20
danoCritico.Parent = tool

local cooldown = Instance.new("NumberValue")
cooldown.Name = "Cooldown"
cooldown.Value = 1
cooldown.Parent = tool

-- Configurar como arremessável
local tipoArma = Instance.new("StringValue")
tipoArma.Name = "TipoArma"
tipoArma.Value = "arremessavel"
tipoArma.Parent = tool

-- Valores de arremesso
local arremessoSpeed = Instance.new("NumberValue")
arremessoSpeed.Name = "ArremessoSpeed"
arremessoSpeed.Value = 50
arremessoSpeed.Parent = tool

local arremessoDano = Instance.new("NumberValue")
arremessoDano.Name = "ArremessoDano"
arremessoDano.Value = 25
arremessoDano.Parent = tool

-- IDs das animações
local slashAnim = Instance.new("StringValue")
slashAnim.Name = "slashAnimation"
slashAnim.Value = "rbxassetid://SEU_ID_AQUI"
slashAnim.Parent = tool

local specialAnim = Instance.new("StringValue")
specialAnim.Name = "specialAnimation"
specialAnim.Value = "rbxassetid://SEU_ID_AQUI"
specialAnim.Parent = tool
``` 
