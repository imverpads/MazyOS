# Apresentação para o Cliente — ODL Pet

## Objetivo

Documento de referência para construir a apresentação visual que o Joabe envia ou mostra ao cliente após a reunião de diagnóstico. A apresentação consolida o que foi encontrado, o score e os gargalos priorizados — e serve como ponte para a proposta.

---

## Quando gerar a apresentação

Após a reunião de diagnóstico, com [mapa_gargalos_pet.md](mapa_gargalos_pet.md) e [score_empresa_pet.md](score_empresa_pet.md) preenchidos.

Enviar ao cliente **antes** de apresentar a proposta — nunca junto. O diagnóstico tem que ser absorvido separadamente para que a proposta tenha contexto.

---

## Formato

**HTML responsivo, exportável para PDF via Ctrl+P.**

- Inline CSS, sem dependências externas além de Google Fonts
- Identidade visual do Joabe Silva (ler `identidade/design-guide.md`)
- Estrutura de seções lineares — não slides
- Mobile-friendly (o cliente pode abrir no celular)

---

## Estrutura da apresentação

### Seção 1 — Capa
- Nome da empresa + segmento
- "Diagnóstico ODL Pet"
- Data + "Por Joabe Silva"

### Seção 2 — Quem analisou e como
Breve contexto sobre o que foi analisado e como — sem autopropaganda.

> "Esta análise foi preparada com base em auditoria digital dos canais públicos do [Nome], complementada pela reunião realizada em [data]. O objetivo é mapear o que está funcionando, o que está faltando e o que tem mais impacto no crescimento."

### Seção 3 — Situação atual

Resumo honesto e direto do que foi encontrado. 3–5 frases.

> Exemplo: "O [Pet Shop X] tem uma base ativa de clientes e um serviço com boa reputação local. O principal limitador hoje é a ausência de processo: sem lembrete de retorno, sem presença ativa no Google e sem atendimento estruturado no WhatsApp, o crescimento depende de o cliente lembrar de voltar — não de um sistema que garante isso."

### Seção 4 — Score ODL Pet

Visual com o score por pilar — tabela ou gráfico simples.

| Pilar | Nota | Máximo |
|-------|------|--------|
| Posicionamento | X | 15 |
| Presença Digital | X | 20 |
| Aquisição | X | 15 |
| Conversão | X | 15 |
| Atendimento | X | 15 |
| Automação | X | 10 |
| Escalabilidade | X | 10 |
| **Total** | **X** | **100** |

Classificação: [texto de interpretação]

### Seção 5 — Os 3 principais gargalos

Para cada gargalo: problema encontrado → impacto → o que muda se resolvido.

Usar linguagem de impacto no negócio, não de tecnologia ou marketing.

> Exemplo:
> **Recorrência sem processo**
> O cliente que faz banho mensalmente não recebe lembrete. A taxa de retorno espontânea é em torno de 40–50% da base. Para cada 10 clientes que fizeram serviço, 5–6 precisam ser reconquistados todo mês.
> *Se implementado:* sistema de lembrete automático no D-25 pode elevar a taxa de retorno para 70–80% — sem nenhuma ação adicional do dono no dia a dia.

### Seção 6 — Pontos fortes

O que já funciona — honesto, não forçado. Isso valida o trabalho do empresário e demonstra leitura completa (não só o que falta).

### Seção 7 — Próximos passos

CTA claro para o próximo passo: receber a proposta.

> "Com base nesse diagnóstico, vou preparar uma proposta com o que faz sentido implementar primeiro. Cada solução vai ser diretamente ligada a um gargalo encontrado aqui — não é um pacote padrão."

---

## Dicas de apresentação

**Ao enviar:**
> "Oi [Nome], como combinado, aqui está o diagnóstico do [Pet Shop]. É uma leitura de uns 10 minutos. Qualquer dúvida sobre o que encontrei, me chama. Vou te mandar a proposta com o plano de implementação nos próximos [X] dias."

**Se o cliente perguntar preço antes da proposta:**
> "Ainda não definido — depende do escopo que você quiser atacar primeiro. A proposta vai ter os valores detalhados por solução."

---

## Arquivo de saída

Salvar em `clientes/<NomeEmpresa>/diagnostico/`:
- `apresentacao-diagnostico.html` — versão visual para envio ao cliente
- Gerada com base nos dados do `mapa_gargalos_pet.md` e `score_empresa_pet.md`

---

## Próximo passo

Apresentação enviada → [proposta_odl_pet.md](../proposta/proposta_odl_pet.md)
