

# **Plano de Desenvolvimento de Aplicação: Disruption Club**

## **Introdução: Engenharia da Disrupção \- Um Novo Modelo para a Genialidade Colaborativa**

**Application Development Plan: Disruption Club**

**Introduction: Engineering Disruption \- A New Model for Collaborative Genius**

This document outlines the technical development plan for the "Disruption Club" application. The project represents a direct application of Clayton Christensen's theory of disruptive innovation.1 The Disruption Club is not an incremental improvement on existing collaboration tools; it is a "new market disruption" 4 that creates an unprecedented value network for a select group of high-impact individuals. Its success will not be measured by mass adoption, but by the quality and disruptive potential of the ideas it fosters. The application itself is a process, not merely a product, designed to execute the "job to be done" 1 of structured, high-consequence ideation.

The application's design is rooted in the psychology of creativity. It provides a mechanism to "capture new ideas" 5, "amplify knowledge" through expert collaboration, and engage in a form of asynchronous group "brainwriting" 5 through the shared idea map. The club's exclusivity directly addresses the principle of surrounding oneself with "interesting people" to stimulate innovative thinking.5

The architecture rests on four fundamental pillars:

1. **Decentralized Identity and Verifiable Membership:** Utilization of ERC-721 NFTs 7 and smart contracts for a transparent governance layer and member ownership.  
2. **AI-Native Experience:** Leveraging a powerful LLM (Gemini) not as a feature, but as the central engine for knowledge synthesis, orchestrated via the Model Context Protocol (MCP).8  
3. **Offline-First Resilience:** Ensuring the application is a persistent and reliable thinking tool, independent of constant connectivity, by using a robust local database and a state management strategy.10  
4. **Zero Trust Security and Privacy:** Implementing a defense-in-depth security posture for highly sensitive data, from infrastructure to application logic, recognizing the necessary compromises between end-to-end encryption (E2EE) and AI processing.

**Section 1: Core Architecture and Technology Stack**

This section describes the high-level system architecture and provides clear justification for each technology choice, forming the bedrock of the development plan. The selection of each component is not merely based on popularity, but on how it specifically addresses a core project requirement. For instance, the choice of WatermelonDB over AsyncStorage is not just about performance; it's a strategic decision to support the complex, relational nature of the "idea map" in an offline-first context.12 Similarly, the choice of the Apple Developer Enterprise Program is not a simple implementation decision; it's a fundamental business dependency that dictates project viability.15 The stack is, therefore, a mosaic where each piece is chosen for its unique contribution to the overall vision.

**High-Level System Diagram**

A visual diagram would depict the following interconnected components:

* **React Native Client:** The mobile application, containing the UI, local database (WatermelonDB), and connectivity management logic.  
* **Backend Services (Node.js on AWS):** A suite of microservices handling API requests, blockchain interactions, and AI orchestration.  
* **AI Core:** The Gemini LLM, RAG pipeline, and real-time STT service.  
* **Blockchain (Polygon):** The public ledger hosting the Membership NFT and Invitation smart contracts.  
* **Vector Database (Pinecone):** The specialized database storing meeting transcript embeddings for semantic search.  
* **IPFS/Pinata:** Decentralized storage for NFT metadata.

**Table: Technology Stack Justification**

This table serves as a definitive reference for the development team, codifying the "what" and "why" of our core technologies. It prevents architectural drift and ensures all team members understand the rationale behind the tools they are using.

| Domain                     | Selected Technology          | Justification and Supporting Research

Este documento delineia o plano de desenvolvimento técnico para a aplicação "Disruption Club". O projeto representa uma aplicação direta da teoria da inovação disruptiva de Clayton Christensen.1 O Disruption Club não é uma melhoria incremental das ferramentas de colaboração existentes; é uma "disrupção de novo mercado" 4 que cria uma rede de valor inédita para um grupo seleto de indivíduos de alto impacto. O seu sucesso não será medido pela adoção em massa, mas pela qualidade e pelo potencial disruptivo das ideias que fomenta. A aplicação em si é um processo, não apenas um produto, concebida para executar o "trabalho a ser feito" 1 de ideação estruturada e de alta consequência.

O design da aplicação está enraizado na psicologia da criatividade. Fornece um mecanismo para "capturar novas ideias" 5, "ampliar o conhecimento" através da colaboração de especialistas e engajar-se numa forma de "brainwriting" de grupo assíncrono 5 através do mapa de ideias partilhado. A exclusividade do clube aborda diretamente o princípio de se rodear de "pessoas interessantes" para estimular o pensamento inovador.5

A arquitetura assenta em quatro pilares fundamentais:

1. **Identidade Descentralizada e Afiliação Verificável:** Utilização de NFTs ERC-721 7 e contratos inteligentes para uma camada de governação transparente e propriedade dos membros.  
2. **Experiência Nativa de IA:** Aproveitamento de um poderoso LLM (Gemini) não como uma funcionalidade, mas como o motor central para a síntese de conhecimento, orquestrado através do Model Context Protocol (MCP).8  
3. **Resiliência Offline-First:** Garantir que a aplicação é uma ferramenta de pensamento persistente e fiável, independente de conectividade constante, utilizando uma base de dados local robusta e uma estratégia de gestão de estado.10  
4. **Segurança e Privacidade Zero Trust:** Implementação de uma postura de segurança de defesa em profundidade para dados altamente sensíveis, desde a infraestrutura até à lógica da aplicação, reconhecendo os compromissos necessários entre a encriptação de ponta a ponta (E2EE) e o processamento por IA.

## **Secção 1: Arquitetura Fundamental e Stack Tecnológico**

Esta secção descreve a arquitetura de sistema de alto nível e fornece uma justificação clara para cada escolha tecnológica, formando a base do plano de desenvolvimento. A seleção de cada componente não se baseia apenas na popularidade, mas na forma como aborda especificamente um requisito central do projeto. Por exemplo, a escolha do WatermelonDB em detrimento do AsyncStorage não é apenas uma questão de desempenho; é uma decisão estratégica para suportar a natureza complexa e relacional do "mapa de ideias" num contexto offline-first.12 Da mesma forma, a escolha do Apple Developer Enterprise Program não é uma simples decisão de implementação; é uma dependência de negócio fundamental que dita a viabilidade do projeto.15 O stack é, portanto, um mosaico onde cada peça é escolhida pela sua contribuição única para a visão geral.

### **Diagrama de Sistema de Alto Nível**

Um diagrama visual representaria os seguintes componentes interligados:

* **Cliente React Native:** A aplicação móvel, contendo a UI, base de dados local (WatermelonDB) e lógica de gestão de conectividade.  
* **Serviços de Backend (Node.js em AWS):** Um conjunto de microsserviços que lidam com pedidos de API, interações com a blockchain e orquestração de IA.  
* **Núcleo de IA:** O LLM Gemini, o pipeline RAG e o serviço de STT em tempo real.  
* **Blockchain (Polygon):** O registo público que aloja os contratos inteligentes de Membership NFT e Invitation.  
* **Base de Dados Vetorial (Pinecone):** A base de dados especializada que armazena embeddings de transcrições de reuniões para pesquisa semântica.  
* **IPFS/Pinata:** Armazenamento descentralizado para metadados de NFT.

### **Tabela: Justificação do Stack Tecnológico**

Esta tabela serve como uma referência definitiva para a equipa de desenvolvimento, codificando o "quê" e o "porquê" das nossas tecnologias centrais. Previne o desvio arquitetónico e garante que todos os membros da equipa compreendem a lógica por trás das ferramentas que estão a utilizar.

