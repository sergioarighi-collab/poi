# POI Digital: briefing do Design

Síntese da apresentação "POI Digital: Conversa inicial com o Design", de 30/10/2026, com o status de cada pergunta no protótipo **Mesa POI**. As palavras seguem o documento original. **Nenhum número da empresa está aqui.**

> Por que esta apresentação existe: mostrar o POI a partir das necessidades da diretoria e da reunião, e não do formato atual dos relatórios, para que qualquer proposta de desenho parta do porquê.

## Legenda de termos

**Termos de negócio**

| Termo | Significado |
|---|---|
| POI | Planejamento Operacional Integrado. Retrato semanal da operação usado pela diretoria na reunião de terça. |
| Semana do POI | Segunda a domingo. A semana da operação fecha no domingo. |
| Semana do RH | Fecha na quinta. Por isso pessoas e operação têm datas de corte diferentes. |
| Fluxo de caixa | Realizado contra previsto do caixa, entregue pelo Financeiro. |
| Informativo | Página do fluxo de caixa exclusiva da Presidência. |
| Ranking | Ranking semanal de vendas por marca e linha, enviado pelo Comercial. |
| LL | Lucro líquido. O POI leva o resumo por marca. |
| MI / ME | Mercado interno / mercado externo. |

**Termos técnicos**

| Termo | Significado |
|---|---|
| Mapa Diário | Base gerencial de onde sai a maior parte do POI (faturamento, pedidos, carteira, produção, matéria-prima, estoque). |
| GER5003 | Relatório do POI, gerado pela TI na segunda de madrugada. |
| GER4002 | Conferência Mapa Diário × POI, em versão semanal e mensal. |
| GER5004 | Análise de lucro líquido. As duas folhas finais formam o LL resumo. |
| GER5011 | Vendas, diferenças no estoque e devolução de transportadora. |
| sbr0438_r | Relatório do ranking de vendas, rodado pelo Comercial. |

## O POI na mesa

Toda terça a diretoria se reúne com o retrato da semana anterior. Ao redor, as áreas que alimentam esse retrato, cada uma com seu prazo e seu formato.

| | |
|---|---|
| **Quem lê** | Presidência e diretoria. |
| **Quando** | Reunião presencial na terça-feira, com a semana da operação fechada até domingo. |
| **Para quê** | Acompanhar vendas, pedidos, produção, estoque, pessoas e caixa, e decidir onde agir. |
| **Como é lido** | Linha a linha, quadro a quadro, com atenção à semana que está ocorrendo. |

## Uma mesa, materiais diferentes

| Conteúdo | O que tem |
|---|---|
| **Núcleo da mesa** (comum) | Retrato da semana, pessoas, resultado por marca, ranking e fluxo de caixa. |
| **Aprofundamentos** (por pessoa) | Informativo exclusivo, base diária completa, análises de estoque, devolução e lucro. |

- O fluxo de caixa também chega a diretores direto pelo Financeiro, por um caminho separado. As visões podem não ser iguais.
- Às vezes a Controladoria deixa o material impresso na sala antes da reunião: precisa saber quem senta onde.

**Desafio de design:** como o mesmo material atende a mesa inteira e, ao mesmo tempo, o interesse de cada leitor?

## A semana do POI

Cada peça tem o seu dono, o seu prazo e o seu formato. Tudo converge na terça.

1. **Quinta, pessoas fecham:** o RH fecha a semana de funcionários.
2. **Sexta, RH envia:** Excel de funcionários por e-mail.
3. **Domingo, operação fecha:** a semana da operação vai de segunda a domingo.
4. **Segunda, tudo se junta:** de manhã, a TI entrega o Mapa Diário, o GER5003 e o GER4002. A Controladoria confere e monta. À tarde ou no fim do dia, chega o fluxo de caixa.
5. **Terça, reunião:** a diretoria se reúne. Raramente, o fluxo chega na manhã do mesmo dia.

**Desafio de design:** duas datas de corte convivem no mesmo material (pessoas até quinta, operação até domingo). E uma peça pode chegar por último.

## As peças e seus donos

| Peça | Quem produz | Como chega | Quando | Origem |
|---|---|---|---|---|
| Faturamento, pedidos, carteira, produção, matéria-prima, estoque e devoluções | TI, a partir do Mapa Diário | Gerado automaticamente (GER5003) | Segunda de manhã | Sistema |
| Previsão de entrada de pedidos | Controladoria | Recebida e lançada no sistema | Antes do fechamento | Sistema |
| Conferência da base com o material | TI | Relatório automático de diferenças (GER4002) | Segunda de manhã | Sistema |
| Lucro líquido por marca | Controladoria | Relatório gerado no sistema (GER5004) | Segunda | Sistema |
| Quadro de funcionários | RH | Excel por e-mail, remontado pela Controladoria em outro formato | Até sexta | Excel |
| Fluxo de caixa | Financeiro | Excel com linhas que variam de semana para semana | Segunda à tarde ou fim do dia | Excel |
| Ranking de vendas | Comercial | Relatório por e-mail, com parâmetros que variam | Semanal | E-mail |

