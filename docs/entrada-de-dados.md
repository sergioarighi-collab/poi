# Entrada de dados: como as áreas alimentam o POI

Hoje cada área monta o seu Excel e manda para a Controladoria, que converte, junta e imprime. A Mesa do POI só funciona se esses dados entrarem na plataforma sem criar trabalho novo para as áreas.

## Quem entrega o quê (hoje)

| Peça | Área | Formato atual | Já está em sistema? |
|---|---|---|---|
| Faturamento, pedidos, carteira, produção, MP, estoque, devoluções | TI (mapa diário → GER5003) | Report | **Sim** |
| Previsão de entrada de pedidos | Controladoria | Lançada no sistema | **Sim** |
| Lucro líquido por marca | Controladoria | Gerencial | **Sim** |
| Ranking de vendas / mix | Comercial | Relatório (chega como Excel) | Provavelmente sim; confirmar a origem |
| Quadro de funcionários | RH | Excel (convertido pela Controladoria) | **Não** |
| Fluxo de caixa | Financeiro (conferido com o Clóvis) | Excel, entregue impresso | **Não** (o sistema de fluxo existe, mas não é usado) |

Conclusão: a maior parte dos dados já está no sistema. As planilhas manuais se resumem basicamente a **RH e Financeiro**, além do que cada diretor leva por conta própria.

## Proposta em fases

### Fase 1: subir a planilha como ela é (junto com o piloto)

- Cada área **arrasta o Excel de sempre** para a plataforma. Não muda o layout e não precisa de treinamento.
- A **IA lê a planilha** e mapeia as colunas para o modelo do POI (filial, semana, métrica, valor). No primeiro envio, alguém da área confirma o mapeamento. Depois, ele é reaproveitado.
- **Conferência automática antes de publicar:**
  - o total bate com a soma das linhas?
  - falta alguma filial?
  - algum número variou demais contra a semana anterior?
  - a semana está certa?

  Se algo não bate, o sistema mostra e a área corrige ali mesmo.
- **Painel de entregas da semana:** quem já mandou, quem falta e o prazo (segunda até o meio-dia), com lembrete automático. Isso acaba com o "papel deixado por baixo da porta".
- A Controladoria **aprova e publica** a edição da semana. É ela quem fecha o material da semana, como hoje.

### Fase 2: módulo admin

- **Cadastro do que antes era manutenção de report:** filiais, regionais, marcas, aberturas (ex.: bolsas produção × revenda), quem vê o quê e a ordem do material de cada diretor. Mudança de última hora vira configuração, e a TI deixa de editar o layout.
- **Formulários simples** para as áreas que preferirem digitar em vez de subir Excel.
- **Histórico e auditoria:** quem enviou, quando, e o que mudou entre versões.

### Fase 3: integração direta

- O que já está no sistema (GER5003, previsão, LL, ranking) vem **direto do banco**, sem planilha.
- RH e Financeiro: avaliar a integração com a folha e com o sistema de fluxo de caixa quando fizer sentido para as áreas. Até lá, o upload continua.

## Por que começar pela planilha

- **Zero mudança para as áreas** no começo. A adoção depende de não dar trabalho extra.
- Permite validar a Mesa com os diretores **antes** de investir em integração.
- A IA lendo planilhas variadas é exatamente o tipo de trabalho que ela faz bem, e a conferência evita que um erro chegue à mesa da diretoria.

## Perguntas para as áreas

1. RH e Financeiro: podem mandar exemplos reais dos Excel de algumas semanas? (Servem para testar a leitura automática.)
2. O layout dessas planilhas muda com frequência?
3. Quem hoje confere os números antes de chegar à Controladoria?
4. O fluxo de caixa precisa passar pelo Clóvis **antes** de entrar na plataforma? Se sim, a aprovação dele vira uma etapa do fluxo.
5. Que outros materiais os diretores levam por conta própria (a "pastinha" do João)? Devem entrar como anexos da edição?
