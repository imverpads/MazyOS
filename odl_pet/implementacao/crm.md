# Implementação — CRM e Gestão de Agenda (ODL Pet)

## Objetivo

Implementar um sistema que registre clientes, histórico dos animais e agenda — para que o negócio não dependa da memória do dono e possa gerar lembretes, retornos e relatórios de forma automática.

---

## O problema sem CRM

Sem sistema:
- A agenda fica no caderno ou em grupos de WhatsApp
- O dono não sabe quantos clientes tem ativos
- Não sabe quem sumiu no mês
- Não sabe quando o pet de cada cliente fez o último banho
- Não consegue enviar lembrete sem olhar manualmente

Com sistema:
- Agenda visível para toda a equipe
- Histórico completo do animal (data de nascimento, raça, peso, histórico de serviços, vacinas)
- Lembrete automático de retorno
- Relatório de atendimentos por período

---

## Opções por perfil de negócio

### Banho e tosa (pequeno, 1–3 funcionários)

| Sistema | Destaques | Custo |
|---------|-----------|-------|
| PetSoft | CRM pet completo, lembrete por WhatsApp, agenda | R$ 80–150/mês |
| Greennote | Prontuário eletrônico, agenda, financeiro | R$ 90–180/mês |
| AgendaCom (genérico) | Simples, agenda online com link de agendamento | R$ 30–60/mês |
| Planilha Google | Gratuito, manual, sem automação | Gratuito |

**Recomendação:** PetSoft ou Greennote para quem quer automação de lembretes sem precisar de integração técnica.

### Clínica veterinária

| Sistema | Destaques | Custo |
|---------|-----------|-------|
| VetSoftware | Prontuário clínico completo, receita digital, vacinas | R$ 150–300/mês |
| Vet.one | Nuvem, mobile, gestão de internação | R$ 120–250/mês |
| CliniVet | Prontuário + financeiro + estoque | R$ 100–200/mês |

---

## O que o sistema precisa registrar (campos mínimos)

### Cliente (tutor)
- Nome completo
- WhatsApp
- Bairro/endereço (para segmentação local)
- Data do primeiro atendimento
- Canal de origem (como chegou: Google, indicação, Instagram, etc.)

### Animal
- Nome
- Raça
- Peso/porte
- Data de nascimento / Idade
- Observações de comportamento ou saúde
- Vacinas (com datas de vencimento)
- Histórico de serviços (com data, serviço realizado e responsável)

### Agendamento
- Data e hora
- Serviço
- Animal
- Responsável (quem vai atender)
- Status: confirmado / realizado / cancelado / não compareceu

---

## Processo de migração do caderno para o sistema

Para negócios que já têm clientes:

1. Exportar lista de clientes conhecidos para planilha (nome + WhatsApp)
2. Importar para o sistema (maioria dos CRMs aceitam CSV)
3. Para cada cliente que agendar nos próximos 30 dias: complementar o cadastro (animal, histórico)
4. Não tentar cadastrar toda a base de uma vez — cadastrar conforme o cliente aparecer

---

## Implantação em fases

**Semana 1:** configurar sistema, campos básicos, importar lista de clientes existente
**Semana 2:** treinar equipe no fluxo de cadastro durante atendimento
**Semana 3–4:** ligar o lembrete automático e validar que está funcionando
**Mês 2:** analisar o primeiro relatório de atendimentos e taxa de retorno
