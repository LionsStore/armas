# Sistema de Armas - Instruções

## Tipos de Armas

### 1. Arma Melee (Normal)
- Clique normal: Ataque normal com animação de slash
- Tecla E: Ataque especial com animação especial

### 2. Arma Arremessável
- Clique normal: Arremessa a arma com animação de arremesso
- Tecla E: Ataque normal (igual ao ataque normal de uma arma melee) com animação de slash

## Como Criar uma Arma Melee

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
slashAnim.Value = "rbxassetid://SEU_ID_AQUI" -- Animação do ataque normal
slashAnim.Parent = tool

local specialAnim = Instance.new("StringValue")
specialAnim.Name = "specialAnimation"
specialAnim.Value = "rbxassetid://SEU_ID_AQUI" -- Animação do ataque especial
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
danoNormal.Value = 10 -- Dano do ataque normal quando usa tecla E
danoNormal.Parent = tool

local danoCritico = Instance.new("NumberValue")
danoCritico.Name = "DanoCritico"
danoCritico.Value = 20 -- Dano crítico do ataque normal quando usa tecla E
danoCritico.Parent = tool

-- Dano e velocidade do arremesso (para o clique normal)
local arremessoSpeed = Instance.new("NumberValue")
arremessoSpeed.Name = "ArremessoSpeed"
arremessoSpeed.Value = 50 -- Velocidade do arremesso
arremessoSpeed.Parent = tool

local arremessoDano = Instance.new("NumberValue")
arremessoDano.Name = "ArremessoDano"
arremessoDano.Value = 25 -- Dano do arremesso
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
specialAnim.Value = "rbxassetid://SEU_ID_AQUI" -- Animação do arremesso (clique normal)
specialAnim.Parent = tool
```

## Como Modificar Valores

### Arma Melee
- `DanoNormal`: Dano do ataque normal (clique)
- `DanoCritico`: Dano crítico do ataque normal
- `Cooldown`: Tempo entre ataques
- `slashAnimation`: ID da animação do ataque normal
- `specialAnimation`: ID da animação do ataque especial

### Arma Arremessável
- `DanoNormal`: Dano do ataque normal (tecla E)
- `DanoCritico`: Dano crítico do ataque normal (tecla E)
- `ArremessoSpeed`: Velocidade do arremesso (clique normal)
- `ArremessoDano`: Dano causado pelo arremesso (clique normal)
- `Cooldown`: Tempo entre ataques
- `slashAnimation`: ID da animação do ataque normal (tecla E)
- `specialAnimation`: ID da animação do arremesso (clique normal)

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
