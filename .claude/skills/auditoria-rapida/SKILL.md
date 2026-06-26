---
name: auditoria-rapida
description: >
  Executa a preparação da reunião de diagnóstico ODL Pet. Analisa a presença digital de um
  negócio pet (GMB, Instagram, site, WhatsApp) após a reunião ser confirmada — nunca antes
  do primeiro contato. Calcula o Score ODL Pet inicial, mapeia os gargalos visíveis e gera
  roteiro de reunião. Use quando o usuário disser "preparar reunião com", "preparar análise
  de", "montar briefing de reunião", "auditoria de", "/auditoria-rapida" ou indicar que
  uma reunião com um cliente pet foi confirmada e precisa de preparação.
---

# /auditoria-rapida — Preparação de reunião ODL Pet

Executa a análise digital de um negócio pet após a reunião estar confirmada. Não é ferramenta de prospecção fria. A análise só acontece quando há reunião marcada — isso garante que o tempo investido em análise seja sobre alguém que vai aparecer.

## Posição no fluxo ODL Pet

```
Captação → Prospecção → Qualificação → Agendamento
                                              ↓
                                   /auditoria-rapida  ← AQUI
                                              ↓
                                   /diagnostico-odl (durante a reunião)
                                              ↓
                                   /proposta-odl
```

## Arquitetura de dados

```
clientes/<Empresa>/
├── empresa.json                  ← criado/atualizado
└── preparacao/
    ├── preparacao-reuniao.md     ← análise narrativa por canal
    ├── score-inicial.md          ← pontuação estimada com evidências
    ├── roteiro-reuniao.md        ← perguntas e pontos a apresentar
    └── auditoria.json            ← dados estruturados para /diagnostico-odl
```

## Dependências

- `_memoria/empresa.md` — contexto do negócio e posicionamento da marca
- `_memoria/preferencias.md` — tom de voz
- `clientes/<Empresa>/empresa.json` — carregado se o cliente já existir
- Acesso web (WebFetch/WebSearch) — para acessar GMB, Instagram e site

---

## Workflow

### Passo 1 — Verificar cliente existente

Checar se `clientes/<Empresa>/empresa.json` já existe.

- **Se existir:** carregar os dados e informar: "Já tenho dados de [Empresa]. Vou preparar a análise para a reunião confirmada."
- **Se não existir:** coletar os dados necessários antes de continuar

### Passo 2 — Confirmar dados da reunião

Verificar o que o usuário forneceu e solicitar apenas o que falta:

- [ ] Nome da empresa
- [ ] Segmento (pet shop / banho e tosa / clínica / misto)
- [ ] Cidade/bairro
- [ ] Link do Instagram (quando existir)
- [ ] Link do Google Meu Negócio (quando existir)
- [ ] Site (quando existir)
- [ ] Data da reunião confirmada

### Passo 3 — Executar análise por canal

Para cada canal disponível, analisar com WebFetch/WebSearch quando os links forem fornecidos.

#### Google Meu Negócio
- Perfil existe? Está verificado?
- Nota média e número de avaliações
- Avaliações respondidas? Com que qualidade?
- Fotos: quantidade e qualidade
- Categorias corretas?
- Horário atualizado?
- Posts recentes (últimos 30 dias)?
- Posição nos resultados locais: aparece no top 3 para "[serviço] [cidade/bairro]"?

#### Instagram
- Conta comercial ou pessoal?
- Bio: clara, com proposta de valor e link de contato?
- Data da última postagem
- Frequência dos últimos 3 meses
- Qualidade visual: consistente ou improvisada?
- Tipo de conteúdo: fotos do serviço, promoções, bastidores?
- Link na bio: onde vai? Funciona?

#### Site
- Existe e está no ar?
- Carrega no mobile?
- CTA visível (WhatsApp ou agendamento)?
- Serviços descritos claramente?

#### WhatsApp
- Número Business ou pessoal? Testar se disponível
- Mensagem automática configurada?
- Tempo de resposta estimado

### Passo 4 — Calcular Score ODL Pet inicial

Pontuar cada pilar com base nas evidências coletadas. Usar `odl_pet/metodo/score_odl_pet.md` como referência.

Pilares que não têm evidência suficiente de análise remota (Conversão, Atendimento, Automação, Escalabilidade) → marcar como "a confirmar na reunião".

