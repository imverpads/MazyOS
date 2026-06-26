# Implementação — IA (ODL Pet)

## Objetivo

Implementar agentes de IA que executam tarefas de atendimento, triagem e comunicação no setor pet — ampliando a capacidade da operação sem contratar mais pessoas.

---

## O que faz sentido automatizar com IA no setor pet

### Atendimento inicial via WhatsApp
Um agente que recebe os primeiros contatos, identifica o que o cliente quer e encaminha para o agendamento ou para um atendente humano.

**O que o agente pode fazer:**
- Saudar o cliente
- Identificar se é agendamento, dúvida ou reclamação
- Coletar informações básicas (nome, pet, serviço desejado)
- Verificar horários disponíveis no sistema de agenda
- Confirmar agendamento
- Encaminhar para humano quando necessário

**O que o agente NÃO deve fazer:**
- Discutir preço sem confirmação humana
- Responder reclamações de forma autônoma
- Tomar decisão sobre situações de saúde do animal

---

### Triagem de mensagens
Em pet shops com volume alto, a IA classifica as mensagens recebidas antes de chegar para o atendente:

- Agendamento → fluxo de agenda
- Dúvida sobre preço → resposta padrão + oferta de conversa
- Reclamação → alerta imediato para o dono
- Emergência veterinária → resposta de urgência + número direto

---

### Geração de conteúdo para Instagram
IA (Claude) usada para:
- Criar legendas a partir de fotos tiradas no dia
- Adaptar conteúdo educativo para o tom do negócio
- Gerar respostas para comentários e DMs no Instagram

---

## Ferramentas por caso de uso

| Caso de uso | Ferramenta | Complexidade |
|------------|-----------|--------------|
| Atendimento WhatsApp | Evolution API + N8N + Claude/GPT | Média |
| Agendamento via chat | Qualquer CRM pet com bot integrado | Baixa |
| Geração de conteúdo | Claude (via MazyOS) | Baixa |
| Análise de avaliações | Claude (manual ou automático) | Baixa |
| Triagem de mensagens | N8N + Claude | Média |

---

## O que comunicar ao cliente sobre IA

A maioria dos tutores de pets prefere sentir que está sendo atendido por uma pessoa. A implementação de IA deve:

- Não se identificar como robô na primeira mensagem (não cria confiança)
- Ter personalidade alinhada ao tom do negócio (não robótica, não genérica)
- Ter handoff limpo para humano quando necessário

**Exemplo de abertura de bot bem configurado:**
> "Oi! Aqui é o atendimento do [Nome do Pet Shop] 🐾
> Como posso ajudar você hoje?"

O tutor não precisa saber que é IA. Precisa ser bem atendido.

---

## Quando NÃO implementar IA

- Quando o negócio não tem processo humano funcionando — automação de caos gera caos mais rápido
- Quando o volume de atendimento é muito baixo (menos de 20 mensagens/dia) — não justifica o investimento
- Quando o dono não tem tempo de monitorar os primeiros 30 dias da implementação
