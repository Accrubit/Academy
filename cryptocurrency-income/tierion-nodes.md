# Tierion Nodes

### Getting Started

I will be going over how to easily setup a [Tierion Network Node](https://github.com/chainpoint/chainpoint-node) from beginning to end using Amazon Web Services. You do not need to use Amazon to run a Tierion node, however I prefer to use them over others for the simplicity of this setup. 

If you do not want to use Amazon for whatever reason, do not follow this guide. I will also not be getting into the economics of running a node, but if you are interested, I have an ongoing [profitability assessment here](https://www.accrubit.com/terion-news.html).  
  
So if you would like to start a node quickly and as painlessly as possible, this setup will get you there in these 8 simple steps:

1. ​Setting up Your Node's Ethereum Wallet
2. Creating an Amazon Lightsail Account
3. Purchasing an Ubuntu Virtual Server
4. Pairing a Static IP Address to Your Ubuntu Server
5. Setting Up Your Ubuntu Virtual Server
6. Starting Up and Verifying Your Tierion Node
7. Monitoring your Tierion Node

{% hint style="info" %}
In this guide you will see some code boxes representing command interfaces, the only thing we are putting in there are the commands.
{% endhint %}

### Setting Up Your Node's Wallet​​

In order to manage your node, I recommend first creating a new ERC-20 compatible wallet on [https://www.myetherwallet.com](https://www.myetherwallet.com). 

Once you have created your wallet, ensure it has:

* Ethereum \(ETH\) for gas fees \(I use 0.01 ETH as a base\) 
* At least 5000 TNT for node eligibility.

![MEW Wallet](https://www.accrubit.com/uploads/2/8/3/7/28374731/editor/mew-image.png?1505627506)

### Creating an Amazon Lightsail Account

Go to [https://amazonlightsail.com/](https://amazonlightsail.com/) and sign up. You don't need customer support, so when prompted don’t buy into the upsell offer as the service is free by itself. 

![](https://www.accrubit.com/uploads/2/8/3/7/28374731/lightsail-image_orig.png)

### Purchasing an Ubuntu Virtual Server

Now that you have a Amazon Lightsail account, you want to create your first instance. The instructions are as follows:

1. Select Create Instance
2. Select the Region and Zone you want for your node
3. Select OS Onl
4. Select Ubuntu
5. Choose the $10 plan
6. Name Your Ubuntu instance

![Creating an instance](https://www.accrubit.com/uploads/2/8/3/7/28374731/tierion-node-example-lightsail_1_orig.png)

{% hint style="info" %}
### **Note**

We use the $20 plan for future proofing in case we want to use the nodes to verify our own data, or in case minimum specifications exceed the plan. Tierion has explicitly stated they want more powerful nodes, not less as time progresses.
{% endhint %}

### Pairing a Static IP Address to Your Ubuntu Server

​Now that you have your Ubuntu machine purchased, you will need to create a static IP for your node.

1. Select "Create static IP"
2. Select the Location and Zone that your Ubuntu Server is in.
3. Attach the Static IP to your Ubuntu Server
4. Name your Static IP

![](https://www.accrubit.com/uploads/2/8/3/7/28374731/lamboip_orig.png)

### Setting Up Your Ubuntu Server

Time to actually begin setting up your machine. Whether you have used Linux command line interfaces or not, we are going to make this as easy to perform as possible for you.  Each line is a command. You need to press the enter key to send. The commands below will update Ubuntu on your machine.

#### Step 1: Updating and Upgrading Ubuntu Packages

```bash
sudo -i
apt update
apt upgrade
y
```

When prompted, press enter to keep the existing version installed, it is the default option so there is nothing else you need to do.

{% hint style="info" %}
**Intermediate:** Setup additional security measures for users and remote access. [Learn more](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-16-04)
{% endhint %}

#### Step 2: Installing Tierion Core Software 

Next you will be installing the core software needed for the operations of a Tierion Node and editing the directory file for your specific credentials.  To install this software, the Tierion team created a simple command script to enter that installs all of the required packages and configurations automatically.

* Docker
  * Docker Compose
* Persistent 2GB swap file
* Downloads Chainpoint Node repository to the home folder
* Creates a default .env environment file, ready for you to edit

```bash
curl -sSL https://cdn.rawgit.com/chainpoint/chainpoint-node/13b0c1b5028c14776bf4459518755b2625ddba34/scripts/docker-install-ubuntu.sh | bash
```

#### Step 3: Modifying the Directory for Your Credentials

Now that the Tierion Chainpoint Node software is installed, you want to edit the node files with your own credentials. We will be using the VI text editor in Linux for this.

```text
vi ~/chainpoint-node
```

1. Use the arrow keys to move over ".env" and press enter
2. Press "i" to allow the input of entries
3. Use arrow keys to navigate down to "NODE\_TNT\_ADDRESS=" and input your node's wallet address that you created earlier.
4. Use the arrow keys to  navigate to  "CHAINPOINT\_NODE\_PUBLIC\_URI=" and input http://yourstaticipaddress
5. Press the "esc" key to exit input mode
6. Save and close the VI text editor by typing the below command and pres enter

```text
:wq
```

You should now have edited your node's .env file to contain your wallet address and your static IP address.

### Starting Up and ​Verifying Your Tierion Node 

Time for the moment you have been waiting for, node startup. To startup your node and perform the basic system checks you will do the following:

1. Enter the node directory
2. Startup the node
3. Analyze the node for a registration confirmation
4. Verify successful startup

#### Step 1: Initializing Your Tierion Node

Enter the chainpoint node directory

```text
cd ~/chainpoint-node
```

Check for the latest version, update if needed, add NTP services if missing, and start up the node.

```text
make upgrade
```

Verify all core processes are up

```text
make ps
```

Watch logs for the registration and key confirmation

```text
make logs
```

You will know your node is working if there are no errors, and that you are seeing "Validated and Stored to Core" blocks. 

If you see "Firewall: "\#\#\#\#" IPs Blocked" this is normal so don't worry about it. 

If you see that registration is full, simply wait for the next registration announcement from Tierion on their [blog](https://medium.com/tierion).

If you are seeing any other errors check out the [node FAQ](https://github.com/chainpoint/chainpoint-node/wiki/Frequently-Asked-Questions) for resolution.

{% hint style="info" %}
**Tip:** For those unaware, you do not need to leave the logs open for the software to run. They are just for your use as an administrator to know what's going on with your node. To learn some basic Linux commands [go here.](https://maker.pro/linux/tutorial/basic-linux-commands-for-beginners)
{% endhint %}

### Monitoring Your Tierion Node

Congratulations, you node is now setup. It will take around 2 hours \(**4 calendar verifications**\) for your node to become eligible for rewards. If you don't know what the calendar is, you should read the [Tierion whitepaper](https://tokensale.tierion.com/TierionTokenSaleWhitePaper.pdf).

{% hint style="warning" %}
### How do you know if your node is working properly and eligible?

1. Did you receive the registration with core message in the logs upon startup? 
2. Do you currently have 5000 TNT in your node's wallet? 
3. Are you validating calendar blocks in your logs? 
4. Is your calendar up to date? 
5. Are your NTP tolerances within acceptable parameters? \(5 Seconds\)
{% endhint %}

If the above check out, you can then login to your node's interface using your browser like so:

1. **Visit the web interface for your node:** http://YourNode'sStaticIP
2. **Enter your node's password:** yourwalletaddress

Once you are logged in, click the three bar menu tab and go to the about section. This is the place where you will find all of the needed information about your node and it's health in the network.

It should look something like my node below:

![](https://www.accrubit.com/uploads/2/8/3/7/28374731/published/fireshot-capture-105-chainpoint-node-dashboard-http-18-221-150-84-about_1.png?1527979165)

​​If you want to run another node, simply repeat this guide in it's entirety for each new node. You need 5000 TNT, a new server, a new IP, and a new wallet for each node. 

Unless of course you are running containerized server hardware with multiple Global IP's allocated for you to use from you ISP.

For more detailed documentation on Tierion Nodes and the capabilities of them, please go to the [official GitHub repository](https://github.com/chainpoint/chainpoint-node).

