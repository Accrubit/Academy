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

### 1: Data storage and transfers

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

**In the** [**next chapter** ](https://learn.accrubit.com/blockchain-for-business/business-use-cases)**we will** 

{% tabs %}
{% tab title="Chapter References" %}
1. 2. 3.  [https://blockchain.info/charts/n-transactions-per-block](https://blockchain.info/charts/n-transactions-per-block)
{% endtab %}
{% endtabs %}

