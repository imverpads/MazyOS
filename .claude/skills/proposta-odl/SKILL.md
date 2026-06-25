---
name: proposta-odl
description: >
  Gera proposta comercial consultiva e personalizada para um cliente a partir do diagnóstico ODL.
  Nunca usa pacotes fixos — cada proposta é construída com base nos gargalos identificados,
  objetivos do cliente e prioridades de implementação definidas no diagnóstico. Use quando o
  usuário disser "criar proposta para", "montar proposta de", "proposta ODL para", "/proposta-odl"
  ou após concluir um diagnóstico com /diagnostico-odl.
---

# /proposta-odl — Proposta comercial consultiva

Terceira skill do núcleo ODL. Transforma o diagnóstico em proposta personalizada. A entrada principal é o `gargalos.json` — o conteúdo da proposta deriva integralmente do que foi encontrado no diagnóstico, não de um template genérico.

## Arquitetura de dados

```
clientes/<Empresa>/
├── empresa.json                       ← lido e atualizado (fase: proposta)
├── diagnostico/
│   └── gargalos.json                  ← entrada principal obrigatória
└── proposta/
    ├── proposta-<YYYY-MM-DD>.md       ← versão editável
    └── proposta-<YYYY-MM-DD>.html     ← versão visual para apresentação e exportação PDF
```

## Dependências

- `clientes/<Empresa>/diagnostico/gargalos.json` — obrigatório, entrada principal
- `clientes/<Empresa>/empresa.json` — dados básicos do cliente
- `identidade/design-guide.md` — identidade visual para a versão HTML
- `_memoria/empresa.md` — contexto do negócio (Joabe Silva / ODL)
- `_memoria/preferencias.md` — tom de voz

---

## Workflow

### Passo 1 — Carregar diagnóstico

1. Verificar se `clientes/<Empresa>/diagnostico/gargalos.json` existe
2. **Se não existir:** não prosseguir. Informar:
   > "Preciso do diagnóstico de [Empresa] antes de montar a proposta. Quer que eu inicie com /diagnostico-odl?"
3. **Se existir:** carregar e ler os gargalos, prioridades, problema central e recomendações
4. Carregar `empresa.json` para complementar os dados

### Passo 2 — Coletar complementos necessários

Com base no `gargalos.json`, identificar o que ainda falta para montar a proposta:

- **Anotações da reunião:** decisões, preferências ou contexto discutido que não está no diagnóstico?
- **Objetivos declarados do cliente:** o que ele quer alcançar nos próximos 3-6 meses?
- **Restrições:** orçamento aproximado, prazo, recursos disponíveis?
- **Soluções já discutidas informalmente:** alguma coisa foi apresentada na reunião de diagnóstico?

Solicitar apenas o que não estiver disponível no `gargalos.json` ou `empresa.json`.

### Passo 3 — Definir escopo da proposta

Com base nos gargalos e objetivos, definir:

1. **Soluções recomendadas** — quais pilares ODL serão trabalhados e por quê (referência direta ao diagnóstico)
2. **O que não entra nessa fase** — e por quê (mostrar raciocínio estratégico, não limitação)
3. **Cronograma de implementação** — dividido em fases com entregas concretas
4. **Investimento** — solicitar ao Joabe os valores antes de incluir; nunca inventar ou estimar

Para cada solução recomendada, registrar internamente:
- Gargalo do `gargalos.json` que ela resolve
- Pilar ODL correspondente
- Impacto esperado
- Prazo de implementação

### Passo 4 — Gerar proposta em Markdown (proposta-YYYY-MM-DD.md)

