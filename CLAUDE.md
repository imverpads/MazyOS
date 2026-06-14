# Joabe Silva — MazyOS

Consultoria de estruturação digital para negócios locais. Aqui ficam o método ODL, os clientes, as propostas, os conteúdos e as entregas. O sistema opera como um segundo cérebro — conhecimento documentado, processos replicáveis, operação previsível.

**Estrutura de pastas:**
- `_memoria/` — quem é o negócio, como falamos, foco atual
- `identidade/` — marca Joabe Silva (aplicada em todas as peças)
- `clientes/` — uma subpasta por cliente, autossuficiente
- `briefings/` — briefings antes de virar cliente
- `propostas/` — propostas em andamento
- `marketing/` — conteúdo institucional e de autoridade
- `saidas/` — documentos pontuais, análises, entregáveis avulsos
- `dados/` — arquivos a analisar (relatórios de cliente, exports)
- `scripts/` — automações, agentes e ferramentas internas

---

## Contexto do negócio

No início de toda conversa, ler os seguintes arquivos (quando existirem e estiverem preenchidos):

1. `_memoria/empresa.md` — quem é o Joabe, o que faz, como funciona o negócio
2. `_memoria/preferencias.md` — tom de voz, estilo de escrita, o que evitar
3. `_memoria/estrategia.md` — foco atual, prioridades, prazos

Usar essas informações como base pra qualquer resposta ou decisão. Ao sugerir prioridades, formatos ou abordagens, considerar o foco atual descrito em `estrategia.md`.

Pra qualquer tarefa visual (carrossel, post, proposta, landing page), consultar `identidade/design-guide.md` como referência de estilo.

Não listar o que foi lido nem confirmar a leitura. Usar o contexto naturalmente.

---

## Sobre a consultoria

Joabe Silva é uma consultoria especializada em estruturação digital para negócios locais via método ODL (Operação Digital Local). Opera em modelo consultivo: diagnóstico, planejamento, implementação e otimização.

Atende: clínicas, pet shops, imobiliárias, lojas, barbearias, prestadores de serviço — negócios com demanda existente mas operação digital desorganizada.

Serviços: posicionamento digital, Instagram estratégico, Google Meu Negócio, sites de autoridade e captação, automação de WhatsApp, agentes de IA, CRM, processos comerciais, tráfego pago, SEO local.

Operação solo, desenhada para escalar via IA, sistemas e processos documentados.

---

## Clientes ativos

*(Atualizar com `/atualizar` conforme novos clientes forem iniciados)*

---

## O que mais produzimos aqui

- Diagnósticos de operação digital para novos clientes
- Planos de implementação ODL
- Propostas comerciais
- Conteúdo estratégico e de autoridade (Instagram, LinkedIn)
- Agentes de IA e automações
- Sites e estruturas de captação
- Relatórios e análises de performance

---

## Tom de voz

Direto, diagnóstico, consultivo. Explica o porquê do problema antes de apresentar a solução. Frases curtas, sem enrolação, autoridade sem arrogância. Tecnologia traduzida para impacto financeiro e operacional.

**Evitar:** "vamos juntos", "alavanque", "potencialize", "método revolucionário", "sinergia", "mindset", "jornada", linguagem de guru de marketing, promessas milagrosas, hype, emojis em materiais formais, linguagem corporativa vazia.

---

## Regras do sistema

- Cliente novo → criar pasta `clientes/<NomeCliente>/` com briefing, diagnóstico ODL, estratégia e subpastas conforme entregas contratadas
- Proposta nova → `propostas/<cliente>-<data>.html` antes de fechar
- Casos de sucesso → `clientes/<NomeCliente>/caso.md` (reuso em pitches e conteúdo)
- Todo conteúdo gerado deve passar pelo filtro de tom de voz em `_memoria/preferencias.md`
- Para qualquer visual, consultar `identidade/design-guide.md` antes de criar

---

## Fluxo de trabalho

Antes de executar qualquer tarefa, verificar se existe skill relevante em `.claude/skills/`. Se encontrar, seguir as instruções da skill. Se não encontrar, executar normalmente.

Ao concluir uma tarefa que não tinha skill mas parece repetível, perguntar:
> "Isso pode virar uma skill pra próxima vez. Quer que eu crie?"

---

## Aprender com correções

Quando o Joabe corrigir algo ou der instrução permanente ("na verdade é assim", "não faça mais isso", "prefiro assim", "sempre que...", "da próxima vez..."), perguntar:
> "Quer que eu salve isso pra não precisar repetir?"

Se sim, identificar onde salvar:
- Sobre o negócio → `_memoria/empresa.md`
- Sobre preferências e estilo → `_memoria/preferencias.md`
- Sobre prioridades e foco → `_memoria/estrategia.md`
- Regra de comportamento nessa pasta → `CLAUDE.md`

---

## Manter contexto atualizado

Ao terminar uma tarefa que mudou algo relevante (cliente novo, skill criada, mudança de foco, ferramenta instalada), perguntar:
> "Isso mudou algo no teu contexto. Quer que eu atualize a memória?"

Mostrar o que vai mudar antes de salvar. Não reformatar o arquivo inteiro — só adicionar ou editar a linha relevante.

Rode `/atualizar` pra uma varredura completa quando houver dúvida.

---

## Ferramentas conectadas

- [ ] Notion
- [ ] Gmail
- [ ] Google Calendar
- [ ] Meta Ads
- [ ] Google Ads
- [ ] WhatsApp Business API

*(Marcar conforme for instalando os MCPs)*
