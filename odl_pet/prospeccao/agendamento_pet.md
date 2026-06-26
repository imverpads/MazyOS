# Agendamento — ODL Pet

## Objetivo desta etapa

Confirmar data, horário e formato da reunião de diagnóstico. O empresário precisa aparecer na reunião com expectativa clara do que vai acontecer — não do que vai ser vendido.

**Saída esperada:** reunião confirmada com data, horário e formato definidos.

---

## O que é a reunião de diagnóstico

A reunião de diagnóstico é uma conversa estruturada de 40–60 minutos onde o Joabe apresenta o que analisou do negócio e aprofunda com perguntas que o empresário raramente se faz.

O empresário sai da reunião com uma visão clara do que está impedindo o crescimento do negócio — independentemente de fechar ou não.

**Como posicionar ao agendar:**
> "A reunião é de uns 40–50 minutos. Não é apresentação de pacote. É uma análise do negócio de vocês — vou trazer o que identifiquei e vamos conversar sobre o que está funcionando, o que não está e o que poderia mudar. Você sai com clareza sobre o que fazer, mesmo que decida não trabalhar comigo."

---

## Formatos da reunião

| Formato | Quando usar | Vantagens |
|---------|------------|-----------|
| Presencial | Cliente na mesma cidade | Maior rapport, melhor para mostrar materiais |
| Google Meet / Zoom | Cliente em outra cidade ou cliente muito ocupado | Mais fácil de agendar, gravável |
| WhatsApp Vídeo | Cliente avesso a tecnologia, prefere informalidade | Baixa barreira de entrada |

**Preferência:** presencial quando possível. Reunião presencial tem conversão de proposta significativamente maior.

---

## Como propor o agendamento

Após qualificação, propor com duas opções de data (não perguntar "quando você pode" — isso cria atraso):

> "Faz sentido a gente sentar [ou se falar] pra eu te mostrar o que vi e a gente conversar sobre o negócio. Tenho disponibilidade [terça às 10h ou quinta às 14h] — qual funciona melhor pra você?"

Se nenhuma das duas servir:
> "Me fala o que tem livre essa semana ou a próxima — prefiro encaixar no teu horário do que perder a conversa."

---

## Confirmação da reunião

Após o empresário confirmar data e horário:

1. Registrar no calendário
2. Enviar confirmação por WhatsApp:

> "Confirmado! [Data] às [horário] — [local / link do Meet].
> Vou preparar a análise do [nome do pet shop] antes da reunião. Se quiser me mandar o link do Instagram e do Google de vocês antes, já consigo preparar algo mais detalhado."

O pedido dos links serve duas funções: permite preparação real antes da reunião (→ [preparacao_reuniao_pet.md](preparacao_reuniao_pet.md)) e aumenta o comprometimento do empresário com o agendamento.

3. Lembrete automático (ou manual) 24h antes:

> "Oi [Nome]! Só confirmando nossa conversa amanhã às [horário]. Já preparei a análise do [nome do pet shop] — vai ser uma boa conversa."

---

## Objeções ao agendar

### "Me manda o que você faz primeiro pra eu ver."
> "Prefiro não mandar material antes porque o que eu apresento é específico do seu negócio — não é um portfólio genérico. O que vou mostrar na reunião é o que encontrei no [nome do pet shop] especificamente. Vale 40 minutos pra você ver."

### "Pode ser por áudio mesmo?"
> "Posso, mas pra essa conversa prefiro que seja por vídeo ou presencial — preciso mostrar alguns pontos visualmente. Fica melhor pra você também entender o que identifiquei. [data] às [horário] funciona pra uma chamada rápida?"

### "Minha esposa/sócio precisa participar também."
> "Melhor ainda. Se puder trazer ela/ele, ótimo — a reunião fica mais completa."

### "Você cobra por essa reunião?"
> "Não. A reunião de diagnóstico é sem custo. O que vem depois, se você decidir contratar, aí sim tem investimento — mas isso a gente conversa na reunião depois que você ver o que eu trouxe."

---

## Registro

Atualizar `empresa.json`:

```json
{
  "fase": "reuniao_agendada",
  "reuniao": {
    "data": "YYYY-MM-DD",
    "horario": "HH:MM",
    "formato": "presencial | meet | whatsapp",
    "confirmada": true
  }
}
```

---

## Próximo passo

Reunião confirmada → [preparacao_reuniao_pet.md](preparacao_reuniao_pet.md)
