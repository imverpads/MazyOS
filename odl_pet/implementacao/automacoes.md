# Implementação — Automações (ODL Pet)

## Objetivo

Implementar fluxos que executam tarefas de atendimento, lembrete e follow-up sem que o dono precise intervir manualmente em cada etapa.

---

## Princípio

Automação no setor pet não é sobre tecnologia. É sobre não depender do dono para cada interação do cliente com a empresa.

Cada automação implementada libera tempo do dono e aumenta a consistência do atendimento — que deixa de depender de humor, energia ou memória.

---

## Automações prioritárias (por impacto)

### 1. Lembrete de retorno de banho (impacto: muito alto)

**O que faz:** envia mensagem personalizada 25 ou 30 dias após o último serviço.

**Por que é prioritário:** é a automação com maior impacto em recorrência. Sem ela, o cliente que deveria voltar em 30 dias volta quando lembrar — ou vai para o concorrente que lembrou primeiro.

**Fluxo:**
```
Serviço concluído → registra data no CRM
→ D+25 ou D+30: dispara mensagem WhatsApp:
  "Oi [Nome]! O [pet] já está na hora de dar um banho 🐾
   Quer agendar essa semana? Tenho horário disponível."
→ Se responder: atendente assume a conversa e agenda
→ Se não responder em 48h: follow-up automático:
  "Qualquer hora que quiser, é só me chamar!"
```

**Como implementar:** CRM pet com lembrete integrado (PetSoft, Greennote) ou Z-API + N8N.

---

### 2. Confirmação automática de agendamento (impacto: alto)

**O que faz:** após o agendamento ser criado no sistema, envia confirmação imediata.

**Mensagem:**
> "Confirmado! 🐾 [Nome do pet] está agendado para [dia] às [hora].
> Endereço: [endereço]
> Qualquer dúvida, é só responder aqui. Até [dia]!"

---

### 3. Lembrete 24h antes do agendamento (impacto: alto)

**O que faz:** reduz cancelamentos de última hora e "esquecimento" do tutor.

**Mensagem:**
> "Oi [Nome]! Só lembrando que [nome do pet] tem [serviço] amanhã às [hora].
> Esperamos vocês! 🐶"

---

### 4. Solicitação de avaliação pós-serviço (impacto: médio-alto)

**O que faz:** após o serviço, envia link para avaliação no Google.

**Tempo:** enviar 1–2 horas após a saída do animal (o tutor ainda está satisfeito e com o pet na mão).

**Mensagem:**
> "O [nome do pet] ficou incrível! 🐾
> Se quiser deixar uma avaliação rapidinha, ajuda muito a gente:
> [link do GMB]
> Obrigado por confiar no [Nome do Pet Shop]!"

---

### 5. Lembrete de vacina (impacto: médio — requer dados cadastrados)

**Pré-requisito:** ter data de vacina registrada no CRM.

**Fluxo:**
```
30 dias antes do vencimento:
"Oi [Nome]! A vacina [nome] do [pet] vence em [data].
 Quer que a gente agende a renovação?"
```

---

### 6. Reativação de clientes inativos (impacto: médio)

**O que faz:** identifica clientes que não retornaram após 45–60 dias e envia mensagem de reativação.

**Mensagem:**
> "Oi [Nome]! Já faz um tempinho que não vejo o [pet] por aqui 😊
> Quando quiser retomar, é só me chamar!"

---

## Stack técnica recomendada

| Nível | Ferramentas | Para quem |
|-------|------------|-----------|
| Básico | WhatsApp Business + CRM pet com lembrete nativo | Pet shop pequeno, sem experiência técnica |
| Intermediário | Z-API + N8N + Planilha Google | Quem quer mais controle sem custo alto |
| Avançado | Evolution API + N8N + banco de dados | Operação maior, múltiplas unidades, escalabilidade |

---

## O que NÃO automatizar

- Resposta a reclamações — sempre humano
- Conversa de venda (proposta de upgrade de serviço) — sempre consultiva
- Situações de emergência do animal — exige julgamento humano imediato
