# Relatório POI (GER5003): anatomia

Fonte: capturas das páginas 2 a 6 do relatório `POI - GER5003`, edição de **10/2026**, emitida em 26/10/2026 às 04:08 e gerada pela TI. Faltam a página 1 (faturamento) e a página 7 (comparativo do mês).

> Os números citados servem só para entender a estrutura e ilustrar a proposta. As imagens originais **não** foram versionadas.

## Padrão visual comum

- Cabeçalho: código `GER5003`, título "Planejamento Operacional Integrado", mês de referência, data e hora de emissão, "Página X de 7".
- Cores fixas por cenário: **Previsto = amarelo**, **Realizado = verde**, **ano anterior (2025) = azul-claro**. Variação negativa contra o ano anterior em **laranja**.
- Grade de **6 períodos**: as semanas do mês (01–04, 05–11, 12–18, 19–25, 26–31) mais o **Total do mês**. Algumas páginas trazem também a "Semana anterior" (do mês passado).
- Linha de **TOTAL** ao final de cada bloco.
- Papel paisagem, fonte muito pequena, de 300 a 600 números por página.

## Página por página

### Página 2: Entrada de pedidos interno/externo, por filial
- **Linhas:** Igrejinha FL01, Osório FL03, Mato Leitão FL06, Teutônia FL08, Candelária FL10, Candelária FL11, Roca Sales FL12, Novo Hamburgo FL16, Sapiranga FL17, Santa Clara FL18, Sapiranga FL23, Sapiranga FL30, Total.
- **Colunas por período:** Pares e Valor, cada um com Previsto, Realizado, % realizado/previsto, 2025 e % contra 2025.

### Página 3: Entrada de pedidos por marca, mais saldo de pedidos
- **Bloco 1:** mesma grade da página 2, com **marcas** nas linhas: Actvitta, Allegro, Beira Rio, BR Sport, Molekinho, Molekinha, Modare, Moleca, Vizzano.
- **Bloco 2, saldo de pedidos (carteira) por filial:**
  - quantidade e valor para cada mês de entrega (set/26, out/26, nov/26, dez/26, jan/27);
  - **carteira atual**;
  - **carteira do ano anterior**, com a variação %.

### Página 4: Produção, por filial
- Pares por período: Previsto, Realizado, %, 2025, %.
- **Média de pares por dia:** previsto e realizado, semanal e mensal.
- **Preço médio mensal:** previsto × realizado.
- **Dias úteis por semana**, 2026 × 2025. Os cortes das semanas são diferentes entre os anos (ex.: 01–04 × 01–05), e a primeira semana de 2026 teve só 2 dias úteis.

### Página 5: Matéria-prima
- **Disponibilidade por filial,** com as linhas extras Central SUP e MP Trânsito. Colunas por período: Sem giro 15 dias, Disponibilidade total e 2025. Hoje só a Central SUP tem valores em "sem giro".
- **Consumo por filial:** Realizado × 2025 por semana e total do mês.

### Página 6: Devoluções e produto pronto
- **Devoluções disponíveis (transportadora):** entradas, saídas e saldo, em pares e valor, por período, incluindo semana anterior e total de outubro/2025.
- **Produto pronto, disponível por filial:** pares, valor e **PM (preço médio)**. Subtotais de calçados, bolsas e meias.
- **Produto pronto, empenhado por filial:** mesma estrutura.
- **Geral:** total, calçados, bolsas e meias.
- Aqui entra a futura separação de **bolsas em produção × revenda** citada na reunião.

## O que isso revela

**Os dados têm uma estrutura única.** Quase tudo é a mesma "fatia":

```
fato(métrica, cenário, período, dimensão, valor)

  métrica   = pares | valor | preço médio | disponibilidade | consumo | saldo ...
  cenário   = previsto | realizado | ano anterior
  período   = semana do mês | total do mês | semana anterior | mês de entrega
  dimensão  = filial | marca | tipo de produto (calçados/bolsas/meias; produção/revenda)
```

Se o layout for gerado a partir desse modelo, uma filial ou abertura nova vira **um dado novo, não uma manutenção de report**. Isso ataca diretamente a maior dor da TI.

**Ruídos que o papel esconde ou cria:**
- Linhas sempre zeradas, como Sapiranga FL17 e Allegro, ocupam espaço todo mês.
- Na semana que ainda não aconteceu (26–31), o % aparece como **0**, como se fosse uma queda. O certo seria "sem dado".
- Comparar com 2025 por semana mistura calendários diferentes (dias úteis diferentes). Faz mais sentido comparar por dia útil ou pelo acumulado.
- O mesmo número aparece repetido em páginas diferentes: o total de pedidos por filial e por marca é idêntico.

**O "Realizado" do total do mês não é só realizado.** Nas páginas de pedidos e de produção, a coluna "Realizado" do **Total do mês** soma o realizado das semanas que já passaram **com o previsto da semana que ainda não aconteceu** (26–31). Em pedidos: R$ 362,8 mi realizados + R$ 105,0 mi previstos = os R$ 467,8 mi impressos. Na prática é uma projeção com rótulo de realizado.

**A história que a grade não conta.** Exemplo com os dados de outubro até o dia 25, só com o que já aconteceu:

| Indicador | Realizado até 25/10 | % do previsto | vs mesmo período de 2025 |
|---|---|---|---|
| Entrada de pedidos (valor) | R$ 362,8 mi | **69%** | **−22%** |
| Entrada de pedidos (pares) | 7,22 mi | 67% | **−23%** |
| Produção (pares) | 8,60 mi | 99% | +1% |
| Carteira atual (pares) | 15,45 mi | — | **−15%** (contra out/2025) |

Leitura possível: a fábrica está entregando o plano, mas a entrada de pedidos caiu cerca de 22% contra o ano passado, e a carteira está encolhendo. Hoje essa conclusão exige cruzar três páginas com a régua. Numa versão digital, ela seria a **primeira frase** da tela.

## Perguntas novas

1. A "semana anterior" das páginas 5 e 6 é a última semana do mês passado? Por que ela não aparece nas páginas 2 a 4?
2. Previsto × realizado: quem define o previsto de cada página (Controladoria, comercial, PCP)?
3. O valor de entrada de pedidos é bruto ou líquido? Em qual tabela de preço?
4. Faz sentido comparar com o ano anterior por dia útil em vez de por semana do calendário?
5. Linhas zeradas (FL17, Allegro) devem ser escondidas automaticamente?
6. A diretoria sabe que o "Realizado" do total do mês inclui o previsto da semana que falta? É isso que querem ver (projeção) ou preferem o realizado puro?
