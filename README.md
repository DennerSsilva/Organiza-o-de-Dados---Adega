# Adega Online — Gestão de Vendas e Estoque

Sistema de automação comercial e gestão de dados desenvolvido para apoiar as operações de uma organização real que atua nos segmentos de adega e tabacaria.

O projeto tem como foco centralizar o cadastro de produtos, o controle de estoque, o registro de vendas, o gerenciamento de clientes que realizam compras a prazo ("fiado") e o acompanhamento das operações realizadas pelos usuários do sistema.

---

## Metadados

### Integrantes

| Nome | RGM |
|---|---:|
| Denner | 4733816 |
| Guilherme Schiavinato | 47769068 |
| Gustavo Castro | 47353716 |
| Juan Craveiro | 45005273 |
| Victor Silva | 47787945 |

---

# 1. Caracterização da Organização

## Nome e natureza da organização

A organização escolhida para o desenvolvimento do projeto é a **Adega Online**, um estabelecimento comercial privado e com fins lucrativos que atua conjuntamente nos segmentos de **adega e tabacaria**.

O grupo possui acesso direto à organização para realização da pesquisa de campo, pois um dos integrantes da equipe é colaborador do local. Essa condição possibilitou observar a operação e levantar informações relacionadas aos processos reais do estabelecimento.

## Contexto e porte

A operação possui uma equipe enxuta de aproximadamente **4 colaboradores**. Apesar do número reduzido de funcionários, o estabelecimento apresenta alta rotatividade operacional, com volume de vendas e movimentação contínua de mercadorias.

Também existe a gestão de contas de crédito interno, popularmente chamadas de **"fiado"**, utilizadas por clientes recorrentes.

## Problemas e necessidades identificados

Durante o levantamento foram identificados problemas relacionados principalmente à falta de centralização e automatização dos processos:

- **Desorganização do estoque:** dificuldade de manter um controle rigoroso sobre entradas e saídas de mercadorias.
- **Vendas fragmentadas:** ausência de integração adequada entre vendas e controle financeiro.
- **Gestão de fiados:** controle descentralizado de clientes devedores e valores em aberto.
- **Desalinhamento operacional:** dificuldade de acompanhar se os procedimentos de registro e controle estão sendo seguidos corretamente.
- **Risco de perdas e divergências:** maior possibilidade de erros humanos, esquecimentos e divergências no controle financeiro e de mercadorias.

## Justificativa da escolha

A Adega Online foi escolhida por dois motivos principais.

Primeiramente, existe acesso direto à organização por meio de um integrante do grupo que trabalha no local, facilitando a pesquisa de campo e o levantamento dos requisitos.

Além disso, a organização apresenta processos suficientemente diversificados para a aplicação dos conceitos de modelagem de dados, envolvendo produtos, estoque, vendas, clientes, crédito interno e usuários.

## Evidências da organização

**Nome fantasia:** Adega Online  
**Endereço:** Rua Dona Eloá do Vale Quadros, nº 17  
**Telefone:** (11) 98501-3455

O grupo realizou levantamento de campo e possui registros fotográficos da organização.

### Registro da organização

![Evidência da organização](evidencias/adega-online.jpg)

### Registro relacionado à pesquisa de campo

![Pesquisa de campo](evidencias/pesquisa-campo.jpg)

> **Observação:** as imagens acima devem ser colocadas no repositório nas pastas indicadas, utilizando os nomes de arquivo correspondentes.

---

# 2. Processos de Negócio

A operação da Adega Online está estruturada em torno de rotinas comerciais essenciais para o atendimento, controle financeiro e gerenciamento das mercadorias.

## Principais processos mapeados

### Cadastro de Produtos

Registro dos itens comercializados, incluindo informações como descrição, preço e dados necessários para o controle dos produtos.

### Controle de Estoque

Monitoramento da quantidade de produtos disponíveis nas prateleiras e no depósito, permitindo acompanhar as saídas e auxiliar na reposição.

### Cadastro de Clientes — Fiado

Gerenciamento dos clientes autorizados a realizar compras a prazo, mantendo informações relacionadas aos débitos e ao histórico de consumo.

### Realização de Vendas

Registro dos produtos solicitados pelo cliente, processamento do pagamento — incluindo a modalidade de fiado — e finalização do atendimento.

### Abertura e Fechamento de Caixa

Rotina de controle dos valores movimentados durante o período de operação, incluindo abertura do caixa, entradas e conferência do valor final.

## Fluxo operacional atual

O levantamento realizado identificou um fluxo de venda composto, de forma geral, pelas seguintes etapas:

1. **Atendimento:** o cliente chega ao estabelecimento e é atendido pelo funcionário.
2. **Operação e registro:** o funcionário realiza a venda e processa o pagamento ou registra a modalidade de fiado.
3. **Armazenamento:** os dados da operação são registrados.
4. **Gestão e monitoramento:** posteriormente, o responsável pode consultar os dados para conferência e acompanhamento da operação.

A proposta do sistema é reduzir a dependência de processos manuais e integrar as informações de vendas, estoque e crédito.

---

# 3. Requisitos do Sistema

## 3.1 Requisitos Funcionais

| Código | Requisito |
|---|---|
| **RF01** | O sistema deve permitir o cadastro, alteração, exclusão e consulta de produtos, incluindo descrição, preço de custo, preço de venda e quantidade em estoque. |
| **RF02** | O sistema deve atualizar automaticamente a quantidade de itens no estoque a cada venda realizada ou produto cadastrado. |
| **RF03** | O sistema deve permitir o registro e a consulta de clientes autorizados a realizar compras a prazo, mantendo histórico de débitos e pagamentos. |
| **RF04** | O sistema deve permitir o registro de vendas, calculando o valor total, aplicando formas de pagamento à vista ou fiado e registrando o operador responsável. |
| **RF05** | O sistema deve permitir registrar a abertura do caixa com o troco inicial, as entradas do dia e o fechamento com o balanço financeiro. |

## 3.2 Requisitos Não Funcionais

| Código | Requisito |
|---|---|
| **RNF01 — Usabilidade** | A interface deve ser intuitiva e de fácil aprendizado, permitindo que novos funcionários operem o software rapidamente. |
| **RNF02 — Desempenho e leveza** | O software deve exigir poucos recursos de hardware para funcionar de maneira adequada em computadores simples ou antigos. |
| **RNF03 — Disponibilidade / Operação offline** | O sistema deve funcionar sem dependência constante de conexão com a internet, permitindo a continuidade das vendas e do controle de caixa em caso de queda da rede. |
| **RNF04 — Segurança e privacidade** | Os dados dos clientes e do caixa devem ser protegidos, com acesso restrito a usuários autorizados por meio de senhas. |

---

# 4. Regras de Negócio

### Regras de negócio — versão atualizada

- **RN01 — Controle de pagamentos:** Todo pagamento registrado deve estar associado a um caixa.
- **RN02 — Identificação do cliente:** Toda venda deve possuir um cliente cadastrado e associado.
- **RN03 — Telefones do cliente:** Cada cliente deve possuir pelo menos um telefone cadastrado.
- **RN04 — Conferência de pagamentos:** Quando uma venda possuir mais de um pagamento, a soma dos valores pagos deve corresponder ao total da venda.
- **RN05 — Segurança de acesso:** As senhas dos usuários devem ser armazenadas por meio de hash, e cada usuário deve possuir login e nível de acesso.
- **RN06 — Integridade dos dados:** Os dados derivados devem ser calculados ou controlados pelo sistema, evitando inconsistências entre informações armazenadas.
- **RN07 — Troco:** O troco deve ser calculado somente para pagamentos em dinheiro.
- **RN08 — Venda por atacado:** O preço de atacado deve ser aplicado quando a quantidade de produtos atingir a quantidade mínima definida para essa modalidade.
- **RN09 — Controle de estoque:** O estoque deve ser atualizado automaticamente após vendas e entradas de mercadorias.
- **RN10 — Totalização:** O valor total da venda deve corresponder à soma dos itens vendidos, considerando suas quantidades e preços unitários.
- **RN11 — Controle de caixa:** O sistema deve controlar a abertura e o fechamento dos caixas, impedindo situações incompatíveis com as regras de funcionamento.
- **RN12 — Padronização de endereços:** Os dados de endereço devem utilizar o CEP como referência para evitar a repetição de informações de logradouro, bairro, cidade e estado.
- **RN13 — Cupom fiscal:** Cada venda poderá possuir, no máximo, um cupom fiscal associado.

---

# 5. Dicionário de dados

O dicionário de dados apresenta as entidades, seus atributos e suas respectivas funções no sistema Adega Online — Gestão de Vendas e Estoque.

