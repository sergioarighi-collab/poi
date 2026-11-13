# POI Digital — Descoberta

Documento vivo. Consolida o que sabemos, o que precisamos decidir e as primeiras hipóteses. Atualizar a cada reunião.

## Problema

A diretoria conduz a reunião semanal do POI em papel. Cada diretor recebe um "jogo" de relatórios em formato de planilha impressa, montado à mão pela Controladoria. A leitura é lenta e linha a linha. Perguntas feitas na hora ficam sem resposta, as anotações se perdem, e cada mudança de layout pedida de última hora força a TI a correr contra o prazo.

## Objetivo da iniciativa

Repensar **sem amarras** como a diretoria consome a informação do POI: antes da reunião, na mesa e depois dela. A frente "padrão" é a da Paloma; esta é a frente livre.

## Requisitos que já sabemos

**Precisa ter**
- Retrato da semana: previsto × realizado × variação × ano anterior, por filial, marca e produto, mais o total do mês e a semana anterior.
- Os blocos atuais: faturamento, entrada de pedidos, carteira, produção, matéria-prima, estoque/produto pronto, devoluções, pessoas, fluxo de caixa, lucro líquido por marca e ranking/mix (com imagem).
- **Conteúdo por pessoa:** núcleo comum, peças exclusivas e níveis de detalhe diferentes (o fluxo de caixa é o caso mais sensível).
- **Navegação independente:** cada diretor no seu ritmo, sem ficar preso a quem está falando.
- **Anotações** por reunião, por linha ou registro e por célula. Persistentes, consultáveis nas semanas seguintes, feitas antes, durante e depois.
- **Funcionar offline**, com internet ruim e sem TV.
- **Números grandes e legíveis.**
- **Estrutura dinâmica:** filiais, regionais e aberturas novas (ex.: bolsas de produção × revenda) entram ou saem sem retrabalho de layout.

**Desejável**
- Gráficos que contem a história, com tabela por trás e drill-down.
- Respostas na hora ("o pedido X faturou?") consultando a base, talvez com IA.
- Diretor montando o próprio jogo com muito pouco esforço.
- Áreas publicando material próprio para os diretores.
- Espelhar a tela numa TV quando houver.

## Perguntas em aberto

**Uso e pessoas**
1. Qual dispositivo? Tablet individual, TV compartilhada ou os dois? Algum diretor usaria notebook ou celular?
2. Dá para fazer uma sessão de observação de uma reunião POI, ou ao menos conversar com o Rodrigo?
3. Os diretores aceitariam um "modo apresentação", em que quem fala conduz a tela da TV, e cada um continuaria livre no seu tablet?
4. As anotações são privadas, compartilhadas ou as duas coisas? Viram tarefas ou pendências?
5. As perguntas da reunião precisam ser respondidas na hora ou podem virar um registro para alguém responder depois?

**Dados**
6. Com que frequência os dados atualizam? O snapshot semanal "congelado" para a reunião é suficiente ou querem dado vivo?
7. Fluxo de caixa: entra no app? Entra o processo de conferência Financeiro + Clóvis ou só o número fechado?
8. Funcionários e fluxo de caixa: como capturar sem obrigar as áreas a mudar de sistema agora (upload do Excel, template, formulário)?
9. Ranking/mix: qual é a fonte real no sistema comercial?
10. Quais regras de permissão existem hoje (quem vê o quê) e quem as define?

**Operação**
11. Quem publica a edição da semana? Continua sendo a Controladoria?
12. Que segurança exigir para usar fora da empresa (tablet perdido, offline com dado sensível)?

## Hipóteses iniciais de solução (para validar)

- **"Edição semanal" offline-first:** um pacote da semana é publicado e sincronizado nos tablets antes da terça e funciona sem rede. As anotações sincronizam quando houver conexão.
- **Narrativa em vez de grade:** cada bloco abre com 2 ou 3 destaques, como "faturamento 25% abaixo do previsto; filial X puxou a queda". A tabela completa fica a um toque.
- **Escala e leitura:** fonte grande por padrão, foco numa filial por vez, modo "régua" que destaca a linha em leitura.
- **Layout gerado a partir de metadados:** filial, regional e abertura são dados, não desenho. Novas dimensões aparecem sem manutenção de report. A análise do GER5003 mostra que quase tudo cabe num modelo único: métrica × cenário × período × dimensão. Ver [anatomia do relatório](relatorios/ger5003-poi.md).
- **Meu jogo:** um jogo base vem pronto da Controladoria, e o diretor reordena, fixa ou oculta blocos e anexa material próprio.
- **Camada de anotações** ligada à semana, ao bloco e à célula, com histórico ("o que anotei sobre a filial 10?").
- **Assistente de perguntas (IA)** com consulta ao vivo quando houver rede, ou fila de perguntas para responder depois.
