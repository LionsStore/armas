# Sistema de Combate BDR (Briga de Rua Realista)

## 📖 Índice
1. [Introdução](#introdução)
2. [Criando uma Arma Melee](#criando-uma-arma-melee)
3. [Criando uma Arma Arremessável](#criando-uma-arma-arremessável)
4. [Sistema de Sons](#sistema-de-sons)
5. [Solução de Problemas](#solução-de-problemas)

## Introdução
Este é um sistema de combate corpo a corpo (melee) realista para Roblox, desenvolvido especialmente para jogos de PVP com temática apocalíptica. O sistema inclui efeitos sangrentos, dano localizado e efeitos de status realistas.

## 📋 Características

- Sistema de dano localizado por região do corpo
- Efeitos realistas de sangue e ferimentos
- Sistema de atordoamento e sangramento
- Cooldown personalizável por arma
- Sistema de animações único por arma
- Sistema de habilidades múltiplas
- Detecção de hits precisa
- Otimizado para combate próximo
- Sistema de armas arremessáveis
- Limite de 3 arremessos por arma
- Física realista de arremesso
- Sistema de coleta de armas dropadas

## 🎯 Sistema de Dano

O sistema aplica o dano base configurado em cada arma, sem multiplicadores por região. O dano é determinado pelos seguintes valores:

- **DanoNormal**: Dano do ataque primário
- **DanoEspecial**: Dano do ataque especial
- **ArremessoDano**: Dano do arremesso (para armas arremessáveis)

### Efeitos de Status
- **Sangramento**: 
  - 25% de chance base
  - Causa 5 de dano a cada 2 segundos por 10 segundos
  - Efeito visual de sangue contínuo

- **Atordoamento**:
  - 15% de chance base
  - Reduz velocidade de movimento e pulo pela metade
  - Dura 2 segundos
  - Efeito visual de estrelas

### Dano de Arremesso
- Dano base configurável por arma
- Velocidade de arremesso ajustável
- Armas ficam disponíveis para coleta após o arremesso

## 🛠️ Como Criar uma Nova Arma

1. Crie uma nova Tool no StarterPack ou ReplicatedStorage
2. Adicione os seguintes NumberValues à Tool:

```lua
-- Configurações de Dano
local danoNormal = Instance.new("NumberValue")
danoNormal.Name = "DanoNormal"
danoNormal.Value = 15  -- Dano do ataque normal

local danoEspecial = Instance.new("NumberValue")
danoEspecial.Name = "DanoEspecial"
danoEspecial.Value = 25  -- Dano do ataque especial

local cooldown = Instance.new("NumberValue")
cooldown.Name = "Cooldown"
cooldown.Value = 1.5  -- Tempo entre ataques

-- Configurações de Efeitos
local stunChance = Instance.new("NumberValue")
stunChance.Name = "StunChance"
stunChance.Value = 0.15  -- 15% de chance

local bleedChance = Instance.new("NumberValue")
bleedChance.Name = "BleedChance"
bleedChance.Value = 0.25  -- 25% de chance
```

3. Adicione as animações de ataque:

```lua
-- Animação do ataque primário (clique)
local slashAnim = Instance.new("StringValue")
slashAnim.Name = "slashAnimation"
slashAnim.Value = "rbxassetid://SEU_ID_DE_ANIMACAO"

-- Animação do ataque secundário (tecla E)
local specialAnim = Instance.new("StringValue")
specialAnim.Name = "specialAnimation"
specialAnim.Value = "rbxassetid://SEU_ID_DE_ANIMACAO_ESPECIAL"
```

Para criar uma arma arremessável, adicione:

```lua
-- Configurar tipo da arma
local tipoArma = Instance.new("StringValue")
tipoArma.Name = "TipoArma"
tipoArma.Value = "arremessavel"
tipoArma.Parent = tool

-- Configurações de arremesso
local arremessoSpeed = Instance.new("NumberValue")
arremessoSpeed.Name = "ArremessoSpeed"
arremessoSpeed.Value = 50  -- Velocidade do arremesso
arremessoSpeed.Parent = tool

local arremessoDano = Instance.new("NumberValue")
arremessoDano.Name = "ArremessoDano"
arremessoDano.Value = 25  -- Dano do arremesso
arremessoDano.Parent = tool
```

## 🎮 Valores Padrão

Se não forem especificados os valores, o sistema usará:
- DanoNormal: 10
- DanoEspecial: 15
- Cooldown: 1 segundo
- StunChance: 15%
- BleedChance: 25%
- ArremessoSpeed: 50
- ArremessoDano: 25
- Limite de Arremessos: 3

## ⚔️ Sistema de Habilidades

O sistema suporta dois tipos de ataques por arma:
1. **Ataque Primário**
   - Ativado pelo clique do mouse
   - Ideal para golpes rápidos e diretos

2. **Ataque Secundário**
   - Ativado pela tecla E
   - Ideal para golpes especiais ou finalizadores

## 🔧 Configurações de Hitbox

A hitbox é otimizada para combate corpo a corpo realista:
```lua
DEFAULT_SIZE = Vector3.new(4, 4, 4)  -- Tamanho compacto para precisão
SAMPLES = 100  -- Alta taxa de amostragem
FORWARD_OFFSET = 1.5  -- Alcance curto para combate próximo
```

## 🎨 Efeitos Visuais

O sistema inclui efeitos visuais realistas:
- Partículas de sangue dinâmicas
- Decalques de sangue permanentes
- Efeitos visuais de atordoamento
- Efeitos de sangramento contínuo
- Cores e tamanhos realistas

## 📝 Exemplo de Criação de Arma Completa

```lua
-- Criar uma faca de combate
local faca = Instance.new("Tool")
faca.Name = "FacaCombate"

-- Configurar valores de dano e cooldown
local danoNormal = Instance.new("NumberValue")
danoNormal.Name = "DanoNormal"
danoNormal.Value = 12
danoNormal.Parent = faca

local danoEspecial = Instance.new("NumberValue")
danoEspecial.Name = "DanoEspecial"
danoEspecial.Value = 20
danoEspecial.Parent = faca

local cooldown = Instance.new("NumberValue")
cooldown.Name = "Cooldown"
cooldown.Value = 0.8  -- Ataque rápido
cooldown.Parent = faca

-- Configurar chances de efeitos
local stunChance = Instance.new("NumberValue")
stunChance.Name = "StunChance"
stunChance.Value = 0.1  -- 10% de chance
stunChance.Parent = faca

local bleedChance = Instance.new("NumberValue")
bleedChance.Name = "BleedChance"
bleedChance.Value = 0.4  -- 40% de chance
bleedChance.Parent = faca

-- Adicionar animações
local slashAnim = Instance.new("StringValue")
slashAnim.Name = "slashAnimation"
slashAnim.Value = "rbxassetid://SEU_ID_DE_ANIMACAO"
slashAnim.Parent = faca

local specialAnim = Instance.new("StringValue")
specialAnim.Name = "specialAnimation"
specialAnim.Value = "rbxassetid://SEU_ID_DE_ANIMACAO_ESPECIAL"
specialAnim.Parent = faca

-- Adicionar modelo 3D da faca
local handle = Instance.new("Part")
handle.Name = "Handle"
handle.Size = Vector3.new(0.4, 1.2, 0.1)
handle.Parent = faca

-- Adicionar LocalScriptTool
local localScript = Instance.new("LocalScript")
localScript.Name = "LocalScriptTool"
-- Copie o código do LocalScriptTool.lua para aqui
localScript.Parent = faca
```

## 🔍 Dicas de Balanceamento

1. **Armas Cortantes (Facas, Espadas)**:
   - Alto chance de sangramento (30-40%)
   - Dano base moderado
   - Cooldown baixo

2. **Armas Contundentes (Bastões, Cassetetes)**:
   - Alta chance de atordoamento (20-30%)
   - Dano base alto
   - Cooldown alto

3. **Armas Improvisadas**:
   - Chances médias de efeitos
   - Dano base baixo
   - Cooldown médio

4. **Armas Arremessáveis**:
   - Dano de arremesso maior que dano normal
   - Velocidade de arremesso baseada no peso
   - Maior chance de sangramento
   - Cooldown baixo para compensar perda da arma

## ⚠️ Observações Importantes

1. Mantenha o balanceamento realista
2. Ajuste os efeitos visuais de acordo com a classificação etária do jogo
3. Teste todas as armas em diferentes situações de combate
4. O sistema limpa automaticamente:
   - Efeitos de sangue após 2 segundos
   - Efeitos de status ao morrer
   - Cache de animações ao trocar de personagem
5. Sistema de arremesso:
   - Limite de 3 arremessos por arma
   - Armas ficam disponíveis para coleta
   - Física realista com ricochete
   - Dano baseado na velocidade do impacto

## 🆘 Solução de Problemas

1. Se os efeitos de sangue não aparecerem:
   - Verifique se as partículas estão habilitadas
   - Confirme se o ID da textura de sangue está correto

2. Se os efeitos de status não funcionarem:
   - Verifique se os NumberValues de chance estão configurados
   - Confirme se o personagem tem todas as partes necessárias

3. Se o dano localizado não funcionar:
   - Verifique se as partes do corpo têm os nomes corretos
   - Confirme se a hitbox está no tamanho adequado

4. Se o arremesso não funcionar:
   - Verifique se o TipoArma está configurado como "arremessavel"
   - Confirme se o Handle está configurado corretamente
   - Verifique se o contador de arremessos não excedeu o limite

5. Se a arma não puder ser coletada após o arremesso:
   - Verifique se o Handle tem CanCollide ativado
   - Confirme se a física está configurada corretamente

## 🔊 Sistema de Áudio

O sistema inclui sons de combate que são reproduzidos no servidor, permitindo que todos os jogadores próximos ouçam os efeitos sonoros:

### Sons para Armas Melee
- **SonoroNormal**: Som do ataque normal
- **SonoroEspecial**: Som do ataque especial

### Sons para Armas Arremessáveis
- **SonoroArremesso**: Som do arremesso
- **SonoroEspecial**: Som do ataque especial

### Configuração dos Sons
Para configurar os sons de uma arma, adicione objetos Sound dentro da Tool:

```lua
-- Para armas melee
local sonoroNormal = Instance.new("Sound")
sonoroNormal.Name = "SonoroNormal"
sonoroNormal.SoundId = "rbxassetid://SEU_ID_DE_SOM"
sonoroNormal.Volume = 0.5  -- Volume padrão
sonoroNormal.RollOffMaxDistance = 50  -- Distância máxima que o som pode ser ouvido
sonoroNormal.RollOffMode = Enum.RollOffMode.LinearSquare
sonoroNormal.Parent = tool

local sonoroEspecial = Instance.new("Sound")
sonoroEspecial.Name = "SonoroEspecial"
sonoroEspecial.SoundId = "rbxassetid://SEU_ID_DE_SOM"
sonoroEspecial.Volume = 0.5
sonoroEspecial.RollOffMaxDistance = 50
sonoroEspecial.RollOffMode = Enum.RollOffMode.LinearSquare
sonoroEspecial.Parent = tool

-- Para armas arremessáveis
local sonoroArremesso = Instance.new("Sound")
sonoroArremesso.Name = "SonoroArremesso"
sonoroArremesso.SoundId = "rbxassetid://SEU_ID_DE_SOM"
sonoroArremesso.Volume = 0.5
sonoroArremesso.RollOffMaxDistance = 50
sonoroArremesso.RollOffMode = Enum.RollOffMode.LinearSquare
sonoroArremesso.Parent = tool
```

Se os sons não forem configurados, o sistema criará objetos Sound vazios que podem ser configurados posteriormente.

### Características do Sistema de Áudio
- Sons 3D espaciais
- Atenuação de volume baseada na distância
- Reprodução no servidor para sincronização
- Limpeza automática dos sons após reprodução
- Volume e distância configuráveis por arma 

## Criando uma Arma Melee

### 1. Criação Básica
1. Crie uma nova Tool no Roblox Studio
2. Adicione um Part como Handle
3. Configure a aparência da arma como desejar

### 2. Configurações Obrigatórias
Adicione os seguintes valores à Tool:

```lua
-- Tipo da arma (StringValue)
local tipoArma = Instance.new("StringValue")
tipoArma.Name = "TipoArma"
tipoArma.Value = "melee"

-- Cooldown entre ataques (NumberValue)
local cooldown = Instance.new("NumberValue")
cooldown.Name = "Cooldown"
cooldown.Value = 1 -- Em segundos

-- Dano do ataque normal (NumberValue)
local danoNormal = Instance.new("NumberValue")
danoNormal.Name = "DanoNormal"
danoNormal.Value = 5

-- Dano do ataque especial (NumberValue)
local danoEspecial = Instance.new("NumberValue")
danoEspecial.Name = "DanoEspecial"
danoEspecial.Value = 8
```

### 3. Configuração das Animações
Adicione IDs de animação para os ataques:

```lua
-- Animação de ataque normal (StringValue)
local slashAnimation = Instance.new("StringValue")
slashAnimation.Name = "slashAnimation"
slashAnimation.Value = "rbxassetid://SEU_ID_DE_ANIMACAO"

-- Animação de ataque especial (StringValue)
local specialAnimation = Instance.new("StringValue")
specialAnimation.Name = "specialAnimation"
specialAnimation.Value = "rbxassetid://SEU_ID_DE_ANIMACAO"
```

### 4. Configuração dos Sons
Adicione os objetos Sound necessários:

```lua
-- Som de equipar
local sonoroEquipar = Instance.new("Sound")
sonoroEquipar.Name = "SonoroEquipar"
sonoroEquipar.SoundId = "rbxassetid://SEU_ID_DE_SOM"
sonoroEquipar.Volume = 0.5
sonoroEquipar.RollOffMaxDistance = 50

-- Som de desequipar
local sonoroDesequipar = Instance.new("Sound")
sonoroDesequipar.Name = "SonoroDesequipar"
sonoroDesequipar.SoundId = "rbxassetid://SEU_ID_DE_SOM"
sonoroDesequipar.Volume = 0.5
sonoroDesequipar.RollOffMaxDistance = 50

-- Som de ataque normal
local sonoroNormal = Instance.new("Sound")
sonoroNormal.Name = "SonoroNormal"
sonoroNormal.SoundId = "rbxassetid://SEU_ID_DE_SOM"
sonoroNormal.Volume = 0.5
sonoroNormal.RollOffMaxDistance = 50

-- Som de ataque especial
local sonoroEspecial = Instance.new("Sound")
sonoroEspecial.Name = "SonoroEspecial"
sonoroEspecial.SoundId = "rbxassetid://SEU_ID_DE_SOM"
sonoroEspecial.Volume = 0.5
sonoroEspecial.RollOffMaxDistance = 50

-- Som de erro (quando não acerta nada)
local sonoroErrouAlvo = Instance.new("Sound")
sonoroErrouAlvo.Name = "SonoroErrouAlvo"
sonoroErrouAlvo.SoundId = "rbxassetid://SEU_ID_DE_SOM"
sonoroErrouAlvo.Volume = 0.5
sonoroErrouAlvo.RollOffMaxDistance = 50
```

## Criando uma Arma Arremessável

### 1. Criação Básica
Siga os mesmos passos iniciais da arma melee, mas com algumas configurações adicionais.

### 2. Configurações Obrigatórias
```lua
-- Tipo da arma (StringValue)
local tipoArma = Instance.new("StringValue")
tipoArma.Name = "TipoArma"
tipoArma.Value = "arremessavel"

-- Cooldown entre arremessos (NumberValue)
local cooldown = Instance.new("NumberValue")
cooldown.Name = "Cooldown"
cooldown.Value = 1

-- Dano do arremesso (NumberValue)
local danoArremesso = Instance.new("NumberValue")
danoArremesso.Name = "ArremessoDano"
danoArremesso.Value = 12

-- Velocidade do arremesso (NumberValue)
local arremessoSpeed = Instance.new("NumberValue")
arremessoSpeed.Name = "ArremessoSpeed"
arremessoSpeed.Value = 50

-- Dano do ataque especial (NumberValue)
local danoEspecial = Instance.new("NumberValue")
danoEspecial.Name = "DanoEspecial"
danoEspecial.Value = 8
```

### 3. Configuração das Animações
```lua
-- Animação de arremesso (StringValue)
local specialAnimation = Instance.new("StringValue")
specialAnimation.Name = "specialAnimation"
specialAnimation.Value = "rbxassetid://SEU_ID_DE_ANIMACAO"
```

### 4. Configuração dos Sons
```lua
-- Som de equipar
local sonoroEquipar = Instance.new("Sound")
sonoroEquipar.Name = "SonoroEquipar"
sonoroEquipar.SoundId = "rbxassetid://SEU_ID_DE_SOM"
sonoroEquipar.Volume = 0.5
sonoroEquipar.RollOffMaxDistance = 50

-- Som de desequipar
local sonoroDesequipar = Instance.new("Sound")
sonoroDesequipar.Name = "SonoroDesequipar"
sonoroDesequipar.SoundId = "rbxassetid://SEU_ID_DE_SOM"
sonoroDesequipar.Volume = 0.5
sonoroDesequipar.RollOffMaxDistance = 50

-- Som de arremesso
local sonoroArremesso = Instance.new("Sound")
sonoroArremesso.Name = "SonoroArremesso"
sonoroArremesso.SoundId = "rbxassetid://SEU_ID_DE_SOM"
sonoroArremesso.Volume = 0.5
sonoroArremesso.RollOffMaxDistance = 50

-- Som de impacto em personagem
local sonoroNormal = Instance.new("Sound")
sonoroNormal.Name = "SonoroNormal"
sonoroNormal.SoundId = "rbxassetid://SEU_ID_DE_SOM"
sonoroNormal.Volume = 0.5
sonoroNormal.RollOffMaxDistance = 50

-- Som de ataque especial
local sonoroEspecial = Instance.new("Sound")
sonoroEspecial.Name = "SonoroEspecial"
sonoroEspecial.SoundId = "rbxassetid://SEU_ID_DE_SOM"
sonoroEspecial.Volume = 0.5
sonoroEspecial.RollOffMaxDistance = 50

-- Som quando erra o alvo
local sonoroErrouAlvo = Instance.new("Sound")
sonoroErrouAlvo.Name = "SonoroErrouAlvo"
sonoroErrouAlvo.SoundId = "rbxassetid://SEU_ID_DE_SOM"
sonoroErrouAlvo.Volume = 0.5
sonoroErrouAlvo.RollOffMaxDistance = 50
```

### 5. Configuração do Handle
Para armas arremessáveis, o Handle precisa de configurações específicas:
```lua
local handle = tool:WaitForChild("Handle")
handle.CanCollide = true
handle.CustomPhysicalProperties = PhysicalProperties.new(
    0.7,  -- Densidade
    0.3,  -- Fricção
    0.5,  -- Elasticidade
    1,    -- Peso
    1     -- Força do material
)
```

## Controles
- **Clique Esquerdo**: Ataque normal (melee) ou arremesso (arremessável)
- **Tecla E**: Ataque especial
- **ShiftLock**: Ativado automaticamente ao equipar a arma

## Sistema de Sons
O sistema inclui os seguintes sons:

### Sons Comuns (Todas as Armas)
- **SonoroEquipar**: Toca ao equipar a arma
- **SonoroDesequipar**: Toca ao desequipar a arma
- **SonoroErrouAlvo**: Toca quando um ataque não acerta nenhum alvo

### Sons para Armas Melee
- **SonoroNormal**: Toca quando um ataque normal acerta
- **SonoroEspecial**: Toca quando um ataque especial acerta

### Sons para Armas Arremessáveis
- **SonoroArremesso**: Toca no momento do arremesso
- **SonoroNormal**: Toca quando a arma arremessada atinge um personagem
- **SonoroEspecial**: Toca quando o ataque especial acerta
- **SonoroErrouAlvo**: Toca quando a arma atinge o ambiente

## Solução de Problemas

### Arma não causa dano
- Verifique se todos os valores numéricos estão configurados
- Confirme se o TipoArma está correto
- Verifique se a hitbox está no tamanho adequado

### Arremesso não funciona
- Verifique se TipoArma está como "arremessavel"
- Confirme se o Handle está configurado corretamente
- Verifique se o contador de arremessos não excedeu o limite (3)

### Sons não tocam
- Verifique se todos os objetos Sound estão presentes
- Confirme se os IDs dos sons são válidos
- Verifique se o Volume e RollOffMaxDistance estão configurados

### Animações não funcionam
- Verifique se os IDs das animações são válidos
- Confirme se os nomes dos valores de animação estão corretos
- Verifique se as animações estão no formato R15/R6 correto 

# Sistema de Armas - Instruções

## Tipos de Armas

### 1. Arma Melee (Normal)
- Clique normal: Ataque normal com animação de slash (usa DanoNormal)
- Tecla E: Ataque especial com animação especial (usa DanoEspecial)

### 2. Arma Arremessável
- Clique normal: Arremessa a arma com animação de arremesso (usa ArremessoDano)
  - O arremesso e o som acontecem 0.2 segundos antes do fim da animação
  - O cooldown determina a duração total da animação
- Tecla E: Ataque normal com animação de slash (usa DanoNormal)

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
danoNormal.Value = 10 -- Dano do ataque normal
danoNormal.Parent = tool

local danoEspecial = Instance.new("NumberValue")
danoEspecial.Name = "DanoEspecial"
danoEspecial.Value = 10 -- Dano do ataque especial (tecla E)
danoEspecial.Parent = tool

-- Cooldown (NumberValue)
local cooldown = Instance.new("NumberValue")
cooldown.Name = "Cooldown"
cooldown.Value = 1 -- Duração da animação em segundos
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

-- Dano e velocidade do arremesso (para o clique normal)
local arremessoSpeed = Instance.new("NumberValue")
arremessoSpeed.Name = "ArremessoSpeed"
arremessoSpeed.Value = 50 -- Velocidade do arremesso
arremessoSpeed.Parent = tool

local arremessoDano = Instance.new("NumberValue")
arremessoDano.Name = "ArremessoDano"
arremessoDano.Value = 10 -- Dano do arremesso
arremessoDano.Parent = tool

-- Cooldown
local cooldown = Instance.new("NumberValue")
cooldown.Name = "Cooldown"
cooldown.Value = 1 -- Duração total da animação em segundos
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
- `DanoEspecial`: Dano do ataque especial (tecla E)
- `Cooldown`: Tempo entre ataques e duração da animação
- `slashAnimation`: ID da animação do ataque normal
- `specialAnimation`: ID da animação do ataque especial

### Arma Arremessável
- `DanoNormal`: Dano do ataque normal (tecla E)
- `ArremessoSpeed`: Velocidade do arremesso (clique normal)
- `ArremessoDano`: Dano causado pelo arremesso (clique normal)
- `Cooldown`: Duração total da animação de arremesso
  - O arremesso acontece 0.2 segundos antes do fim da animação
  - Exemplo: Se Cooldown = 1, o arremesso acontece em 0.8 segundos
- `slashAnimation`: ID da animação do ataque normal (tecla E)
- `specialAnimation`: ID da animação do arremesso (clique normal)

## Configuração de Arma Arremessável

### Valores Específicos
- `ArremessoSpeed` - Velocidade do arremesso
- `ArremessoDano` - Dano do arremesso

### Comportamento
- Clique normal: Arremessa a arma
  - A arma é arremessada 0.2 segundos antes do fim da animação
  - O som de arremesso toca junto com o arremesso
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
cooldown.Value = 1 -- Arremesso acontece em 0.8 segundos
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
