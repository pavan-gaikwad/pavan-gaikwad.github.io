---
layout: post
title:  "Blockchain Transactions"
date:   2022-12-02 21:48:43 +0530
categories: blockchain
---
Below is an overview of how Transactions are written to the Blockchain. If you are new to Blockchains, a lot of this won’t make sense - but I hope after we break down one idea after another - by the end of this series, you would have a decent understanding of how Blockchain transactions work. Later in this post, we will understand what Blockchain Wallets are.

- First, a user initiates a transaction through their **Blockchain Wallet**. The wallet then broadcasts the transaction to the relevant **Blockchain Nodes**.
    
- The transaction is added to the **pool of unconfirmed transactions**, waiting to be picked up for processing.
    
- The **miners** on the **Blockchain network** pick up a bunch of transactions from the pool and start the mining process. There are many parameters based on which **miners select transactions to add to the Blockchain.**
    
- Depending on the **validation** and **consensus mechanism** of the Blockchain, the miner performs the necessary activities to be selected for adding these transactions to the Blockchain.
    
- If selected to write, the miner writes the Block of transactions to the Blockchain, confirming the transactions.
    
- As this process repeats, new Blocks are added to the Blockchain. Every new Block added on top of the user’s transaction acts as a **Block Confirmation**.
    
    ---
    

### **Blockchain Wallets.**

- A Wallet is your gateway to the world of Blockchains. Think about how a web browser is your gateway to the information on the internet.
    
- A Wallet stores a combination of Public and Private Keys.
    
- For simplicity, think of a Public Key as your account number on the blockchain and the Private Key as the password to this account. Your account number can be shared with anyone without any problems. But if someone gets hold of your password, then they can steal from your account.
    
- A wallet creates these keys for you when you create an account through the wallet. However, you can also bring your own keys and import them to the wallet.
    
- If you are wondering what a Public Key and a Private Key look like, they are long, random text containing numbers and alphabets. For those who have some background on this - here’s a good explainer image.
    
- [
    
    ![](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2Ff1ed0452-7878-474e-911d-117e51f3d5fa_998x420.jpeg)
    
    
    
    ](https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2Ff1ed0452-7878-474e-911d-117e51f3d5fa_998x420.jpeg)
    
- As a user, you use the Wallet to perform transactions on the Blockchain.
    
- Software wallets usually do look similar to the bank app on your phone.
    
- When you start a transaction, say you want to transfer funds to your friend's wallet address, then this transaction request is signed with your Private Key (the password) to prove that it is indeed coming from you.
    
- This way Private Key is used to prove your identity on the Blockchain.
    
- **A Blockchain wallet is more similar to a bank app than a wallet because your wallet actually holds cash. A Blockchain wallet does not actually hold cash, it merely lets you access it.**
    
- Just like your Bank App on your phone does not actually hold the money, the Blockchain Wallet does not actually have your Crypto Currency. It merely holds the account details that enable you to interact securely with a Blockchain.
    
- There are many kinds of wallets.
    
    - _Hardware Wallets_ - These are [physical devices](https://www.coinbureau.com/analysis/best-hardware-wallets/) that hold your details.
        
    - _Software Wallets_ - These are [software applications](https://www.investopedia.com/best-crypto-software-wallets-5220762) that you can download on your phone or your desktop.
        
    - _Paper Wallets_ - Since your Wallets hold Keys that are nothing but long random text, you can write them down on paper and use these keys whenever you want to sign transactions.
        
- Depending on whether a Wallet is online or offline, they are categorized as:
    
    - _Hot wallets_ - Signing of transactions are done online. These are usually software wallets.
        
    - _Cold wallets_ - These wallets are usually hardware wallets that are offline and can sign transactions offline before sending them online.
        
- Every Blockchain is different from others and hence each one might require a wallet that is designed to work with it. There are however many multi-blockchain wallets that can interact with multiple Blockchains.
    
- There are also multi-signature wallets that require more than one Private Key to perform a transaction thereby increasing security. Imagine a joint account or an account that needs multiple passwords to access. These are not widely used yet.
    
- Imagine you have a bank account in XYZ bank. In this case, you would be required to use XYZ bank's app to manage your funds. In the case of Public Blockchains, the ledger is public, hence you have options to choose from multiple wallet apps - even simultaneously - to manage your funds on the Blockchain.