**Desafio de design:** a ordem do pacote e as próprias peças mudam com o tempo. A Controladoria precisa poder mover, trocar, incluir e retirar peças sem depender de TI.

## O que a diretoria quer saber

| Bloco | Pergunta | No protótipo |
|---|---|---|
| Faturamento | Quanto vendemos na semana e no mês, em pares e em reais, no mercado interno e externo? | Sim (MI e ME, em reais) |
| Entrada de pedidos | Quanto entrou de pedido, por filial e por marca, contra o previsto? | Sim (por filial) |
| Carteira | Quanto temos para faturar nos próximos meses? | Sim |
| Produção | Quantos pares produzimos, por filial e por dia útil? | Sim |
| Matéria-prima | Quanto compramos, consumimos e temos em estoque? | Sim (Minha mesa do João) |
| Estoque e devoluções | Quanto produto pronto está disponível ou empenhado, e quanto voltou? | Parcial (devoluções, na Minha mesa do Clóvis) |
| Pessoas | Quantos funcionários diretos e indiretos temos, e quantos afastados? | Sim |
| Caixa | Como o realizado se compara ao previsto? | Sim (resumo para todos; Informativo só da Presidência) |
| Produto e resultado | O que mais vende, com que margem, e qual o lucro por marca? | Parcial (ranking com margem; falta o LL por marca) |

## A estrutura muda com a empresa

- **Filiais e regionais:** nascem, se juntam ou deixam de existir ao longo do ano.
- **Linhas variáveis:** o fluxo de caixa mostra mais ou menos linhas conforme a semana, e às vezes surgem linhas inéditas.
- **Recortes diferentes:** o ranking pode ser tirado de muitas formas, conforme os parâmetros escolhidos.

**Desafio de design:** o material precisa absorver mudanças de estrutura sem ser redesenhado a cada vez.

## Como o diretor usa o POI

| Necessidade | Hoje |
|---|---|
| Ler a semana | Leitura linha a linha de cada quadro, com foco na semana que está ocorrendo. |
| Perguntar na hora | Da leitura nascem perguntas: um cliente, um pedido, uma linha. Hoje a resposta depende de outra pessoa. |
| Anotar e reencontrar | Anotações antes e durante a reunião, para falar na mesa ou para si. Querem reencontrar o que foi falado nas reuniões passadas. Hoje não há registro. |
| Acompanhar a mesa | Cada diretor tem o seu ritmo: enquanto um fala, outros podem estar em outra página. |

**Aonde queremos chegar:** o diretor chega à resposta sozinho, na hora, sem depender de alguém para olhar e responder.

**A anotação faz parte da reunião:** antes, preparar (marcar o que levar à mesa); durante, registrar (anotar o que foi falado e decidido); depois, retomar (reencontrar na semana seguinte o que ficou combinado). A memória da reunião passa a ficar junto do material, e não espalhada em papéis e cadernos.

**Cada um no seu ritmo:** liberdade (ler, voltar, preparar o próprio ponto) e foco comum (todos no ponto de quem está falando, quando necessário).

## Onde a reunião acontece

| Condição | Situação |
|---|---|
| Internet | A reunião pode acontecer em local sem internet ou com sinal ruim. |
| Tela da sala | Pode haver TV, ou não. |
| Horário das peças | A última peça pode chegar na manhã da própria reunião (raro). |
| Local e lugares | Costuma ser na Filial 20, com lugares definidos à mesa. Integrantes e lugares podem mudar de uma reunião para outra. |
| Formato | Presencial, com a diretoria à mesa (sempre). |

**Ordem da mesa na Filial 20:** três lugares de um lado, dois do outro e a Presidência na cabeceira. Quem senta em cada lugar pode mudar.

## O limite é o dado, não o desenho

| | O quê | Impacto |
|---|---|---|
| **Liberdade total:** como mostrar | Ordem, agrupamento, gráficos, destaques, navegação, leitura em tela ou na mesa. | Sem impacto na base de dados. |
| **Avaliar juntos:** o que mostrar | Indicador novo, abertura nova, outro recorte, comparação com período diferente. | Bem-vindo, mas pode pedir rotina nova e recálculo do histórico. Cada ideia é avaliada à parte. |
| **Oportunidade:** peças de fora do sistema | Funcionários, fluxo de caixa e ranking chegam por Excel e e-mail. | O desenho pode propor como essas peças chegam. |

## As 17 perguntas deixadas para o Design × o protótipo

Legenda: ✅ respondida no protótipo · 🟡 parcialmente · ⬜ ainda não.

