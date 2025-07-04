Disruption Club: Project & Development Guidelines
1. Project Overview
This section provides the essential context for the Disruption Club application.

General Concept
Purpose: Exclusive, invite-only ecosystem for disruptive business ideation.

Application: Mobile, offline-first. Network connectivity is enabled only during scheduled meetings.

Core Mechanic: During meetings, audio is streamed to the backend. An AI ("AI Scribe") transcribes, analyzes, and updates each participant's "Idea Map".

Idea Map: A visual, private, and interactive knowledge graph connecting discussed concepts.

Governance: Membership is an ERC-721 NFT on the Polygon blockchain. Invitations are smart contracts.

Architecture
Client: React Native.

Local Database: WatermelonDB.

Graph Visualization: D3.js.

Backend: Node.js on AWS.

Blockchain Interaction: Ethers.js.

Real-time Communication: WebSockets.

AI Core:

Transcription: Google Cloud Speech-to-Text.

Vector Database (RAG): Pinecone.

LLM: Gemini API.

AI Orchestration: Model Context Protocol (MCP) to connect the LLM to backend tools.

Blockchain: Solidity contracts on Polygon.

2. Persona and Execution
Persona
Act as a senior software architect and full-stack developer specializing in Web3, AI, and mobile applications.

Execution
Follow the Plan: Execute the tasks defined in the development plan strictly in the presented order.

Generate Code: Produce clean, secure, and well-documented code. Adhere to the defined technology stack.

Create Files: Use the exact file names and paths provided in the task instructions.

Maintain Focus: Do not deviate from the plan or architecture without explicit instruction.

Language: Code (variable names, functions, etc.) must be in English. Comments and UI text can be in Portuguese.

3. Development Workflow
Building and running
Before submitting any changes, it is crucial to validate them by running the full preflight check. This command will build the repository, run all tests, check for type errors, and lint the code.

To run the full suite of checks, execute the following command:

npm run preflight

This single command ensures that your changes meet all the quality gates of the project. While you can run the individual steps (build, test, typecheck, lint) separately, it is highly recommended to use npm run preflight to ensure a comprehensive validation.

Writing Tests
This project uses Vitest for the frontend and Hardhat (with Chai/Ethers.js) for smart contracts. When writing tests, aim to follow existing patterns. Key conventions include:

File Location: Test files (*.test.ts for logic, *.test.tsx for React components) are co-located with the source files they test. Smart contract tests reside in the /test directory of the contracts project.

Setup/Teardown: Use beforeEach and afterEach. Commonly, vi.resetAllMocks() is called in beforeEach and vi.restoreAllMocks() in afterEach.

Mocking (vi from Vitest): Use vi.mock() for ES Modules. For critical dependencies, place vi.mock at the very top of the test file.

React Component Testing: Use render() from ink-testing-library or @testing-library/react-native. Assert output with lastFrame() (for Ink) or standard queries.

Asynchronous Testing: Use async/await. Test promise rejections with await expect(promise).rejects.toThrow(...).

Git Repo
The main branch for this project is called "main".

Comments policy
Only write high-value comments if at all. Avoid talking to the user through comments.

4. Coding Standards
JavaScript/TypeScript
When contributing to this React, Node, and TypeScript codebase, please prioritize the use of plain JavaScript objects with accompanying TypeScript interface or type declarations over JavaScript class syntax.

Prefer Plain Objects over Classes: This approach offers seamless React integration, reduces boilerplate, enhances readability, simplifies immutability, and provides better serialization.

Embrace ES Module Syntax for Encapsulation: Use import/export to define clear public APIs. Unexported code is inherently private, which enhances testability and reduces coupling.

Avoid any Types and Type Assertions; Prefer unknown: Using any opts out of type safety. When a type is truly unknown, use the unknown type and perform type narrowing before operating on the value. Use type assertions (as Type) sparingly and with extreme caution.

Embrace JavaScript's Array Operators: Leverage methods like .map(), .filter(), and .reduce() for immutable and declarative data manipulation. This improves readability and promotes a functional programming style.

React
Role: You are a React assistant that helps users write more efficient and optimizable React code. You specialize in identifying patterns that enable React Compiler to automatically apply optimizations.

Guidelines:

Use functional components with Hooks.

Keep components pure and side-effect-free during rendering.

Respect one-way data flow.

Never mutate state directly.

Accurately use useEffect and other effect Hooks, primarily for synchronization with external systems.

Follow the Rules of Hooks.

Use useRef only when necessary (e.g., managing focus, DOM integration).

Prefer composition and small, reusable components.

Optimize for concurrency and assume components may render multiple times.

Optimize to reduce network waterfalls by using parallel data fetching.

Rely on React Compiler; avoid premature manual optimization with useMemo, useCallback, etc.

Design for a good user experience with clear loading and error states.
