# Arquitetura: primeiras decisões

Rascunho para discutir com a TI. Nada aqui está fechado, exceto o que está em **Decisões**.

## Decisões (14/11/2026)

1. **Primeiro formato: tablet.** É o substituto direto do papel na mesa de reunião.
2. **Depois: versão web,** para quem quiser preparar a reunião no computador ou usar fora dela.
3. **IA conectada ao Claude da empresa,** com a conta corporativa, não a conta pessoal de cada usuário como no protótipo.

## Proposta: um app web só, instalável no tablet

Para não construir duas vezes, a recomendação é fazer desde o início **um app web responsivo e instalável (PWA)**:

- No tablet, ele é instalado na tela inicial, abre em tela cheia e **funciona offline**.
- No computador, o mesmo app abre no navegador. A "versão web" sai quase de graça.
- Um app nativo (iPad ou Android) só se justifica se aparecer algo que o PWA não resolve, como a gestão de dispositivos (MDM) exigir.

## Como a IA se conecta

```
 Tablet / Web (Mesa do POI)
        │  pergunta do diretor
        ▼
 Backend do POI  ── autentica o usuário (SSO da empresa)
        │          ── aplica o que cada diretor pode ver
        ▼
 Claude (conta da empresa)
        │  "preciso dos pedidos de Novo Hamburgo nas últimas 4 semanas"
        ▼
 Ferramentas do backend ──► dados (ERP, mapa diário, Excel do RH e do financeiro)
```

**Princípios:**

- **O app nunca fala direto com a IA nem com o banco.** Tudo passa pelo backend, que guarda a chave da empresa e registra cada pergunta.
- **A IA não recebe o banco inteiro.** Ela recebe **ferramentas** (tool use), como `consultar_pedidos`, `consultar_producao`, `consultar_carteira` e `buscar_pedido_do_cliente`. O backend executa cada consulta e devolve só o resultado. É assim que "o pedido do cliente X faturou?" passa a ter resposta.
- **A permissão fica nas ferramentas, não no texto do prompt.** Se o fluxo de caixa completo é só do Sr. Roberto, a ferramenta de caixa devolve o nível de detalhe conforme o usuário logado. A IA não consegue "pular" essa regra.
- **Dois momentos de IA:**
  - **Edição da semana (segunda-feira):** o modelo mais capaz escreve as frases e os destaques. A Controladoria revisa e publica. Com isso o tablet tem tudo **offline** na terça.
  - **Perguntas na reunião:** um modelo rápido, para responder em segundos. Sem internet, a pergunta entra numa fila e é respondida quando a conexão voltar.
- **Cache de prompt:** o contexto da semana (dados e instruções) é o mesmo para todas as perguntas da reunião. Reaproveitá-lo deixa as respostas mais rápidas e mais baratas.

## Formas de contratar o Claude corporativo

Depende de qual nuvem a empresa já usa:

| Caminho | Quando faz sentido |
|---|---|
| **API da Anthropic (conta da organização)** | O caminho mais simples, com recursos novos primeiro. Admin, chaves e limites de gasto num só lugar |
| **AWS** (Claude Platform on AWS ou Amazon Bedrock) | Se a empresa já está na AWS e quer cobrança e governança por lá |
| **Google Cloud** (Vertex AI ou o serviço gerenciado pela Anthropic) | Se a empresa está no Google Cloud |
| **Microsoft Foundry (Azure)** | Se a empresa é Microsoft/Azure (o SSO provavelmente já é Entra ID) |

O código do backend muda pouco entre esses caminhos: o SDK oficial tem um cliente para cada um.

**Retenção de dados:** como passam dados financeiros e de pessoas, é preciso confirmar com o fornecedor a política de retenção do contrato. Existem opções de retenção zero, mas alguns recursos e modelos exigem retenção mínima. Isso deve pesar na escolha do modelo e do caminho.

## Perguntas para a TI

1. Qual nuvem a empresa usa hoje (AWS, Google, Azure)? Já existe contrato com a Anthropic ou com alguma dessas nuvens para IA?
2. Onde ficam os dados do POI: banco do ERP, data warehouse, só nos reports?
3. Qual é o SSO (Entra ID / Azure AD, Google)?
4. Os tablets da diretoria: iPad ou Android? Existe gestão de dispositivos (MDM)?
5. Quais são as regras de segurança para dado financeiro em tablet fora da empresa (criptografia, bloqueio remoto, tempo de sessão)?
6. Fluxo de caixa e RH continuam em Excel. Aceitam um upload semanal padronizado como primeiro passo?
