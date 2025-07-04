Disruption Club: Development Task Plan
This document outlines the detailed, step-by-step tasks for developing the Disruption Club application. Each task is designed to be a minimal, actionable unit of work for the Gemini CLI.

Phase 1: Decentralized Identity & Governance Foundation
Epic 1: Smart Contract Development (Hardhat)
Task ID: 1.1
Title: Initialize Hardhat Project
Status: To Do
Dependencies: None
Priority: High
Description: Set up the Hardhat development environment for the smart contracts.
Details:
Run in the terminal: mkdir disruption-club-contracts && cd disruption-club-contracts && npx hardhat init. Select 'Create a JavaScript project' and accept the defaults.

Test Strategy:
Verify that a new Hardhat project is created with the standard directory structure (contracts, scripts, test).

Task ID: 1.2
Title: Install OpenZeppelin Contracts
Status: To Do
Dependencies: 1.1
Priority: High
Description: Add OpenZeppelin's secure, audited contract libraries to the project.
Details:
Run in the terminal: npm install @openzeppelin/contracts

Test Strategy:
Verify that the @openzeppelin/contracts package is listed as a dependency in package.json.

Task ID: 1.3
Title: Create DisruptionClubNFT Contract
Status: To Do
Dependencies: 1.2
Priority: High
Description: Implement the core ERC-721 contract that represents club membership.
Details:
Create the file ./contracts/DisruptionClubNFT.sol. Implement a Solidity contract named DisruptionClubNFT that inherits from OpenZeppelin's ERC721URIStorage and Ownable. The contract must have a public function safeMint(address to, uint256 tokenId, string memory uri) that can only be called by the contract owner.

Test Strategy:
The contract must compile without errors using npx hardhat compile. The safeMint function must have the onlyOwner modifier.

Task ID: 1.4
Title: Create InvitationController Contract
Status: To Do
Dependencies: 1.3
Priority: High
Description: Implement the contract that will manage the invitation logic and minting of new membership NFTs.
Details:
Create the file ./contracts/InvitationController.sol. Implement a Solidity contract named InvitationController that is Ownable. It must have an address variable for the DisruptionClubNFT contract, set in the constructor. Implement the following functions: issueInvite(address candidate, bytes32 inviteCode) and acceptInvite(bytes32 inviteCode). The issueInvite function must only be callable by an authorized backend service account (add a separate role or use onlyOwner initially). The acceptInvite function must verify the invite code, call the safeMint function on the NFT contract, and mark the invite as used.

Test Strategy:
The contract must compile without errors. The logic for interacting with the NFT contract must be correctly defined.

Task ID: 1.5
Title: Write Comprehensive Smart Contract Tests
Status: To Do
Dependencies: 1.4
Priority: High
Description: Ensure the robustness and security of the contracts with unit and integration tests.
Details:
Create a test file at ./test/DisruptionClub.test.js. Using Hardhat, Ethers.js, and Chai, write tests for the following scenarios:

Deployment correctly assigns ownership.

Only the InvitationController can mint a new NFT.

An invitation can be successfully issued and accepted.

An invitation cannot be reused.

Only the authorized service account can issue invitations.

The owner can successfully withdraw any funds from the InvitationController.

Test Strategy:
All tests must pass when npx hardhat test is executed.

Epic 2: Blockchain Deployment & Configuration
Task ID: 2.1
Title: Configure Hardhat Networks
Status: To Do
Dependencies: 1.5
Priority: High
Description: Prepare the project for deployment to Polygon's testnet and mainnet.
Details:
Modify the hardhat.config.js file. Add network configurations for 'mumbai' (Polygon testnet) and 'mainnet' (Polygon). Use environment variables (via the dotenv package) for the RPC_URL and PRIVATE_KEY for each network.

Test Strategy:
The network configurations must be present and correctly load the environment variables.

Task ID: 2.2
Title: Create Deployment Scripts
Status: To Do
Dependencies: 2.1
Priority: High
Description: Automate the process of deploying the contracts to the blockchain.
Details:
Create a script file at ./scripts/deploy.js. The script must:

