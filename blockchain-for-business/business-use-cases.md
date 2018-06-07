---
description: >-
  In this chapter we will be reviewing the current and potential use cases for
  blockchain technology across a wide range of industries, and how to evaluate
  blockchain solutions for business use cases
---

# Blockchain Use Cases

![](../.gitbook/assets/blockchain-for-business2.png)

Blockchain technology has come a long way since it's first inception as a Bitcoin payments ledger. So much so, that most of the information online about the use cases for blockchain are  polarized between grand visionary futures of an interconnected internet of value and warnings of financial doom resembling the financial bubbles of the past.

As usual with popularized technology, the answer lies somewhere in the middle. Due to this polarizing atmosphere, what we will be doing is laying out the strengths and pitfalls of blockchain technology based on irrefutable facts, and then determine the feasibility and most appropriate uses for a blockchain based on that.

{% hint style="danger" %}
### Main issues with blockchains

1. Data storage and transfer is minimal
2. Human error can cause dire and irreversible circumstances
3. Accounts and transactions are not very user friendly
{% endhint %}

### Issue 1: Data storage and transfers

As we learned in the Intro to Blockchain, these ledgers are immutable, meaning the data cannot be modified, deleted, or moved elsewhere. The problem this adds is with the peer-to-peer nature of blockchain systems. If each and every participant maintains a full working copy of the blockchain, then every time any data is added to it, it must be added to the hard drives of all participants in the network.

#### Example:

> You are the owner of a modest media and design firm that focuses on technology based clients. You have heard a lot about blockchain from these clients, and have become interested yourself at the possibilities. After reading about the benefits and how they work, you decide you could use one within your own business to streamline the access and copyright protection of images created in house. You envision:
>
> * A secure master file for all company IP
> * Irrefutable transaction signatures to secure copyrighted content
> * Elimination of cloud storage providers by leveraging your employees empty hard drive space to store your images on the shared blockchain.
>
> At first glance, you see blockchain as a great way to create a secure master file of all company images and avoid the hosting costs of cloud storage providers. Now blockchain enables everyone to share their files and encrypt them in real time.
>
> At first, it's amazing. The IT department setup a notification system the let's employees know when images were added from specific departments, which helps employees save time that they would otherwise use checking the company. They also setup an application that automatically forwards images to be submitted for copyright protection.  
>   
> So each time one of your designers, photographers, or editors creates an image it get's automatically added to the blockchain. And when an employee needs an image, they simply use whatever naming convention you came up with to retrieve them. Life is good.  
>   
> As time progresses however, everyone's systems start moving extremely slow, and eventually the network becomes unusable. There is simply too much bandwidth moving from employee to employee for anybody to use the internet. You clients however are amazed by your innovative firm, and love being able to retrieve their images anytime from the app using their unique signatures. So you buckle down and pay for more bandwidth.  
>   
> Fast forward and it's been a year. Your internet costs are astronomically higher than the costs of cloud storage, and everyone is out of hard drive space.  You are forced to move all images back to a cloud storage provider and have lost many employees and clients due to the frustratingly slow experience. Your idea failed, your app failed, and your company is worse off than it was before.

#### What went wrong?

Let's say the average image was 2 MB in file size, which is double the current maximum size of an entire Bitcoin block, which houses upwards of 1250 transactions as of this writing. \[3\]

Now as we covered previously, Bitcoin is not blockchain, so the amount of data you can put in each block to be written to a blockchain is entirely up to you. So lets say the blockchain was designed to have block sizes of 2GB.

As you can probably surmise, if there were 1000 participants all sharing even a single 2MB image each day for an entire year, they would all have a blockchain taking up 730 GB of data storage on their machines, or a combined total of 730 Terrabytes for the company as a whole. The block height would be 365,000 for those also following along with the chain of things.  
  
What a colossal waste of bandwidth and storage space. So as you can see, blockchains are not good for storing or transferring rich data. 

{% hint style="info" %}
### How could this be solved?

Since storing data directly to a blockchain is a bad idea, we have to think deeper into the systems to achieve the same results. There are actually multiple working Blockchain solutions designed just to store data. 

The most common of which are StorJ and IPFS. These networks borrow some key properties of cryptography from blockchain ledgers and use them to build retrieval systems that provide the security of the blockchain without storing files directly to one.

Instead, these systems break apart your files and distribute them across specialized nodes that store files economically. These nodes send back unique signatures that identify your files on the network. 

It is these unique signatures that you would store to a blockchain, and anytime you needed to retrieve a file, you simply request your signature from the blockchain and then submit that to the storage system which unlocks and retrieves your files for you.

**In simple terms, you would just take the signature of image to store, not the image itself.**
{% endhint %}

### Issue 2: Human error breeds catastrophe

This is possibly one of the most glossed over attributes of blockchain systems in the industry. While we can all imagine the benefits of automated contracts, distributed value systems, and individual digital ownership of assets, we should all be equally as concerned about them. For example:

* If you make a transaction to the wrong address, that asset transfer is unrecoverable. 
* If you deploy a smart contract with an exploit in the programming, the software can't just be updated to fix it.
* If you don't maintain secure and accessible environments for your access keys, you can be locked out your accounts forever.
* If the consensus model isn't secure for your distributed network, an attacker can seize control of the entire blockchain.

