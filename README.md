## Spring 2023 Developing Blockchain Use Cases Lab 3                             
### Carnegie Mellon University                  
### Due: 11:59 PM, Monday, April 24, 2023                                
### 10 Points

### Lab Assistance provided by Michael McCarthy, Atharva Joshi, and Nikita Vignesh Kumar
### See Office Hours on Canvas

**Learning Objectives:** The object of Part A is to introduce the student to an Ethereum wallet (Enkrypt) and crowd sale contracts. The objective of Part B is to experiment with the Algorand Wallet and its Testnet API.

### Part A. Using the Remix web IDE and the Enkrypt wallet

1. In Lab 1, you installed Ganache and you will be using it again here. Run Ganache Quickstart and leave it running for the remainder of Part A. This is, essentially, a client server application. Ganache is the server and is used to hold a single instance blockchain. We will visit the server with two clients - the Remix application running in a browser and an Enkript wallet, also running in a browser. One of these tools, the Remix IDE, is useful for smart contract development and testing. The other of these tools, the Enkript wallet, is for everyday users to transfer tokens and cryptocurrencies.

2. We will be using the Remix IDE to compile Solidity source code. This smart contract code will implement a crowd sale contract. We will also use Remix to deploy byte code to the Ethereum Virtual Machine (EVM) running on Ganache. Using Remix and Enkrypt, we will interact with the contract using JSON-RPC. Remix runs in your browser. You don't need to install it.