| Entidade | Principais atributos | Descrição |
|---|---|---|
| USUARIO | id_usuario, nome, login, senha_hash, nivel_acesso | Armazena os dados dos usuários que acessam o sistema. |
| CAIXA | id_caixa, numero_caixa, data_hora_abertura, data_hora_fechamento, valor_inicial, valor_final, id_usuario | Registra a abertura, o funcionamento e o fechamento dos caixas. |
| CEP | cep, logradouro, bairro, cidade, uf | Armazena os dados de endereço vinculados ao CEP. |
| CLIENTE | id_cliente, nome, numero, complemento, cep | Armazena os dados cadastrais dos clientes. |
| TELEFONE_CLIENTE | id_telefone, id_cliente, telefone | Armazena os telefones associados aos clientes. |
| VENDA | id_venda, data_hora, total, id_caixa, id_cliente | Registra as vendas realizadas no sistema. |
| ITEM_VENDA | id_item_venda, id_venda, id_produto, quantidade, preco_unitario | Registra os produtos e quantidades que compõem cada venda. |
| PAGAMENTO | id_pagamento, id_caixa, forma_pagamento, data_pagamento, valor_pago, troco | Registra os pagamentos recebidos pelo caixa. |
| CUPOM_FISCAL | id_cupom, id_venda, numero_cupom, chave_acesso | Armazena os dados do cupom fiscal associado à venda. |
| PRODUTO | id_produto, nome, preco, preco_atacado, qtd_minima_atacado, quantidade_estoque, estoque_minimo | Armazena os dados dos produtos e seu controle de estoque. |
| FORNECEDOR | atributos definidos no modelo lógico | Armazena os dados dos fornecedores da adega. |
| NF_ENTRADA | atributos definidos no modelo lógico, incluindo id_fornecedor | Registra notas fiscais de entrada de mercadorias. |
| ITEM_NOTA | atributos definidos no modelo lógico, incluindo id_nota e id_produto | Registra os produtos e quantidades presentes em cada nota de entrada. |
| CONTAS_A_PAGAR | atributos definidos no modelo lógico, incluindo referência à nota de entrada | Controla os valores a pagar aos fornecedores. |

---

# 6. Modelagem Conceitual (Entidades, Atributos, Relacionamentos)

### 6. Entidades do modelo lógico

O modelo lógico do sistema Adega Online é composto pelas seguintes entidades:

1. **USUARIO:** controla os usuários e seus níveis de acesso.
2. **CAIXA:** registra os caixas e suas operações de abertura e fechamento.
3. **CEP:** centraliza os dados de endereço.
4. **CLIENTE:** armazena os dados cadastrais dos clientes.
5. **TELEFONE_CLIENTE:** permite registrar os telefones dos clientes.
6. **VENDA:** registra as vendas realizadas.
7. **ITEM_VENDA:** relaciona os produtos e suas quantidades em cada venda.
8. **PAGAMENTO:** registra os pagamentos recebidos pelo caixa.
9. **CUPOM_FISCAL:** armazena os dados fiscais associados às vendas.
10. **PRODUTO:** mantém o cadastro dos produtos e suas informações de estoque e preço.
11. **FORNECEDOR:** registra os fornecedores.
12. **NF_ENTRADA:** registra as notas fiscais de entrada.
13. **ITEM_NOTA:** relaciona os produtos às respectivas notas fiscais de entrada.
14. **CONTAS_A_PAGAR:** controla os compromissos financeiros da adega com seus fornecedores.

O modelo contempla as operações de venda, recebimento, controle de estoque, entrada de mercadorias e obrigações financeiras com fornecedores.
Cada entidade possui atributos responsáveis por identificar e descrever os elementos armazenados no modelo. Os identificadores são utilizados para distinguir cada registro, enquanto os demais atributos representam as informações necessárias para os processos da organização.

## Relacionamentos

O modelo conceitual atual representa os seguintes relacionamentos principais:

- **CLIENTE — Fiado_na_venda — VENDA:** relaciona o cliente às vendas realizadas na modalidade de crédito.
- **USUARIO — realiza_e_fiado — VENDA:** relaciona o usuário responsável à operação de venda.
- **PRODUTO — possui — ESTOQUE:** relaciona produtos às respectivas quantidades controladas.
- **PRODUTO / VENDA — itens_venda_rei:** representa a composição das vendas por produtos, registrando quantidade e preço unitário.
- **CAIXA — possui — VENDA:** representa o controle de vendas do dia/semana/mês da loja, controle da meta estipulada e também horário de abertura e fechamento de caixa.

## Restrições e políticas aplicadas ao modelo

O modelo considera as regras de estoque, crédito, identificação do operador e controle de acesso descritas na Seção 4.

---

# 7. Diagrama Entidade-Relacionamento (DER)

O DER representa graficamente as entidades, atributos, relacionamentos e cardinalidades identificados durante o levantamento.

Relacionamento	            Cardinalidade
USUARIO — CAIXA	              0:N — 1:1
CAIXA — PAGAMENTO	          0:N — 1:1
CAIXA — VENDA	              0:N — 1:1
CEP — CLIENTE	              0:N — 1:1
CLIENTE — TELEFONE_CLIENTE	  1:N — 1:1
CLIENTE — VENDA               0:N — 1:1
VENDA — CUPOM_FISCAL	      0:1 — 1:1
VENDA — PRODUTO	              1:N — 0:N
FORNECEDOR — NF_ENTRADA	      0:N — 1:1
NF_ENTRADA — PRODUTO	      1:N — 0:N
NF_ENTRADA — CONTAS_A_PAGAR	  0:N — 1:1

