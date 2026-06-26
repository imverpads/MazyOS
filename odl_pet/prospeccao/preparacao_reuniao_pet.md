# Preparação da Reunião — ODL Pet

## Objetivo desta etapa

Analisar o negócio do cliente antes da reunião de diagnóstico para chegar com evidências reais, não perguntas genéricas. O Joabe entra na reunião sabendo o que está errado — a reunião aprofunda, não descobre.

Esta é a etapa onde o Método ODL Pet é aplicado pela primeira vez. Não antes do primeiro contato. Não antes da qualificação. Após a reunião estar confirmada.

**Saída esperada:** dossiê de preparação com Score ODL Pet inicial, gargalos visíveis por pilar e roteiro da reunião.

---

## Por que a preparação acontece aqui

Fazer análise aprofundada antes de qualquer contato seria desperdício — a maioria dos leads não avança. A preparação acontece apenas quando o empresário confirmou que vai aparecer. Isso garante que o tempo de análise seja investido em quem tem real potencial de fechar.

---

## O que analisar antes da reunião

### 1. Google Meu Negócio

Acessar o perfil no Google e analisar:

- [ ] Perfil verificado?
- [ ] Nota média e número de avaliações
- [ ] Avaliações respondidas? Com que qualidade?
- [ ] Fotos: quantidade, qualidade, última atualização
- [ ] Categorias: corretas para o tipo de negócio?
- [ ] Horário de funcionamento: atualizado?
- [ ] Posts recentes? (últimos 30 dias)
- [ ] Perguntas sem resposta?
- [ ] Posição nos resultados locais: aparece no top 3 para "banho e tosa [cidade]"?

**Registrar:** nota do pilar Presença Digital (GMB) + evidências específicas

### 2. Instagram

Acessar o perfil e analisar:

- [ ] Conta comercial ou pessoal?
- [ ] Bio: tem proposta de valor, localização e link de contato?
- [ ] Última postagem: quando foi?
- [ ] Frequência dos últimos 3 meses: quantas postagens por mês?
- [ ] Qualidade visual: consistente ou improvisada?
- [ ] Tipo de conteúdo: fotos do trabalho, promoções, memes, bastidores?
- [ ] Engajamento: likes e comentários visíveis nos posts
- [ ] Uso de stories e reels?
- [ ] Link na bio: onde vai? Funciona?

**Registrar:** evidências com prints mentais ou anotações, última data de postagem, padrão de conteúdo

### 3. Site (quando existir)

- [ ] Está no ar?
- [ ] Abre corretamente no mobile?
- [ ] Tem botão de WhatsApp ou contato visível?
- [ ] Descreve os serviços claramente?
- [ ] Tem algum CTA acima da dobra?
- [ ] Aparece na busca orgânica do Google?

### 4. WhatsApp Business

- [ ] É WhatsApp Business ou pessoal?
- [ ] Tem mensagem automática de saudação? Testar enviando uma mensagem ("Boa tarde, quero saber sobre banho e tosa")
- [ ] Tem catálogo de serviços?
- [ ] Horário de atendimento configurado?
- [ ] Link direto (wa.me/) disponível no site ou Instagram?

### 5. Busca local

Pesquisar no Google: "[banho e tosa / pet shop / veterinário] [bairro/cidade]"

- [ ] Em que posição o negócio aparece?
- [ ] Quem são os 3 primeiros resultados? O que eles têm que esse negócio não tem?

---

## Score ODL Pet — versão preparação

Calcular o score pelos 7 pilares com base nas evidências coletadas. Usar [score_odl_pet.md](../metodo/score_odl_pet.md) como referência.

**Importante:** na preparação, alguns pilares não têm evidência suficiente para pontuação precisa (Conversão, Atendimento, Escalabilidade). Marcar como "a confirmar na reunião" e calcular com o que é visível.

| Pilar | Peso | Nota estimada | Evidência |
|-------|------|--------------|-----------|
| Posicionamento | 15 | | |
| Presença Digital | 20 | | |
| Aquisição | 15 | | |
| Conversão | 15 | (a confirmar) | |
| Atendimento | 15 | (a confirmar) | |
| Automação | 10 | (a confirmar) | |
| Escalabilidade | 10 | (a confirmar) | |
| **Total** | **100** | | |

---

## Gargalos identificados

Listar os 3–5 problemas mais evidentes encontrados, em ordem de impacto:

```
1. Pilar: [nome]
   Problema: [o que foi encontrado]
   Evidência: [o que foi visto — específico]
   Impacto provável: [o que isso custa ao negócio]

2. ...
```

---

## Roteiro da reunião

Com base no que foi encontrado, definir a sequência da reunião:

### Abertura (5 min)
> Agradecer o tempo, posicionar a reunião: "Preparei uma análise do [nome do negócio] com base no que está público. Vou te mostrar o que encontrei e depois quero entender melhor como funciona a operação por dentro."

### Apresentação do que foi encontrado (15 min)
Mostrar os gargalos identificados na análise — com evidências. Não opinião. Fato.

> "Quando pesquiso [serviço] no [bairro], vocês aparecem em [posição]. Os três que aparecem antes têm [X avaliações / fotos / postagens]. Isso significa que o tutor que pesquisa hoje tem mais chance de ligar para eles do que pra vocês."

### Perguntas de aprofundamento (20 min)
Usar perguntas do [diagnostico_odl_pet.md](../diagnostico/diagnostico_odl_pet.md) para os pilares que não puderam ser avaliados remotamente.

### Síntese e próximos passos (10 min)
Apresentar o diagnóstico consolidado e propor o próximo passo natural: a proposta.

---

## Arquivos de saída

Salvar em `clientes/<NomeEmpresa>/preparacao/`:

- `preparacao-reuniao.md` — análise completa pré-reunião
- `roteiro-reuniao.md` — roteiro de perguntas e pontos a apresentar
- `score-inicial.md` — score estimado com evidências

Atualizar `empresa.json`:

```json
{
  "fase": "preparacao_reuniao",
  "preparacao": {
    "data": "YYYY-MM-DD",
    "score_estimado": 0,
    "gargalos_pre_reuniao": []
  }
}
```

---

## Próximo passo

Preparação concluída → [diagnostico_odl_pet.md](../diagnostico/diagnostico_odl_pet.md)