Get the contract artifacts for DisruptionClubNFT and InvitationController.

Deploy DisruptionClubNFT.

Deploy InvitationController, passing the deployed NFT address to its constructor.

Call the transferOwnership function on the DisruptionClubNFT instance to transfer ownership to the deployed InvitationController contract.

Print the addresses of the deployed contracts to the console.

Test Strategy:
The script must successfully deploy both contracts and set the ownership correctly when run against a local Hardhat network.

Task ID: 2.3
Title: Deploy and Verify on Testnet
Status: To Do
Dependencies: 2.2
Priority: High
Description: Perform the deployment to the Polygon Mumbai testnet and verify the source code on the block explorer.
Details:
Run in the terminal: npx hardhat run scripts/deploy.js --network mumbai. After deployment, use the 'hardhat-etherscan' plugin to verify both contracts on Polygonscan.

Test Strategy:
The contracts are active on the Mumbai network, and their source code is visible and verified on Polygonscan.

Task ID: 2.4
Title: Document Contract Artifacts
Status: To Do
Dependencies: 2.3
Priority: Medium
Description: Provide the backend team with the necessary information to interact with the deployed contracts.
Details:
Create a README.md file in the root of the contracts project. In this file, document the deployed contract addresses on Mumbai and provide the full JSON ABI files for both contracts.

Test Strategy:
The documentation is clear, complete, and allows a developer to instantiate the contracts using Ethers.js.

Phase 2: Backend Services & Intelligence Core
Epic 3: Secure Backend Foundation (Node.js on AWS)
Task ID: 3.1
Title: Set Up Node.js Project and AWS Infrastructure
Status: To Do
Dependencies: None
Priority: High
Description: Establish the foundation for the backend services using Infrastructure as Code.
Details:
Create a new Node.js project with Express.js. Use the AWS CDK (or Terraform) to define the core infrastructure: a new VPC with public and private subnets, an Application Load Balancer, an ECS Fargate cluster for the services, and an AWS Secrets Manager instance to store credentials.

Test Strategy:
The infrastructure can be successfully deployed to an AWS account via the cdk deploy command. The base Node.js service runs in Fargate and is accessible through the load balancer.

Task ID: 3.2
Title: Implement Service Wallet Authentication
Status: To Do
Dependencies: 3.1
Priority: High
Description: Create and secure the wallet identity that the backend will use to interact with the blockchain.
Details:
Generate a new Ethereum key pair. Store the private key securely in AWS Secrets Manager. Create a function in the Node.js service that retrieves this private key from Secrets Manager to initialize an Ethers.js wallet instance.

Test Strategy:
The backend service can load its wallet on startup without the private key being hardcoded. The service can successfully query its own balance on the Mumbai testnet.

Epic 4: Blockchain Service Layer
Task ID: 4.1
Title: Create BlockchainService
Status: To Do
Dependencies: 2.4, 3.2
Priority: High
Description: Abstract all smart contract interactions into a single, reusable service layer.
Details:
Create a service file blockchain.service.js. Use Ethers.js, the contract ABIs, and addresses to instantiate contract objects. Implement a function triggerInvite(candidateAddress) that generates a unique invite code, calls the issueInvite function on the InvitationController contract, and stores the code securely. Implement an API endpoint that the mobile app can call to get the necessary transaction data for the acceptInvite function.

Test Strategy:
The service can successfully issue an on-chain invitation. The API endpoint returns the correct data payload for a client to sign the acceptInvite transaction.

Epic 5: Real-time Meeting Ingestion
Task ID: 5.1
Title: Implement WebSocket Server and MeetingService
Status: To Do
Dependencies: 3.1
Priority: High
Description: Create the entry point for real-time audio streams from clients.
Details:
In the Node.js project, add the ws library. Create a WebSocket server. Create a meeting.service.js that, upon receiving a start_meeting signal from a client, establishes a streaming connection to the Google Cloud Speech-to-Text API. The service must forward audio chunks received from the client to the STT API.

