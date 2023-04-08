## Spring 2023 Developing Blockchain Use Cases Lab 3                             
### Carnegie Mellon University                  
### Due: 11:59 PM, Monday, April 24, 2023                                
### 10 Points

### Lab Assistance provided by Michael McCarthy, Atharva Joshi, and Nikita Vignesh Kumar
### See Office Hours on Canvas




**Learning Objectives:** The object of Part A is to introduce the student to the MetaMask wallet and crowdsale contracts. The objective of Part B is to introduce the student to debugging smart contracts using the truffle debugger. The objective of Part C is to experiment with the Algorand Testnet.


### Part A. Using the Remix web IDE and the MetaMask wallet

1. In Lab 1, you installed Ganache and you will be using it again here. Run Ganache Quickstart and leave it running for the remainder of Part A. This is, essentially, a client server application. Ganache is the server and is used to hold a single instance blockchain. We will visit the server with two clients - the Remix application running in a browser and a MetaMask wallet, also running in a browser.


2. We will be using the Remix IDE to compile Solidity source code. We will also use Remix to deploy byte code to the Ethereum Virtual Machine (EVM) running on Ganache. Using Remix and MetaMask, we will interact with the contract using JSON-RPC. Remix runs in your browser. You don't need to install it.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;See: https://remix.ethereum.org/

Run Remix in the same browser where you installed your MetaMask wallet.

The MetaMask wallet was installed in Lab 1.

3. In Remix, create a Solidity file and name it "Lab3PartA.sol". [Paste the code at this link](../../blob/master/PartA/Lab3PartA.sol) into Lab3PartA.sol and click on "Select new compiler version" dropdown and select "0.4.18+commit". The contract should compile successfully and you may ignore the warnings. Select your provider as "Web3 Provider" and connect to Ganache on port 7545. You will deploy the contract soon.

4. Click on the MetaMask plugin in your Chrome browser. There is a circle icon on the top right that is the "Accounts" icon. Click this icon and open "Settings". Under "Advanced", set "Advanced Gas Controls" to "ON". Also, set "Show Conversion on Testnets" to "ON".

At this point, a new network needs to be added to metamask. Metamask ships with a default "Localhost 8545" network, but this is not compatible with Ganache out of the box. We need to delete this network and add it with the correct settings to get it to work. Under "Settings" > "Networks", click on "Localhost 8545" and then on "Delete". Confirm Deleting the Network by pressing the red button.

Click on the Add a network button on the top right. Under "Network Name" enter Ganache, under "New RPC URL" enter http://127.0.0.1:7545, under "ChainID" enter 1337, and under Currency Symbol enter "ETH" and then select "Save". You will now be able to import accounts from Ganache. Always ensure that you are working with the "Custom RPC" network and not any other networks in MetaMask.

To see an expanded view of your wallet, click on the "Account Options" ellipsis to the right of the account and click on "Expand View".

5. Currently, your account name is "Account 1" and you control 0 ETH. To complete transactions through the wallet, you will import accounts from Ganache into your MetaMask wallet as "imported" accounts. In Ganache, you can view the key icon to the right of the public key of each account, click on the key icon and you can view the private key of the account. Copy the private key and use it for importing the account into MetaMask.

6. In the expanded view of MetaMask, click on the "My Accounts" image on the top right, and select "Import Account", select "Private Key" from the dropdown menu and paste the copied private key from the previous step. Click on "Import" and you have successfully imported a Ganache account to your MetaMask Wallet. You now control 100 ETH from "Account 2".

Under "Details", use the pencil icon to change the name of "Account 2" to "Alice".

7. Import the next 3 accounts from Ganache to your MetaMask wallet as "Bob", "Charlie" and "Donna". You will use these accounts to participate in the crowdsale and execute transactions with ETH and CMU Tokens.

8. Once you have imported the 4 accounts, use Remix to select the "Alice" account - make sure her address appears in the Remix account box. Using Remix, compile the code and click on the box containing"ApproveAndCallFallBack" and select "CMUToken".

Next click on "Deploy" and your crowdsale contract will be deployed on the blockchain through Alice's account. If you don't get an error message, and the contract gets deployed successfully, you should be able to view "CMUToken" along with its address under "Deployed Contracts" in Remix. You should also notice that Alice paid for that deployment by looking at her account on Ganache or MetaMask.