**O conteúdo**

| # | Pergunta | Status | Como o protótipo responde |
|---|---|---|---|
| 1 | **Duas datas de corte no mesmo material:** como o leitor percebe que cada bloco tem a sua própria data? | ✅ | Cada cartão traz a sua data de corte ("Operação até dom", "Pessoas até qui"). O detalhe explica a diferença. |
| 2 | **A estrutura muda com a empresa:** como o material absorve mudanças sem ser redesenhado? | 🟡 | Os cartões são gerados a partir dos dados (filial nova vira linha nova). Falta a tela de cadastro (módulo admin). |
| 3 | **A peça que chega por último:** como o material lida com o fluxo que chega na segunda à tarde ou na manhã da reunião? | ✅ | O cartão do caixa fica "Aguardando o Financeiro" e todos são avisados quando chega. A IA também sabe que a peça está pendente. |
| 4 | **O mesmo assunto por dois caminhos:** como evitar que a mesa discuta duas versões do mesmo número? | 🟡 | O fluxo da mesa é um só, com o selo "batido com o Clóvis". Falta marcar explicitamente a versão oficial. |
| 5 | **Volume e margem no ranking:** como mostrar o que vende muito e o que vende bem? | ✅ | O cartão de ranking cruza pares e margem e destaca margem negativa. |
| 6 | **Mostrar que está conferido:** como transmitir confiança sem mostrar a conferência? | ✅ | Selo "Conferido com a base" em cada cartão; o detalhe diz de onde vem e como foi conferido. |
| 7 | **Mover e trocar as peças:** como a Controladoria muda a ordem e inclui ou retira peças sem depender de TI? | 🟡 | Cada diretor oculta e fixa cartões. Falta o modo da Controladoria para montar a edição. |

**O uso**

| # | Pergunta | Status | Como o protótipo responde |
|---|---|---|---|
| 8 | **Do quadro até o detalhe:** como ir do número até o cliente, o pedido ou a linha sem se perder? | 🟡 | O detalhe abre ao lado, sem sair da tela; a IA busca o pedido do cliente. Falta navegação explícita por níveis. |
| 9 | **Anotação pessoal ou da mesa:** o que é só meu e o que é compartilhado? | ✅ | Cada anotação escolhe "Só eu" (cadeado) ou "Mesa". |
| 10 | **Reencontrar o que foi falado:** pela data, pelo assunto ou pelo número? | 🟡 | A ata da reunião e as decisões ficam registradas. Falta a busca no histórico. |
| 11 | **A anotação que vira acompanhamento:** como "ver isso na próxima semana" volta à mesa? | ✅ | "Virar pendência" e decisões com indicador acompanhado. |
| 12 | **Quando o número muda depois:** como a anotação mostra o valor do momento em que foi escrita? | ✅ | A anotação guarda o valor da época: "anotado quando o número era X · hoje: Y". |

**A mesa**

| # | Pergunta | Status | Como o protótipo responde |
|---|---|---|---|
| 13 | **Acompanhar quem está falando:** seguir deve ser opcional ou automático? | ✅ | "Mostrar a todos" leva a mesa ao cartão; seguir é opcional. |
| 14 | **Mostrar a todos o que estou vendo:** com e sem TV, quem assume a tela? | 🟡 | Na reunião ao vivo, cada tablet segue quem mostra. Falta um modo TV e a regra de passar a vez. |
| 15 | **O que não vai para a tela:** como separar o que vai para a mesa do que é só de quem mostra? | ✅ | Modo apresentação: ao mostrar, as anotações pessoais e a Minha mesa ficam ocultas. |
| 16 | **Sem internet:** o que precisa estar com o diretor antes da reunião? | 🟡 | A edição da semana fica no aparelho, e as perguntas entram numa fila. Falta definir o pacote offline da versão real. |
| 17 | **Quem vai e onde senta:** como a Controladoria monta a mesa de cada reunião? | ✅ | "Mesa desta reunião": seis lugares e a cabeceira, editáveis, com quem está conectado em destaque. |

## Pontos em aberto

| Ponto | Situação |
|---|---|
| Previsão de entrada de pedidos | Pelo manual de montagem da Controladoria, é recebida e lançada pela Controladoria. **Pendente:** confirmar se vale em 2026. |
| Dia da reunião | A apresentação registra montagem na segunda e reunião na terça (**confirmado**). A análise de negócio registra reunião na segunda. **Pendente:** alinhar. |
| Composição da mesa | Na Filial 20 vale a ordem da mesa do manual de montagem; integrantes e lugares podem mudar (**confirmado**). Hoje não há registro por reunião. |
| Semanas | A apresentação segue as semanas do calendário do POI e do RH. A análise de negócio adota blocos fixos (01–07, 08–14…). **Pendente:** alinhar. |
