# Conceito: Mesa do POI

> Todos os números do protótipo são **fictícios**, na mesma estrutura do relatório do POI. Os dados reais da empresa não ficam no protótipo nem no repositório.

> Protótipo navegável: https://claude.ai/artifact/7EF9MUmoHhztHvHTLC6m3A (privado; compartilhe pelo menu Share)

## A ideia

Digitalizar as tabelas só muda o problema de lugar: a diretoria continuaria lendo linha a linha, agora numa tela. A Mesa do POI muda **o que a reunião faz**:

| Hoje | Na Mesa |
|---|---|
| Ler a grade e descobrir o que importa | **A semana chega lida**: 5 ou 6 frases com o que mudou, cada uma com o número principal e um gráfico mínimo de prova |
| Pergunta sem resposta ("o pedido X faturou?") | **Pergunta à IA na hora**, falando ou escrevendo. A resposta vira um cartão na mesa |
| Anotação no papel, perdida na semana seguinte | **Marcar, anotar e editar** a própria frase. Tudo fica guardado |
| A reunião termina sem registro | **Saídas da reunião**: decisões, pendências e perguntas abertas, cada uma com um responsável. O que fica aberto volta na semana seguinte |
| Promessas ditas na mesa se perdem | **"Promessa da semana passada"**: a Mesa confere o que foi dito contra o que aconteceu (ex.: uma filial que ia recuperar com pedidos a liberar: recuperou ou não?) |
| Mudança de layout pedida na segunda de manhã | Pedir à IA ("separa bolsas de produção e revenda") em vez de abrir manutenção de report |

## Princípios

1. **Frase antes de número, número antes de tabela.** A tabela continua existindo, mas a um toque, como prova.
2. **Editável por quem lê.** O diretor corrige a frase quando sabe mais que o dado ("vai superar: tem pedido a liberar").
3. **Rápido e direto.** Uma tela, sem menus. Fonte grande, com controle de tamanho.
4. **Funciona sem internet.** A edição da semana (frases, números, gráficos) é gerada na publicação e fica no tablet. Só a IA precisa de rede; sem rede, as perguntas sugeridas continuam respondendo.
5. **A reunião produz decisões, não leitura.**

## O que o protótipo já faz

- 6 cartões gerados a partir de dados fictícios, na estrutura do GER5003 (pedidos, onde está a queda, produção, carteira, promessa da semana passada, mês até o dia 25).
- Frase editável (toque e reescreva), com opção de voltar ao original.
- Marcar, anotar, "Por quê?" (pede à IA a explicação) e "Virar pendência".
- Barra de pergunta com ditado por voz. A IA responde com um cartão no mesmo formato ou registra itens ("anota que…").
- Painel de saídas: decisões, pendências e perguntas, com responsável e check.
- Respostas locais para as perguntas sugeridas, que funcionam sem IA.

## Simulação da arquitetura (versão 2)

O protótipo agora reproduz o fluxo descrito em [arquitetura.md](arquitetura.md):

- **Entrar como:** escolha o diretor. As permissões mudam conforme quem está logado: o fluxo de caixa detalhado aparece só para o Sr. Roberto, e os demais veem o resumo.
- **Backend simulado:** a IA não recebe os dados de uma vez. Ela chama consultas (`consultar_pedidos`, `consultar_producao`, `consultar_carteira`, `buscar_pedido_cliente`, `consultar_fluxo_caixa`), como faria no servidor real.
- **"Como chegou nessa resposta":** cada resposta mostra as consultas feitas e se alguma foi negada.
- **Online / Sem internet:** sem conexão, as frases da semana e as perguntas sugeridas continuam funcionando, e as outras perguntas entram numa fila respondida quando a conexão volta.
- Pedidos de clientes e fluxo de caixa usam **dados fictícios**, porque não estão no GER5003.

Código do protótipo: [`prototipos/mesa-poi.html`](../prototipos/mesa-poi.html), um fragmento de página publicado como artifact.

## Reunião ao vivo e novos insights (versão 3)

**Reunião ao vivo:** um botão coloca todos na mesma mesa.

- Barra "Na mesa" mostra quem está na reunião.
- Marcações, frases editadas, comentários, insights e saídas da reunião aparecem para todos na hora, com o nome de quem fez.
- **Mostrar a todos:** quem está falando leva a mesa para um cartão. Quem marcou "Seguir quem está mostrando" vai junto; quem quiser continua lendo no próprio ritmo.
- Fora do modo ao vivo, tudo continua individual, só no aparelho.

**Insights:**

- **A IA procura novos insights:** a IA consulta pedidos, produção e carteira e procura cruzamentos que a tabela esconde. Exemplos (com dados fictícios):
  - o previsto desta semana é bem menor que o da anterior, então o "% do previsto" parece melhor do que é;
  - uma filial produz no plano, mas os pedidos e a carteira despencaram.
