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

## Regras operacionais

### RN01 — Validação de estoque

Uma venda somente pode ser concluída se houver quantidade suficiente do produto em estoque. O sistema não deve permitir que uma venda gere estoque negativo. 

### RN02 — Condição para venda fiada

Uma venda na modalidade fiado somente pode ser realizada quando o cliente estiver cadastrado, ativo e dentro do limite de crédito ou prazo estabelecido. O prazo de pagamento é ate uma semana, caso não seja pago o estabelecimento não prestara serviço ate o pagamento ser realizado ou um acordo ser feito com o cliente, independente do tempo de atraso do pagamento do fiado não será cobrado taxa ou juros que poderá ser pago por debito/credito, pix e dinheiro.

### RN03 — Fechamento de caixa

O caixa diário somente deve ser encerrado após a conferência e o registro das movimentações realizadas durante o período.

### RN04 — Obrigatoriedade de operador

As movimentações de venda e alterações realizadas no sistema devem estar vinculadas ao usuário responsável, permitindo a identificação das operações.

## Restrições organizacionais

### RN05 — Proibição de venda de bebidas alcoólicas a menores

A venda de bebidas alcoólicas a menores de idade é proibida. O processo de venda deve observar essa restrição legal e realizar a conferência de identidade quando necessário.

### RN06 — Política de crédito

A organização estabelece limites para compras fiadas. Quando o cliente ultrapassar o limite definido, novas compras a prazo devem ser bloqueadas até que ocorra a quitação parcial ou total do débito, conforme a política estabelecida.

### RN07 — Acesso restrito a funções gerenciais

Funções críticas, como alterações manuais de preços, exclusão de registros e liberação de crédito especial, devem ser restritas aos usuários com perfil de gerente.

### RN08 - Controle de estoque 

Parte essencial que analisa com um sistema interno quantos produtos foram vendidos e o reabastecimento sempre é feito por distribuidoras diversas como o atacadão. 

---

# 5. Dicionario de Dados Conceitual

### Entidade: CLIENTE

| Atributo | Tipo | Descrição |
|---|---|---|
| id_cliente | INT | Identificador único do cliente. |
| nome | VARCHAR(100) | Nome completo do cliente. |
| numero | VARCHAR(10) | Número do endereço. |
| complemento | VARCHAR(60) | Complemento do endereço. |
| cep | CHAR(8) | Chave estrangeira relacionada à entidade CEP. |

### Entidade: CEP

| Atributo | Tipo | Descrição |
|---|---|---|
| cep | CHAR(8) | Identificador do CEP. |
| logradouro | VARCHAR(120) | Rua ou avenida. |
| bairro | VARCHAR(60) | Bairro do endereço. |
| cidade | VARCHAR(60) | Cidade. |
| uf | CHAR(2) | Unidade federativa. |

### Entidade: USUARIO

| Atributo | Tipo | Descrição |
|---|---|---|
| id_usuario | INT | Identificador do usuário. |
| nome | VARCHAR(100) | Nome do usuário. |
| login | VARCHAR(50) | Identificação de acesso. |
| senha_hash | VARCHAR(255) | Senha armazenada em formato de hash. |
| nivel_acesso | VARCHAR(20) | Nível de permissão do usuário. |

### Entidade: PRODUTO

| Atributo | Tipo | Descrição |
|---|---|---|
| id_produto | INT | Identificador do produto. |
| nome | VARCHAR(120) | Nome do produto. |
| preco | DECIMAL(10,2) | Preço de venda. |
| preco_atacado | DECIMAL(10,2) | Preço de atacado. |
| qtd_minima_atacado | INT | Quantidade mínima para atacado. |
| quantidade_estoque | INT | Quantidade disponível. |
| estoque_minimo | INT | Limite mínimo de estoque.
---

# 6. Modelagem Conceitual (Entidades, Atributos, Relacionamentos)

USUARIO

CAIXA

CEP

CLIENTE

TELEFONE_CLIENTE

VENDA

ITEM_VENDA

PAGAMENTO

CUPOM_FISCAL

PRODUTO

FORNECEDOR

NF_ENTRADA

ITEM_NOTA

CONTAS_A_PAGAR

## Atributos e classificações

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

![Diagrama Entidade-Relacionamento](der/DER-Adega-Online.png)

O arquivo do DER deve ser mantido separadamente no repositório, conforme solicitado pela atividade.

---

# 8. Justificativa Técnica

A modelagem foi construída a partir dos processos observados na Adega Online e dos requisitos levantados para o sistema.

A entidade **PRODUTO** foi definida porque o estabelecimento precisa identificar e controlar as mercadorias comercializadas. O relacionamento com **ESTOQUE** permite representar a quantidade disponível de cada produto.

A entidade **VENDA** foi utilizada para centralizar as informações de cada operação comercial, como data, total e forma de pagamento. Como uma venda pode envolver diferentes produtos, o relacionamento **itens_venda_rei** registra a quantidade e o preço unitário de cada item.

A entidade **CLIENTE** foi incluída devido à existência do processo de compras a prazo. O relacionamento de fiado permite associar as vendas aos clientes correspondentes.

A entidade **USUARIO** representa os operadores responsáveis pelas movimentações e permite considerar o controle de acesso previsto nos requisitos não funcionais e nas regras de negócio.

As cardinalidades do DER foram definidas de acordo com a forma como os processos foram representados no modelo conceitual atual, buscando permitir a identificação dos participantes de cada operação e a composição das vendas por produtos.

O modelo também foi estruturado de maneira que possa servir como base para as próximas etapas do projeto, nas quais poderão ser detalhadas as estruturas físicas do banco de dados e as funcionalidades do sistema.

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
│   ├── DER-Adega-Online.png
│   └── DER-Adega-Online.pdf
│
├── documentos/
│   ├── modelo_logico_corrigido_v2.pdf
│   ├── dicionario_de_dados.md
│   ├── regras_de_negocio.md
│   └── alteracoes_modelagem.md
│
└── evidencias/
    ├── adega-online.jpg
    └── pesquisa-campo.jpg
```

---

## Considerações finais

O projeto **Adega Online** busca representar, por meio da modelagem conceitual, os principais dados e processos envolvidos na operação real do estabelecimento.

A proposta concentra-se na integração entre **vendas, produtos, estoque, clientes e usuários**, criando uma base estruturada para as próximas etapas de desenvolvimento do sistema e implementação do banco de dados.