[Remix may be found here](https://remix.ethereum.org/)

[Encrypt may be found here](https://www.myetherwallet.com/wallet/create)

Using Google Chrome, select Install Enkrypt Browser Extension.

### Notes on using the wallet:

You will need to keep a copy of the word list so that you can regenerate your private keys.

We only want one Enkrypt wallet installed on our computer. If you have installed more than
one wallet, delete them both and install only one. The system becomes unstable with more
than one wallet.

If you restart Ganache, you may need to delete and re-install the wallet. Best to start with
a fresh wallet and a fresh copy of Ganache.

On Ganache, select the icon on the top right and just to the right of SWITCH. Choose
Server and set HOSTNAME to All Interfaces. Select restart.

These are my notes when running Enkrypt on Chrome to connect to Ganache:

a. Choose Manage Networks at the bottom left of the wallet.  

b. Click the icon to the right of the search bar.  

c. Click Custom Network.  

d. Use these setting (the name "Ganache" may change to "Geth Testnet", no worries):  

```
Network Name:   Ganache
New RPC URL:    HTTP://0.0.0.0:7545
Chain ID:       5777
```

e. Under Manage Networks: Turn them all off except for Ganache.  

f. Ganache should now display on your dashboard side menu.  

g. Click the EVM Account drop down arrow.  

h. Select Import Account from another Wallet.  

i. We need to take private keys from Ganache and import them into the wallet. Import the first account from Ganache into Enkrypt. In Ganache, you can view the key
icon to the right of the public key of each account, click on the key icon and you can
view the private key of the account. Copy the private key and use it for importing
the account into Enkrypt. Give this account the name Alice. Do the same for Bob, Charlie, and Donna.
You will use these accounts to participate in the crowd sale and execute transactions with ETH and CMU Tokens.

3. Run Remix in the same browser where you installed your Enkrypt wallet. In Remix, create a Solidity file and name it "Lab3PartA.sol". [Paste the code at this link](../../blob/master/PartA/Lab3PartA.sol) into Lab3PartA.sol and click on "Select new compiler version" dropdown and select "0.4.18+commit". The contract should compile successfully and you may ignore the warnings. Select your provider as "Dev Ganache Provider" and connect to Ganache on port 7545. You will deploy the contract soon.

8. All 10 accounts should be visible (near the top left) in Remix. Use Remix to select the "Alice" account - make sure her address appears in the Remix account box. Using Remix, compile the code and click on the box containing"ApproveAndCallFallBack" and select "CMUToken". That is, we do not want to deploy ApproveAndCallFallBack but we do want to select and deploy "CMUToken".

Next click on "Deploy" and your crowd sale contract will be deployed on the blockchain through Alice's account. If you don't get an error message, and the contract gets deployed successfully, you should be able to view "CMUToken" along with its address under "Deployed Contracts" in Remix. You should also notice that Alice paid for that deployment by looking at her account on Ganache or Enkrypt. When working with tokens, we need to provide to the Enkrypt wallet the address of the token contract.

#### Part A Problems

Note: You will be working with a crowd sale contract and steps 9 through 17 should be completed without delay - early players will get their tokens at a discount. Note too that Charlie delays his purchase in question 18. Be sure to review the contract to see how time is handled. You need to actually delay Charlie's purchase. That is, you need to take a break from this lab and come back to it later. Otherwise, Charlie will be getting the tokens at the discount rate.

9. Alice sends 10 ETH to Donna. She does not need a contract to do this. She only uses her wallet to perform a send operation. Using Ganache, copy Donna's public address to the clipboard. Paste it into Alice's wallet to perform the transfer.

10. Alice sends 10 ETH to Bob and Charlie too. That is 10 ETH per person.

11. Donna sends 5 ETH to Alice and Bob (Alice and Bob both receive 5 ETH.)

12. At this point, take a screenshot of the 10 accounts on Ganache.

13. Since the CMU Token contract implements the ERC 20 standard interface, the Enkrypt wallet is able to automatically track CMU Tokens. In this step, we will inform the wallet that we are interested in tracking these tokens. In Remix, click on the "Copy value to clipboard" icon next to the contract address. This will be used to add the CMU Token to the Enkrypt wallet. You might also take this address directly from Ganache. In Enkrypt, expand the view of Alice's account and click on "Add Custom Token" to add the CMU Token to her account. Paste the copied address in the "Contract Address" and click on "Add Token". You have now successfully added CMU Tokens to the wallet. Bob, Charlie, and Donna also have these tokens.

 To repeat, the wallet is able to handle these tokens because the contract developer implemented the methods defined by a standard interface and the wallet developer was ably to rely on these methods being there.

14. Each of our players (Alice, Bob, Charlie, and Donna) buys 5 ETH worth of CMUC from
the contract. After the purchases, take a screenshot of each of these wallets (showing ETH and CMUC). This is done by sending 5 ETH to the contract. So, for each account, select the account and then perform a send operation. The destination of this send operation is the contract address. The contract has a function marked as "payable". After the purchases, take a screenshot of each of these four accounts (showing ETH and CMUC).

15. Alice sends 12 CMUC to Bob. Be sure that you are sending CMUC and not ETH.

16. Bob sends 13 CMUC to Charlie. Be sure that you are sending CMUC and not ETH.

17. After these last two transfers are complete, take a screenshot of the wallets of Alice, Bob, and Charlie (showing ETH and CMUC).

18. Charlie has tokens but wants more. He wants to buy 20 ETH more. He waits too long
and must buy them at the higher price specified in the contract. Show Charlie's
wallet (ETH and CMUC balances) after buying these additional (and more expensive) tokens.
You will actually have to wait. Come back to this after you have waited long enough. See the contract
and figure out how long you must wait. The grader will be looking for this high price purchase.

19. Show a screen shot of the four accounts from Ganache. This screen shot will show the final balances in ETH of Alice, Bob, Charlie, and Donna.

:checkered_flag:**To receive credit for Part A, submit a document named Lab3PartA.pdf containing clearly labelled sections that include: a screen shot of Ganache accounts from question 12, a screen shot of the four wallets from question 14, a screen shot of the three wallets from question 17, a screen shot of Charlie's wallet after question 18, and a screenshot of the accounts from Ganache described in question 19.**

### Part B. Using an Algorand wallet and calling the Algorand's Testnet API.

In Part B, we are not using the Ethereum tools that we have grown to know and love. We are not
using Ganache, Remix, Truffle, or Enkrypt. We will use a wallet designed for Alogrand and experiment with the Algorand test net.

Algorand is a modern blockchain that competes with Ethereum.

To get started using Algorand, we need an Algorand wallet and an account.  

0. [Visit this site](https://perawallet.app/) and launch [Pera Web](https://web.perawallet.app/).
1. Choose "Create an Account" and choose a password. This is stored on your local machine.
2. Choose an account name. You might use your Andrew id. This too is stored on your local machine.
3. Locate your recovery phrase. See "view pass phrase" after clicking the three horizontal dots on the Accounts page. Take a screen shot and save it locally on disk. A recovery phrase should never be shared. From the recovery phrase, your private key can be generated.
4. Keep the recovery phrase in some place private. It is suggested that this phrase be stored on paper and off any computer. If you lose your recovery phrase, you lose your money. Do not include your recovery phrase on the PDF that you will submit.
5. Change to the Algorand testnet by selecting "Settings" and then "Node Settings" and then "testnet". We are NOT using the mainnet. The mainnet Algos have real value. The testnet Algos have no value. But note that your private key (or recovery phrase) will work on both the mainnet and the testnet.
6. [Visit the dispenser](https://testnet.algoexplorer.io/dispenser) to get funds for the testnet.
7. Use your account address to get funds from the dispenser and be sure to save the transaction ID. You will need that ID later.
8. You may be asked to prove that you are human.
9. Algos will be dispensed to your account (that is, the transfer will be recorded on the testnet blockchain). There are no Algos physically "in" your wallet. Note that you need to look at the testnet and not the mainnet to see the Algos controlled by your wallet.
10. After some time, the wallet will show the new balance of 10 Algos.
11. Transfer 5 Algos from your account to my account address. My account address is
```
K2EP3LIPR3KEI7QOVW3UHLN6JGASMF442YRI5IPO6N6UWPUVNZJ6BVFT4U
```
NOTE: These are testnet Algos and not real Algos. We cannot exchange them for anything of value.

12. Also, keep a copy of the transaction ID.
In a recent transaction, my transaction ID was 4CTARWVWGPBL6G4GOKBIQQLKH5NOHOGV3EVF5XMFQGIGUA72HN6Q.

Next, we want to visit the Algorand blockchain using API's. "API" stands for Application Programmer Interface. There are two API's available. One is the Algorand Node V2 and the other is the Algorand Indexer V2. We will use the Algorand Indexer V2 API.

13. First, we will view the details of the genesis block on the Algorand testnet, we need to generate the following HTTP request and send it to the Algorand explorer API.

```
HTTPS GET https://node.testnet.algoexplorerapi.io/genesis

```

There are several ways to make this HTTP request - using various tools. Here, we will make this
request using a program written in Javascript. You could also make the same request using
Python, curl, or Postman.

Create a file in a new directory and name the file "getGenesisBlock.js". The contents of the
file is a small Javascript program shown next.

```
/*  Read the genesis block on the Algorand Testnet
    Modified from:
    https://blog.logrocket.com/5-ways-to-make-http-requests-in-node-js/
*/
const https = require('https');

https.get('https://node.testnet.algoexplorerapi.io/genesis', res => {
  let data = [];
  const headerDate = res.headers && res.headers.date ? res.headers.date :
'no response date';
  console.log('Status Code:', res.statusCode);
  console.log('Date in Response header:', headerDate);

  res.on('data', chunk => {
    data.push(chunk);
  });

  res.on('end', () => {
    console.log('Response ended: ');
    const dataFromBlock = JSON.parse(Buffer.concat(data).toString());
    console.log(dataFromBlock);
  });
}).on('error', err => {
  console.log('Error: ', err.message);
});

```
Run this program by entering the following command at the command line:

```
node getGenesisBlock.js
```

14. [Visit the api explorer](https://testnet.algoexplorer.io/api-dev/indexer-v2) and note the base URL.
The base URL is https://algoindexer.testnet.algoexplorerapi.io/. Compare the base URL with the one in the Javascript program above. In that code, we were searching for the first block on the Algorand blockchain - the so called "genesis" block.

15. Browse the API's and experiment with some API calls. Create a new Javascript program (based on getGenesisBlock.js) named getDispenserTransaction.js. This program will create an HTTP request to visit the testnet blockchain and get the details associated with the transaction that you sent to extract funds from the dispenser. Run this program and paste the program and its output to the pdf.

16. Create a new Javascript program (based on getGenesisBlock.js) named getTransferTransaction.js. This program will show the transaction details when you sent 5 Algos to me. Run this program and paste the program and its output to the pdf.

:checkered_flag:**To receive credit for Part C, submit a document named Lab3PartB.pdf containing clearly labelled sections that include: getDispenserTransaction.js and its output and getTransferTransaction.js and its output.**

:checkered_flag:**Place your two submission documents (Lab3PartA.pdf and Lab3PartB.pdf) into a single directory and zip that directory. Name the zip file \<YourAndrewID\>Lab3.zip. Submit this single zip file to Canvas.**

##### Grading rubric for the materials in the submission directory

##### Part A Summary: There are five Points for successful completion of Part A.

1. Include a screen shot of Ganache accounts from question 12.

2. Include a screen shot of the four wallets from question 14.

3. Include a screen shot of the three wallets from question 17.

4. Include a screen shot of Charlie's wallet after question 18.  

5. Include a screen shot of Ganache accounts from question 19.

##### Part B Summary: There are four Points for successful completion of Part B.   

1. Include getDispenserTransaction.js.

2. Include the output of getDispenserTransaction.js.

3. Include getTransferTransaction.js.

4. Include the output of getTransferTransaction.js.  

##### One Point for overall presentation

+1 Point for clear labeling and clear presentations in the submission files.    

##### Penalty for any late  work

-1 point per day late