| Domínio | Tecnologia Selecionada | Justificação e Pesquisa de Suporte |
| :---- | :---- | :---- |
| **Framework Móvel** | React Native | Desenvolvimento multiplataforma para iOS e Android a partir de uma única base de código, alinhado com o âmbito do projeto. Ecossistema extenso para as integrações necessárias (Web3, offline-sync, etc.). |
| **Base de Dados Local** | WatermelonDB | Otimizado para aplicações React Native offline-first. Construído sobre SQLite, tornando-o adequado para os dados relacionais do mapa de ideias (nós, arestas). A sua arquitetura de carregamento lento (lazy-loading) garante alto desempenho mesmo com grandes conjuntos de dados, e a sua natureza observável simplifica as atualizações da UI.12 |
| **Blockchain** | Polygon (EVM) | A compatibilidade com EVM permite o desenvolvimento padrão em Solidity. Taxas de transação mais baixas e maior débito em comparação com a mainnet do Ethereum são adequadas para as funções de gestão de convites e membros.18 |
| **Desenvolvimento de Contratos Inteligentes** | Hardhat & OpenZeppelin | Hardhat é o padrão da indústria para compilar, testar e implementar contratos Solidity.19 OpenZeppelin fornece modelos seguros e auditados para padrões como ERC-721, reduzindo o risco de desenvolvimento.7 |
| **Runtime de Backend** | Node.js (em AWS) | Excelentes capacidades de I/O assíncrono, ideal para lidar com WebSockets (para STT) e pedidos de API. Ecossistema forte com bibliotecas robustas para AWS, Ethers.js e integrações de IA.22 |
| **Interação com Blockchain** | Ethers.js | Uma biblioteca completa e moderna para interagir com blockchains do tipo Ethereum a partir de um ambiente JavaScript. Recomendada em detrimento de bibliotecas mais antigas como Web3.js.18 |
| **Modelo de IA** | Google Gemini API | Um LLM poderoso e multimodal especificado pelo utilizador. O seu suporte para instruções de sistema e chamada de funções (via MCP) torna-o ideal para um fluxo de trabalho agêntico.25 |
| **Orquestração de IA** | Model Context Protocol (MCP) | Um padrão aberto para conectar LLMs a ferramentas. Permite uma forma modular, segura e escalável para o Gemini interagir com os nossos serviços de backend (ex: atualizar o mapa de ideias), conforme especificado na consulta.8 |
| **Base de Dados Vetorial** | Pinecone | Uma base de dados vetorial totalmente gerida e sem servidor que simplifica a complexidade operacional de armazenar e consultar embeddings de alta dimensão. O seu desempenho e facilidade de uso são ideais para o pipeline RAG.28 |
| **Transcrição em Tempo Real** | Google Cloud Speech-to-Text | Oferece alta precisão para múltiplos oradores, suporta streaming em tempo real via WebSockets e integra-se bem num stack de IA centrado no Google (Gemini).31 |
| **Visualização de Grafos** | React Native SVG \+ D3.js | Fornece as primitivas de baixo nível necessárias para construir uma visualização de grafo completamente personalizada e não padrão, como o mapa de estilo Obsidian. Outras bibliotecas são demasiado restritivas. D3 fornece algoritmos de layout poderosos.34 |
| **Conexão de Carteira** | WalletConnect | O padrão de facto para conectar dApps móveis a carteiras externas, permitindo que os utilizadores assinem transações de forma segura sem expor chaves privadas à aplicação.37 |
| **Armazenamento de Metadados de NFT** | IPFS \+ Pinata | O IPFS garante armazenamento descentralizado e endereçado por conteúdo para os metadados do NFT. A Pinata atua como um serviço de pinning, garantindo que os dados permanecem disponíveis sem que o projeto precise de executar o seu próprio nó IPFS.40 |

## **Secção 2: Fase 1 \- Fundação de Identidade Descentralizada e Governança**

Esta fase estabelece os componentes on-chain que definem a afiliação e o controlo de acesso. Os contratos inteligentes são mais do que apenas código; são os estatutos imutáveis do Disruption Club. O contrato DisruptionClubNFT é o livro de registo de membros, enquanto o InvitationController é o porteiro automatizado. O design deve ser simples, seguro e eficiente em termos de gás. A forma mais segura e padrão de implementar isto é com um contrato ERC-721 para os NFTs 7 e um contrato separado controlado pelo

owner para gerir a lógica de emissão e convite. Esta separação de preocupações segue as melhores práticas. A utilização do Hardhat 20 fornece um framework robusto para testes, o que não é negociável para código que lida com valor e permissões.

### **Épico 1: Desenvolvimento de Contratos Inteligentes (Hardhat)**

* **Tarefa 1.1:** Inicializar o projeto Hardhat.  
  * **Descrição:** Configurar o ambiente de desenvolvimento Hardhat para os contratos inteligentes.  
  * **Detalhes:**  
    * **Instruções para o Gemini CLI:** Execute no terminal: mkdir disruption-club-contracts && cd disruption-club-contracts && npx hardhat init. Selecione 'Create a JavaScript project' e aceite as predefinições.  
    * **Critérios de Aceitação:** Um novo projeto Hardhat é criado com a estrutura de diretórios padrão (contracts, scripts, test).  
* **Tarefa 1.2:** Instalar dependências do OpenZeppelin.  
  * **Descrição:** Adicionar as bibliotecas de contratos seguros do OpenZeppelin ao projeto.  
  * **Detalhes:**  
    * **Instruções para o Gemini CLI:** Execute no terminal: npm install @openzeppelin/contracts  
    * **Critérios de Aceitação:** O pacote @openzeppelin/contracts está listado em package.json.  
* **Tarefa 1.3:** Criar o contrato DisruptionClubNFT.sol.  
  * **Descrição:** Implementar o contrato ERC-721 que representará a afiliação ao clube.  
  * **Detalhes:**  
    * **Instruções para o Gemini CLI:** Crie o ficheiro./contracts/DisruptionClubNFT.sol. Implemente um contrato Solidity chamado DisruptionClubNFT que herda de ERC721URIStorage e Ownable da OpenZeppelin. O contrato deve ter uma função pública safeMint(address to, uint256 tokenId, string memory uri) que só pode ser chamada pelo proprietário (owner).  
    * **Critérios de Aceitação:** O contrato compila sem erros. A função safeMint tem o modificador onlyOwner.  
* **Tarefa 1.4:** Criar o contrato InvitationController.sol.  
  * **Descrição:** Implementar o contrato que irá gerir a lógica de convites e a emissão de novos NFTs.  
  * **Detalhes:**  
    * **Instruções para o Gemini CLI:** Crie o ficheiro./contracts/InvitationController.sol. Implemente um contrato Solidity chamado InvitationController. Deve ter uma variável de endereço para o contrato DisruptionClubNFT. Implemente as seguintes funções: issueInvite(address candidate, bytes32 inviteCode), acceptInvite(bytes32 inviteCode) e withdraw(). A função issueInvite só deve ser chamada por uma conta de serviço de backend autorizada. A função acceptInvite deve verificar o código do convite, chamar a função safeMint no contrato NFT e marcar o convite como utilizado.  
    * **Critérios de Aceitação:** O contrato compila sem erros e a lógica de interação entre os dois contratos está corretamente definida.  
* **Tarefa 1.5:** Escrever testes abrangentes.  
  * **Descrição:** Garantir a robustez e segurança dos contratos através de testes unitários e de integração.  
  * **Detalhes:**  
    * **Instruções para o Gemini CLI:** Crie um ficheiro de teste em./test/DisruptionClub.test.js. Usando o Hardhat, Ethers.js e Chai, escreva testes para os seguintes cenários: 1\. A implementação dos contratos atribui corretamente a propriedade. 2\. Apenas o InvitationController pode cunhar um NFT. 3\. Um convite pode ser emitido e aceite com sucesso. 4\. Um convite não pode ser reutilizado. 5\. Apenas a conta de serviço pode emitir convites. 6\. O proprietário pode retirar fundos.  
    * **Critérios de Aceitação:** Todos os testes passam quando npx hardhat test é executado.

### **Épico 2: Implementação e Configuração da Blockchain**

* **Tarefa 2.1:** Configurar redes no Hardhat.  
  * **Descrição:** Preparar o projeto para a implementação nas redes de teste e principal da Polygon.  
  * **Detalhes:**  
    * **Instruções para o Gemini CLI:** Modifique o ficheiro hardhat.config.js. Adicione as configurações de rede para 'mumbai' (testnet da Polygon) e 'mainnet' (mainnet da Polygon). Use variáveis de ambiente (através de dotenv) para o RPC\_URL e PRIVATE\_KEY de cada rede.  
    * **Critérios de Aceitação:** As configurações de rede estão presentes e carregam as variáveis de ambiente corretamente.21  
