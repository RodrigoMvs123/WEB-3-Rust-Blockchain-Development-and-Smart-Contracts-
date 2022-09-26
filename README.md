# WEB-3-Rust-Blockchain-Development-and-Smart-Contracts-


https://www.youtube.com/watch?v=hDfkyF8U-pw
https://web3.freecodecamp.org/web3  

https://github.com/freeCodeCamp/web3-curriculum/tree/544b18f451f063438a73e49e02d509f8fb79521f

https://www.totvs.com/blog/gestao-juridica/smart-contracts/

https://www.rust-lang.org/pt-BR/

https://www.blockchain.com/
https://learn.microsoft.com/en-us/training/paths/ethereum-blockchain-development/

##

foundraising-contract 
on-transaction.js 
const { addTransaction, updateContractState } = (await import('./blockchain-helpers.js'));

const contractState = JSON.parse(process.env.CONTRACT_STATE);
const contractAddress = process.env.CONTRACT_ADDRESS;
const privateKey = process.env.PRIVATE_KEY;
const creatorAddress = process.env.CREATOR_ADDRESS;
const transaction = JSON.parse(process.env.TRANSACTION);
// Add your code below

contractState.transaction.push(transaction);
contractState.raised += transaction.amaunt;
updateContractState (contractAddress, contractState);

if (contractState.raised => 150) {
    addTransaction (privateKey, creatorAddress, contractState.raised)
    contractState.status ="closed"

}

updateContractState (creatorAddress, contractState);

##

on-new-block.js
const { addTransaction, updateContractState } = (await import('./blockchain-helpers.js'));

const contractState = JSON.parse(process.env.CONTRACT_STATE);
const contractAddress = process.env.CONTRACT_ADDRESS;
const privateKey = process.env.PRIVATE_KEY;
const creatorAddress = process.env.CREATOR_ADDRESS;
const blockchainLength = process.env.BLOCKCHAIN_LENGTH;
// Add your code below

if(blockchainLength >= 7 && contractState.status !=) 'closed' ) {
    contractState.addTransactions.forEach(tx => {
        addTransaction{privateKey, tx.fromAddress, tx.amaunt}
    });
    
    contractState.status = 'closed';
    updateContractState (creatorAddress, contractState);
}


##