Note: If you restart a new instance of Ganache, you will want to reset the accounts in
your wallet. Do this for each account with "My Accounts/Settings/Advanced/Reset Account".

Note: If a transaction does not complete successfully, do not give up. Try it again
with a higher gas price (say 8 GWEI) or a higher gas limit. You may have to play
with MetaMask a bit to get it to cooperate. You may want to reset the account as described
in the previous note.

#### Part A Problems

Note: You will be working with a crowdsale contract and steps 9 through 17 should be completed without delay - the players will get their tokens at a discount. Note too that Charlie delays his purchase in question 18. Be sure to review the contract to see how time is handled.

9. Alice sends 10 ETH to Donna. She does not need a contract to do this. She only uses her wallet to perform a send operation. Using Ganache, copy Donna's public address to the clipboard. Paste it into Alice's wallet to perform the transfer.

10. Alice sends 10 ETH to Bob and Charlie too. That is 10 ETH per person.

11. Donna sends 5 ETH to Alice and Bob (Alice and Bob both receive 5 ETH.)

12. At this point, take a screenshot of the 10 accounts on Ganache.

13. Since the CMU Token contract implements the ERC 20 standard interface, the MetaMask wallet is able to automatically track CMU Tokens. In this step, we will inform the wallet that we are interested in tracking these tokens. In Remix, click on the "Copy value to clipboard" icon next to the contract address. This will be used to add the CMU Token to the MetaMask wallet. You might also take this address directly from Ganache. In MetaMask, expand the view of Alice's account and click on "Add Tokens" to add the CMU Token to her account. Click on "Custom Token" and paste the copied address in the "Token Contract Address" and click on "Add Custom Token", and then click on "Import Tokens". You have now successfully added CMU Tokens to your Alice account. So that Bob, Charlie, and Donna can exchange tokens, repeat this process for the remaining accounts.

 To repeat, the wallet is able to handle these tokens because the contract developer implemented the methods defined by a standard interface and the wallet developer was ably to rely on these methods being there.

14. Each of our players (Alice, Bob, Charlie, and Donna) buys 5 ETH worth of CMUC from
the contract. After the purchases, take a screenshot of each of these wallets (showing ETH and CMUC). <This is done by sending 5 eth to the account. I don't believe this is clear, should we be adding this into the steps?>

15. Alice sends 12 CMUC to Bob.

16. Bob sends 13 CMUC to Charlie.

17. After these last two transfers are complete, take a screenshot of the wallets of Alice, Bob, and Charlie (showing ETH and CMUC).

18. Charlie has tokens but wants more. He wants to buy 20 ETH more. He waits too long
and must buy them at the higher price specified in the contract. Show Charlie's
wallet (ETH and CMUC balances) after buying these additional (and more expensive) tokens.

19. Show a screen shot of the four accounts from Ganache. This screen shot will show the final balances in ETH of Alice, Bob, Charlie, and Donna.

:checkered_flag:**To receive credit for Part A, submit a document named Lab3PartA.pdf containing clearly labelled sections that include: a screen shot of Ganache accounts from question 12, a screen shot of the four wallets from question 14, a screen shot of the three wallets from question 17, a screen shot of Charlie's wallet after question 18, and a screenshot of the accounts from Ganache described in question 19.**


### Part B. Debugging smart contracts using the Truffle suite

These instructions are modified from the tutorial found here:

```
https://trufflesuite.com/guides/debugging-an-example-smart-contract/

```

There are three distinct places in these directions where you need to
paste a copy of your transaction receipt to a submission file named
Lab3PartB.pdf.

1. Make a new directory named debugging-exercise and cd into it.

2. Create a truffle directory structure:

```
   truffle init

```
3. Save the following file in the contracts directory and name it Store.sol.

```
   pragma solidity ^0.5.0;


   contract SimpleStorage {


       uint myVariable;


       function set(uint x) public {

          myVariable = x;

       }


       function get() view public returns (uint) {

           return myVariable;

       }

  }

```

4. Save the following file in the migrations directory and name it
 2_deploy_contracts.js.



```
     var SimpleStorage = artifacts.require("SimpleStorage");


        module.exports = function(deployer) {

          deployer.deploy(SimpleStorage);

        };

```

5. We would like to work with this SimpleStorage contract in development mode. Run the following command:

```
     truffle develop
```

Note: When you want to exit truffle(develop), use "control-d".

6. A development blockchain is provided for this work. Public and private keys are also provided.
 We need to compile and deploy the contract.

```
     truffle(develop)>migrate --reset
```

7. Access the contract's get method with a call:

```
     truffle(develop)>SimpleStorage.deployed().then(function(instance){return instance.get.call();}).then(function(value){return value.toNumber()});

```

8. Access the contract's set method:


```
     truffle(develop)>SimpleStorage.deployed().then(function(instance){return instance.set(4);});

```

9. Notice the "from:"" and "to:"" values in the receipt. In your own words, describe
what the value of "from:"" refers to and what the value of "to:"" refers to.


:checkered_flag:**Copy the question 8 receipt and paste it into your submission file.
Do the same with your answer to question 9.**

10. The above operation returns the transaction ID, transaction receipt, and the event logs. It also includes enough information for the blockchain client to derive the public key and the address of the external account.  

  The logsBloom may be used by a client to check if any particular event was generated during the contract's execution.

11. Note that we can make a copy (without the single quotes) of the transaction ID (also called the transaction hash). Our debugging efforts will concentrate on particular transactions and this hash will identify the transaction that we wish to debug.

12. Make another call to the get function to verify that the value has been saved in the contract's storage.

```
truffle(develop)>SimpleStorage.deployed().then(function(instance){return instance.get.call();}).then(function(value){return value.toNumber()});

```

The output should be:

```
4
```

13. Let's introduce an error. Modify the set method to include an infinite loop:

```
      function set(uint x) public {
         while(true) {
            myVariable = x;
         }
      }

```

14. Within the development console, compile and migrate the new contract:

```
truffle(develop)>migrate --reset

```

15. Within the development console, execute the contract's new set method:

```
truffle(develop)>SimpleStorage.deployed().then(function(instance){return instance.set(4);});
```

We get an error. We are out of gas. We have executed too many operations. Note that we have no transaction receipt to examine. We need to see the server side logs.

In a new shell, visit the directory 'debugging-exercise', execute the following command:


```
truffle develop --log

```
It should respond with:

```
Connected to existing Truffle Develop session at http://127.0.0.1:9545/

```

16. Return to the first console window and execute the new set method again.

```
truffle(develop)>SimpleStorage.deployed().then(function(instance){return instance.set(4);});

```  
Note that we now have access to the transaction ID in the logs. Make a copy of the transaction hash.

17. From within the truffle development environment, execute the debugger:

```
truffle(develop)>debug <transaction hash>

```
18. A list of commands is presented. By simply hitting the enter key you can step through the code associated with this particular transaction.  
By entering the 'h' command you can view the list of available commands. The 'v' command allows you to see the list of variables and their values. By carefully stepping through the code, we can debug the contract. Take some time and step through the code.

 The infinite loop becomes apparent.

19. Exit the debug session with the 'q' command.

20. In Store.sol, replace the set method with the following:

```
function set(uint x) public {
    assert(x == 0);
    myVariable = x;
}


```

If the expression in the assert statement is false, an exception is thrown. In this case, we are only permitted to set 'myVariable' to 0. Anything else will cause an exception.


21. Within the development environment, compile and deploy with

```
truffle(develop)> migrate --reset

```
22. Run the method with 0 so that the assert does not fail.

```
truffle(develop)>SimpleStorage.deployed().then(function(instance){return instance.set(0);});

```
:checkered_flag:**Copy your receipt from question 22 and paste it into your submission file:**

23. Run the method with 7 and force the assert statement to fail:

```
truffle(develop)>SimpleStorage.deployed().then(function(instance){return instance.set(7);});

```
24. Run the debugger. To debug the error, we need the transaction hash from the log window.

```
truffle(develop)>debug <transaction hash>

```

25. Step through the code and view the values of the two variables 'myVariable' and 'x'. The transaction will halt with a runtime error just after evaluating the assert statement. Use 'q' to stop debugging this transaction.

26. Modify your contract so that it contains two events and a new set method:

```
// declare an Odd event
event Odd();

// declare an Even event
event Even();

function set(uint x) public {
    myVariable = x;
    if (x % 2 == 0) {  
        emit Odd();
    } else {
        emit Even();
    }
}
```