Test Strategy:
The WebSocket server accepts connections. When audio data is sent, it is successfully forwarded to the Google Cloud STT API, and no errors are thrown.

Task ID: 5.2
Title: Process STT Transcripts
Status: To Do
Dependencies: 5.1
Priority: High
Description: Receive transcription results and pass them to the next stage of the pipeline.
Details:
In meeting.service.js, add a listener for the results from the STT API. As transcription results (interim and final) are received, push them to the RAG pipeline service for further processing.

Test Strategy:
Text transcripts are received from the STT service and successfully passed to the RAG service component.

Epic 6: RAG Pipeline and Knowledge Base
Task ID: 6.1
Title: Set Up Vector DB and Embedding Service
Status: To Do
Dependencies: 3.1
Priority: High
Description: Prepare the infrastructure for storing and generating vector representations of knowledge.
Details:
Create a Pinecone account and a vector index. In the Node.js project, create a vector.db.service.js to interact with the Pinecone API. Create an embedding.service.js that uses the Gemini API (text-embedding model) to convert text chunks into vector embeddings.

Test Strategy:
The backend can successfully generate an embedding for a string of text and store it in the Pinecone index.

Task ID: 6.2
Title: Implement RAG Ingestion Flow
Status: To Do
Dependencies: 5.2, 6.1
Priority: High
Description: Build the pipeline that ingests, processes, and stores knowledge from meetings.
Details:
Create a rag.service.js. This service will receive transcribed text from the MeetingService. Implement the logic to:

Split the text into meaningful chunks (chunking).

Call the EmbeddingService for each chunk.

Call the VectorDBService to upsert the text chunks and their corresponding embeddings into Pinecone.

Test Strategy:
Meeting transcripts are processed and stored as searchable vectors. A query in the Pinecone UI for a concept discussed in the meeting returns the correct text chunks.

Task ID: 6.3
Title: Implement Knowledge Base Query Function
Status: To Do
Dependencies: 6.2
Priority: High
Description: Create the function that allows the AI to retrieve relevant knowledge.
Details:
In rag.service.js, create a function queryKnowledgeBase(queryText). This function must:

Call the EmbeddingService to generate a vector for the queryText.

Use this vector to query the Pinecone index via the VectorDBService.

Return the most semantically similar text documents.

Test Strategy:
The function successfully retrieves relevant context from the vector database based on a text query.

Phase 3: The Member Experience (React Native App)
Epic 7: Project Setup & UI Foundation
Task ID: 7.1
Title: Initialize and Structure React Native Project
Status: To Do
Dependencies: None
Priority: High
Description: Create the skeleton of the mobile application.
Details:
Run in the terminal: npx react-native init DisruptionClubApp. Inside the project, create the following directory structure within a new /src folder: /components, /screens, /services, /db, /state.

Test Strategy:
The project is created, and the file structure is organized. The app runs successfully on an emulator/simulator.

Task ID: 7.2
Title: Build Main UI Screens
Status: To Do
Dependencies: 7.1
Priority: High
Description: Implement the user interface based on the provided wireframe.
Details:
Create the screen components for Login, Home (with the idea map placeholder), and Meeting Details. Implement the custom UI elements from the wireframe, including the 'Badge NFT' display area and the dark 'Aurora borea' style background. Use placeholder data.

Test Strategy:
The screens render correctly and visually match the wireframe. Navigation between screens works.

Epic 8: Offline-First Persistence (WatermelonDB)
Task ID: 8.1
Title: Install and Configure WatermelonDB
Status: To Do
Dependencies: 7.1
Priority: High
Description: Integrate the local database into the application.
Details:
Follow the official WatermelonDB installation guide for React Native. Install all necessary dependencies, including JSI for improved performance.

Test Strategy:
WatermelonDB is set up, and the application launches without any database-related errors.