O arquivo do DER deve ser mantido separadamente no repositório, conforme solicitado pela atividade.

---

# 8. Justificativa Técnica

A modelagem lógica do sistema Adega Online foi estruturada para organizar os dados relacionados às vendas, aos clientes, aos produtos, aos caixas e ao controle financeiro da adega.

A separação das informações em entidades específicas contribui para a organização, a integridade e a manutenção do banco de dados.

A entidade CEP foi utilizada para centralizar os dados de endereço, evitando a repetição de informações em diferentes registros de clientes. A entidade TELEFONE_CLIENTE foi criada para permitir que um cliente possua mais de um telefone cadastrado.

A entidade ITEM_VENDA representa o relacionamento entre vendas e produtos, permitindo registrar a quantidade e o preço unitário de cada produto vendido. De forma semelhante, ITEM_NOTA relaciona os produtos às notas fiscais de entrada.

A entidade PAGAMENTO foi separada de VENDA para registrar as movimentações financeiras recebidas pelo caixa, contemplando dinheiro, cartão de débito, cartão de crédito e PIX.

O controle de estoque foi integrado à entidade PRODUTO, que armazena a quantidade disponível e o estoque mínimo. Também foram incluídas as entidades FORNECEDOR, NF_ENTRADA e CONTAS_A_PAGAR para representar o processo de aquisição de mercadorias e os compromissos financeiros da adega com seus fornecedores.

A modelagem utiliza chaves primárias e estrangeiras para estabelecer os relacionamentos entre as entidades e manter a integridade referencial. A organização dos dados busca reduzir redundâncias e facilitar futuras consultas, atualizações e operações do sistema.

O modelo foi elaborado considerando o MySQL 8.0.16 ou superior, especialmente para utilização de restrições de integridade, como as cláusulas CHECK.
---

# 9. Uso de Inteligência Artificial

Foi utilizada a ferramenta **ChatGPT** durante a elaboração e organização da documentação do projeto.

| Item | Registro |
|---|---|
| **Ferramenta e etapa** | ChatGPT — organização e redação do README.md e estruturação das informações fornecidas pelo grupo. |
| **Motivação** | Auxiliar na organização das informações do levantamento, na adequação do conteúdo à estrutura solicitada pela atividade e na revisão da documentação. |
| **Prompt(s) utilizados** | Solicitação para analisar o esqueleto de entrega fornecido pela faculdade e os arquivos do projeto, organizando o conteúdo em um README.md compatível com os requisitos da atividade. |
| **Resposta recebida** | Estruturação do README com as seções de caracterização da organização, processos de negócio, requisitos, regras de negócio, dicionário conceitual, modelagem, DER, justificativa técnica e uso de IA. |
| **Fontes consultadas e verificadas** | Informações e documentos fornecidos pelo próprio grupo, incluindo requisitos, processos de negócio, perguntas do levantamento, metadados da organização e DER. |
| **Trechos rejeitados ou corrigidos** | Informações não presentes nos materiais fornecidos não foram tratadas como fatos observados. O conteúdo foi mantido alinhado ao material do grupo. |
| **Justificativa da escolha final** | A versão final foi organizada para atender à estrutura exigida no esqueleto da atividade, mantendo os dados e processos fornecidos pelo grupo. |
| **Reflexão crítica** | A IA foi utilizada como apoio à organização e documentação. As informações referentes à organização devem ser conferidas pelo grupo com base na pesquisa de campo, pois a IA não substitui a observação da organização nem a validação dos requisitos pelos integrantes. |

---

# Arquivos do projeto

Sugestão de organização do repositório:

```text
Organiza-o-de-Dados---Adega/
│
├── README.md
│
├── der/
│   └── der_atualizado.png
│
├── evidencias/
│   └── ...
│
└── documentos/
    ├── modelo_logico_corrigido_v2.pdf
    ├── dicionario_de_dados.md
    ├── regras_de_negocio.md
    └── alteracoes_modelagem.md
```

---

## Considerações finais

O projeto **Adega Online** busca representar, por meio da modelagem conceitual, os principais dados e processos envolvidos na operação real do estabelecimento.

A proposta concentra-se na integração entre **vendas, produtos, estoque, clientes e usuários**, criando uma base estruturada para as próximas etapas de desenvolvimento do sistema e implementação do banco de dados.
