# POI Digital: material de hoje (relatórios)

Inventário do material que compõe o POI hoje, com a estrutura de cada relatório. Serve **para consulta de conteúdo**, não como ponto de partida de formato. As palavras seguem o documento original. **Nenhum número da empresa está aqui.**

## As peças

| Peça | Relatório | Quem gera | Tratamento no material de referência |
|---|---|---|---|
| Retrato da semana | GER5003 (sete páginas) | TI, a partir do Mapa Diário | Sem máscara |
| Pessoas | Quadro de funcionários (Excel do RH, remontado) | RH → Controladoria | Só contagens |
| Resultado | LL resumo (GER5004, duas folhas) | Controladoria | Sem máscara |
| Produto | Ranking de vendas (sbr0438_r) | Comercial | Margem mascarada |
| Caixa | Fluxo de caixa (Excel do Financeiro) | Financeiro | Valores mascarados |
| Aprofundamento | GER5011 (quatro páginas) | TI | Sem máscara |
| Conferência | GER4002 (semana e mês) | TI | Sem máscara |

Também relacionado: GER1004 (Mapa Diário automático do POI).

## Ordem do pacote na mesa

Conforme o manual da Controladoria:

**POI páginas 1 a 6 → Funcionários → LL resumo → POI página 7 → Ranking.**

O fluxo de caixa é entregue à parte, pelo Financeiro.

> No protótipo, essa é a ordem padrão da edição. A Controladoria pode mudá-la e voltar à ordem do manual quando quiser.

## 1. Retrato da semana (GER5003)

Gerado pela TI na segunda de madrugada, com posição até domingo.

| Página | Conteúdo | Estrutura |
|---|---|---|
| 1 | Faturamento do mercado interno e externo, por semana e no mês, em pares e em reais | Por unidade: previsto, realizado, %, ano anterior, %. Quadro final: faturamento líquido, (−) devoluções, N.F. (refaturamento), devoluções − refaturamento. Linha de prazo médio previsto e real. |
| 2 | Entrada de pedidos por filial, realizado contra previsto | Mesma grade da página 1, em pares e valor. |
| 3 | Entrada de pedidos por marca e saldo da carteira | Grade por marca + saldo de pedidos por mês de entrega, carteira atual e carteira anterior. |
| 4 | Produção por filial | Pares por semana; média de pares por dia; preço médio mensal; dias úteis do mês, deste ano e do anterior. |
| 5 | Disponibilidade de matéria-prima | Sem giro 15 dias, disponibilidade total e ano anterior, por unidade; consumo de matéria-prima. |
| 6 | Devoluções disponíveis e estoque de produto pronto | Entradas, saídas e saldo de devoluções; produto pronto disponível e empenhado, com preço médio; totais de calçados, bolsas e meias. |
| 7 | Comparativo do mês atual | **Por dia útil:** pedidos de pronta entrega, entrada total e faturamento, em pares e reais, contra o mesmo dia útil do ano anterior; variação percentual do preço médio. |

## 2. Pessoas: quadro de funcionários

Montado pela Controladoria a partir do Excel do RH. As semanas do RH fecham na quinta.

- Diretos, indiretos e total por unidade: filiais, regionais e áreas administrativas.
- Diferença semanal.
- Afastados por motivo e por filial.

## 3. Resultado: resumo do lucro líquido (GER5004)

As duas folhas finais da análise de lucro líquido, por marca.

- **Folha 1:** lucro por marca, semana a semana, no mercado interno (MI) e externo (ME), com quantidade de pares, preço de venda e LL %.
- **Folha 2:** acumulado das semanas e mensal realizado do ano anterior.

## 4. Produto: ranking de vendas (sbr0438_r)

Enviado pelo Comercial por e-mail.

- Por marca e por categoria (Aberto, Botas, Fechado, Bolsas), com o total de linhas.
- Cada item tem posição, referência, foto, pares e MC (margem de contribuição).
- A Controladoria confere se todos os itens têm foto, pares, margem e linha.

## 5. Caixa: fluxo de caixa (Excel do Financeiro)

Linhas que variam de semana para semana. As páginas 1 e 2 vão a todos; a página extra é restrita.

- **Página 1:** por semana, previsto e real, total do mês, média do ano anterior e percentual da semana.
  - Ingressos: recebimentos MI, cheques negociados, vendor, ACC, recebimentos ME.
  - Desembolsos operacionais: matéria-prima, matéria-prima importada, pessoal, comercial, impostos e demais linhas.
  - Saldo operacional.
  - Ingressos e desembolsos não operacionais.
  - Saldo não operacional, saldo inicial e saldo final.
- **Página 2:** contas a pagar, exportações e duplicatas a receber.
- **Página extra, o Informativo (Presidência):** aplicações financeiras, valor ACC, saldo total de empréstimos, informativo de aplicações e aumento do capital de giro.

## 6. Aprofundamento: vendas, diferenças de estoque e devolução (GER5011)

Material adicional de parte da diretoria.

- **Vendas do mês:** produto pronto (pares, preço médio, faturamento), realizado × orçado × variação; matéria-prima; sucata e imobilizado.
- **Diferença no estoque:** saldo inicial, compras líquidas, mão de obra, consumo, saldo da semana e a diferença resultante.
- **Devolução de transportadora por motivo,** em MI e ME. Exemplos de motivos: mercadoria apreendida pela fiscalização, comercial solicitou lançamento do DIS, não tem pedido, recusa clientes especiais, desacordo com pedido, aguardando agendamento, mercadoria fora do prazo, retido na transportadora, loja fechada, pedido cancelado.

## 7. Conferência: Mapa Diário × POI (GER4002)

Relatório da TI que aponta diferenças entre a base e o retrato da semana. Usado na montagem; **não vai à mesa**. Tem versão semanal e mensal.

Indicador por indicador, com o valor no Mapa, o valor no POI e a diferença (destacada quando não é zero):

- **Indicadores industriais:** produção real, compras, mão de obra atelier, consumo de matéria-prima.
- **Estoque:** total de matéria-prima, total de produto pronto, beneficiamento, consignação.
- **Entrada de pedidos, faturamento, devoluções:** pares e valor.
- **Carteira atual e carteira dos próximos meses.**

## Como o protótipo usa este inventário

Com dados **fictícios** e respeitando a regra da leveza:

| Do material de hoje | No protótipo |
|---|---|
| Ordem do pacote do manual | Ordem padrão da edição, no perfil da Controladoria |
| LL resumo | Cartão "Resultado por marca · LL" (MI no gráfico; ME e acumulado no detalhe) |
| Página 7 (por dia útil) | "Ritmo por dia útil" no detalhe de pedidos e de faturamento |
| Quadro do faturamento líquido | Detalhe do faturamento |
| Estrutura do fluxo de caixa | Detalhe do caixa; Informativo na Minha mesa da Presidência |
| Devolução de transportadora por motivo | Minha mesa do Clóvis |
| GER4002 | Quadro de conferência no perfil da Controladoria |
| Ranking por categoria, com MC e checagem | Detalhe do ranking; checagem no perfil da Controladoria |
| Pessoas por unidade e afastados | Detalhe de Pessoas |
