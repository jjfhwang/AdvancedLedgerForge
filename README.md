# AdvancedLedgerForge: A Decentralized, Immutable Ledger for Enhanced Data Integrity

AdvancedLedgerForge is a TypeScript-based project focused on creating a robust and decentralized immutable ledger using Merkle tree anchoring, smart contract deployment, consensus algorithm simulations, and advanced cryptographic primitives. It aims to provide a secure and transparent data storage solution suitable for a wide range of applications, including supply chain management, auditing, and identity verification. The project facilitates the creation of tamper-proof records while providing a framework for exploring and implementing cutting-edge blockchain-inspired technologies without the overhead of a full-fledged blockchain.

This repository serves as a research and development platform for exploring the practical applications of Merkle trees, consensus mechanisms, and cryptographic techniques in building trustless data storage systems. The core concept revolves around anchoring the root hash of a Merkle tree, representing a batch of transactions or data entries, to a secure, immutable storage medium, such as a smart contract deployed on a public blockchain or a distributed database. This anchoring mechanism ensures the integrity of the data by allowing anyone to verify that the data has not been tampered with since the anchor was created. The simulation components allow developers to test different consensus strategies to determine the best fit for their application's needs.

AdvancedLedgerForge is not intended to be a production-ready blockchain. Instead, it provides the tools and framework for developers to experiment with the building blocks of decentralized ledgers. The use of TypeScript allows for a type-safe and maintainable codebase, while the modular architecture facilitates easy integration of different components and customization to specific use cases. The repository also includes detailed documentation and examples to guide developers through the process of deploying smart contracts, simulating consensus algorithms, and utilizing cryptographic primitives. The project aims to simplify the complexities involved in creating secure and trustworthy data storage solutions.

## Key Features

*   **Merkle Tree Implementation:** A highly optimized Merkle tree data structure implemented in TypeScript, supporting efficient calculation of Merkle roots and generation of Merkle proofs for data integrity verification. The implementation uses a hash function (configurable) for creating node hashes.
*   **Smart Contract Deployment:** Functionality to deploy anchoring smart contracts (written in Solidity) to Ethereum-compatible blockchains. Includes scripts for compiling, deploying, and interacting with the contracts using libraries like ethers.js or web3.js. The anchoring contract stores the Merkle root hash and allows verification of Merkle proofs against it.
*   **Consensus Algorithm Simulations:** Simulation environment for various consensus algorithms, such as Proof-of-Work (PoW), Proof-of-Stake (PoS), and Delegated Proof-of-Stake (DPoS). Allows developers to experiment with different parameters and evaluate their performance in a simulated distributed network environment.
*   **Cryptographic Primitive Explorations:** Implementations and examples of various cryptographic primitives, including digital signatures (e.g., ECDSA), hash functions (e.g., SHA-256, Keccak-256), and encryption schemes (e.g., AES). These primitives are used for securing the ledger and ensuring data privacy.
*   **Data Integrity Verification:** Tools and functions for verifying the integrity of data stored in the ledger using Merkle proofs. This allows anyone to independently verify that the data has not been tampered with since it was anchored to the blockchain. The verification process involves recalculating the Merkle root from the provided proof and comparing it to the anchored root hash.
*   **TypeScript Type Safety:** The entire codebase is written in TypeScript, providing static type checking and improved code maintainability. This helps prevent runtime errors and makes the codebase easier to understand and modify.
*   **Modular Architecture:** The project is designed with a modular architecture, allowing developers to easily extend and customize the functionality to their specific needs. Components such as the Merkle tree implementation, consensus simulation environment, and smart contract deployment scripts can be used independently or integrated into larger systems.

## Technology Stack

*   **TypeScript:** The primary programming language used for developing the core logic of the ledger, providing type safety and improved code maintainability.
*   **Solidity:** Used for writing smart contracts deployed on Ethereum-compatible blockchains for anchoring Merkle root hashes.
*   **Ethers.js/Web3.js:** JavaScript libraries for interacting with Ethereum blockchains, used for deploying and interacting with smart contracts.
*   **Node.js:** JavaScript runtime environment for executing TypeScript code and running scripts.
*   **Hardhat:** Ethereum development environment used for compiling, testing, and deploying smart contracts.
*   **Merkle Tree Libraries:** Optimized libraries for efficient Merkle tree construction and proof generation.

## Installation

1.  Clone the repository:

    git clone https://github.com/jjfhwang/AdvancedLedgerForge.git

2.  Navigate to the project directory:

    cd AdvancedLedgerForge

3.  Install dependencies:

    npm install

4.  Install Hardhat globally:

    npm install --global hardhat

## Configuration

1.  Create a `.env` file in the project root directory.

2.  Define the following environment variables:

    *   `BLOCKCHAIN_NETWORK`: The Ethereum network to deploy the smart contract to (e.g., "localhost", "ropsten", "mainnet").

    *   `PRIVATE_KEY`: Your Ethereum account's private key for deploying the smart contract.

    *   `INFURA_API_KEY` (Optional): Your Infura API key for connecting to Ethereum networks. Required for networks other than localhost.

    *   `NODE_URL` (Optional): Alternative URL to connect to the blockchain node. This can be useful for using a custom or private node.

## Usage

1.  **Deploying the Smart Contract:**

    npx hardhat compile

    npx hardhat run scripts/deploy.ts --network [BLOCKCHAIN_NETWORK]

    Replace `[BLOCKCHAIN_NETWORK]` with the name of the network defined in your `.env` file.

2.  **Creating a Merkle Tree:**

    import { MerkleTree } from './src/merkle-tree'; // Adjust path as necessary

    const leaves = ['data1', 'data2', 'data3', 'data4'];
    const tree = new MerkleTree(leaves);
    const rootHash = tree.getRoot();
    console.log('Merkle Root:', rootHash);

3.  **Generating a Merkle Proof:**

    const leafIndex = 2; // Index of the leaf for which to generate the proof
    const proof = tree.getProof(leafIndex);
    console.log('Merkle Proof:', proof);

4.  **Verifying a Merkle Proof:**

    import { verifyProof } from './src/merkle-tree'; // Adjust path as necessary

    const leaf = 'data3'; // The data corresponding to the leaf
    const isValid = verifyProof(proof, leaf, rootHash);
    console.log('Proof is valid:', isValid);

5. **Consensus Simulation:**
  Run the consensus simulation scripts located in the 'simulation' directory. Each simulation comes with its own configuration file allowing for experimentation with parameters. Example:
  node ./simulation/pow_simulation.js --config ./simulation/pow_config.json

## Contributing

We welcome contributions to AdvancedLedgerForge! Please follow these guidelines:

*   Fork the repository and create a branch for your feature or bug fix.

*   Write clear and concise commit messages.

*   Submit a pull request with a detailed description of your changes.

*   Ensure that your code adheres to the project's coding style and passes all tests.

## License

This project is licensed under the MIT License. See the [LICENSE](https://github.com/jjfhwang/AdvancedLedgerForge/blob/main/LICENSE) file for details.

## Acknowledgements

We would like to thank the open-source community for their contributions to the technologies used in this project. Special thanks to the developers of TypeScript, Solidity, Ethers.js, Web3.js, and Hardhat.