Task ID: 8.2
Title: Define Database Schema and Models
Status: To Do
Dependencies: 8.1
Priority: High
Description: Create the data structure for the application within WatermelonDB.
Details:
Create the file /src/db/schema.js. Define the tables: users, meetings, nodes, and edges. The schema should include columns for IDs, content, types, and relationships (foreign keys). Create the corresponding model files in /src/db/models/.

Test Strategy:
The schema is defined, and WatermelonDB models are created. The app can successfully write and read a sample record to/from each table.

Epic 9: Wallet Integration & On-Chain Interaction
Task ID: 9.1
Title: Integrate WalletConnect
Status: To Do
Dependencies: 7.1
Priority: High
Description: Allow the app to connect to external mobile wallets for signing transactions.
Details:
Install the necessary libraries for WalletConnect v2 in React Native. Set up the WalletConnect provider at the root level of your application.

Test Strategy:
The app can initiate a WalletConnect connection and display a QR code or deep link. A connection can be established with a mobile wallet like MetaMask Mobile.

Task ID: 9.2
Title: Implement Onboarding and Login Flow
Status: To Do
Dependencies: 4.1, 9.1
Priority: High
Description: Manage the process of accepting invitations and authenticating members.
Details:
Create an Onboarding screen. Implement the flow:

User enters their invite code.

The app sends the code to the backend to get the acceptInvite transaction parameters.

The app uses WalletConnect to request the user to sign the transaction.

Upon success, implement a Login screen where the user signs a message to prove ownership of their wallet to gain access.

Test Strategy:
New members can join the club, and existing members can authenticate securely. The user's address and NFT details are stored in the local DB upon successful login.

Epic 10: The Idea Map Visualization
Task ID: 10.1
Title: Install Visualization Dependencies
Status: To Do
Dependencies: 7.1
Priority: High
Description: Add the SVG and D3 libraries to the project.
Details:
Run in the terminal: npm install react-native-svg d3-force and npm install --save-dev @types/d3-force.

Test Strategy:
The libraries are installed and linked correctly.

Task ID: 10.2
Title: Create the IdeaMap Component
Status: To Do
Dependencies: 8.2, 10.1
Priority: High
Description: Develop the React component that renders the interactive graph.
Details:
Create the component /src/components/IdeaMap.js. In the component:

Use WatermelonDB's APIs to fetch all nodes and edges records.

Initialize a d3-force simulation with this data.

On each 'tick' of the simulation, update the component's state with the new node positions.

Render the nodes and edges using the <Svg>, <Circle>, and <Line> components from react-native-svg.

Add gesture handlers for pan and zoom functionality.

Test Strategy:
The idea map renders on screen with mock data. Nodes move according to the force simulation. The user can pan and zoom the map.

Epic 11: Connectivity State Management
Task ID: 11.1
Title: Create ConnectivityManager
Status: To Do
Dependencies: 7.1
Priority: High
Description: Implement the central service for controlling network access.
Details:
Create a React context/service named ConnectivityManager. Use the @react-native-community/netinfo library to detect the physical network state. The manager should expose a state (e.g., isMeetingActive) and functions (startMeetingSession, endMeetingSession).

Test Strategy:
The application's connectivity state can be managed centrally. Toggling the state correctly enables/disables network-dependent features in the UI.

Task ID: 11.2
Title: Implement Offline Queue
Status: To Do
Dependencies: 8.2, 11.1
Priority: Medium
Description: Ensure user actions performed offline are saved and synced later.
Details:
Modify all services that make API calls. Before each request, check the ConnectivityManager state. If offline, instead of making the request, add the mutation (e.g., create a new node) to an offline_queue table in WatermelonDB. When the state changes to online, process and sync all items in the queue.

Test Strategy:
Actions performed while the device is in airplane mode are persisted locally. When connectivity is restored, the actions are successfully synced with the backend.

