---
name: conteudo-odl
description: >
  Transforma um único tema, insight, case, dor de empresário local ou erro identificado em
  diagnóstico em pacote completo de conteúdo multi-canal: carrossel Instagram, legenda, story
  com CTA, LinkedIn, Facebook, artigo SEO, roteiro Reels/Shorts, e-mail, mensagem WhatsApp e
  prompts de arte. Usa o posicionamento ODL e o método da marca. Use quando o usuário disser
  "criar conteúdo sobre", "conteúdo ODL", "transformar esse tema em conteúdo", "pacote de
  conteúdo", "/conteudo-odl" ou fornecer um insight, case ou dor para transformar em publicação.
---

# /conteudo-odl — Pacote de conteúdo multi-canal

Transforma um único ponto de partida em conteúdo estratégico para todos os canais. O objetivo de todo conteúdo é gerar autoridade, despertar consciência nos empresários locais e criar oportunidades de conversa — não apenas engajamento.

## Arquitetura de dados

```
marketing/conteudo/
└── pack-<slug-do-tema>-<YYYY-MM-DD>/
    ├── tema.md                 ← briefing e mensagem central aprovada
    ├── instagram/
    │   ├── carrossel.html      ← gerado via /carrossel
    │   ├── render.js           ← gerado via /carrossel
    │   ├── legenda.md
    │   ├── story.md
    │   └── slides/             ← PNGs renderizados via /carrossel
    ├── linkedin.md
    ├── facebook.md
    ├── email.md
    ├── whatsapp.md
    ├── artigo-seo.md
    ├── roteiro-reels.md
    └── prompts-arte.md
```

## Dependências

- `_memoria/preferencias.md` — tom de voz e termos proibidos — LER ANTES de qualquer texto
- `_memoria/empresa.md` — posicionamento, método ODL, público-alvo
- `identidade/design-guide.md` — identidade visual (usada pelo /carrossel)
- Skill `/carrossel` — invocar para gerar o visual do Instagram (carrossel.html + PNGs)

---

## Workflow

### Passo 1 — Receber e entender o tema

Identificar o ponto de partida fornecido pelo usuário:

- **Dor de empresário:** problema recorrente que empresários locais enfrentam
- **Erro de diagnóstico:** algo encontrado em auditoria ou reunião com cliente
- **Case ou melhoria:** resultado implementado em cliente (anonimizar se necessário)
- **Insight de estudo ou experiência:** aprendizado que muda como o empresário enxerga o problema
- **Pergunta frequente:** o que empresários perguntam com mais frequência
- **Tecnologia aplicada:** IA, automação ou ferramenta explicada no contexto de negócios locais
- **Notícia ou tendência:** mudança de mercado traduzida para impacto em negócios locais

Se o ponto de partida não estiver claro, perguntar:
> "Qual é o problema ou insight central? Em uma frase: o que você quer que o empresário perceba depois de consumir esse conteúdo?"

### Passo 2 — Ler contexto da marca

1. Ler `_memoria/preferencias.md` — tom de voz, termos proibidos, estilo
2. Ler `_memoria/empresa.md` — posicionamento ODL, público, o que a marca representa
3. Verificar: o tema está alinhado com o posicionamento ODL? Ele educa, diagnostica ou demonstra autoridade?

### Passo 3 — Definir ângulo e mensagem central

Antes de escrever qualquer canal, definir e apresentar ao usuário:

- **Mensagem central (uma frase):** o que o conteúdo prova, ensina ou muda no pensamento do empresário?
- **Público específico:** qual perfil de empresário esse conteúdo fala — segmento, tamanho, maturidade digital?
- **Ângulo:** qual é a perspectiva única — diagnóstico, dado, caso real, erro comum, comparação, revelação?
- **CTA implícito:** o que o empresário deve perceber, sentir ou fazer depois de consumir?

**CHECKPOINT:** Apresentar ao usuário. Aguardar aprovação antes de gerar os canais.
Se não aprovado, ajustar ângulo e reapresentar.

### Passo 4 — Gerar conteúdo por canal

Com a mensagem central aprovada, adaptar para cada canal:

#### Instagram — Carrossel
Invocar `/carrossel` com o tema e ângulo definidos.
O `/carrossel` é responsável por: HTML, PNGs e legenda.
Salvar os outputs na pasta `instagram/`.

#### Instagram — Story com CTA
- 1 frame simples: pergunta direta ou dado impactante
- CTA: "Arrasta pra cima" (link) ou "Responde aqui" (enquete)
- Tom: mais informal e imediato que o carrossel
- Máximo 15 palavras na tela

