---
name: diagnostico-odl
description: >
  Realiza o diagnóstico completo de um cliente pelo método ODL durante ou após a reunião.
  Importa automaticamente os dados da auditoria rápida quando existirem, evitando perguntas
  repetidas. Analisa os 7 pilares ODL em profundidade, gera relatório técnico interno (.md),
  apresentação HTML para o cliente e gargalos.json como base para a proposta. Use quando o
  usuário disser "diagnóstico de", "fazer diagnóstico ODL", "analisar cliente", "reunião de
  diagnóstico com", "/diagnostico-odl" ou iniciar a fase de diagnóstico de um cliente.
---

# /diagnostico-odl — Diagnóstico completo pelo método ODL

Segunda skill do núcleo ODL. Aprofunda a análise iniciada na auditoria rápida durante a reunião com o cliente. Entrega o Dossiê ODL completo: relatório interno, apresentação para o cliente e `gargalos.json` para alimentar a proposta.

## Arquitetura de dados

```
clientes/<Empresa>/
├── empresa.json                  ← lido e atualizado (fase: diagnostico)
├── prospeccao/
│   └── auditoria.json            ← lido se existir, evita repetição de dados
└── diagnostico/
    ├── relatorio-odl.md          ← relatório técnico interno
    ├── apresentacao.html         ← apresentação para o cliente
    └── gargalos.json             ← entrada obrigatória para /proposta-odl
```

## Dependências

- `_memoria/empresa.md` — contexto e posicionamento do negócio
- `_memoria/preferencias.md` — tom de voz para todos os textos gerados
- `identidade/design-guide.md` — identidade visual para a apresentação HTML
- `clientes/<Empresa>/empresa.json` — dados básicos do cliente
- `clientes/<Empresa>/prospeccao/auditoria.json` — dados da auditoria rápida (quando existir)

---

## Workflow

### Passo 1 — Carregar contexto existente

1. Verificar se `clientes/<Empresa>/empresa.json` existe — carregar se existir
2. Verificar se `clientes/<Empresa>/prospeccao/auditoria.json` existe — carregar se existir
3. Informar o que já está disponível:
   > "Já tenho a auditoria de [Empresa] (Score ODL: [X]/100). Vou usar essas informações como base e aprofundar o que for necessário na reunião."
4. Se não houver nenhum dado anterior: coletar nome, segmento, cidade e canais antes de continuar

### Passo 2 — Identificar lacunas e preparar perguntas de reunião

Com base nos dados existentes (ou na ausência deles), gerar perguntas de aprofundamento organizadas por pilar. Adaptar para não repetir o que já foi coletado na auditoria.

**Banco de perguntas por pilar (selecionar as mais relevantes):**

- **Posicionamento:** "Como você descreveria seu diferencial para alguém que nunca ouviu falar de você?" / "Quem é seu cliente ideal — o que ele tem, quer e onde está?"
- **Presença Digital:** "Quando foi a última vez que você atualizou seu perfil no Google?" / "Você sabe quantas pessoas encontram sua empresa pelo Google por mês?"
- **Aquisição:** "De onde vêm a maioria dos seus clientes hoje — indicação, busca, redes sociais, tráfego pago?" / "Você faz alguma ação ativa para trazer clientes ou espera eles chegarem?"
- **Conversão:** "Quando alguém entra em contato, quanto tempo leva até você responder?" / "Quantos dos contatos que chegam viram clientes? Você sabe esse número?"
- **Atendimento:** "Você usa algum sistema para acompanhar os leads que não fecharam?" / "O que acontece depois que o cliente fecha — tem algum processo de pós-venda?"
- **Automação:** "O que no seu atendimento ainda depende 100% de você para funcionar?" / "Se você tivesse 10x mais leads amanhã, sua operação aguentaria?"
- **Escalabilidade:** "Se você ficasse 2 semanas sem trabalhar, o que pararia de funcionar?" / "Tem alguém que faz o que você faz quando você não está?"

### Passo 3 — Executar diagnóstico por pilar

Após a reunião ou com base nas respostas coletadas, analisar cada pilar em profundidade:

