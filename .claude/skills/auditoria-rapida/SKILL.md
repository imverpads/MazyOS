---
name: auditoria-rapida
description: >
  Audita uma empresa local durante a prospecção fria, antes do primeiro contato. Analisa
  presença digital (GMB, Instagram, site, WhatsApp), calcula um Score ODL inicial e gera
  oportunidades visíveis + abordagem comercial personalizada. Use quando o usuário disser
  "auditar empresa", "prospecção de X", "analisar empresa antes de contato", "score ODL de",
  "/auditoria-rapida" ou pedir análise de um negócio para prospecção.
---

# /auditoria-rapida — Auditoria de prospecção fria

Primeira skill do núcleo ODL. Analisa um negócio antes do primeiro contato, identifica oportunidades visíveis e prepara a abordagem comercial. Toda saída é salva em arquivos estruturados que alimentam as skills seguintes.

## Arquitetura de dados

```
clientes/<Empresa>/
├── empresa.json              ← criado/atualizado nessa skill
└── prospeccao/
    ├── auditoria-rapida.md   ← análise por canal
    ├── score-odl.md          ← pontuação por pilar
    ├── oportunidades.md      ← oportunidades priorizadas
    ├── abordagem-whatsapp.md ← mensagem de abordagem personalizada
    └── auditoria.json        ← dados estruturados para reutilização pelas próximas skills
```

## Dependências

- `_memoria/empresa.md` — contexto do negócio e posicionamento da marca
- `_memoria/preferencias.md` — tom de voz para a abordagem gerada
- `clientes/<Empresa>/empresa.json` — carregado se o cliente já existir no sistema
- Acesso web (WebFetch/WebSearch) — para auditar GMB, Instagram e site quando os links forem fornecidos

---

## Workflow

### Passo 1 — Verificar cliente existente

Checar se `clientes/<Empresa>/empresa.json` já existe.

- **Se existir:** carregar os dados e informar: "Já tenho dados de [Empresa] no sistema. Vou atualizar a auditoria com as informações novas."
- **Se não existir:** prosseguir para coleta de dados

### Passo 2 — Coletar dados disponíveis

Identificar o que o usuário já forneceu e listar o que ainda falta:

**Dados necessários:**
- [ ] Nome da empresa
- [ ] Segmento de atuação
- [ ] Cidade/região
- [ ] Link do Instagram (quando existir)
- [ ] Link do Google Meu Negócio (quando existir)
- [ ] Site (quando existir)
- [ ] WhatsApp comercial (quando disponível)

Solicitar APENAS os dados ausentes. Se a empresa não tiver algum canal, registrar como "ausente" — isso já é um gargalo identificado.

### Passo 3 — Executar auditoria por canal

Para cada canal disponível, analisar os pontos abaixo. Usar WebFetch/WebSearch para acessar os links fornecidos quando disponível.

#### Google Meu Negócio
- Perfil existe? Está verificado?
- Avaliação média e número de avaliações
- Empresa responde avaliações? Com que qualidade e frequência?
- Fotos: quantidade e qualidade
- Categorias: corretas e completas?
- Horário de funcionamento: atualizado?
- Posts no GMB: existe atividade?
- Perguntas e respostas: preenchidas?
- Telefone e site vinculados corretamente?

#### Instagram
- Perfil existe? É conta comercial ou pessoal?
- Bio: clara, com proposta de valor e link de contato?
- Frequência de postagem: ativo ou abandonado?
- Tipo de conteúdo: educativo, promocional, entretenimento, bastidores?
- Engajamento aparente (likes, comentários visíveis)
- Uso de stories, reels, highlights?
- Link na bio: para onde vai? Funciona?
- Identidade visual: consistente ou improvisada?

#### Site
- Existe? Está no ar?
- Carregamento: rápido ou lento?
- Mobile: responsivo?
- CTA claro acima da dobra?
- Formulário de contato ou botão WhatsApp?
- SEO básico: title, meta descrição, indexado no Google?
- Conteúdo: atualizado ou desatualizado?

#### WhatsApp
- Número comercial (WhatsApp Business) ou pessoal?
- Mensagem automática de saudação configurada?
- Catálogo de produtos/serviços?
- Horário de atendimento configurado?
- Link direto acessível no site/Instagram?

### Passo 4 — Calcular Score ODL

Pontuar cada pilar com base nos dados coletados. Total: 100 pontos.

