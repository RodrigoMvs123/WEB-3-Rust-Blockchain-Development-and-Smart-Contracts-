# WEB-3-Rust-Blockchain-Development-and-Smart-Contracts-


https://www.youtube.com/watch?v=hDfkyF8U-pw
https://web3.freecodecamp.org/web3  

https://github.com/freeCodeCamp/web3-curriculum/tree/544b18f451f063438a73e49e02d509f8fb79521f

##
https://raw.githubusercontent.com/RodrigoMvs123/WEB-3-Rust-Blockchain-Development-and-Smart-Contracts-/main/README.md
##
https://github.com/RodrigoMvs123/WEB-3-Rust-Blockchain-Development-and-Smart-Contracts-/blame/main/README.md
##

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

Wallets.json 
{
  "Me": {
    "publicKey": "047f18310ca11477a0ccd328df42d7ff9cd068ac6816d9c76535b0fe1b7b45ab7312ff6167964c050e66c6db00642c5492",
    "privateKey": "477203cb2cfb900466f1ca7d79335aa3775857a333cdd0ef"
  },
  "You": {
    "publicKey": "0412bb6129d866a633aa62270e84be8630ebf803a64f6879a5ac08f12cde2aeca2eb272481fcc742d568aad80e44ba68c5",
    "privateKey": "9fa063a824dd98371d1194f2360cd417509050e68f76c769"
  },
  "I": {
    "publicKey": "041608a1e5bc12c505bb60b52bf64ca40f816f14acc9e31bfa21c6c7ba435a215a8f54ba49ce767b950cfdfea2efe261a9",
    "privateKey": "182ea9005fedd24b3a4d93c84936ce4400380d85949743"
  }
} 

##
Transactions.json
[
    {
        "fromAddress": null,
        "toAddress": 047f18310ca11477a0ccd328df42d7ff9cd068ac6816d9c76535b0fe1b7b45ab7312ff6167964c050e66c6db00642c5492
        "amount": 50
    },
    {
        "fromAddress": 0412bb6129d866a633aa62270e84be8630ebf803a64f6879a5ac08f12cde2aeca2eb272481fcc742d568aad80e44ba68c5
        "toAddress": 
        "amount"
        "hash": 
        "signature":
    }
        "fromAddress": 
        "toAddress": "041608a1e5bc12c505bb60b52bf64ca40f816f14acc9e31bfa21c6c7ba435a215a8f54ba49ce767b950cfdfea2efe261a9"
        "amount": 50 

]

##

Contract-wallets.json
{
    "fundrasing-contract" {
        "publicKey": 
        "privateKey": 
    } 
}

##
Get-address-info.js
import {
  getAddressBalance,
  getWalletAddressFromName
} from './blockchain-helpers.js';

const nameOfAddress = process.argv[2];

const wallet = getWalletAddressFromName(nameOfAddress);
const addressBalance = getAddressBalance(wallet.publicKey);

console.log(
  `\nThe public address for ${nameOfAddress} is: ${wallet.publicKey}`
);
console.log(`${nameOfAddress} has a balance of ${addressBalance}`);

##

build-a-peer-to-peer-network 
Index.js 
import { getTransactions, writeTransactions } from './blockchain-helpers.js';
import { getKnownPeerAddresses } from './network-helpers.js';

import WebSocket, { WebSocketServer } from 'ws';
import dotenv from 'dotenv';
import { Socket } from 'dgram';
import { SocketAddress } from 'net';
import { connected } from 'process';
dotenv.config();

const knownPeers = getKnownPeerAddresses();
const MY_PORT = process.env.PORT;
const MY_ADDRESS = `ws://localhost:${MY_PORT}`;
const transactions = getTransactions();
const openedSockets = [];
const connectedAddresses = [];
const attemptingToConnectAddresses = [];
// Add your code below

const myServer = new WebSocketServer ({port: MY_PORT});
myServer.on('connection', Socket =>{
    console.log('connection recieved');
    Socket.on ('message', dataString => {
    console.log ('message recieved': + dataString);
    const message = JSON.parse(dataString);
    message.data.forEach(address => connect(address));
    
    });
});

function connect (address) {
    if(address != MY_ADDRESS && !attemptingToConnectAddresses.includes(address) && !connectedAddresses(includesadrress)) {
    attemptingToConnectAddresses.push(address);
    console.log('attempting to connect to' + address);
}

    const socket = new WebSocket (address);
    socket.on('open', ()=> {
    console.log('connection to ' + address + ' opened');
        attemptingToConnectAddresses.splice(attemptingToConnectAddresses.indexOf (address), ]);
        connectedAddresses.push(address);
        socket.send(
            JSON.stringify{(TYPE:'HANDSHAKE', data: [MY_ADDRESS, ...connectedAddress] }))); 

    });

    socket.on('close', () => {
           console.log ('connection to' + adrress + ' closed');
           attemptingToConnectAddresses.splice(Connected    Addresses.indexOf (address), 1);
    });

    socket.on('error', () => {
          console.log('error connecting to ' + address);
          const index = attemptingToConnectAddresses.indexOf (address)
          if (index => 0) {
          attemptingToConnectAddresses.splice(index, 1);
          }
    )};