#### 1. Posicionamento (peso: 15)
- Nicho claro? Especialista ou generalista?
- Proposta de valor: o cliente consegue dizer em uma frase o que a empresa faz e para quem?
- Diferenciação: o que os concorrentes não têm ou não fazem?
- Comunicação: o posicionamento aparece de forma consistente nos canais digitais?

#### 2. Presença Digital (peso: 20)
- GMB: completo, verificado, ativo, com avaliações e respostas?
- Instagram: frequência, qualidade, identidade visual consistente?
- Site: funcional, persuasivo, otimizado para conversão e mobile?
- Consistência entre canais: nome, telefone, categoria, horário, foto de perfil?

#### 3. Aquisição (peso: 15)
- Canais de entrada: ativos ou apenas passivos (esperar o cliente chegar)?
- Tráfego pago: Google Ads, Meta Ads — usa? Com que estratégia e resultado?
- SEO local: aparece quando o cliente pesquisa o serviço + cidade?
- Indicação: tem processo estruturado ou é aleatória e não escalável?
- Captação: tem lista de contatos, e-mail ou WhatsApp estruturado?

#### 4. Conversão (peso: 15)
- Primeira resposta: tempo e qualidade do atendimento inicial
- Script de atendimento: existe ou improvisa em cada contato?
- Taxa de conversão: quantos contatos viram clientes? Sabe o número?
- Proposta ou orçamento: tem padrão ou é feito do zero a cada vez?
- Objeções comuns: como lida com preço, prazo, "vou pensar"?

#### 5. Atendimento (peso: 15)
- Pós-venda: existe acompanhamento depois do fechamento?
- Retenção: clientes voltam? Com que frequência?
- Indicação espontânea: clientes indicam? Com que frequência?
- Reclamações: como são identificadas e tratadas?

#### 6. Automação (peso: 10)
- WhatsApp Business: configurado com mensagens automáticas?
- CRM: usa algum sistema de gestão de clientes?
- Processos: alguma etapa do atendimento é automatizada (notificações, lembretes, follow-up)?
- Dependência operacional: o que para quando o dono não está?

#### 7. Escalabilidade (peso: 10)
- Dependência do dono: o que só funciona com ele presente?
- Equipe: tem? É capacitada para operar sem o dono?
- Processos documentados: existe algum SOP, checklist, roteiro?
- Tecnologia: usa ferramentas que escalam sem aumentar o esforço proporcionalmente?

### Passo 4 — Identificar problema central e causa raiz

Após analisar os 7 pilares, sintetizar:

- **Problema central:** qual é o gargalo que mais limita o crescimento hoje?
- **Causa raiz:** por que esse problema existe — o que o originou e o mantém?
- **Impacto no negócio:** o que esse problema custa em receita, tempo ou reputação?
- **Prioridade de implementação:** quais pilares atacar primeiro (menor esforço + maior impacto)?
- **Próximos passos:** o que acontece nas próximas 4 semanas se nada mudar?

### Passo 5 — Gerar relatório técnico interno (relatorio-odl.md)

```markdown
# Dossiê ODL — [Nome da Empresa]
Data: [data] | Consultor: Joabe Silva

## Resumo Executivo
[Síntese de 3-5 frases: quem é a empresa, qual é o problema central, qual é a oportunidade]

## Pontos Fortes
[O que já funciona bem — honesto, não forçado]

## Mapa de Gargalos ODL
| Pilar | Nota | Situação |
|-------|------|----------|
| Posicionamento | /15 | [síntese] |
| Presença Digital | /20 | [síntese] |
| Aquisição | /15 | [síntese] |
| Conversão | /15 | [síntese] |
| Atendimento | /15 | [síntese] |
| Automação | /10 | [síntese] |
| Escalabilidade | /10 | [síntese] |
| **Total** | **/100** | |

## Análise por Pilar

### [Nome do Pilar]
**Situação atual:** [o que foi encontrado com base em evidências]
**Causa raiz:** [por que isso acontece]
**Impacto:** [o que isso custa ao negócio — concreto]
**Recomendação:** [o que implementar para resolver]

[Repetir para os 7 pilares]

## Problema Central
[Uma frase clara que resume o gargalo principal]

## Prioridade de Implementação
1. [Ação mais urgente] — impacto: [X] — prazo estimado: [Y]
2. ...

## Próximos Passos
[O que acontece a partir do fechamento da proposta]

## Checklist de Melhorias
- [ ] [item por pilar, em ordem de prioridade]
```