As you can see, these are some serious drawbacks to using a blockchain system.

I've had the displeasure of informing clients from high level fund managers to your average consumer that there isn't any third party that can come to their rescue after mismanaging their assets. This is last thing anybody wants to hear after losing any sum of money.

{% hint style="warning" %}
###  Common Human Errors in Blockchain

* Using an Incorrect Recipient Address
* Falling for Phishing Attacks
* Programming Vulnerable Smart Contracts
* Designing Vulnerable Consensus Networks
* Sending Assets to Incompatible Wallets
* Ignoring the Advice of Experts and the Failures of Yesterday
* Using Blockchains for Incompatible Use Cases
* Assuming Blockchain Systems can be Compatible
* Not Securing Account Information and Keys Sufficiently
{% endhint %}

#### Case Study: The DAO Hack

> "The DAO" was the name of a specific Distributed Autonomous Organization, which launched on the Ethereum platform April 30th, 2016.

> At the time, The DAO was represented everything innovative and comforting about public crowd sales at the time, and promised to build a decentralized organization that would allow democratic management of both commercial and non-profit enterprises. At the time, The DAO was the largest crowdfunding in history, with over $150 million in capital raised in just 28 days.
>
> The creators of The DAO were not expecting any of this to happen, and were not prepared for what happened next.

> Once the crowdsale was over, many issues were addressed regarding potential vulnerabilities and exploits of the smart contracts managing the organization. After all, this was the most complicated attempt at such an organization to date. One such exploit that was discussed, was the "recursive call bug", which had been found in the software by one of the founders.
>
> Despite the vulnerability, the founders insisted that it was patched before launching and that DAO funds were not at any risk of being exploited.
>
> In June 2016, users exploited the vulnerability which enabled them to steal 3.6 million ether, worth around $80 million at the time, of The DAO's funds. In July 2016 at Block 1,920,000 on the Ethereum blockchain, the Ethereum development community voted to hard-fork the Ethereum blockchain to restore virtually all funds that were stolen to the original accounts.
>
> This was highly controversial and led to a lasting fork in Ethereum. This is why there is an Ethereum Classic \(Original Chain\) and an Ethereum \(Developer Approved Chain\).

> The DAO was completely delisted from all exchanges and the project was pronounced dead in the water in just a few months time.

Now it's important to simplify what happened here so you can understand the gravity of what can happen in blockchain systems: 

* A successfully funded startup raised over 100 million dollars and lost it all due to just a **few lines of code** in their smart contracts.
* The founders ignored the advice and recommendations of legal and technical experts all over the world and decided to push forward on a project prematurely.
* The SEC concluded that DAO tokens sold on the Ethereum blockchain were securities and therefore possible violations of U.S. securities laws.
* Ethereum was forced to bail the DAO and their investors out at their own expense by initiating a hard fork that returned stolen funds back to the original accounts.

{% hint style="info" %}
### How could the DAO hack have been prevented?

You have to expect security flaws to show up in any IT system, period. There isn't a developer alive who doesn't leave a vulnerability in their program, and not because they aren't experienced enough, but because human ingenuity always finds a new attack vector to exploit.

In the DAO's case, they simply rushed their technology and ignored the warning signs of significant vulnerabilities.

Good news is, there are pretty standard practices to follow to help bolster the efficiency and security of your blockchain system:

1. Smart Contract Audits
2. Network Stress Testing
3. Multiple Product Phases Prior to Launch
4. Formal Security Audits
5. Bug Bounties
6. Did I say test? Keep testing
7. Consult with expert advisers in every piece of your use case

If the DAO had simply slowed down, broken their product launch into lengthy test phases, performed professional audits, and heeded the warnings of their advisers, then the hack likely would have never occurred.
{% endhint %}

The scope of human error extends into the most catastrophic circumstances in blockchain systems. Unlike traditional centralized systems, there are no third parties to rely on for support, and there isn't a quick way to patch or reverse exploits once they are found. Furthermore, if you are operating on a public network without KYC, there may not even be an avenue for legal support. 

Blockchain is still new technology, and isn't a full stack system, so don't rush into it without expecting copious amounts of trial and error. Next, we will talking about the last main issue, poor user experience, which unfortunately acts as a multiplier on the problem of human error.

### Issue 3:  User experience is uncompromising and technical



{% hint style="success" %}
### Main benefits of blockchains
{% endhint %}

{% hint style="success" %}
### **Chapter Summary**

* 
{% endhint %}

{% hint style="warning" %}
### **Time to Reflect:**

* 
{% endhint %}

**In the** [**next chapter** ](https://learn.accrubit.com/blockchain-for-business/business-use-cases)**we will be evaluating the most prominent blockchain solutions, from protocols to front-ends, and how to choose the one that's right for you.**

{% tabs %}
{% tab title="Chapter References" %}
1. 2. 3.  [https://blockchain.info/charts/n-transactions-per-block](https://blockchain.info/charts/n-transactions-per-block)
4. 5. 6. 7. 8. 9. [https://medium.com/swlh/the-user-experience-of-blockchain-applications-ea7defc388df](https://medium.com/swlh/the-user-experience-of-blockchain-applications-ea7defc388df)
10. 11. 12. 13. 14. 15. 16. 17. 18. 19. 20. 
{% endtab %}
{% endtabs %}

