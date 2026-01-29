# 🔍 Azure Cognitive Search: Mineração de Conhecimento

[![Azure](https://img.shields.io/badge/Azure-0089D6?style=for-the-badge&logo=microsoft-azure&logoColor=white)](https://azure.microsoft.com/)
[![Cognitive Search](https://img.shields.io/badge/Cognitive%20Search-0058AD?style=for-the-badge&logo=microsoft&logoColor=white)]()

Este projeto foca na configuração de uma solução de **Busca Inteligente (AI Search)** utilizando o Azure. O objetivo é extrair insights de dados não estruturados e criar um índice de pesquisa eficiente, simulando uma base de conhecimento para suporte ao cliente ou análise de dados corporativos.

Vamos imaginar que você trabalha para a Fourth Coffee, uma rede nacional de cafés. Você foi solicitado a ajudar a criar uma solução de mineração de conhecimento que facilite a busca de insights sobre as experiências dos clientes. Você decide criar um índice do Azure AI Search usando dados extraídos de avaliações de clientes.

Neste laboratório você irá:

- Criar recursos do Azure
- Extrair dados de uma fonte de dados
- Enriqueçer os dados com habilidades de IA
- Utilizar o indexador do Azure no portal do Azure
- Consultar seu índice de pesquisa
- Revisar os resultados salvos em uma Loja de conhecimento

[Documentação](https://microsoftlearning.github.io/mslearn-ai-fundamentals/Instructions/Labs/11-ai-search.html)

## Crie um recurso do Azure Al Search

Primeiramente você deve acessar o seu Portal Azure, através do [Portal Azure](https://portal.azure.com/learn.docs.microsoft.com?azure-portal=true).

![Criar um Recurso](https://github.com/cezarscarvalho/DIO-Projeto-Microsoft-Speech/assets/158849910/0c9f2c5d-aeaa-44f8-bfb6-3dbb594bce46)

![GIF criando Recursos](https://github.com/cezarscarvalho/DIO-Projeto-Microsoft-Cognitive/assets/158849910/ca7b0b37-4ea0-4191-8b03-31555c3cc476)





...

- Associe sua Assinatura do Azure;
- Associe a um Grupo de recursos (resource group) ou crie um;
- Defina uma Região;
- Crie um nome:
- Defina Pricing tier (Nível de preço) como Padrão SO;


# 💡
 Não esqueça de selecionar a caixa By checking this box (Li e compreendi)
 - Clicar em Review + create (Revise + crie)


![Criando um Machine Learning](https://github.com/cezarscarvalho/DIO-Projeto-Microsoft-Speech/assets/158849910/5d6ba3ac-edb9-4c06-bcad-16d10b6aee3d)

...

- Clicar em Create (Criar)

![Criar](https://github.com/cezarscarvalho/DIO-Projeto-Microsoft-Speech/assets/158849910/b6a61abf-433f-4138-bc00-74c433a5233a)

- Indicação de Recurso Criado

![Recurso Criado](https://github.com/cezarscarvalho/DIO-Projeto-Microsoft-Speech/assets/158849910/33ed6feb-fe44-4bf6-bb62-ec8083fd30df)

## Crie uma conta de armazenamento

- Retorne a página inicial do Azure.
- Clique em + Create a resource (+ Criar um Recurso).
- Localize Storage account (Conta de armazenamento).
- Clique em + Create (+ Criar).

![Criando Conta de Armazenamento](https://github.com/cezarscarvalho/DIO-Projeto-Microsoft-Cognitive/assets/158849910/dd6659e1-17fd-4599-9645-fca6e81da963)

#  💡

Lembre-se de selecionar a opção Standard

![Standard](https://github.com/cezarscarvalho/DIO-Projeto-Microsoft-Cognitive/assets/158849910/b4662c2e-57f0-4cb5-9086-8e395f1338f8)

Selecione a opção (LRS)

![LRS](https://github.com/cezarscarvalho/DIO-Projeto-Microsoft-Cognitive/assets/158849910/a0db7a1a-931f-463e-93aa-46c13a3977e1)

- Clique em Review + create (Revisão + criação)
- clique em Create (Criar)

![Criação Final Storage](https://github.com/cezarscarvalho/DIO-Projeto-Microsoft-Cognitive/assets/158849910/cf7d59b6-15bd-4796-bea9-3efdef079b73)

# 📒 Precisamos permitir o acesso anônimo ao blob, já que este laboratório trata-se apenas de um estudo aos princípios da Inteligência Artificial

No Storage account criado, selecionar Settings (Configurações) ➡️ Configuration (Configuração). Na seção Allow Blob anonymous access (Permitir acesso anônimo do Blob), marcaremos Enabled (Habilitado). Save (Salvar).

![Configuração Blob](https://github.com/cezarscarvalho/DIO-Projeto-Microsoft-Cognitive/assets/158849910/3e5cbfe7-22be-40d7-a996-c3b496e8b948)

## Criando um Container

Em Data storage (Armazenamento de dados), clique em Containers.
Nele serão inseridos as avaliações dos clientes da cafeteria, onde através das ferramentas da IA iremos otimizar avaliações de sentimentos com a opnião dos clientes.

![Criação de Container](https://github.com/cezarscarvalho/DIO-Projeto-Microsoft-Cognitive/assets/158849910/1e194603-1ea1-4fe2-a163-ca16ac158720)

Preencheremos:
- Name : coffeereviews
- Anonymous access level : Container

![Nome do Container](https://github.com/cezarscarvalho/DIO-Projeto-Microsoft-Cognitive/assets/158849910/16417bd0-cd5e-4949-98b3-706567d6e19a)

Clicar em Create (Criar), observe sua criação

![Coffeereviews criado](https://github.com/cezarscarvalho/DIO-Projeto-Microsoft-Cognitive/assets/158849910/5ac4afc7-49e9-47a9-b168-95e43da41904)

Selecionar o Container criado e selecione Upload para carregar o arquivo .zip de avaliações exemplo que constam na documentação deste Laboratório.

![Upload de Arquivos](https://github.com/cezarscarvalho/DIO-Projeto-Microsoft-Cognitive/assets/158849910/fd4349a2-1aaf-4786-94ee-e4eff3e77b2b)

![Upload coffeereviews](https://github.com/cezarscarvalho/DIO-Projeto-Microsoft-Cognitive/assets/158849910/ed5b62d3-93e6-45be-8ad1-bbed9665d388)

## Importação e indexação de dados para o IA Search

Neste ponto indexaremos os dados fornecidos e assim criaremos um índice de pesquisa.
No Portal Azure localize o Al search 

No meu caso, após clicar em Al search tive que criar um serviço para sim poder seguir para a importação dos dados

![Importar dados](https://github.com/cezarscarvalho/DIO-Projeto-Microsoft-Cognitive/assets/158849910/70083726-b226-4cef-b8c6-cc7ea8e887e6)

Em Connect to your data (Conectar-se aos seus dados), na lista Data Source (Fonte de dados), selecionar Azure Blob Storage e preencha os detalhes do armazenamento de dados com os seguintes dados:

![Conectar Dados](https://github.com/cezarscarvalho/DIO-Projeto-Microsoft-Cognitive/assets/158849910/fbfba3dc-f2b7-4738-a21a-63f6907b971b)

![Preenchimento de dados](https://github.com/cezarscarvalho/DIO-Projeto-Microsoft-Cognitive/assets/158849910/b859c6c9-79d3-479c-a972-ea630c41fe04)

clique em Next: Add cognitive skills (Optional) (Próximo: Adicionar habilidades cognitivas (opcional))

![Próximo Habilidades Cognitivas](https://github.com/cezarscarvalho/DIO-Projeto-Microsoft-Cognitive/assets/158849910/a3fdfc62-5d47-4ae3-9f19-3dd01f639435)

Adicionar Enriquecimentos - Add enrichments

![Adicionar Enriquecimentos](https://github.com/cezarscarvalho/DIO-Projeto-Microsoft-Cognitive/assets/158849910/888d4942-3d7d-41eb-92a2-73fc89b034a3)

![Adicionar Enriquecimentos 2](https://github.com/cezarscarvalho/DIO-Projeto-Microsoft-Cognitive/assets/158849910/ae45f2e6-319c-4a96-b910-9a4baf2a06d9)

![Adicionar Enriquecimentos 3](https://github.com/cezarscarvalho/DIO-Projeto-Microsoft-Cognitive/assets/158849910/913578d6-1dfa-44ee-85de-00959e337aa2)

Em Save enrichments to a knowledge store (Salvar enriquecimentos em um armazenamento de conhecimento) preencher seguindo o modelo abaixo:

![Conhecimento de Enriquecimento ](https://github.com/cezarscarvalho/DIO-Projeto-Microsoft-Cognitive/assets/158849910/80cbcdd3-4352-4d16-9fea-2ba569f9219d)

Personalize o Customize target index (índice de destino)

![indice de destino](https://github.com/cezarscarvalho/DIO-Projeto-Microsoft-Cognitive/assets/158849910/432bb66d-3e37-46bb-b19d-9b78e920fde7)

Revise as Configurações e selecione FILTERABLE (FILTRÁVEL) para todos os campos que já estão selecionados por padrão.

![Dados filtrados](https://github.com/cezarscarvalho/DIO-Projeto-Microsoft-Cognitive/assets/158849910/9ac3be0e-646c-43ba-9225-95e53a9273f7)


## Crie um indexador (Create an indexer)

Expanda as opções avançadas

![Opções Avançadas](https://github.com/cezarscarvalho/DIO-Projeto-Microsoft-Cognitive/assets/158849910/a9c2655e-5bc9-4bff-94b8-f85aafb64339)

![Opção Avançadas Indexador](https://github.com/cezarscarvalho/DIO-Projeto-Microsoft-Cognitive/assets/158849910/acf0b235-7082-4765-a63a-e4a3376d58a4)

## Consultando o Índice

Clique em Search explorer (Explorador de pesquisa)

![Consulta de indice](https://github.com/cezarscarvalho/DIO-Projeto-Microsoft-Cognitive/assets/158849910/a2d044d8-908a-4290-8f4b-469276da1d20)

Clique em View - Json

![indice json](https://github.com/cezarscarvalho/DIO-Projeto-Microsoft-Cognitive/assets/158849910/6418affa-8fed-4ffd-9fe0-c996355ddb83)

![Resultado json](https://github.com/cezarscarvalho/DIO-Projeto-Microsoft-Cognitive/assets/158849910/0588cd42-cac3-438e-858d-bb88a016a9fd)


## As ferramentas de IA facilitam a consulta de documentos, depoimentos otimizando as consultas nas Empresas.

## 📚 Outros Projetos de IA e Cloud (Microsoft Azure)

Este repositório faz parte da minha trilha de especialização em Inteligência Artificial. Confira outros projetos realizados:

* [**IA Generativa e Copilot**](https://github.com/cezarscarvalho/DIO-Projeto-Microsoft-IA-Generativa) - Exploração de modelos de linguagem e prompts.
* [**Azure Speech**](https://github.com/cezarscarvalho/DIO-Projeto-Microsoft-Speech) - Reconhecimento de fala e conversão de texto.
* [**Azure Vision**](https://github.com/cezarscarvalho/DIO-Projeto-Azure-Microsoft-Vision) - Análise de imagens e OCR.
* [**Azure Machine Learning**](https://github.com/cezarscarvalho/DIO-Projeto-Azure-Microsoft-Machine-Learning) - Modelagem de dados preditivos.
---

# 🤝 Contribuição em Projetos Open Source

[![Git](https://img.shields.io/badge/GIT-E44C30?style=for-the-badge&logo=git&logoColor=white)](https://git-scm.com/)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/)

Repositório focado no aprendizado do fluxo de trabalho colaborativo (Git Flow). Aqui documento o processo de **Fork, Clone, Pull Request e Code Review**, competências essenciais para qualquer profissional que atue em times de tecnologia modernos e ágeis.

* [**Contribuição Open Source**](https://github.com/cezarscarvalho/dio-lab-open-source)


## ✉️ Contato

[![Gmail](https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:cezar.souza03@gmail.com)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/cezar-de-souza-carvalho-ti/)
[![WhatsApp](https://img.shields.io/badge/WhatsApp-25D366?style=for-the-badge&logo=whatsapp&logoColor=white)](https://wa.me/5511988541006)








