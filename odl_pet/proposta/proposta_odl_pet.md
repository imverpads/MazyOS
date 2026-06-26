# Proposta ODL Pet

## Objetivo desta etapa

Apresentar ao empresário um plano personalizado de implementação com escopo, cronograma e investimento — construído diretamente a partir dos gargalos identificados no diagnóstico.

**O objetivo da proposta não é convencer. É apresentar um raciocínio claro que o empresário consegue seguir do problema até a solução.**

**Saída esperada:** proposta em .md (editável) e .html (visual para apresentação e PDF).

---

## Princípio fundamental

Cada solução na proposta referencia um gargalo específico do mapa de gargalos. Não existe "pacote padrão com 10 entregas" — existe "solução X porque encontramos problema Y que está causando impacto Z".

Se não tem gargalo mapeado, não entra na proposta.

---

## Pré-requisito obrigatório

`gargalos.json` preenchido em `clientes/<NomeEmpresa>/diagnostico/`.

Se não existir: executar [diagnostico_odl_pet.md](../diagnostico/diagnostico_odl_pet.md) antes de gerar a proposta.

---

## O que coletar antes de montar a proposta

Com o diagnóstico concluído, verificar o que ainda falta para a proposta:

- [ ] Objetivos declarados do cliente (o que ele quer nos próximos 3–6 meses?)
- [ ] Restrições de orçamento ou prazo mencionadas na reunião
- [ ] Alguma solução discutida informalmente que o cliente demonstrou interesse?
- [ ] **Valores:** solicitar ao Joabe antes de incluir. Nunca inventar, estimar ou deixar "a definir".

---

## Estrutura da proposta

### 1. Contexto da empresa
Síntese de 2–3 parágrafos mostrando que o Joabe entende a operação antes de propor qualquer coisa.

### 2. Diagnóstico resumido
- Problema central (extraído do gargalos.json)
- Causa raiz
- Impacto atual (concreto, sem exagero)
- Os 3 principais gargalos com descrição e impacto

### 3. Objetivos da implementação
O que será alcançado — baseado no que o cliente declarou querer, não em promessas genéricas.

### 4. Solução recomendada
**Título da implementação** (ex: "ODL Pet — Fase 1: Fundação")

Parágrafo explicando a lógica: por que essas soluções, nessa ordem, para esse cliente específico.

Para cada solução:
- **Problema que resolve:** gargalo do diagnóstico
- **O que será feito:** descrição objetiva da entrega
- **Resultado esperado:** impacto concreto

### 5. O que não entra nessa fase (e por quê)
Mostrar o que ficou fora e o raciocínio. Isso prova que houve estratégia, não limitação.

### 6. Cronograma de implementação

| Fase | Período | Entregas |
|------|---------|----------|
| Fase 1 — Fundação | Semanas 1–2 | [entregas específicas] |
| Fase 2 — Estruturação | Semanas 3–4 | [entregas específicas] |
| Fase 3 — Ativação | Mês 2 | [entregas específicas] |

### 7. Investimento

| Solução | Valor |
|---------|-------|
| [Solução 1] | R$ X |
| [Solução 2] | R$ X |
| **Total** | **R$ X** |

Forma de pagamento: [conforme prática do Joabe]
Validade: 15 dias a partir de [data]

### 8. Próximos passos
1. Aprovação da proposta
2. [Primeira ação pós-fechamento]
3. Início da implementação

---

## Como apresentar a proposta

**Não enviar sem aviso.** Avisar antes:
> "Oi [Nome], terminei a proposta com o plano de implementação. Prefere que eu te mande por aqui pra você ler no seu tempo ou você prefere que a gente se fale pra eu apresentar ao vivo?"

Se o cliente preferir receber por mensagem:
> "Vou te mandar. Leva uns 10 minutos de leitura. Qualquer dúvida, me chama."

Se o cliente preferir apresentação ao vivo: agendar 30 minutos (não mais) para apresentar e responder perguntas.

---

## Objeções comuns na proposta

### "Tá caro."
> "Me conta: o que você achou mais caro — o total ou alguma solução específica? Posso te explicar por que incluí cada item."
> Se necessário: "Posso ajustar o escopo pra Fase 1 menor. O que não posso fazer é tirar o que é fundamental e entregar resultado parcial."

### "Preciso pensar."
> "Claro. O que ficou em aberto — é o valor, o escopo ou você precisa conversar com alguém?"
> Identificar o real bloqueio antes de fazer follow-up.

### "Posso começar com só uma parte?"
> Avaliar se a parte solicitada faz sentido isolada. Se sim: ajustar proposta. Se não: explicar o porquê da sequência.

### "Não é o momento agora."
> "Entendo. Me fala: o que mudaria pra ser o momento?" → Identificar se é objeção de dinheiro, tempo ou confiança.

---

## Arquivos de saída

Salvar em `clientes/<NomeEmpresa>/proposta/`:
- `proposta-YYYY-MM-DD.md` — versão editável
- `proposta-YYYY-MM-DD.html` — versão visual (identidade Joabe Silva, exportável para PDF)

Atualizar `empresa.json`:
```json
{
  "fase": "proposta",
  "proposta": {
    "data": "YYYY-MM-DD",
    "validade": "YYYY-MM-DD",
    "valor_total": 0,
    "status": "enviada | aprovada | rejeitada | negociando"
  }
}
```

---

## Próximo passo

Proposta aprovada → [plano_implementacao.md](plano_implementacao.md)
