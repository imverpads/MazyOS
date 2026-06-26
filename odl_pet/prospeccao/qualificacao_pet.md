# Qualificação — ODL Pet

## Objetivo desta etapa

Entender, em poucos minutos de troca de mensagens ou em uma conversa rápida, se o empresário tem perfil, momento e interesse para avançar para uma reunião de diagnóstico.

**Saída esperada:** decisão binária — agendar reunião ou arquivar o lead.

Não é triagem de quem merece o serviço. É identificação de quem está no momento certo para comprar.

---

## Princípio fundamental

Qualificação não é interrogatório. É uma conversa onde o Joabe está entendendo o negócio para saber se consegue ajudar — e o empresário está decidindo se vale o tempo dele ouvir mais.

O tom é consultivo desde o primeiro segundo. Perguntas que parecem controle ou checklist afastam. Perguntas que demonstram raciocínio sobre o negócio aproximam.

---

## O que qualifica um lead no setor pet

### Critérios de avançar (pelo menos 3 dos 5):
- [ ] Tem clientes ativos e fluxo de atendimento estabelecido
- [ ] Reconhece que o digital não está funcionando bem (mesmo que não saiba por quê)
- [ ] É o dono ou decisor — não precisa consultar ninguém para decidir
- [ ] Tem capacidade financeira mínima para contratar (faturamento aparente acima de R$ 8–10k/mês)
- [ ] Está aberto a conversar — não deu a resposta só para encerrar a conversa

### Critérios de arquivar:
- Acabou de abrir (menos de 6 meses) — base de clientes ainda muito pequena para o método gerar resultado
- Está em processo de crise financeira — não conseguirá implementar nem pagar
- Já tem agência ativa com boa presença — o problema que o ODL Pet resolve pode não existir
- É funcionário, não dono — sem poder de decisão

---

## Perguntas de qualificação

Não fazer todas de uma vez. Usar na conversa de forma natural. O objetivo é ter as respostas de 3–4 dessas perguntas antes de propor a reunião.

### Sobre o negócio:
> "Há quanto tempo o [nome do pet shop] está funcionando?"
> "Vocês atendem só banho e tosa ou tem outros serviços?"
> "Você é o dono ou sócio?"

### Sobre o momento:
> "Você tem sentido que poderia estar captando mais clientes? Ou o problema maior é a recorrência — cliente que aparece uma vez e some?"
> "O que mais toma o teu tempo no dia a dia operacional?"

### Sobre consciência do problema:
> "Como os clientes de vocês chegam hoje — é mais pelo Google, indicação ou redes sociais?"
> "Alguém já tentou fazer algo com o digital de vocês antes ou está tudo na estaca zero?"

### Sobre decisão:
> "Se a gente conversar e fizer sentido pra você, a decisão é sua ou tem mais alguém envolvido?"

---

## Como fazer a qualificação

### Via WhatsApp (mais comum)
Após a resposta ao primeiro contato, conduzir 2–3 perguntas curtas de forma conversacional. Não mandar todas de uma vez.

**Exemplo de sequência:**
> Empresário: "Que horas você pode falar?"
> Joabe: "Boa! Antes de agendar, me conta rápido: vocês atendem só banho e tosa ou têm outros serviços também?"
> Empresário: "[responde]"
> Joabe: "E os clientes que chegam hoje — é mais por indicação ou tem alguém que pesquisou no Google e achou vocês?"
> Empresário: "[responde]"
> Joabe: "Entendido. Acho que faz sentido a gente conversar. [→ agendamento_pet.md]"

### Via ligação rápida (5–10 minutos)
Se o empresário preferir ligar, conduzir a qualificação de forma direta:

> "Que bom você ter respondido. Antes de eu mostrar o que identifiquei no seu negócio, me conta um pouco: há quanto tempo vocês estão? Como é a operação hoje — só você ou tem equipe?"

Nessa chamada, o objetivo não é vender — é entender o suficiente para dizer: "Faz sentido agendar uma conversa de 45 minutos onde eu apresento o que vi e o que eu faria diferente."

---

## Objeções comuns na qualificação

### "Não tenho dinheiro agora."
> "Entendo. Não precisa decidir agora nada. O que eu proporia é uma conversa onde você me conta mais sobre o negócio e eu te mostro o que está impedindo crescimento — sem compromisso. Se fizer sentido e o momento for esse, a gente conversa. Se não for agora, tudo bem."

### "Já tentei marketing digital antes e não funcionou."
> "Que tipo de trabalho foi esse? Redes sociais, anúncios, site?" → Ouvir → "Faz sentido que não tenha funcionado, porque [razão específica]. O que eu faço é diferente — começo pelo diagnóstico, não pela execução. Mas melhor você ver isso numa conversa de 40 minutos do que eu explicar aqui."

### "Tô muito ocupado agora."
> "Entendo. Me fala: qual semana costuma ser menos corrida pra você — começo ou final do mês?"

---

## Registro pós-qualificação

Após qualificar (ou arquivar), atualizar o `empresa.json` do lead:

```json
{
  "qualificado": true,
  "data_qualificacao": "YYYY-MM-DD",
  "decisor": true,
  "observacoes_qualificacao": "breve resumo do que foi conversado",
  "fase": "agendamento"
}
```

---

## Próximo passo

Lead qualificado → [agendamento_pet.md](agendamento_pet.md)
Lead não qualificado → arquivar com data de retorno (60–90 dias)
