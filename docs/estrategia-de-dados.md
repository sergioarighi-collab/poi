# Estratégia de dados: como as áreas alimentam o board

> Recomendação: **nem uma API por área, nem planilha para sempre.** Uma camada de dados única que lê o que já está nos sistemas. A planilha entra só como ponte temporária. O board serve de motivo para automatizar o trabalho das áreas na origem.

## O ponto de partida

Pelo GER5003 e pela primeira reunião, as fontes do POI se dividem em três tipos:

| Tipo | O que é | Exemplos | Quanto do POI |
|---|---|---|---|
| **1. Já está no sistema** | O dado nasce no ERP e o relatório só o lê | Pedidos, faturamento, carteira, produção, matéria-prima, estoque, devoluções, previsão de pedidos, lucro por marca, ranking | A grande maioria |
| **2. Está em Excel, mas vem de um sistema** | Alguém extrai, cola e formata | Quadro de funcionários (vem da folha/ponto); boa parte do fluxo de caixa (contas a pagar e a receber) | Uma parte pequena |
| **3. É julgamento de alguém** | Não existe em sistema nenhum | Projeções do caixa, ajustes do financeiro com o Clóvis, comentários e previsões das áreas | Pouco, mas importante |

Cada tipo pede uma solução diferente.

## Por que não uma API por área

- **As áreas não são donas dos sistemas.** RH, Financeiro e Comercial usam o ERP e a folha. Uma API "do RH" seria, na prática, uma API em cima do mesmo banco, feita e mantida pela TI.
- **Multiplica o trabalho.** Cada API precisa de contrato, autenticação, versão, monitoramento e alguém de plantão. Com cinco ou seis áreas, a manutenção cresce rápido.
- **Não resolve o tipo 3.** Julgamento não está em banco nenhum. Não existe endpoint para "o que o Clóvis acha do caixa".

## Por que não planilha para sempre

Você tocou no ponto certo: se o board só recebe Excel, ele fica mais bonito, mas o trabalho manual continua igual. As áreas seguem extraindo, colando e conferindo toda semana. O problema só muda de lugar.

## A recomendação: dado na origem, em três trilhas

### Trilha 1: ligar direto o que já está no sistema (tipo 1)

- A TI cria **visões de leitura (views)** no banco do ERP ou no data warehouse, no formato do modelo do POI: *métrica × cenário (previsto/realizado/ano anterior) × período × dimensão (filial, marca, produto)*.
- O backend do board expõe **uma única API**: as consultas que já simulamos no protótipo (`consultar_pedidos`, `consultar_producao`, `consultar_carteira` e outras). A IA e as telas usam essa API, e as permissões por diretor ficam nela.
- **Ganho imediato para a TI:** acaba a manutenção de layout de report. Filial nova vira linha nova na view, e a tela se ajusta sozinha.

### Trilha 2: automatizar na origem o que hoje é copiado (tipo 2)

Para cada planilha, um diagnóstico rápido com a área, coluna por coluna:

| A coluna é… | O que fazer |
|---|---|
| **Copiada de um sistema** | Ler direto do sistema (vira trilha 1) |
| **Calculada por fórmula** | Virar regra no backend, escrita uma vez e testada |
| **Digitada ou opinião** | Virar campo de formulário (trilha 3) |

Priorizar pelas **horas economizadas por semana**. O RH, por exemplo, provavelmente tem quase tudo vindo da folha: dá para gerar o quadro de funcionários automaticamente e o RH só confere. O fluxo de caixa pode ter as contas a pagar e a receber automáticas, deixando para o financeiro só a projeção e os ajustes.

**Ganho para as áreas:** elas deixam de montar a planilha e passam a só conferir e ajustar. E podem usar o mesmo painel para o próprio trabalho, não só para a reunião.

### Trilha 3: dar um lugar para o julgamento (tipo 3)

- Um **formulário simples no próprio board**, que é o módulo admin já previsto. Ali a área registra previsão, ajuste ou comentário, com nome, data e histórico.
- Inclui **fluxos de aprovação** quando necessário. Exemplo: o caixa só publica depois que o Clóvis confere.
- **Ganho:** o que hoje se perde em e-mail, papel debaixo da porta e versões de Excel fica registrado e rastreável.

### A planilha como ponte, com data para acabar

Enquanto as trilhas 1 a 3 não estão prontas, a área pode **subir o Excel de sempre**. A IA lê e organiza a planilha, e o sistema confere antes de publicar. Duas regras:

1. Cada planilha recebida já é **o mapa do que automatizar**: as colunas viram o backlog da trilha 2.
2. Cada planilha tem uma **data prevista para deixar de existir**, combinada com a área.

## Sequência sugerida

| Fase | Duração estimada | Entregas |
|---|---|---|
| **0. Inventário** | 2 a 4 semanas | Mapear com a TI onde está cada dado; diagnóstico coluna a coluna das planilhas de RH e Financeiro; dicionário de dados (ex.: o que é "realizado do mês") |
| **1. Piloto** | 6 a 8 semanas | Views e API para os dados do tipo 1 (a maior parte do POI); upload com conferência para RH e Financeiro; board em uso numa reunião real |
| **2. Automação na origem** | Contínua, por prioridade | Quadro de funcionários automático; contas a pagar e a receber automáticas; formulários para previsões e ajustes; aprovação do caixa |
| **3. O board vira a fonte** | Quando as planilhas acabarem | As áreas param de mandar Excel; a Controladoria deixa de montar os jogos e passa a revisar e publicar |

As durações são estimativas para discutir com a TI, não compromisso.

## Governança mínima

- **Um dono por dado:** quem responde se o número estiver errado.
- **Horário de fechamento:** por exemplo, segunda ao meio-dia, com o painel de entregas mostrando quem já fechou.
- **Dicionário de dados:** cada indicador com definição escrita. Encontramos um caso real: o "Realizado" do total do mês no GER5003 inclui o previsto da semana que ainda não aconteceu.
- **Conferência automática:** totais, filiais faltando e variações fora do normal são checados antes de publicar.

## Perguntas para destravar a fase 0

1. **TI:** os dados do GER5003 vêm direto do banco do ERP ou de um data warehouse? Existe ambiente de leitura que não pese no sistema de produção?
2. **RH:** de qual sistema sai a planilha de funcionários? Quanto tempo leva por semana para montar?
3. **Financeiro:** que partes do fluxo de caixa vêm de contas a pagar e a receber no ERP, e quais são projeção manual? Por que o sistema de fluxo existente não é usado?
4. **Comercial:** de onde sai o ranking de vendas?
5. **Controladoria:** quanto tempo leva hoje para montar os jogos toda segunda?