- **Meu insight:** cada diretor publica a própria leitura como um cartão. Os outros podem marcar e comentar.

**Para testar com outra pessoa:** compartilhe o artifact pelo menu Share. A pessoa precisa de permissão para usar (Contributor ou acima) para escrever na mesa.

## Minha mesa: uma página por diretor (versão 5)

Três camadas, cada uma com um papel:

| Camada | Para quê | Quem vê |
|---|---|---|
| **Minha mesa** | Preparar-se antes e acompanhar depois | Só o diretor |
| **Semana / Insights / Saídas** | A leitura comum da semana | Todos |
| **Reunião ao vivo** | Discutir e decidir juntos, na hora | Todos, ao mesmo tempo |

A Minha mesa de cada diretor tem:

- **Sua parte na pauta:** os blocos que ele apresenta.
  - Maribel: pedidos e carteira.
  - João: produção e a promessa da semana anterior.
- **Um cartão exclusivo:**
  - Clóvis: devoluções em transportadora.
  - João: matéria-prima.
  - Maribel: carteira por mês de entrega.
  - Sr. Roberto: fluxo de caixa detalhado (fictício).
  - Rodrigo: o que está aberto na mesa, por responsável.
- **Fixados por você:** qualquer cartão da semana ou insight que ele queira acompanhar.
- **Minha pauta para terça:** os pontos que ele quer levar. A IA sugere itens a partir dos números da parte dele, e "Levar à mesa" transforma um item em pergunta aberta para todos.
- **Minhas pendências:** os itens das saídas da reunião em nome dele.
- **Compartilhar com a mesa:** a pauta é privada por padrão. Se o diretor quiser, ele a compartilha, e ela aparece para todos em "Pautas da reunião", no topo da aba Saídas. Na reunião ao vivo, a pauta sincroniza na hora e pode voltar a ser privada a qualquer momento.

No protótipo, troque o papel no menu do topo para ver a página de cada um.

## Decisões acompanhadas e ata automática (versão 6)

**Decisões com indicador:**

- Em Saídas, cada decisão pode acompanhar um indicador, por exemplo "Pedidos · Teutônia, % do previsto". O board guarda o valor do dia da decisão e, nas edições seguintes, mostra o antes e o depois.
- O cartão **"Decisões em acompanhamento"**, na aba Semana, mostra quantas decisões melhoraram o indicador desde que foram tomadas.
- Exemplo no protótipo (dados fictícios): "Liberar os pedidos travados de Candelária FL10", decidida na semana de 12 a 18, mostra o indicador antes e depois.

**Ata automática:**

- O botão **"Gerar ata da reunião"** monta a ata com resumo da semana, decisões (com responsável e indicador), pendências, perguntas abertas, destaques (cartões marcados, comentários e insights) e pautas compartilhadas.
- A IA escreve só o resumo e os destaques. Decisões e responsáveis vêm direto do que foi registrado, sem reescrita.
- Na reunião ao vivo, a ata fica publicada para todos. O botão "Copiar texto" leva a ata para um e-mail. Na versão final, ela será enviada automaticamente.

## Respostas ao briefing do Design (versão 7)

As perguntas do briefing ([briefing-design.md](briefing-design.md)) viraram funcionalidades:

- **Data de corte em cada cartão:** "Operação até dom" ou "Pessoas até qui".
- **Selo de conferência:** "Conferido com a base", "Excel do RH", "Excel do Financeiro" ou "E-mail do Comercial", com a explicação no detalhe.
- **Peça que chega por último:** o fluxo de caixa aparece como "Aguardando o Financeiro" até chegar, e todos são avisados.
- **Núcleo completo:** faturamento (MI e ME), pessoas, ranking com volume e margem, e caixa resumido para todos; o Informativo do caixa é só da Presidência.
- **Anotação "Só eu" ou "Mesa",** guardando o valor do número no momento em que foi escrita.
- **Modo apresentação:** ao mostrar a tela, as anotações pessoais e a Minha mesa ficam ocultas.
- **Mesa desta reunião:** a Controladoria define quem vai e onde senta (Filial 20: três lugares de um lado, dois do outro, Presidência na cabeceira).

## Limites do protótipo

- Anotações e decisões ficam só no navegador de quem usa. Na versão real, elas são compartilhadas entre os diretores, com o que é privado separado do que é da mesa.
- Só pedidos, produção e carteira. Faltam faturamento, matéria-prima, produto pronto, pessoas, caixa e mix.
- Sem permissões por diretor (ex.: o fluxo de caixa completo só para o Sr. Roberto).

## Para validar com a diretoria

- O Rodrigo usaria isso no lugar do papel? O que ele sentiria falta?
- As frases geradas soam como a diretoria fala? Quem revisa antes de publicar (a Controladoria)?
- Tablet individual, TV compartilhada ou os dois?
- Quais perguntas surgem de verdade na reunião? (Ótimo material para treinar e testar a IA.)