* **Tarefa 2.2:** Criar scripts de implementação.  
  * **Descrição:** Automatizar o processo de implementação dos contratos na blockchain.  
  * **Detalhes:**  
    * **Instruções para o Gemini CLI:** Crie um ficheiro de script em./scripts/deploy.js. O script deve: 1\. Obter os artefactos dos contratos DisruptionClubNFT e InvitationController. 2\. Implementar o DisruptionClubNFT. 3\. Implementar o InvitationController, passando o endereço do NFT implementado para o seu construtor. 4\. Chamar a função transferOwnership no NFT para transferir a propriedade para o contrato InvitationController. 5\. Imprimir os endereços dos contratos implementados.  
    * **Critérios de Aceitação:** O script implementa ambos os contratos e define a propriedade corretamente.  
* **Tarefa 2.3:** Implementar e verificar na testnet.  
  * **Descrição:** Realizar a implementação na testnet da Polygon (Mumbai) e verificar o código fonte no explorador de blocos.  
  * **Detalhes:**  
    * **Instruções para o Gemini CLI:** Execute no terminal: npx hardhat run scripts/deploy.js \--network mumbai. Após a implementação, use o plugin 'hardhat-etherscan' para verificar ambos os contratos no Polygonscan.  
    * **Critérios de Aceitação:** Os contratos estão ativos na rede Mumbai e o seu código fonte é visível e verificado no Polygonscan.  
* **Tarefa 2.4:** Documentar artefactos dos contratos.  
  * **Descrição:** Fornecer à equipa de backend as informações necessárias para interagir com os contratos.  
  * **Detalhes:**  
    * **Instruções para o Gemini CLI:** Crie um ficheiro README.md na raiz do projeto de contratos. Documente os endereços dos contratos implementados na Mumbai e (futuramente) na Mainnet, e forneça os ficheiros ABI JSON completos para ambos os contratos.  
    * **Critérios de Aceitação:** A documentação está clara, completa e permite que a equipa de backend configure as suas interações.18

## **Secção 3: Fase 2 \- Serviços de Backend e Núcleo de Inteligência**

Esta fase constrói a lógica do lado do servidor que alimenta a aplicação, desde a gestão de utilizadores até ao pipeline de IA. Um ponto crítico a ser abordado é o paradoxo entre a encriptação de ponta a ponta (E2EE) e o processamento de IA. A E2EE padrão, como a do Signal, torna o conteúdo da mensagem ilegível para o servidor.44 Isso cria um conflito direto com a necessidade de a IA "ouvir" as reuniões. Se o servidor não consegue ler o fluxo de áudio, não pode transcrevê-lo ou analisá-lo. Portanto, a promessa arquitetónica não pode ser "E2EE de conhecimento zero". Em vez disso, a promessa deve ser um "enclave seguro e confiável". O modelo de segurança muda de impedir que o provedor de serviços

*alguma vez* veja os dados para garantir que a infraestrutura do provedor é uma fortaleza. Todo o processamento de IA ocorrerá dentro de um ambiente AWS rigidamente controlado e isolado. A comunicação para este enclave (o fluxo de áudio) será encriptada via TLS. Este é um compromisso crítico que deve ser compreendido de forma transparente. A arquitetura do backend será projetada com este princípio, usando AWS VPCs, grupos de segurança e políticas IAM rigorosas para criar este enclave.46

### **Épico 3: Estrutura Segura do Backend (Node.js em AWS)**

* **Tarefa 3.1:** Configurar o projeto Node.js e a infraestrutura AWS.  
  * **Descrição:** Estabelecer a base para os serviços de backend.  
  * **Detalhes:**  
    * **Instruções para o Gemini CLI:** Crie um novo projeto Node.js com Express.js. Use o AWS CDK ou Terraform para definir a infraestrutura: uma VPC com sub-redes públicas e privadas, um Application Load Balancer, um cluster ECS Fargate para os serviços e um AWS Secrets Manager para armazenar credenciais.  
    * **Critérios de Aceitação:** A infraestrutura pode ser implementada na AWS e o serviço Node.js base está a correr no Fargate.46  
* **Tarefa 3.2:** Implementar autenticação de serviço.  
  * **Descrição:** Criar e proteger a identidade da carteira que o backend usará para interagir com a blockchain.  
  * **Detalhes:**  
    * **Instruções para o Gemini CLI:** Gere um novo par de chaves Ethereum. Armazene a chave privada de forma segura no AWS Secrets Manager. Crie uma função no serviço Node.js que recupera esta chave privada do Secrets Manager para inicializar uma carteira Ethers.js.  
    * **Critérios de Aceitação:** O backend pode carregar a sua carteira de forma segura sem que a chave privada esteja hardcoded.

### **Épico 4: Camada de Serviço da Blockchain**

* **Tarefa 4.1:** Criar o BlockchainService.  
  * **Descrição:** Abstrair todas as interações com os contratos inteligentes numa única camada de serviço.  
  * **Detalhes:**  
    * **Instruções para o Gemini CLI:** Crie um ficheiro de serviço 'blockchain.service.js'. Use Ethers.js, os ABIs e os endereços dos contratos para instanciar objetos de contrato. Implemente uma função 'triggerInvite(candidateAddress)' que gera um código de convite único, chama a função 'issueInvite' no contrato InvitationController e armazena o código de forma segura. Implemente um endpoint de API que a aplicação móvel possa chamar para obter os dados da transação necessários para a função 'acceptInvite'.  
    * **Critérios de Aceitação:** O serviço pode emitir convites on-chain e fornecer os dados necessários para que os utilizadores os aceitem.18

### **Épico 5: Ingestão de Reuniões em Tempo Real**

* **Tarefa 5.1:** Implementar o servidor WebSocket e o MeetingService.  
  * **Descrição:** Criar o ponto de entrada para os fluxos de áudio em tempo real dos clientes.  
  * **Detalhes:**  
    * **Instruções para o Gemini CLI:** No projeto Node.js, adicione a biblioteca 'ws'. Crie um servidor WebSocket. Crie um 'meeting.service.js' que, ao receber um sinal de 'start\_meeting' de um cliente, estabelece uma conexão de streaming com a API Google Cloud Speech-to-Text. O serviço deve encaminhar os pedaços de áudio recebidos do cliente para a API STT.  
    * **Critérios de Aceitação:** O servidor WebSocket aceita conexões e encaminha com sucesso os dados de áudio para a Google Cloud STT.31  
* **Tarefa 5.2:** Processar transcrições.  
  * **Descrição:** Receber os resultados da transcrição e enviá-los para o próximo estágio do pipeline.  
  * **Detalhes:**  
    * **Instruções para o Gemini CLI:** No 'meeting.service.js', adicione um ouvinte para os resultados da API STT. À medida que os resultados da transcrição (interinos e finais) são recebidos, envie-os para o serviço do pipeline RAG para processamento posterior.  
    * **Critérios de Aceitação:** As transcrições de texto são recebidas e passadas para o componente RAG.

### **Épico 6: Pipeline RAG e Base de Conhecimento**

O pipeline de Geração Aumentada por Recuperação (RAG) é o coração da "compreensão" da IA. Ele transforma a conversa bruta e efémera numa base de conhecimento estruturada e pesquisável. O texto bruto do serviço STT não é útil para consultas complexas; deve ser processado num formato que capture o significado semântico. O padrão RAG 26 é a solução ideal.

* **Tarefa 6.1:** Configurar a base de dados vetorial e o serviço de embedding.  
  * **Descrição:** Preparar a infraestrutura para armazenar e gerar representações vetoriais do conhecimento.  
  * **Detalhes:**  
    * **Instruções para o Gemini CLI:** Crie uma conta Pinecone e um índice vetorial. No projeto Node.js, crie um 'vector.db.service.js' para interagir com a API da Pinecone. Crie um 'embedding.service.js' que usa a API Gemini (modelo text-embedding) para converter pedaços de texto em embeddings vetoriais.  
    * **Critérios de Aceitação:** O backend pode gerar embeddings e armazená-los no Pinecone.28  