Phase 4: Advanced AI Orchestration (MCP)
Epic 12: MCP Server Implementation (Backend)
Task ID: 12.1
Title: Set Up MCP Server
Status: To Do
Dependencies: 3.1, 6.3
Priority: High
Description: Configure the MCP server on the backend to expose tools to the AI.
Details:
In the Node.js project, install the MCP server SDK. Create an mcp.server.js that initializes a new MCP server. Expose the following tools: queryKnowledgeBase(query: string), getIdeaMap(userId: string), updateIdeaMap(userId: string, operations: Operation[]).

Test Strategy:
The MCP server is running and can receive connections from an MCP client. The exposed tools are listed when queried.

Epic 13: Generative AI Workflow
Task ID: 13.1
Title: Develop System Prompt for Gemini
Status: To Do
Dependencies: 12.1
Priority: High
Description: Define the role and instructions for the AI agent.
Details:
Create a prompt file gemini-system-prompt.txt. The system instruction should be: "You are the Scribe of the Disruption Club. Your role is to listen to meeting transcripts, synthesize new information with existing knowledge, and update the members' idea maps. Use the provided tools to achieve this goal."

Test Strategy:
The prompt is clear, concise, and guides the model toward the desired behavior.

Task ID: 13.2
Title: Implement Agentic AI Loop
Status: To Do
Dependencies: 13.1
Priority: High
Description: Orchestrate the interaction between Gemini and the MCP tools.
Details:
In the backend, create an ai.agent.service.js. This service will be triggered by new transcript data. The main loop must:

Send the latest transcript chunk to Gemini with the list of available MCP tools.

Gemini decides which tool to call (e.g., queryKnowledgeBase).

The backend executes the tool and returns the result to Gemini.

Gemini uses the new context to formulate a series of operations (e.g., updateIdeaMap).

The backend executes the final tool, updating the database.

Test Strategy:
The AI can autonomously use the tools to analyze transcripts and update a member's idea map in the database. The changes are reflected correctly.

Phase 5: Hardening, Deployment & Operations
Epic 14: End-to-End Security Implementation
Task ID: 14.1
Title: Implement Security Checklist
Status: To Do
Dependencies: 3.1
Priority: Critical
Description: Apply security best practices across the entire stack.
Details:
Implement each item from the security checklist defined in the project plan. This includes:

Configure VPC network segmentation.

Add AWS WAF to the Application Load Balancer.

Enforce least-privilege IAM roles.

Encrypt all data at rest and in transit (TLS 1.2+).

Sanitize all user input on the backend to prevent injection attacks.

Implement rate limiting on all public API endpoints.

Enable full audit logging with AWS CloudTrail and VPC Flow Logs.

Test Strategy:
Conduct a security audit (manual or automated) to verify that all checklist items are implemented correctly. Penetration testing should be performed before launch.

Epic 15: Private App Distribution
Task ID: 15.1
Title: Prepare for iOS Enterprise Distribution
Status: To Do
Dependencies: 7.1
Priority: High
Description: Fulfill requirements and set up certificates for private iOS distribution.
Details:
Initiate the application process for the Apple Developer Enterprise Program. Once approved, generate an In-House distribution certificate and provisioning profile. Configure Xcode (via the React Native build process) to sign the release build with these credentials.

Test Strategy:
A signed .ipa file can be generated and successfully installed on a registered device.

Task ID: 15.2
Title: Prepare for Android Distribution
Status: To Do
Dependencies: 7.1
Priority: High
Description: Generate the signing key for the Android application.
Details:
Use keytool to generate an upload keystore. Store the keystore and its credentials securely (e.g., AWS Secrets Manager). Configure the android/app/build.gradle file to use this keystore for release builds.

Test Strategy:
A signed .apk or .aab file can be generated.

Task ID: 15.3
Title: Implement Distribution Server
Status: To Do
Dependencies: 15.1, 15.2
Priority: High
Description: Create a secure location for members to download the application.
Details:
Set up a private S3 bucket on AWS. Create a backend API endpoint that, for an authenticated user, generates a time-limited, pre-signed S3 URL to download the .ipa (iOS) or .apk (Android) file.

Test Strategy:
Authenticated members can successfully download the application. Unauthenticated users cannot access the files.