| Pilar | Peso | O que avalia |
|-------|------|--------------|
| Posicionamento | 15 | Clareza do nicho, proposta de valor, diferenciação visível |
| Presença Digital | 20 | GMB, site, Instagram — existência, qualidade e atualização |
| Aquisição | 15 | Captação ativa: tráfego pago, SEO local, indicação estruturada |
| Conversão | 15 | CTA, processo de atendimento, tempo de resposta estimado |
| Atendimento | 15 | Automação, follow-up, qualidade do contato |
| Automação | 10 | WhatsApp Business, CRM, processos automatizados |
| Escalabilidade | 10 | Sistemas, documentação, independência do dono |

**Interpretação do score:**
- 0–30: Operação crítica — presença digital praticamente inexistente
- 31–50: Operação básica — existe mas sem estratégia
- 51–70: Operação em desenvolvimento — alguns pilares funcionam
- 71–85: Operação consolidada — estrutura sólida com pontos de melhoria
- 86–100: Operação referência — sistema completo e eficiente

### Passo 5 — Identificar e priorizar oportunidades

Para cada gargalo encontrado, documentar:

- **Problema:** o que está errado ou ausente
- **Causa provável:** por que isso acontece em negócios locais
- **Impacto:** o que esse gargalo custa ao negócio (clientes perdidos, reputação, receita)
- **Solução ODL:** o que seria implementado para resolver
- **Prioridade:** Alta / Média / Baixa

Ordenar pela combinação de impacto + facilidade de resolução. As oportunidades de Alta prioridade devem aparecer primeiro.

### Passo 6 — Gerar abordagem comercial

Criar mensagem personalizada para primeiro contato via WhatsApp com base nos gargalos encontrados.

A mensagem deve:
- Mencionar um problema específico que a empresa tem — sem ser arrogante ou condescendente
- Demonstrar que houve análise real, não é disparo em massa
- Gerar curiosidade, não vender imediatamente
- Ter no máximo 3-4 frases
- Tom: direto, consultivo, sem "oi tudo bem?" genérico

Seguir `_memoria/preferencias.md` rigorosamente. Evitar toda a lista de termos proibidos.

### Passo 7 — Salvar todos os arquivos

Criar a estrutura de pastas e salvar:

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
  "fase": "prospeccao",
  "criado_em": "YYYY-MM-DD",
  "atualizado_em": "YYYY-MM-DD"
}
```

**`auditoria.json`** (em `prospeccao/`):
```json
{
  "empresa": "",
  "data": "YYYY-MM-DD",
  "canais_analisados": [],
  "score_odl": {
    "total": 0,
    "posicionamento": 0,
    "presenca_digital": 0,
    "aquisicao": 0,
    "conversao": 0,
    "atendimento": 0,
    "automacao": 0,
    "escalabilidade": 0
  },
  "gargalos_visiveis": [
    {
      "pilar": "",
      "problema": "",
      "impacto": "",
      "prioridade": "alta|media|baixa"
    }
  ],
  "oportunidades": [],
  "dados_coletados": {
    "gmb": {},
    "instagram": {},
    "site": {},
    "whatsapp": {}
  }
}
```

**`auditoria-rapida.md`** — análise narrativa por canal com evidências encontradas

**`score-odl.md`** — tabela de pontuação com justificativa por pilar

**`oportunidades.md`** — lista priorizada de oportunidades com impacto e solução recomendada

**`abordagem-whatsapp.md`** — mensagem de abordagem pronta para envio

### Passo 8 — Resumo final

```
Auditoria concluída: [Nome da Empresa]
Score ODL: [X]/100 — [interpretação]

Top 3 oportunidades:
1. [problema] → [impacto estimado] → [solução ODL]
2. ...
3. ...

Arquivos salvos em clientes/[Empresa]/prospeccao/

Próximos passos:
→ Abordagem pronta em abordagem-whatsapp.md
→ /diagnostico-odl para análise completa na reunião com o cliente
```

---

## Regras

- Nunca assumir dados não fornecidos — identificar o que falta e solicitar antes de executar
- Se um canal não existe, registrar a ausência como gargalo — não ignorar
- Não vender ferramentas — diagnosticar problemas, causas e impactos
- Score ODL: ser honesto e baseado em evidências reais, não inflacionar para parecer mais oportunidade
- Abordagem de WhatsApp: personalizada por empresa, nunca template genérico ou disparo em massa
- `auditoria.json` é obrigatório — é o que alimenta o `/diagnostico-odl`
- `empresa.json` deve ser criado ou atualizado em toda execução
- Todos os textos gerados seguem `_memoria/preferencias.md`
- Nenhuma saída fica só na tela — tudo vai para arquivo
