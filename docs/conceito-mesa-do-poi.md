# Conceito: Mesa do POI

> Protótipo navegável: https://claude.ai/artifact/7EF9MUmoHhztHvHTLC6m3A (privado; compartilhe pelo menu Share)

## A ideia

Digitalizar as tabelas só muda o problema de lugar: a diretoria continuaria lendo linha a linha, agora numa tela. A Mesa do POI muda **o que a reunião faz**:

| Hoje | Na Mesa |
|---|---|
| Ler a grade e descobrir o que importa | **A semana chega lida**: 5 ou 6 frases com o que mudou, cada uma com o número principal e um gráfico mínimo de prova |
| Pergunta sem resposta ("o pedido X faturou?") | **Pergunta à IA na hora**, falando ou escrevendo. A resposta vira um cartão na mesa |
| Anotação no papel, perdida na semana seguinte | **Marcar, anotar e editar** a própria frase. Tudo fica guardado |
| A reunião termina sem registro | **Saídas da reunião**: decisões, pendências e perguntas abertas, cada uma com um responsável. O que fica aberto volta na semana seguinte |
| Promessas ditas na mesa se perdem | **"Promessa da semana passada"**: a Mesa confere o que foi dito contra o que aconteceu (ex.: Candelária FL10, de 49% para 81% do previsto) |
| Mudança de layout pedida na segunda de manhã | Pedir à IA ("separa bolsas de produção e revenda") em vez de abrir manutenção de report |

## Princípios

1. **Frase antes de número, número antes de tabela.** A tabela continua existindo, mas a um toque, como prova.
2. **Editável por quem lê.** O diretor corrige a frase quando sabe mais que o dado ("vai superar: tem pedido a liberar").
3. **Rápido e direto.** Uma tela, sem menus. Fonte grande, com controle de tamanho.
4. **Funciona sem internet.** A edição da semana (frases, números, gráficos) é gerada na publicação e fica no tablet. Só a IA precisa de rede; sem rede, as perguntas sugeridas continuam respondendo.
5. **A reunião produz decisões, não leitura.**

## O que o protótipo já faz

- 6 cartões gerados a partir dos dados reais do GER5003 (pedidos, onde está a queda, produção, carteira, promessa da semana passada, mês até o dia 25).
- Frase editável (toque e reescreva), com opção de voltar ao original.
- Marcar, anotar, "Por quê?" (pede à IA a explicação) e "Virar pendência".
- Barra de pergunta com ditado por voz. A IA responde com um cartão no mesmo formato ou registra itens ("anota que…").
- Painel de saídas: decisões, pendências e perguntas, com responsável e check.
- Respostas locais para as perguntas sugeridas, que funcionam sem IA.

## Limites do protótipo

- Anotações e decisões ficam só no navegador de quem usa. Na versão real, elas são compartilhadas entre os diretores, com o que é privado separado do que é da mesa.
- Só pedidos, produção e carteira. Faltam faturamento, matéria-prima, produto pronto, pessoas, caixa e mix.
- Sem permissões por diretor (ex.: o fluxo de caixa completo só para o Sr. Roberto).

## Para validar com a diretoria

- O Rodrigo usaria isso no lugar do papel? O que ele sentiria falta?
- As frases geradas soam como a diretoria fala? Quem revisa antes de publicar (a Controladoria)?
- Tablet individual, TV compartilhada ou os dois?
- Quais perguntas surgem de verdade na reunião? (Ótimo material para treinar e testar a IA.)