| Pilar | Peso | Nota estimada | Evidência |
|-------|------|--------------|-----------|
| Posicionamento | 15 | | |
| Presença Digital | 20 | | |
| Aquisição | 15 | | |
| Conversão | 15 | (a confirmar) | |
| Atendimento | 15 | (a confirmar) | |
| Automação | 10 | (a confirmar) | |
| Escalabilidade | 10 | (a confirmar) | |
| **Total estimado** | **100** | | |

### Passo 5 — Mapear gargalos visíveis

Para cada problema encontrado, registrar:

- **Pilar:** qual pilar está afetado
- **Problema:** o que foi encontrado — baseado em evidência, não suposição
- **Evidência:** o que foi visto especificamente (número de avaliações, data da última postagem, etc.)
- **Impacto provável:** o que esse gargalo custa ao negócio
- **Prioridade:** alta / média / baixa

Ordenar por impacto + evidência. Os gargalos de alta prioridade são os que o Joabe vai apresentar primeiro na reunião.

### Passo 6 — Gerar roteiro da reunião

Com base nos gargalos encontrados, criar roteiro com:

1. **Abertura (5 min):** como posicionar a reunião — o que o empresário vai receber
2. **O que apresentar (15 min):** os gargalos visíveis com evidências — não opinião
3. **Perguntas de aprofundamento (20 min):** para os pilares que não puderam ser avaliados remotamente
4. **Encerramento (10 min):** como posicionar o próximo passo

Exemplo de abertura:
> "Preparei uma análise do [nome do negócio] com base no que está público. Vou te mostrar o que encontrei e depois quero entender melhor como funciona a operação por dentro."

### Passo 7 — Salvar todos os arquivos

**`empresa.json`** (raiz do cliente):
```json
{
  "nome": "",
  "segmento": "",
  "cidade": "",
  "canais": {
    "instagram": "",
    "google_meu_negocio": "",
    "site": "",
    "whatsapp": ""
  },
  "fase": "preparacao_reuniao",
  "reuniao": {
    "data": "YYYY-MM-DD",
    "confirmada": true
  },
  "criado_em": "YYYY-MM-DD",
  "atualizado_em": "YYYY-MM-DD"
}
```

**`auditoria.json`** (em `preparacao/`):
```json
{
  "empresa": "",
  "data_preparacao": "YYYY-MM-DD",
  "data_reuniao": "YYYY-MM-DD",
  "canais_analisados": [],
  "score_estimado": {
    "total": 0,
    "posicionamento": 0,
    "presenca_digital": 0,
    "aquisicao": 0,
    "conversao": "a confirmar",
    "atendimento": "a confirmar",
    "automacao": "a confirmar",
    "escalabilidade": "a confirmar"
  },
  "gargalos_visiveis": [
    {
      "pilar": "",
      "problema": "",
      "evidencia": "",
      "impacto": "",
      "prioridade": "alta|media|baixa"
    }
  ],
  "dados_coletados": {
    "gmb": {},
    "instagram": {},
    "site": {},
    "whatsapp": {}
  }
}
```

**`preparacao-reuniao.md`** — análise narrativa por canal com evidências encontradas

**`score-inicial.md`** — score estimado com justificativa por pilar e nota de que é parcial

**`roteiro-reuniao.md`** — roteiro completo: o que apresentar, em que ordem, perguntas de aprofundamento

### Passo 8 — Resumo final

```
Preparação concluída: [Nome da Empresa]
Reunião confirmada: [data]

Score estimado: [X]/100 (parcial — pilares operacionais a confirmar na reunião)

Top 3 gargalos identificados:
1. [pilar] → [problema] → [evidência]
2. ...
3. ...

Arquivos salvos em clientes/[Empresa]/preparacao/

Próximo passo:
→ /diagnostico-odl durante a reunião para aprofundar e fechar o diagnóstico completo
```

---

## Regras

- Esta skill é executada APÓS a reunião ser confirmada — nunca antes do primeiro contato
- O objetivo é chegar na reunião com evidências reais, não com opiniões
- Pilares operacionais (Conversão, Atendimento, Automação, Escalabilidade) são confirmados na reunião — não presumir sem evidência
- Score estimado é parcial — deixar claro ao usuário que é fotografia do digital público
- Gargalos: baseados em evidências concretas, não em suposições sobre o negócio
- Tom do roteiro: consultivo, diagnóstico — não vendedor
- `auditoria.json` é obrigatório — alimenta o `/diagnostico-odl`
- `empresa.json` deve ser criado ou atualizado em toda execução
- Nenhuma saída fica só na tela — tudo vai para arquivo
