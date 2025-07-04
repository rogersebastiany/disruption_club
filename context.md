# Disruption Club Application Context

This document summarizes the development context for the "Disruption Club" application, based on the initial project files.

## Project Goal

The primary goal is to build an exclusive, invite-only mobile application named "Disruption Club." It is designed for a select group of high-impact individuals to foster and collaborate on disruptive business ideas. The core experience revolves around AI-driven analysis of meetings, which automatically updates a personal "idea map" for each member.

## Core Architectural Pillars

1.  **Decentralized Identity & Governance:** Membership is represented by an ERC-721 NFT on the Polygon blockchain. Access and invitations are managed via smart contracts.
2.  **AI-Native Experience:** Google's Gemini model is the central engine for the application. It handles real-time meeting transcription, knowledge synthesis, and automatically updates the members' idea maps.
3.  **Offline-First Resilience:** The React Native application is designed to be fully functional without an internet connection. Connectivity is only active during scheduled meetings to sync data.
4.  **Zero Trust Security:** A "secure enclave" model will be implemented on AWS to protect sensitive meeting data while allowing for the necessary AI processing, as end-to-end encryption is not feasible for this use case.

## Technology Stack

*   **Mobile:** React Native
*   **Local Database:** WatermelonDB (for offline-first relational data)
*   **Backend:** Node.js on AWS (Fargate)
*   **Blockchain:** Polygon (Smart Contracts in Solidity)
*   **AI:** Google Gemini, Google Cloud Speech-to-Text
*   **Vector Database:** Pinecone (for RAG pipeline)
*   **Idea Map Visualization:** React Native SVG + D3.js

## Development Status

*   **Planning:** A comprehensive `development_plan.md` and a detailed `tasks.md` have been created.
*   **Assets:** A `wireframe disruption club.jpg` has been provided to guide UI development.
*   **Version Control:** A local Git repository has been initialized, containing all initial project documents.
*   **Next Step:** The immediate next action is to begin Phase 1 of the development plan: "Decentralized Identity & Governance Foundation," starting with the setup of the Hardhat environment for smart contract development (Task 1.1).