### Passo 6 — Gerar apresentação HTML para o cliente (apresentacao.html)

Apresentação profissional para ser mostrada durante a reunião ou enviada depois. Requisitos:

- Visual com identidade da marca: ler `identidade/design-guide.md` antes de criar
- HTML responsivo, exportável para PDF via `Ctrl+P → Salvar como PDF`
- Inline CSS, sem dependências externas além de Google Fonts
- Estrutura de seções (não slides) — leitura linear e fluida

**Estrutura de seções:**
1. Capa — nome da empresa, data, "Dossiê ODL por Joabe Silva"
2. Situação atual — resumo honesto e direto
3. Mapa de Gargalos ODL — visual com pontuação por pilar
4. Top 3 oportunidades — com impacto estimado em cada uma
5. Plano de estruturação recomendado — o que seria implementado e por quê
6. Próximos passos — CTA claro para avançar

### Passo 7 — Salvar gargalos.json

```json
{
  "empresa": "",
  "data_diagnostico": "YYYY-MM-DD",
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
  "problema_central": "",
  "causa_raiz": "",
  "impacto_estimado": "",
  "pontos_fortes": [],
  "pilares": {
    "posicionamento": {
      "nota": 0,
      "situacao_atual": "",
      "causa_raiz": "",
      "impacto": "",
      "recomendacao": "",
      "gargalos": []
    },
    "presenca_digital": { "nota": 0, "situacao_atual": "", "causa_raiz": "", "impacto": "", "recomendacao": "", "gargalos": [] },
    "aquisicao": { "nota": 0, "situacao_atual": "", "causa_raiz": "", "impacto": "", "recomendacao": "", "gargalos": [] },
    "conversao": { "nota": 0, "situacao_atual": "", "causa_raiz": "", "impacto": "", "recomendacao": "", "gargalos": [] },
    "atendimento": { "nota": 0, "situacao_atual": "", "causa_raiz": "", "impacto": "", "recomendacao": "", "gargalos": [] },
    "automacao": { "nota": 0, "situacao_atual": "", "causa_raiz": "", "impacto": "", "recomendacao": "", "gargalos": [] },
    "escalabilidade": { "nota": 0, "situacao_atual": "", "causa_raiz": "", "impacto": "", "recomendacao": "", "gargalos": [] }
  },
  "prioridade_implementacao": [
    {
      "ordem": 1,
      "acao": "",
      "pilar": "",
      "impacto": "",
      "prazo_estimado": ""
    }
  ],
  "proximos_passos": []
}
```

### Passo 8 — Atualizar empresa.json

Atualizar `"fase": "diagnostico"` e `"atualizado_em"`.

### Passo 9 — Resumo final

```
Dossiê ODL concluído: [Nome da Empresa]
Score ODL: [X]/100

Problema central: [síntese em uma frase]

Arquivos salvos em clientes/[Empresa]/diagnostico/

Próximo passo:
→ /proposta-odl para transformar esse diagnóstico em proposta comercial
```

---

## Regras

- Sempre carregar `auditoria.json` quando existir — nunca perguntar dados já coletados
- Diagnóstico consultivo: identificar causas e impactos, não listar ferramentas
- Nota por pilar: honesta, baseada em evidências reais, sem inflacionar ou deflacionar
- Apresentação HTML: seguir `identidade/design-guide.md` — não improvisar estilo
- `gargalos.json` é obrigatório — é o que alimenta o `/proposta-odl`
- Tom: direto, diagnóstico, sem rodeios, sem linguagem de guru ou corporativês
- Nenhuma saída fica só na tela — tudo vai para arquivo