```markdown
# Proposta de Estruturação Digital
## [Nome da Empresa] × Joabe Silva
Data: [data] | Válida por: 15 dias

---

## Contexto da Empresa

[Síntese de 2-3 parágrafos sobre a situação atual — honesta, baseada no diagnóstico.
Mostrar que o Joabe entende a operação do cliente antes de apresentar qualquer solução.]

---

## Diagnóstico Resumido

### Problema Central
[Uma frase clara — extraída diretamente do gargalos.json]

### Causa Raiz
[Uma frase — por que esse problema existe]

### Impacto Atual
[O que esse problema está custando ao negócio — concreto, sem exagero]

### Os 3 principais gargalos identificados

1. **[Pilar]:** [descrição do gargalo e seu impacto]
2. **[Pilar]:** [descrição do gargalo e seu impacto]
3. **[Pilar]:** [descrição do gargalo e seu impacto]

---

## Objetivos da Implementação

[O que será alcançado ao final — baseado nos objetivos declarados do cliente, não em promessas genéricas]

---

## Solução Recomendada

**[Título da implementação — ex: "Operação Digital Local — Fase 1: Fundação"]**

[Parágrafo explicando a lógica da escolha: por que essas soluções, nessa ordem, para esse cliente específico]

### O que será implementado

#### [Solução 1 — ex: Estruturação do Google Meu Negócio]
**Problema que resolve:** [gargalo do diagnóstico]
**O que será feito:** [descrição objetiva da entrega]
**Resultado esperado:** [impacto concreto]

#### [Solução 2]
[mesma estrutura]

#### [Solução N]
[mesma estrutura]

---

## O que não entra nessa fase

[Listar o que foi deixado para fora e por quê — mostra raciocínio, não limitação]

---

## Cronograma de Implementação

| Fase | Período | Entregas |
|------|---------|----------|
| Fase 1 — Fundação | Semanas 1-2 | [entregas específicas] |
| Fase 2 — Estruturação | Semanas 3-4 | [entregas específicas] |
| Fase 3 — Ativação | Mês 2 | [entregas específicas] |

---

## Investimento

| Solução | Valor |
|---------|-------|
| [Solução 1] | R$ [X] |
| [Solução 2] | R$ [X] |
| **Total** | **R$ [X]** |

Forma de pagamento: [conforme prática do Joabe]
Validade desta proposta: 15 dias a partir de [data]

---

## Próximos Passos

1. Aprovação da proposta
2. [Primeira ação após fechamento — ex: kick-off de briefing, acesso às ferramentas]
3. [Início da Fase 1]

---

*Esta proposta foi construída com base no diagnóstico realizado em [data]. Cada solução recomendada tem origem direta em um gargalo identificado — não é um pacote padrão adaptado ao nome da empresa.*
```

### Passo 5 — Gerar proposta em HTML (proposta-YYYY-MM-DD.html)

Versão visual profissional para apresentação e exportação em PDF.

- Ler `identidade/design-guide.md` antes de criar — aplicar cores, tipografia e logo
- HTML responsivo, inline CSS, exportável com `Ctrl+P → Salvar como PDF`
- Estrutura de seções com navegação visual clara
- Header: logo Joabe Silva + nome do cliente + data
- Footer: validade, contato, site
- Destaque visual para: problema central, investimento total e próximos passos

**Hierarquia visual das seções:**
1. Capa / Header — identidade + nome do cliente
2. Contexto — fundo neutro, leitura tranquila
3. Diagnóstico — destaque nos gargalos (cor de alerta suave)
4. Solução — destaque positivo (cor da marca)
5. Cronograma — tabela limpa
6. Investimento — box destacado com total
7. Próximos passos — CTA visual claro

### Passo 6 — Atualizar empresa.json

Atualizar `"fase": "proposta"` e `"atualizado_em"`.

### Passo 7 — Resumo final

```
Proposta gerada: [Nome da Empresa]
Data: [data] | Válida por: 15 dias

[N] soluções no escopo | Investimento total: R$ [X]

Arquivos salvos em clientes/[Empresa]/proposta/

Próximos passos:
→ Se o cliente fechar: /novo-projeto para iniciar a implementação
→ Para ajustar escopo ou valores: editar proposta-[data].md e regenerar o HTML
```

---

## Regras

- `gargalos.json` é obrigatório — sem diagnóstico concluído não há proposta
- Nunca criar proposta com soluções genéricas — cada item referencia um gargalo específico
- Não mencionar tecnologias ou ferramentas sem explicar o problema que resolvem
- Investimento: solicitar ao Joabe antes de incluir — nunca inventar, estimar ou deixar em branco com "a definir"
- HTML: usar `identidade/design-guide.md` — não improvisar estilo
- Validade padrão: 15 dias (ajustar se o Joabe indicar outro prazo)
- Tom: consultivo, não vendedor — a proposta explica o raciocínio, não empurra produto
- Nenhuma saída fica só na tela — tudo vai para arquivo