* **Tarefa 6.2:** Implementar o fluxo RAG.  
  * **Descrição:** Construir o pipeline que ingere, processa e armazena o conhecimento das reuniões.  
  * **Detalhes:**  
    * **Instruções para o Gemini CLI:** Crie um 'rag.service.js'. Este serviço deve receber texto transcrito do MeetingService. Implemente a lógica para: 1\. Dividir o texto em pedaços significativos (chunking). 2\. Chamar o EmbeddingService para cada pedaço. 3\. Chamar o VectorDBService para inserir (upsert) os pedaços de texto e os seus embeddings correspondentes no Pinecone.  
    * **Critérios de Aceitação:** As transcrições das reuniões são processadas e armazenadas como vetores pesquisáveis.48  
* **Tarefa 6.3:** Implementar a função de consulta.  
  * **Descrição:** Criar a função que permite à IA recuperar conhecimento relevante.  
  * **Detalhes:**  
    * **Instruções para o Gemini CLI:** No 'rag.service.js', crie uma função 'queryKnowledgeBase(queryText)'. Esta função deve: 1\. Chamar o EmbeddingService para gerar um vetor para o 'queryText'. 2\. Usar este vetor para consultar o Pinecone através do VectorDBService. 3\. Retornar os documentos de texto mais semanticamente semelhantes.  
    * **Critérios de Aceitação:** A função recupera com sucesso o contexto relevante da base de dados vetorial com base numa consulta de texto.48

## **Secção 4: Fase 3 \- A Experiência do Membro (Aplicação React Native)**

Esta fase foca-se na construção da aplicação do lado do cliente com a qual os membros irão interagir. O requisito de a aplicação ser offline por defeito e só se conectar durante as reuniões é um motor arquitetónico central. Isto não pode ser deixado ao acaso ou ao comportamento padrão das bibliotecas. É necessária uma solução de gestão de estado global para controlar explicitamente a atividade de rede. Será criado um serviço ConnectivityManager. Ele manterá um estado ('offline', 'connecting', 'online'). Todos os serviços dependentes da rede (chamadas de API, conexões WebSocket) devem primeiro verificar o estado deste gestor. Quando uma reunião está agendada para começar, o gestor transita para 'online'. Quando a reunião termina, ele transita de volta para 'offline', e todos os pedidos de saída são então encaminhados para uma fila offline gerida pelo WatermelonDB.

### **Épico 7: Configuração do Projeto e Fundação da UI**

* **Tarefa 7.1:** Inicializar o projeto React Native e estruturá-lo.  
  * **Descrição:** Criar o esqueleto da aplicação móvel.  
  * **Detalhes:**  
    * **Instruções para o Gemini CLI:** Execute no terminal: npx react-native init DisruptionClub. Crie a seguinte estrutura de diretórios dentro de /src: /components, /screens, /services, /db, /state.  
    * **Critérios de Aceitação:** O projeto é criado e a estrutura de ficheiros está organizada.  
* **Tarefa 7.2:** Construir os ecrãs principais da UI.  
  * **Descrição:** Implementar a interface do utilizador com base no wireframe fornecido.  
  * **Detalhes:**  
    * **Instruções para o Gemini CLI:** Crie os componentes de ecrã para Login, Home (com o mapa de ideias) e Detalhes da Reunião. Implemente os elementos de UI personalizados do wireframe, incluindo a área de exibição do 'Badge NFT' e o fundo escuro estilo 'Aurora borea'.  
    * **Critérios de Aceitação:** Os ecrãs são renderizados corretamente e correspondem visualmente ao wireframe.

### **Épico 8: Persistência Offline-First (WatermelonDB)**

* **Tarefa 8.1:** Instalar e configurar o WatermelonDB.  
  * **Descrição:** Integrar a base de dados local na aplicação.  
  * **Detalhes:**  
    * **Instruções para o Gemini CLI:** Siga o guia de instalação oficial do WatermelonDB para React Native. Instale todas as dependências necessárias, incluindo JSI para um melhor desempenho.  
    * **Critérios de Aceitação:** O WatermelonDB está configurado e a aplicação inicia sem erros.13  
* **Tarefa 8.2:** Definir o esquema da base de dados e os modelos.  
  * **Descrição:** Criar a estrutura de dados para a aplicação no WatermelonDB.  
  * **Detalhes:**  
    * **Instruções para o Gemini CLI:** Crie o ficheiro /src/db/schema.js. Defina as tabelas 'users', 'meetings', 'nodes' e 'edges' de acordo com a tabela de esquema fornecida. Crie os ficheiros de modelo correspondentes em /src/db/models/.  
    * **Critérios de Aceitação:** O esquema está definido e os modelos WatermelonDB são criados.

#### **Tabela: Esquema do WatermelonDB**

