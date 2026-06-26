# Mapa de Gargalos — ODL Pet

## Objetivo

Consolidar tudo que foi identificado na preparação e na reunião em um documento estruturado que:
1. Define o problema central do negócio
2. Identifica a causa raiz
3. Prioriza as ações por impacto e esforço
4. Serve como base direta para a proposta

O mapa de gargalos não é uma lista de problemas. É uma análise de causa raiz com prioridade de resolução.

---

## Estrutura do mapa

### Problema central

Uma frase que resume o gargalo principal do negócio.

> Exemplo: "O negócio perde recorrência porque não existe nenhum processo de contato com o cliente entre um atendimento e outro."

> Exemplo: "A captação está 100% baseada em indicação, sem nenhum canal ativo — isso cria imprevisibilidade de receita mês a mês."

### Causa raiz

Por que esse problema existe?

> Exemplo: "O dono executa todos os atendimentos e não tem tempo ou processo para fazer follow-up — o pós-venda depende do cliente lembrar de voltar."

### Impacto estimado

O que esse problema está custando ao negócio? Ser concreto.

> Exemplo: "Com 80 clientes na base e frequência mensal, a taxa de retorno espontânea estimada é de 40–50%. Isso significa que todo mês, 40–48 clientes que poderiam voltar precisam ser reconquistados do zero ou são perdidos para concorrência."

---

## Análise por pilar

Para cada pilar, registrar:

### [Nome do Pilar] — Nota: X/[peso máximo]

**Situação atual:** o que foi encontrado — baseado em evidências, não em suposição.

**Causa raiz:** por que isso acontece.

**Impacto:** o que isso custa ao negócio em termos concretos (clientes, receita, tempo, reputação).

**Recomendação:** o que implementar para resolver.

**Gargalos identificados:**
- [gargalo específico 1]
- [gargalo específico 2]

---

## Matriz de priorização

Organizar as ações por impacto (alto/médio/baixo) e esforço de implementação (alto/médio/baixo):

| Ação | Pilar | Impacto | Esforço | Prioridade |
|------|-------|---------|---------|-----------|
| Completar e ativar GMB | Presença Digital | Alto | Baixo | 1 |
| Configurar lembrete de retorno de banho | Automação | Alto | Médio | 2 |
| Criar script de atendimento WhatsApp | Conversão | Alto | Baixo | 3 |
| Ativar publicação semanal Instagram | Presença Digital | Médio | Médio | 4 |
| Implementar processo de avaliação no Google | Atendimento | Alto | Baixo | 5 |
| [demais ações por análise] | | | | |

**Critério de prioridade:**
- Prioridade 1: alto impacto + baixo esforço → implementar primeiro
- Prioridade 2: alto impacto + médio esforço → Fase 1 da proposta
- Prioridade 3: médio impacto + baixo esforço → complementar Fase 1
- Prioridade 4+: alto esforço ou impacto menor → Fase 2 ou posterior

---

## Score ODL Pet definitivo

| Pilar | Peso | Nota |
|-------|------|------|
| Posicionamento | 15 | |
| Presença Digital | 20 | |
| Aquisição | 15 | |
| Conversão | 15 | |
| Atendimento | 15 | |
| Automação | 10 | |
| Escalabilidade | 10 | |
| **Total** | **100** | |

**Interpretação:** [classificação conforme score_odl_pet.md]

---

## Pontos fortes

O que já funciona bem — honesto, não forçado. Documentar para não propor o que já existe.

---

## O que NÃO entra na proposta (e por quê)

Registrar o que foi identificado mas ficará fora do escopo inicial, com justificativa estratégica:

> Exemplo: "Tráfego pago não entra na Fase 1 porque a fundação (GMB, WhatsApp, processo de atendimento) ainda não está estruturada. Anunciar sem fundação desperdiça verba."

Isso mostra raciocínio estratégico, não limitação de serviço.

---

## Formato de saída

Salvar em `clientes/<NomeEmpresa>/diagnostico/`:
- `mapa-gargalos.md` — este documento preenchido
- `gargalos.json` — versão estruturada para referência na proposta

```json
{
  "empresa": "",
  "data_diagnostico": "YYYY-MM-DD",
  "score_odl": {
    "total": 0,
    "posicionamento": 0,
    "presenca_digital": 0,
    "aquisicao": 0,
    "conversao": 0,
    "atendimento": 0,
    "automacao": 0,
    "escalabilidade": 0
  },
  "problema_central": "",
  "causa_raiz": "",
  "impacto_estimado": "",
  "pontos_fortes": [],
  "pilares": {
    "posicionamento": {
      "nota": 0, "situacao_atual": "", "causa_raiz": "",
      "impacto": "", "recomendacao": "", "gargalos": []
    },
    "presenca_digital": { "nota": 0, "situacao_atual": "", "causa_raiz": "", "impacto": "", "recomendacao": "", "gargalos": [] },
    "aquisicao": { "nota": 0, "situacao_atual": "", "causa_raiz": "", "impacto": "", "recomendacao": "", "gargalos": [] },
    "conversao": { "nota": 0, "situacao_atual": "", "causa_raiz": "", "impacto": "", "recomendacao": "", "gargalos": [] },
    "atendimento": { "nota": 0, "situacao_atual": "", "causa_raiz": "", "impacto": "", "recomendacao": "", "gargalos": [] },
    "automacao": { "nota": 0, "situacao_atual": "", "causa_raiz": "", "impacto": "", "recomendacao": "", "gargalos": [] },
    "escalabilidade": { "nota": 0, "situacao_atual": "", "causa_raiz": "", "impacto": "", "recomendacao": "", "gargalos": [] }
  },
  "prioridade_implementacao": [
    { "ordem": 1, "acao": "", "pilar": "", "impacto": "", "esforco": "", "prazo_estimado": "" }
  ],
  "fora_do_escopo": []
}
```

---

## Próximo passo

Mapa concluído → [proposta_odl_pet.md](../proposta/proposta_odl_pet.md)