#### LinkedIn
- Tom: mais analítico e profissional que o Instagram
- Estrutura: contexto do problema → análise → conclusão acionável
- Texto corrido com parágrafos curtos — sem bullet points excessivos
- CTA: convite à reflexão ou à conversa nos comentários ("Você já viu isso acontecer?")
- Tamanho: 800–1.200 caracteres

#### Facebook
- Tom próximo ao Instagram, levemente mais conversacional
- Pode partir do mesmo texto do Instagram com pequenos ajustes de abertura
- CTA: comentário ("Você concorda?") ou compartilhamento ("Manda pra alguém que precisa ver")

#### Artigo para Blog/SEO
- Título com palavra-chave local: ex: "por que [tipo de empresa] perde clientes no Google" ou "como [segmento] em [cidade] pode [resultado]"
- Estrutura: H1, introdução, H2 por seção, conclusão, CTA para contato
- Mínimo 600 palavras, máximo 1.200 para artigos de autoridade
- Linguagem natural, sem jargão técnico excessivo — o empresário local é o leitor
- Terminar com CTA para diagnóstico ou contato

#### Roteiro para Reels/Shorts/TikTok
- Duração alvo: 30–60 segundos
- Estrutura:
  - Gancho (0–3s): afirmação provocadora ou pergunta inesperada
  - Problema (3–15s): o que o empresário está perdendo ou errando
  - Insight/Solução (15–45s): o que ele deveria fazer diferente
  - CTA (45–60s): próximo passo claro
- Descrever cada momento: o que falar, o que mostrar na tela, tom

#### E-mail
- Assunto: específico e curioso — sem "Newsletter de [mês]" ou clickbait
- Estrutura: contexto breve (1 parágrafo) → insight principal (2–3 parágrafos) → CTA claro
- Tom: conversa direta de consultor, não newsletter corporativa
- Assinatura: Joabe Silva | Consultoria ODL | [contato]

#### WhatsApp
- Máximo 3–4 parágrafos curtos
- Tom informal mas com substância — não é broadcast vazio
- Adequado para lista de transmissão ou grupo de empresários locais
- Abrir com algo concreto, não com "Oi, tudo bem?"
- Fechar com pergunta que convida resposta: "Isso acontece no seu negócio?"

#### Prompts de Arte
- Descrever o visual que representaria o conteúdo de forma impactante
- 2–3 variações:
  - Foto realista (para carrossel com foto ou stories)
  - Ilustração conceitual
  - Composição tipográfica
- Prompts em português para ferramentas como DALL-E, Midjourney ou Canva AI
- Nunca sugerir fotos de pessoas/rostos identificáveis

### Passo 5 — Salvar todos os arquivos

Criar pasta `marketing/conteudo/pack-<slug>-<YYYY-MM-DD>/` e salvar cada canal.

Registrar `tema.md` com:
```markdown
# [Título do tema]
Data: [data]

## Tema original
[Exatamente o que o usuário forneceu]

## Mensagem central aprovada
[A frase aprovada no Checkpoint do Passo 3]

## Ângulo
[O ângulo escolhido]

## Público
[Para quem esse conteúdo fala]

## Canais gerados
- [x] Instagram (carrossel + legenda + story)
- [x] LinkedIn
- [x] Facebook
- [x] Artigo SEO
- [x] Roteiro Reels/Shorts
- [x] E-mail
- [x] WhatsApp
- [x] Prompts de arte
```

### Passo 6 — Resumo final

```
Pacote criado: [tema]
Data: [data]

Canais gerados:
✓ Instagram — carrossel + legenda + story
✓ LinkedIn
✓ Facebook
✓ Artigo SEO
✓ Roteiro Reels/Shorts
✓ E-mail
✓ WhatsApp
✓ Prompts de arte

Salvo em: marketing/conteudo/pack-[slug]-[data]/

Próximos passos:
→ /aprovar-post para publicar o carrossel no Instagram
→ /publicar-tema para subir o artigo no blog
```

---

## Regras

- Ler `_memoria/preferencias.md` ANTES de escrever qualquer texto — sem exceção
- Nunca escrever nenhum termo da lista de proibidos: "vamos juntos", "alavanque", "potencialize", "sinergia", "mindset", "jornada", etc.
- Mensagem central: definir e aguardar aprovação ANTES de gerar os canais — todos partem dela
- Instagram visual: sempre via `/carrossel` — nunca criar HTML de carrossel manualmente nessa skill
- LinkedIn: texto corrido, sem bullet points excessivos
- WhatsApp: curto, substancioso, nunca disparo genérico ou vazio
- Artigo SEO: mínimo 600 palavras, título com palavra-chave local
- Todo conteúdo tem como objetivo gerar autoridade e oportunidades de conversa — não apenas likes
- Salvar TODOS os canais em arquivos — nenhuma saída fica só na tela