27. Compile and deploy your new contract.

```
truffle(develop)> migrate --reset
```

28. Send the even value 4 to the contract's set method.


```
truffle(develop)>SimpleStorage.deployed().then(function(instance){return instance.set(4);});
```
29. Notice that the logsBloom has changed and the receipt shows "Odd" rather than "Even".

:checkered_flag:**Copy your receipt from question 28 and paste it into your submission file:**

30. To debug this transaction, copy the transaction hash and execute the debug command.

```
truffle(develop)> debug <transaction hash>
```
31. Use 'n' and 'v' to step through the transaction and view variables. You can see that the Odd event is generated when it should be Even.

:checkered_flag:**To receive credit for Part B, submit a document named Lab3PartB.pdf containing clearly labelled sections that include: the question 8 receipt and the answer to question 9, the question 22 receipt, and the question 28 receipt.**


### Part C. Using an Algorand wallet and calling the Algorand's Testnet API.

Algorand is a blockchain that competes with Ethereum.

To get started using Algorand, we need an Algorand wallet and an account.  

0. Visit https://perawallet.app/ and launch Pera Web to visit https://web.perawallet.app/.
1. Choose "Create an Account" and choose a password. This is stored on your local machine.
2. Choose an account name. You might use your Andrew id. This too is stored on your local machine.
3. Locate your recovery phrase. See "view pass phrase" after clicking the three horizontal dots on the Accounts page. Take a screen shot and save it locally on disk. A recovery phrase should never be shared. From the recovery phrase, your private key can be generated.
4. Keep the recovery phrase in some place private. It is suggested that this phrase be stored on paper and off any computer. If you lose your recovery phrase, you lose your money. Do not include your recovery phrase on the PDF that you will submit.
5. Change to the Algorand testnet by selecting "Settings" and then "Node Settings" and then "testnet". We are NOT using the mainnet. The mainnet Algos have real value. The testnet Algos have no value. But note that your private key (or recovery phrase) will work on both the mainnet and the testnet.
6. Visit https://testnet.algoexplorer.io/dispenser to get funds for the testnet.
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

Next, we want to visit the Algorand blockchain using API's. "API" stands for Application Programmer Interface. There are two API's available. One is the Algorand Node V2 and the other is the Algorand Indexer V2.

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

14. Visit the URL https://testnet.algoexplorer.io/api-dev/indexer-v2 and note the base URL.
The base URL is https://algoindexer.testnet.algoexplorerapi.io/.

15. Browse the API's. Create a new Javascript program (based on getGenesisBlock.js) named getDispenserTransaction.js. This program will create an HTTP request to visit the testnet
blockchain and get the details associated with the transaction that took funds from the dispenser.
Run this program and paste the program and its output to the pdf.

16. Browse the Algorand Indexer V2 API. Create a new Javascript program (based on getGenesisBlock.js) named getTransferTransaction.js. This program will show the transaction details when you sent 5 Algos to me.
Run this program and paste the program and its output to the pdf.

:checkered_flag:**To receive credit for Part C, submit a document named Lab3PartC.pdf containing clearly labelled sections that include: getDispenserTransaction.js and its output and getTransferTransaction.js and its output.**

:checkered_flag:**Place your three submission documents (Lab3PartA.pdf, Lab3PartB.pdf, and Lab3PartC.pdf) into a single directory and zip that directory. Name the zip file \<YourAndrewID\>Lab3.zip. Submit this single zip file to Canvas.**

##### Grading rubric for the materials in the submission directory

##### Three Points for successful completion of Part A

include a screen shot of Ganache accounts from question 12

include a screen shot of the four wallets from question 14

include a screen shot of the three wallets from question 17

include a screen shot of Charlie's wallet after question 18.

include a screen shot of Ganache accounts from question 19.

##### Three Points for successful completion of Part B     

include a receipt from question 8

include a description of "from:"" and "to:"" in question 9.

include a receipt from question 22

include a receipt from question 28  

##### Three Points for successful completion of Part C    

include getDispenserTransaction.js
inlcude the output of getDispenserTransaction.js

include getTransferTransaction.js
include the output of getTransferTransaction.js

##### One Point for overall presentation

+1 Point for clear labeling and clear presentations in the submission files.    

##### Penalty for any late  work

-1 point per day late