| Tabela | Coluna | Tipo | Descrição |
| :---- | :---- | :---- | :---- |
| users | id | string | ID único do utilizador (corresponde ao endereço da carteira). |
|  | name | string | Nome de exibição do utilizador. |
|  | member\_id | string | Nº de membro (ex: \#01). |
| meetings | id | string | ID único da reunião. |
|  | date | number | Timestamp da reunião. |
|  | transcript\_cid | string | (Opcional) CID do IPFS da transcrição completa da reunião. |
| nodes | id | string | ID único para uma ideia/conceito. |
|  | content | string | O conteúdo Markdown do nó. |
|  | type | string | Ex: 'idea', 'concrete\_point', 'question'. |
|  | meeting\_id | string | Chave estrangeira para a tabela meetings. |
| edges | id | string | ID único para uma ligação. |
|  | source\_node\_id | string | Chave estrangeira para a tabela nodes. |
|  | target\_node\_id | string | Chave estrangeira para a tabela nodes. |

### **Épico 9: Integração de Carteira e Interação On-Chain**

* **Tarefa 9.1:** Integrar o WalletConnect.  
  * **Descrição:** Permitir que a aplicação se conecte a carteiras móveis externas para assinar transações.  
  * **Detalhes:**  
    * **Instruções para o Gemini CLI:** Instale as bibliotecas necessárias para o WalletConnect v2 em React Native. Configure o provedor WalletConnect no nível raiz da sua aplicação.  
    * **Critérios de Aceitação:** A aplicação pode iniciar uma conexão WalletConnect e exibir um QR code ou deep link.37  
* **Tarefa 9.2:** Implementar o fluxo de onboarding e login.  
  * **Descrição:** Gerir o processo de aceitação de convites e autenticação de membros.  
  * **Detalhes:**  
    * **Instruções para o Gemini CLI:** Crie um ecrã de Onboarding. Implemente o fluxo: 1\. O utilizador insere o código de convite. 2\. A app envia o código para o backend para obter os parâmetros da transação 'acceptInvite'. 3\. A app usa o WalletConnect para solicitar ao utilizador que assine a transação. 4\. Após o sucesso, implemente um ecrã de Login onde o utilizador assina uma mensagem para provar a posse da sua carteira e obter acesso.  
    * **Critérios de Aceitação:** Novos membros podem juntar-se ao clube e membros existentes podem autenticar-se de forma segura.

### **Épico 10: A Visualização do Mapa de Ideias**

A complexidade do mapa de ideias exige uma solução de duas partes. O WatermelonDB armazena os dados estruturados do grafo. O componente de UI é puramente para renderização. Uma biblioteca de gráficos padrão não funcionará para um grafo direcionado por força, personalizado e interativo. Precisamos de primitivas de desenho. react-native-svg fornece-as.34 Para lidar com a física e o layout complexos de um grafo, uma biblioteca como

d3-force é ideal. O componente consultará o WatermelonDB por todos os nós e arestas, alimentá-los-á numa simulação de força D3 para calcular as posições e, em seguida, usará react-native-svg para renderizar os componentes Circle e Line nas coordenadas calculadas.

* **Tarefa 10.1:** Instalar dependências de visualização.  
  * **Descrição:** Adicionar as bibliotecas SVG e D3 ao projeto.  
  * **Detalhes:**  
    * **Instruções para o Gemini CLI:** Execute no terminal: npm install react-native-svg d3-force  
    * **Critérios de Aceitação:** As bibliotecas estão instaladas e linkadas corretamente.  
* **Tarefa 10.2:** Criar o componente IdeaMap.  
  * **Descrição:** Desenvolver o componente React que renderiza o grafo interativo.  
  * **Detalhes:**  
    * **Instruções para o Gemini CLI:** Crie o componente /src/components/IdeaMap.js. No componente, use as APIs do WatermelonDB para buscar todos os registos de 'nodes' e 'edges'. Inicialize uma simulação d3-force com estes dados. Em cada 'tick' da simulação, atualize o estado do componente com as novas posições dos nós. Renderize os nós e arestas usando os componentes \<Svg\>, \<Circle\> e \<Line\> do react-native-svg. Adicione manipuladores de gestos para funcionalidade de pan e zoom.  
    * **Critérios de Aceitação:** O mapa de ideias é renderizado na tela, e os nós movem-se de acordo com a simulação de força. O utilizador pode interagir com o mapa.

### **Épico 11: Gestão do Estado de Conectividade**

* **Tarefa 11.1:** Criar o ConnectivityManager.  
  * **Descrição:** Implementar o serviço central para controlar o acesso à rede.  
  * **Detalhes:**  
    * **Instruções para o Gemini CLI:** Crie um serviço/contexto React chamado 'ConnectivityManager'. Use a biblioteca '@react-native-community/netinfo' para detetar o estado da rede física. O gestor deve expor um estado (ex: isMeetingActive) e funções (startMeetingSession, endMeetingSession).  
    * **Critérios de Aceitação:** O estado de conectividade da aplicação pode ser gerido centralmente.51  
* **Tarefa 11.2:** Implementar a fila offline.  
  * **Descrição:** Garantir que as ações do utilizador realizadas offline são guardadas e sincronizadas mais tarde.  
  * **Detalhes:**  
    * **Instruções para o Gemini CLI:** Modifique todos os serviços que fazem chamadas de API. Antes de cada pedido, verifique o estado do ConnectivityManager. Se estiver offline, em vez de fazer o pedido, adicione a mutação (ex: criar um novo nó) a uma tabela de 'offline\_queue' no WatermelonDB. Quando o estado mudar para online, processe e sincronize todos os itens na fila.  
    * **Critérios de Aceitação:** As ações offline são persistidas localmente e sincronizadas com sucesso quando a conectividade é restaurada.10

## **Secção 5: Fase 4 \- Orquestração Avançada de IA (Model Context Protocol)**

Esta fase conecta a IA à aplicação, transformando-a de um processador de dados num agente ativo. O MCP permite-nos tratar a IA como um verdadeiro agente. Em vez de o backend ter um fluxo lógico complexo e codificado, ele simplesmente fornece à IA um conjunto de ferramentas. A IA, guiada pelo seu prompt de sistema, decide quais ferramentas usar e em que ordem. Este é um paradigma mais flexível e poderoso.9

### **Épico 12: Implementação do Servidor MCP (Backend)**

* **Tarefa 12.1:** Instalar o SDK do MCP e criar o servidor.  
  * **Descrição:** Configurar o servidor MCP no backend para expor ferramentas à IA.  
  * **Detalhes:**  
    * **Instruções para o Gemini CLI:** No projeto Node.js, instale o SDK do servidor MCP: npm install @modelcontextprotocol/sdk. Crie um 'mcp.server.js' que inicializa um novo servidor MCP. Exponha as ferramentas definidas na tabela de ferramentas MCP.  
    * **Critérios de Aceitação:** O servidor MCP está a correr e pode receber conexões de um cliente MCP.53

#### **Tabela: Definições de Ferramentas MCP**

| Nome da Ferramenta | Parâmetros | Descrição |
| :---- | :---- | :---- |
| queryKnowledgeBase | query: string | Executa uma pesquisa semântica na base de dados vetorial Pinecone e retorna os pedaços de transcrição mais relevantes. |
| getIdeaMap | userId: string | Recupera o estado atual do mapa de ideias de um utilizador da base de dados WatermelonDB. |
| updateIdeaMap | userId: string, operations: Operation | Aplica uma série de operações (ex: createNode, createEdge) ao mapa de ideias de um utilizador. |
| getMemberProfile | userId: string | Obtém o perfil de um determinado membro. |
| scheduleReturn | userId: string, returnDate: string | Lida com o caso de uso do "membro ausente", agendando o seu regresso. |

### **Épico 13: Integração do Cliente MCP (Aplicação Móvel)**

* **Tarefa 13.1:** Integrar o cliente MCP na aplicação React Native.  
  * **Descrição:** Conectar a aplicação móvel ao host MCP do backend durante as reuniões.  
  * **Detalhes:**  
    * **Instruções para o Gemini CLI:** Instale o SDK do cliente MCP na aplicação React Native. Durante uma sessão de reunião ativa (controlada pelo ConnectivityManager), o cliente deve conectar-se ao host MCP do backend. O cliente deve fornecer contexto em tempo real, como o 'currentUser' e 'currentMeetingId', ao host.  
    * **Critérios de Aceitação:** O cliente móvel estabelece uma conexão bem-sucedida com o servidor MCP.

### **Épico 14: Fluxo de Trabalho de IA Generativa**

* **Tarefa 14.1:** Desenvolver o prompt do sistema para o Gemini.  
  * **Descrição:** Definir o papel e as instruções para o agente de IA.  
  * **Detalhes:**  
    * **Instruções para o Gemini CLI:** Crie um ficheiro de prompt 'gemini-system-prompt.txt'. A instrução do sistema deve ser: "Você é o Escriba do Disruption Club. O seu papel é ouvir as transcrições das reuniões, sintetizar novas informações com o conhecimento existente e atualizar os mapas de ideias dos membros. Use as ferramentas fornecidas para atingir este objetivo."  
    * **Critérios de Aceitação:** O prompt está claro, conciso e orienta o modelo para o comportamento desejado.25  
* **Tarefa 14.2:** Implementar o loop de IA agêntica.  
  * **Descrição:** Orquestrar a interação entre o Gemini e as ferramentas MCP.  
  * **Detalhes:**  
    * **Instruções para o Gemini CLI:** No backend, crie um 'ai.agent.service.js'. Este serviço será acionado por novos dados de transcrição. O loop principal deve: 1\. Enviar o último pedaço de transcrição para o Gemini com a lista de ferramentas MCP disponíveis. 2\. O Gemini decide qual ferramenta chamar (ex: queryKnowledgeBase). 3\. O backend executa a ferramenta e retorna o resultado para o Gemini. 4\. O Gemini usa o novo contexto para formular uma série de operações (ex: updateIdeaMap). 5\. O backend executa a ferramenta final, atualizando a base de dados.  
    * **Critérios de Aceitação:** A IA pode autonomamente usar as ferramentas para analisar transcrições e atualizar o mapa de ideias de um membro.9

## **Secção 6: Fase 5 \- Fortalecimento, Implementação e Operações**

Esta fase final prepara a aplicação para o lançamento e manutenção contínua. A segurança é um processo, não uma funcionalidade. Uma aplicação segura requer uma abordagem em várias camadas, abordando tudo, desde a configuração da infraestrutura até às políticas de manuseamento de dados. Este épico consolida todas as tarefas de segurança num único esforço focado.

### **Épico 15: Implementação de Segurança de Ponta a Ponta**

* **Tarefa 15.1:** Implementar a checklist de segurança.  
  * **Descrição:** Aplicar as melhores práticas de segurança em todo o stack.  
  * **Detalhes:**  
    * **Instruções para o Gemini CLI:** Para cada item na Tabela de Checklist de Segurança, implemente a configuração ou política correspondente. Por exemplo, para 'Implementar segmentação de rede', crie as configurações de VPC e sub-rede na sua infraestrutura AWS (IaC). Para 'Higienizar todas as entradas do utilizador', adicione middleware de validação e higienização a todos os endpoints da API Express.js.  
    * **Critérios de Aceitação:** Todos os itens da checklist são implementados e verificados.

#### **Tabela: Checklist de Segurança e Conformidade**

| Domínio | Tarefa | Justificação / Referência |
| :---- | :---- | :---- |
| **Infraestrutura** | Implementar segmentação de rede com VPCs e sub-redes privadas. | Isolar componentes críticos como a base de dados e os serviços de IA do acesso público.46 |
|  | Usar AWS WAF no Application Load Balancer. | Proteger contra explorações web comuns (Injeção, XSS). (A03:2021-Injection) |
|  | Ativar AWS Shield Advanced. | Proteção DDoS para um serviço de alta disponibilidade.54 |
| **Identidade e Acesso** | Forçar o Princípio do Menor Privilégio com papéis IAM granulares. | Garantir que serviços e utilizadores têm apenas as permissões mínimas necessárias.46 |
|  | Usar AWS Secrets Manager para todas as credenciais (BD, APIs, chaves de carteira). | Evitar segredos hardcoded, um dos principais riscos.55 |
|  | Forçar MFA para todo o acesso humano à consola AWS. | Base de identidade forte.46 |
| **Proteção de Dados** | Encriptar todos os dados em repouso (RDS, S3) usando AWS KMS. | Proteger dados sensíveis armazenados.46 |
|  | Forçar TLS 1.2+ para todos os dados em trânsito. | Proteger os dados de escutas.56 |
|  | Implementar uma Política de Retenção de Dados robusta. | Cumprir regulamentos de privacidade como o GDPR e minimizar a exposição de dados.57 |
| **Aplicação** | Higienizar todas as entradas do utilizador no backend. | Prevenir ataques de injeção \[A03:2021-Injection\]. |
|  | Implementar limitação de taxa (rate limiting) em todos os endpoints de API públicos. | Prevenir abuso e ataques DoS. |
| **Logging** | Ativar AWS CloudTrail e VPC Flow Logs. | Garantir rastreabilidade completa de todas as ações e tráfego de rede para auditorias e resposta a incidentes.46 |

### **Épico 16: Distribuição Privada da Aplicação**

O Apple Developer Enterprise Program é uma dependência crítica. Obter acesso pode ser um processo demorado e é um fator decisivo para o projeto.

* **Tarefa 16.1:** Preparar para a distribuição iOS Enterprise.  
  * **Descrição:** Cumprir os requisitos e configurar os certificados para a distribuição privada em iOS.  
  * **Detalhes:**  
    * **Instruções para o Gemini CLI:** Inicie o processo de candidatura ao Apple Developer Enterprise Program. Uma vez aprovado, gere um certificado de distribuição In-House e um perfil de provisionamento. Configure o Xcode (através do processo de build do React Native) para assinar a build de lançamento com estas credenciais.  
    * **Critérios de Aceitação:** A candidatura é submetida e os artefactos de assinatura são gerados.15  
* **Tarefa 16.2:** Preparar para a distribuição Android.  
  * **Descrição:** Gerar a chave de assinatura para a aplicação Android.  
  * **Detalhes:**  
    * **Instruções para o Gemini CLI:** Use o 'keytool' para gerar um keystore de upload. Armazene o keystore e as suas credenciais de forma segura (ex: AWS Secrets Manager). Configure o ficheiro 'android/app/build.gradle' para usar este keystore para builds de lançamento.  
    * **Critérios de Aceitação:** O ficheiro de keystore é gerado e a configuração do Gradle está correta.60  
* **Tarefa 16.3:** Implementar o servidor de distribuição.  
  * **Descrição:** Criar um local seguro para os membros descarregarem a aplicação.  
  * **Detalhes:**  
    * **Instruções para o Gemini CLI:** Configure um bucket S3 privado na AWS. Crie um endpoint de API no backend que, para um utilizador autenticado, gera um URL pré-assinado do S3 com tempo de vida limitado para descarregar o ficheiro.ipa (iOS) ou.apk (Android).  
    * **Critérios de Aceitação:** Membros autenticados podem descarregar a aplicação de forma segura.

### **Épico 17: Governança e Retenção de Dados**

* **Tarefa 17.1:** Formalizar e implementar a política de retenção.  
  * **Descrição:** Garantir que os dados são geridos de acordo com os princípios de privacidade e requisitos legais.  
  * **Detalhes:**  
    * **Instruções para o Gemini CLI:** Crie um script de backend (ex: 'data-retention.job.js') que será executado periodicamente (ex: via um cron job). O script deve consultar a base de dados por registos que excedam o seu período de retenção (conforme a Tabela de Retenção de Dados) e executar uma eliminação segura. Registe todas as ações de eliminação para fins de auditoria.  
    * **Critérios de Aceitação:** A política de retenção é aplicada automaticamente e de forma auditável.57

#### **Tabela: Cronograma de Retenção de Dados**

| Categoria de Dados | Período de Retenção | Justificação | Método de Eliminação |
| :---- | :---- | :---- | :---- |
| **Informação da Conta do Utilizador** | Duração da afiliação \+ 1 ano | Necessário para a operação da conta. Período pós-afiliação para contabilidade/auditorias finais. | Anonimização de PII. |
| **Transcrições de Reuniões (Brutas)** | 2 Anos | O valor primário é para o contexto RAG imediato. O valor a longo prazo diminui. | Eliminação segura da base de dados vetorial e de qualquer armazenamento bruto. |
| **Dados do Mapa de Ideias (Nós/Arestas)** | Duração da afiliação | Esta é a propriedade intelectual central do membro dentro do clube. Retida enquanto for membro. | Eliminação segura do WatermelonDB após o término da afiliação. |
| **Registos de Convite** | 1 Ano | Necessário para auditoria a curto prazo do processo de convite. | Eliminação segura da base de dados. |
| **Logs de Auditoria do Sistema** | 18 Meses | Prática padrão para investigação de incidentes de segurança. | Eliminação segura do agregador de logs. |

## **Conclusões**

Este plano de desenvolvimento representa um roteiro abrangente para a criação da aplicação "Disruption Club". Ele aborda os complexos requisitos multifacetados do projeto, integrando tecnologias de ponta de Web3, IA, desenvolvimento móvel e infraestrutura segura. A arquitetura proposta não é apenas funcional, mas estrategicamente alinhada com os objetivos de negócio do clube: fomentar a inovação disruptiva num ambiente exclusivo, seguro e intelectualmente estimulante.

As principais decisões arquitetónicas, como a adoção do modelo de "enclave seguro" em vez de E2EE de conhecimento zero, a implementação de um gestor de conectividade personalizado e a utilização do Model Context Protocol para uma IA agêntica, são compromissos deliberados que equilibram os requisitos do utilizador com as realidades técnicas. A execução bem-sucedida deste plano resultará numa aplicação que não é apenas uma ferramenta, mas um ecossistema completo para a próxima geração de inovadores. A adesão rigorosa às fases, tarefas e protocolos de segurança aqui delineados será fundamental para mitigar os riscos e garantir que o produto final cumpra a sua visão ambiciosa.

#### **Referências citadas**

1. The Essential Clayton Christensen Articles | Harvard Business Publishing Education, acessado em julho 4, 2025, [https://hbsp.harvard.edu/inspiring-minds/the-essential-clayton-christensen-articles](https://hbsp.harvard.edu/inspiring-minds/the-essential-clayton-christensen-articles)  
2. The Innovator's Dilemma \- Wikipedia, acessado em julho 4, 2025, [https://en.wikipedia.org/wiki/The\_Innovator%27s\_Dilemma](https://en.wikipedia.org/wiki/The_Innovator%27s_Dilemma)  
3. What Is Disruptive Innovation? \- HBS Online \- Harvard Business School, acessado em julho 4, 2025, [https://online.hbs.edu/blog/post/what-is-disruptive-innovation](https://online.hbs.edu/blog/post/what-is-disruptive-innovation)  
4. What Is Disruptive Innovation Theory? 4 Key Concepts \- HBS Online, acessado em julho 4, 2025, [https://online.hbs.edu/blog/post/4-keys-to-understanding-clayton-christensens-theory-of-disruptive-innovation](https://online.hbs.edu/blog/post/4-keys-to-understanding-clayton-christensens-theory-of-disruptive-innovation)  
5. The science of creativity \- American Psychological Association, acessado em julho 4, 2025, [https://www.apa.org/gradpsych/2009/01/creativity](https://www.apa.org/gradpsych/2009/01/creativity)  
6. Creativity | Psychology Today, acessado em julho 4, 2025, [https://www.psychologytoday.com/us/basics/creativity](https://www.psychologytoday.com/us/basics/creativity)  
7. ERC-721 \- OpenZeppelin Docs, acessado em julho 4, 2025, [https://docs.openzeppelin.com/contracts/5.x/erc721](https://docs.openzeppelin.com/contracts/5.x/erc721)  
8. en.wikipedia.org, acessado em julho 4, 2025, [https://en.wikipedia.org/wiki/Model\_Context\_Protocol](https://en.wikipedia.org/wiki/Model_Context_Protocol)  
9. Model Context Protocol: Introduction, acessado em julho 4, 2025, [https://modelcontextprotocol.io/](https://modelcontextprotocol.io/)  
10. Building Offline-First React Native Apps with React Query and TypeScript | Whitespectre, acessado em julho 4, 2025, [https://www.whitespectre.com/ideas/how-to-build-offline-first-react-native-apps-with-react-query-and-typescript/](https://www.whitespectre.com/ideas/how-to-build-offline-first-react-native-apps-with-react-query-and-typescript/)  
11. Offline-First Architecture with WatermelonDB and MongoDB | by Vineetdixit Vns \- Medium, acessado em julho 4, 2025, [https://medium.com/@vineetdixit.vns/offline-first-architecture-with-watermelondb-and-mongodb-7efee1a09bb0](https://medium.com/@vineetdixit.vns/offline-first-architecture-with-watermelondb-and-mongodb-7efee1a09bb0)  
12. Choosing the right database for your React Native app | by Sneh Pandya \- Medium, acessado em julho 4, 2025, [https://medium.com/code-well/choosing-the-right-database-for-your-react-native-app-137f4893b182](https://medium.com/code-well/choosing-the-right-database-for-your-react-native-app-137f4893b182)  
13. Best React Native Database for Your App Development in 2025, acessado em julho 4, 2025, [https://www.excellentwebworld.com/react-native-database/](https://www.excellentwebworld.com/react-native-database/)  
14. How does WatermelonDB compare to Realm? \- Hacker News, acessado em julho 4, 2025, [https://news.ycombinator.com/item?id=17958888](https://news.ycombinator.com/item?id=17958888)  
15. Apple Developer Enterprise Program, acessado em julho 4, 2025, [https://developer.apple.com/programs/enterprise/](https://developer.apple.com/programs/enterprise/)  
16. Understanding Apple App Signing Types \- Applivery, acessado em julho 4, 2025, [https://www.applivery.com/docs/faq/faq/understanding-apple-app-signing-types/](https://www.applivery.com/docs/faq/faq/understanding-apple-app-signing-types/)  
17. Top Database Choices for High-Performance React Native App \- Nous Infosystems, acessado em julho 4, 2025, [https://www.nousinfosystems.com/insights/blog/how-to-select-the-best-database-for-a-react-native-app](https://www.nousinfosystems.com/insights/blog/how-to-select-the-best-database-for-a-react-native-app)  
18. How to Mint an NFT on Polygon with Ethers.js | QuickNode Guides, acessado em julho 4, 2025, [https://www.quicknode.com/guides/other-chains/polygon/how-to-mint-an-nft-on-polygon-with-ethersjs](https://www.quicknode.com/guides/other-chains/polygon/how-to-mint-an-nft-on-polygon-with-ethersjs)  
19. Getting started with Hardhat | Ethereum development environment for professionals by Nomic Foundation, acessado em julho 4, 2025, [https://hardhat.org/hardhat-runner](https://hardhat.org/hardhat-runner)  
20. Hardhat's tutorial for beginners | Ethereum development environment for professionals by Nomic Foundation, acessado em julho 4, 2025, [https://hardhat.org/tutorial](https://hardhat.org/tutorial)  
21. hacktronaut/hardhat-tutorial: Comprehensive tutorial on hard-hat \- GitHub, acessado em julho 4, 2025, [https://github.com/hacktronaut/hardhat-tutorial](https://github.com/hacktronaut/hardhat-tutorial)  
22. How To Interact with Smart Contracts | QuickNode Guides, acessado em julho 4, 2025, [https://www.quicknode.com/guides/ethereum-development/smart-contracts/how-to-interact-with-smart-contracts](https://www.quicknode.com/guides/ethereum-development/smart-contracts/how-to-interact-with-smart-contracts)  
23. How to Use Google Gemini with Node.js App \- Arindam Majumder, acessado em julho 4, 2025, [https://arindam1729.hashnode.dev/how-to-use-google-gemini-with-nodejs-app](https://arindam1729.hashnode.dev/how-to-use-google-gemini-with-nodejs-app)  
24. Blockchain interaction using Ethers.js | Coinmonks \- Medium, acessado em julho 4, 2025, [https://medium.com/coinmonks/how-to-interact-with-blockchain-using-ethers-js-7d0be4a8a6e8](https://medium.com/coinmonks/how-to-interact-with-blockchain-using-ethers-js-7d0be4a8a6e8)  
25. Text generation | Gemini API | Google AI for Developers, acessado em julho 4, 2025, [https://ai.google.dev/gemini-api/docs/text-generation](https://ai.google.dev/gemini-api/docs/text-generation)  
26. Retrieval Augmented Generation (RAG) with Google Gemini AI and Langchain4J \- Kestra, acessado em julho 4, 2025, [https://kestra.io/blogs/rag-with-gemini-and-langchain4j](https://kestra.io/blogs/rag-with-gemini-and-langchain4j)  
27. Specification \- Model Context Protocol, acessado em julho 4, 2025, [https://modelcontextprotocol.io/specification/2025-06-18](https://modelcontextprotocol.io/specification/2025-06-18)  
28. Most Popular Vector Databases You Must Know in 2025 \- Dataaspirant, acessado em julho 4, 2025, [https://dataaspirant.com/popular-vector-databases/](https://dataaspirant.com/popular-vector-databases/)  
29. The 7 Best Vector Databases in 2025 \- DataCamp, acessado em julho 4, 2025, [https://www.datacamp.com/blog/the-top-5-vector-databases](https://www.datacamp.com/blog/the-top-5-vector-databases)  
30. Top 10 Vector Database Solutions for Your AI Project \- The New Stack, acessado em julho 4, 2025, [https://thenewstack.io/top-vector-database-solutions-for-your-ai-project/](https://thenewstack.io/top-vector-database-solutions-for-your-ai-project/)  
31. Transcribe audio from streaming input | Cloud Speech-to-Text Documentation, acessado em julho 4, 2025, [https://cloud.google.com/speech-to-text/docs/transcribe-streaming-audio](https://cloud.google.com/speech-to-text/docs/transcribe-streaming-audio)  
32. Node real time speech-to-text with Google | by Bebity \- Medium, acessado em julho 4, 2025, [https://bebity.medium.com/node-real-time-speech-to-text-with-google-88678ca3ad](https://bebity.medium.com/node-real-time-speech-to-text-with-google-88678ca3ad)  
33. Speech-to-Text AI: speech recognition and transcription \- Google Cloud, acessado em julho 4, 2025, [https://cloud.google.com/speech-to-text](https://cloud.google.com/speech-to-text)  
34. Top 9 React Native Chart Libraries for Data Visualization in 2025 \- OpenReplay Blog, acessado em julho 4, 2025, [https://blog.openreplay.com/react-native-chart-libraries-2025/](https://blog.openreplay.com/react-native-chart-libraries-2025/)  
35. 7 Best React Native Chart Libraries To Use In 2023 \- WebMob Technologies, acessado em julho 4, 2025, [https://webmobtech.com/blog/react-native-chart-libraries/](https://webmobtech.com/blog/react-native-chart-libraries/)  
36. The top 10 React Native charts libraries for 2025 \- LogRocket Blog, acessado em julho 4, 2025, [https://blog.logrocket.com/top-react-native-chart-libraries/](https://blog.logrocket.com/top-react-native-chart-libraries/)  
37. How to Implement WalletConnect in your React Native App | by Abbas Aslanbay \- Medium, acessado em julho 4, 2025, [https://abbaslanbay.medium.com/how-to-implement-walletconnect-in-your-react-native-app-a25abafd243](https://abbaslanbay.medium.com/how-to-implement-walletconnect-in-your-react-native-app-a25abafd243)  
38. cawfree/react-native-walletconnect \- GitHub, acessado em julho 4, 2025, [https://github.com/cawfree/react-native-walletconnect](https://github.com/cawfree/react-native-walletconnect)  
39. Connect with WalletConnect \- Portal Developer Docs, acessado em julho 4, 2025, [https://docs.portalhq.io/guides/react-native/connect-with-walletconnect](https://docs.portalhq.io/guides/react-native/connect-with-walletconnect)  
40. Using a Node.js Script to Upload a Folder to a Remote IPFS Node | by Itay Podhajcer, acessado em julho 4, 2025, [https://www.itaypodhajcer.com/using-a-node-js-script-to-upload-a-folder-to-a-remote-ipfs-node-255fa9e3b766](https://www.itaypodhajcer.com/using-a-node-js-script-to-upload-a-folder-to-a-remote-ipfs-node-255fa9e3b766)  
41. How do I upload files to IPFS? \- Pinata Cloud, acessado em julho 4, 2025, [https://pinata.cloud/blog/how-do-i-upload-files-to-ipfs/](https://pinata.cloud/blog/how-do-i-upload-files-to-ipfs/)  
42. Node.js \- Pinata Docs, acessado em julho 4, 2025, [https://docs.pinata.cloud/frameworks/node-js](https://docs.pinata.cloud/frameworks/node-js)  
43. Deploying Smart Contracts to the Polygon and Ethereum Blockchain Using Hardhat and Ethers.js | by Emmanuel Ayodele Bello | Better Programming \- Medium, acessado em julho 4, 2025, [https://medium.com/better-programming/deploying-smart-contracts-to-the-polygon-and-ethereum-blockchain-using-hardhat-and-ethers-js-2c31aa41aed0](https://medium.com/better-programming/deploying-smart-contracts-to-the-polygon-and-ethereum-blockchain-using-hardhat-and-ethers-js-2c31aa41aed0)  
44. End-to-End encryption for a chat application \- Stack Overflow, acessado em julho 4, 2025, [https://stackoverflow.com/questions/48249900/end-to-end-encryption-for-a-chat-application](https://stackoverflow.com/questions/48249900/end-to-end-encryption-for-a-chat-application)  
45. Building end-to-end security for Messenger \- Engineering at Meta, acessado em julho 4, 2025, [https://engineering.fb.com/2023/12/06/security/building-end-to-end-security-for-messenger/](https://engineering.fb.com/2023/12/06/security/building-end-to-end-security-for-messenger/)  
46. Security \- AWS Well-Architected Framework, acessado em julho 4, 2025, [https://wa.aws.amazon.com/wellarchitected/2020-07-02T19-33-23/wat.pillar.security.en.html](https://wa.aws.amazon.com/wellarchitected/2020-07-02T19-33-23/wat.pillar.security.en.html)  
47. Introduction to AWS infrastructure security | RST Software, acessado em julho 4, 2025, [https://www.rst.software/blog/introduction-to-aws-infrastructure-security](https://www.rst.software/blog/introduction-to-aws-infrastructure-security)  
48. Understanding RAG: Building a RAG system from scratch with Gemini API \- Medium, acessado em julho 4, 2025, [https://medium.com/@saurabhgssingh/understanding-rag-building-a-rag-system-from-scratch-with-gemini-api-b11ad9fc1bf7](https://medium.com/@saurabhgssingh/understanding-rag-building-a-rag-system-from-scratch-with-gemini-api-b11ad9fc1bf7)  
49. Blazing Fast Search with text-embedding-ada-002 in Node.js \- Raja Osama, acessado em julho 4, 2025, [https://rajaosama.me/blogs/blazing-fast-search-with-embedding-model-ada](https://rajaosama.me/blogs/blazing-fast-search-with-embedding-model-ada)  
50. OpenAI Embedding & Semantic Search using Vector data | by Sathishhariram \- Medium, acessado em julho 4, 2025, [https://medium.com/@sathishhariram/openai-embedding-semantic-search-using-vector-data-b785ae7079ff](https://medium.com/@sathishhariram/openai-embedding-semantic-search-using-vector-data-b785ae7079ff)  
51. Building Offline-first Applications with React Native \- DEV Community, acessado em julho 4, 2025, [https://dev.to/zidanegimiga/building-offline-first-applications-with-react-native-3626](https://dev.to/zidanegimiga/building-offline-first-applications-with-react-native-3626)  
52. Model Context Protocol (MCP): Understanding security risks and controls \- Red Hat, acessado em julho 4, 2025, [https://www.redhat.com/en/blog/model-context-protocol-mcp-understanding-security-risks-and-controls](https://www.redhat.com/en/blog/model-context-protocol-mcp-understanding-security-risks-and-controls)  
53. Core architecture \- Model Context Protocol, acessado em julho 4, 2025, [https://modelcontextprotocol.io/docs/concepts/architecture](https://modelcontextprotocol.io/docs/concepts/architecture)  
54. Building secure foundations: A guide to network and infrastructure security at AWS re:Inforce 2025, acessado em julho 4, 2025, [https://aws.amazon.com/blogs/security/building-secure-foundations-a-guide-to-network-and-infrastructure-security-at-aws-reinforce-2025/](https://aws.amazon.com/blogs/security/building-secure-foundations-a-guide-to-network-and-infrastructure-security-at-aws-reinforce-2025/)  
55. OWASP Top 10 Non-Human Identity Risks for 2025: What You Need to Know, acessado em julho 4, 2025, [https://blog.gitguardian.com/owasp-top-10-non-human-identity-risks/](https://blog.gitguardian.com/owasp-top-10-non-human-identity-risks/)  
56. Securing Your React Native App: Best Practices and Strategies \- Morrow, acessado em julho 4, 2025, [https://www.themorrow.digital/blog/securing-your-react-native-app-best-practices-and-strategies](https://www.themorrow.digital/blog/securing-your-react-native-app-best-practices-and-strategies)  
57. GDPR Data Retention: Compliance Guidelines & Best Practices \- Usercentrics, acessado em julho 4, 2025, [https://usercentrics.com/knowledge-hub/gdpr-data-retention/](https://usercentrics.com/knowledge-hub/gdpr-data-retention/)  
58. Data Retention Policy: 10 Best Practices \- FileCloud, acessado em julho 4, 2025, [https://www.filecloud.com/blog/2025/05/data-retention-policy-best-practices/](https://www.filecloud.com/blog/2025/05/data-retention-policy-best-practices/)  
59. How to Secure Your Information on AWS: 10 Best Practices | Tripwire, acessado em julho 4, 2025, [https://www.tripwire.com/state-of-security/secure-information-aws-10-best-practices](https://www.tripwire.com/state-of-security/secure-information-aws-10-best-practices)  
60. Signing Your Applications | Android Developers, acessado em julho 4, 2025, [https://spot.pcc.edu/\~mgoodman/developer.android.com/tools/publishing/app-signing.html](https://spot.pcc.edu/~mgoodman/developer.android.com/tools/publishing/app-signing.html)  
61. Publishing to Google Play Store \- React Native, acessado em julho 4, 2025, [https://reactnative.dev/docs/signed-apk-android](https://reactnative.dev/docs/signed-apk-android)