known.forEach(peer =>connect(peer));


##
Build a Web3 Client-Side Package for Your Dapp

index.js 
import { json } from "body-parser";

export default class Web3 {
    constructor(provider){
        this.address = null;
        this.provider = new URL(provider);
    }
    setClientAddress(address){
        this.address = address;

    }
    async getBalance(address){
        const body = {
        from: from || this.address, to, amount
    };
        const res = await fetch('${this.provider.href}transfer', 
        {
            method: 'POST', 
            headers: {
                'Content-Type': 'application/json' 
            },
            body: JSON.stringify(body)
        });
        const response = await res.json();
        if(response.error){
            throw new Error(response.error);

        }
        return response.result;
    }
    initSmartContract(idl){
        const smartCotract = {};
        for (const instruction of idl.instructions) {
            smartCotract[instruction.handle] = async (...args) => {
                const rpCall = {
                    id: idl.id,
                    method: instructionhandle,
                    args,  
                }
                return await this.call(rpCall);
            }
        }
        return smartCotract;
       }
    async getBalance(address) {
       
    }
    async transfer({from, to, amount }) {

    }
}

const web3 = new Web3();
console.log(web3);

web3.setClientAddress('Tom'); 
console.log(web3.address);
const res = await web3.call({
    id: 0,
    args: [],
    method: 'test',
});

console.log(res);

##
Build a Smart Contract in Rust
lib.rs
}
    };
    Ok(JsValue: : from serde(&context))
}
 
#[wasm_bindgen]
pub fn set_click(context: JsValue, address: String) -> Result<JsValue, JsError> {
    let context: Context = context.into_serde()?;
    let mut account = &mut context.base_account;
    account.total_clicks += 1;
    account.clickers.push(address);

    Ok(JsValue:: from serde(&context).unwrap())
}

#[wasm_bindgen]
pub fn get_contract_account(context: JsValue) -> Result<JsValue,JsError> {
    let context: Context = context.into_sorde()?;
    let account = &context.base_account;
    Ok(JsValue::from_serde(&account).unwrap())
}


// Do not edit below this line!
#[cfg(test)]
mod tests {
    use serde::{Serialize, Deserialize};

    #[test]
    fn account_struct_is_defined() {
        use super::Account;
        let _acc: Account;
        assert!(true, "This test should compile to pass");
    }
    #[test]
    fn account_struct_has_total_clicks() {
        use super::Account;
        fn _total_clicks(acc: Account) -> u64 {
            acc.total_clicks
        }
        assert!(true, "This test should compile to pass");
    }
    #[test]
    fn account_struct_has_clickers() {
        use super::Account;
        fn _clickers(acc: Account) -> Vec<String> {
            acc.clickers
        }
        assert!(true, "This test sho// Write your code here:

use wasm_bindgen: : prelud: :*; 
use serde: : {Deserialize, Serialize}; 

#[derive(Serialize, Deserialize)]

pub struct Account {
    pub total_clicks: u64,
    pub clickers: Vec<String>
}

#[derive(Serialize, Deserialize)]
pub strucut Context {
    pub base_account: Account
}

#[wasm_bindgen]
pub fn initialise() -> Result<JsValue, JsError> {
    let context = Context {
        base_account: Account {
            total_clicks: 0,
            clickers: vec![]
        uld compile to pass");
    }
    #[test]
    fn account_struct_is_serde() {
        use super::Account;
        fn account_serde<'a, T>(_acc: T)
        where T: Serialize + Deserialize<'a>
        {
            assert!(true, "This test should compile to pass");
        }
        let new_acc = Account {
            total_clicks: 10,
            clickers: vec![String::from("Test")]
        };
        account_serde(new_acc);
    }
    #[test]
    fn context_struct_is_defined() {
        use super::Context;
        let _con: Context;
        assert!(true, "This test should compile to pass");
    }
    #[test]
    fn context_struct_has_base_account() {
        use super::{Account, Context};
        fn _base_account(con: Context) -> Account {
            con.base_account
        }
        assert!(true, "This test should compile to pass");
    }
    #[test]
    fn context_struct_is_serde() {
        use super::{Context, Account};
        fn context_serde<'a, T>(_acc: T)
        where T: Serialize + Deserialize<'a>
        {
            assert!(true, "This test should compile to pass");
        }
        let new_acc = Account {
            total_clicks: 10,
            clickers: vec![String::from("Test")]
        };
        let new_con = Context {
            base_account: new_acc
        };
        context_serde(new_con);
    }
}


##
