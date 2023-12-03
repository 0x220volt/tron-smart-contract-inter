# tron-smart-contract-inter       
This script provides a practical interface for deploying, interacting with, and querying information from smart contracts on the Tron blockchain.
const TronWeb = require('tronweb');

const tronWeb = new TronWeb({
    fullNode: 'https://api.trongrid.io',
    solidityNode: 'https://api.trongrid.io',
    eventServer: 'https://api.trongrid.io',
    privateKey: 'your_private_key_here', // Replace with your actual private key
});

async function deploySmartContract() {
    const contractSource = 'your_contract_source_code_here'; // Replace with the actual contract source code

    const contract = await tronWeb.contract().new({
        abi: [], // Replace with the ABI of your smart contract
        bytecode: contractSource,
        feeLimit: 100000000,
        callValue: 0,
        userFeePercentage: 100,
        originEnergyLimit: 10000000,
    });

    console.log(`Smart Contract deployed with address: ${contract.address}`);
}

async function interactWithSmartContract() {
    const contractAddress = 'smart_contract_address_here'; // Replace with the actual address of your deployed smart contract

    const contract = await tronWeb.contract().at(contractAddress);

    // Call contract functions or send transactions here
}

async function queryContractInfo() {
    const contractAddress = 'smart_contract_address_here'; // Replace with the actual address of your deployed smart contract

    const contract = await tronWeb.contract().at(contractAddress);

    // Query contract information here
}

// Example Usage
deploySmartContract()
    .then(() => interactWithSmartContract())
    .then(() => queryContractInfo())
    .catch((error) => console.error(error));
