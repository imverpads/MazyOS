# Implementação — WhatsApp Business (ODL Pet)

## Objetivo

Transformar o WhatsApp em canal de operação estruturado: atendimento com resposta automática, agendamento padronizado, confirmação, lembrete de retorno e processo de avaliação — sem que tudo dependa do dono responder na hora.

---

## Pré-requisito

Número separado do pessoal. Se o cliente usa o celular pessoal para atendimento:
1. Separar um número (chip novo ou número fixo com WhatsApp)
2. Instalar WhatsApp Business nesse número
3. Nunca misturar pessoal e comercial

---

## Configuração inicial

### Perfil do negócio
- [ ] Nome da empresa (não nome do dono)
- [ ] Foto: logo ou fachada — não foto pessoal
- [ ] Categoria: "Pet Shop" ou "Saúde e bem-estar"
- [ ] Descrição: o que faz, onde fica, horário de atendimento
- [ ] E-mail de contato
- [ ] Site (se existir)
- [ ] Endereço

### Mensagens automáticas

**Mensagem de saudação** (quando cliente manda mensagem pela primeira vez ou após 14 dias sem contato):

> "Oi! Bem-vindo ao [Nome do Pet Shop]! 🐾
>
> Estamos aqui de [horário] a [horário], de [dias].
>
> Me conta: o que você precisa?
> 1️⃣ Agendar banho/tosa
> 2️⃣ Consulta veterinária
> 3️⃣ Produtos
> 4️⃣ Outra dúvida"

**Mensagem de ausência** (fora do horário de atendimento):

> "Oi! Recebemos sua mensagem.
>
> Nosso horário de atendimento é [horário].
> Retornaremos em breve!
>
> Se for urgente, ligue: [número]"

### Catálogo de serviços
- [ ] Criar catálogo com: serviço, descrição curta, faixa de preço (opcional)
- Banho pequeno / médio / grande
- Tosa completa / na tesoura
- Banho + tosa
- Hidratação
- Consulta veterinária (se clínica)

---

## Script de agendamento

Processo padrão que a equipe executa ao receber pedido de agendamento:

```
1. Confirmar o serviço:
   "Perfeito! Qual serviço você quer agendar — banho, tosa ou os dois?"

2. Identificar o pet:
   "Me conta: qual o nome do pet, raça e tamanho aproximado?"

3. Verificar disponibilidade e propor data:
   "Tenho disponibilidade [dia] às [hora] ou [dia] às [hora]. Qual funciona melhor?"

4. Confirmar:
   "Confirmado! [Nome do pet] está agendado pra [dia] às [hora].
   Qualquer dúvida, é só me chamar. Até lá!"

5. Lembrete 24h antes:
   "Oi [Nome]! Só lembrando que o [nome do pet] tem banho amanhã às [hora].
   Te esperamos! 🐶"
```

---

## Automação de lembretes de retorno

### Lembrete de retorno de banho (D-25 ou D-30)

Enviado automaticamente 25 ou 30 dias após o último banho:

> "Oi [Nome]! O [nome do pet] já está na hora de dar uma caprichadinha. 🐾
>
> Quer agendar o próximo banho? Tenho horário disponível essa semana.
>
> É só responder aqui!"

### Lembrete de vacina (para clínicas)

30 dias antes do vencimento da vacina (se o sistema registrar a data):

> "Oi [Nome]! Só um aviso: a vacina [nome] do [nome do pet] vence em [data].
>
> Quer que a gente agende a renovação?"

### Aniversário do pet

Na data de aniversário registrada:

> "Hoje é aniversário do [nome do pet]! 🎂🐾
>
> Feliz aniversário de [X] anos! Que tal um banho especial pra comemorar?
>
> — Equipe [Nome do Pet Shop]"

---

## Ferramentas para automação

| Ferramenta | Uso | Custo aproximado |
|-----------|-----|-----------------|
| WhatsApp Business nativo | Saudação, ausência, catálogo | Gratuito |
| Z-API / Evolution API | Automação de lembretes | R$ 50–150/mês |
| N8N (self-hosted) | Orquestração de fluxos | Gratuito (hospedagem própria) |
| Make / Zapier | Fluxos simples sem servidor | R$ 50–200/mês |
| PetSoft / Greennote | CRM pet com lembrete integrado | R$ 80–200/mês |

**Recomendação para início:** Z-API + N8N ou sistema de gestão pet com WhatsApp integrado. Não tentar automatizar com o WhatsApp nativo além das mensagens automáticas básicas.

---

## O que NÃO fazer

- Usar WhatsApp pessoal do dono para atendimento comercial
- Disparar mensagens sem consentimento (LGPD — tutor precisa ter optado por receber)
- Mandar broadcast com "Oi tudo bem" genérico sem personalização
- Deixar mensagem sem resposta por mais de 2 horas durante horário comercial
- Usar grupos de WhatsApp para gestão de agenda
