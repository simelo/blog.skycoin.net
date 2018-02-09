+++
title = "Development Update #17"
tags = [
    "Development",
]
date = "2014-04-22"
categories = [
    "Development Updates",
]
description = "Release notes highlighting the current development behind Skycoin  "
+++

## Summary:

>How does MaidSafe's technology come into play here? It seems like it can complement Skycoin really well?

Yes. We are working on many things that have similar functionality to Maidsafe. If you read about Protoshares, MaidSafe and Skycoin there is a common thread. There are actually hundreds of these related projects going on right now, but Protoshares, Skycoin and MaidSafe are the coin based ones.

https://github.com/redecentralize/alternative-internet

Skycoin is a building an infrastructure for applications. We are building an API for communication, identity and the automatic exchange of services and resources for coins. The original Skycoin was actually a distributed DropBox like MaidSafe has. This is called "Agoric Computing" and its a thirty year old idea. Its not new, but has become popular again recently. Maidsafe has been around for seven years and a lot of companies have played with this, but no one has been successful at selling agoric computing. All the technology people think its cool, but its a technology that does not necessarily solve problems that make people want to use it.

We had our distributed file system  working and components of it are still in the github.

Skycoin originally had mining but added a distributed time stamping system to prevent 51% attacks, then we realized we didnt need mining for consensus anymore. Then we decided "we are going to be the first coin that is 51% attack proof, more secure than Bitcoin and without miners". That added a lot of work to the project. Then we had the wallet team come on and they wanted to build the best wallet that existed and they wanted a web wallet so they could use HTML and Javascript to make it look good, but they also wanted it locally hosted for security. So we had to embeds a web browser in a window and that took a while.

Then people on the cjdns project convinced us to do a meshnet. The meshnet was already very similar in design to the darknet we designed for the distributed file system. That created a massive amount of work.  Then we had to implement a new coin blockchain, which required months of security audits, refactoring and checking for potential hash collisions. The coin itself is only a few thousand lines of code, but every line has to be bulletproof and triple checked.

Then we had the coin working. The blockchain had been running for a few months, but I was not happy with the networking protocol. I started refactoring the networking and that turned into Skywire. It started with the blob replicator, which used a cryptographic variant of the Gossip protocol. I realized that a lot of things were Blob data and used blob replication and that the distributed metadata store for our distributed file system could be implemented on the blob replicator.  That means I could throw out 12,000 lines of code, pull in Skywire library and the whole application was 400 lines and it did the same thing.

The Skycoin distributed file system was called cFTP for cloud file transfer protocol. In traditional FTP, the directory information for files is on the FTP server and the files themselves come from the FTP server. In cFTP the directory information is in the cloud and the files are in the cloud. The directory information is distributed using a distributed metadata library called "Ether" and files could be looked up by hash and the system was like Bitorrent. It would distribute your files across all your computers.  If you drop a file in your folder on your desktop, the file would appear in your media computer attached to the television. The file would look like a normal file, but if the media player started playing it, the file would stream from the desktop over the network to the media player and media player would cache a copy. If you didnt have a copy of the file on the network, it would find someone on the internet who had the file and start downloading it from them. The directory information and the files contents were now separate.

The distributed metadata library is called "Ether" and it is revolutionary. It is as disruptive as the invention of the blockchain data structure. Blockchains are ordered, Blobs are not ordered. So Ether is like an unordered version of a blockchain.

This will be reimplemented someday, but it was decided that the meshnet was the most important thing. We wanted a meshnet and tried a bunch of them and they sucked. They were poorly designed, they were difficult to setup, there was no reason for people to run a node, they did not protect you from lawsuits and liability if the mesh traffic is going through your IP address. We designed a meshnet that did not suck.

When I was finishing up the coin networking, I realized that I needed to sync multiple blockchains for Obelisk (each Obelisk node is running its own personal blockchain, described in whitepaper). So I developed the services infrastructure. You run one daemon and then associate network services with the daemon. Now blob replication, block chain downloads, Ether and the darknet router were just "services". The Skywire library makes developing p2p applications very easy. We now had an application infrastructure that 3rd parties could extend.

Right now, peers are IP addresses. In the future its a very small step to use a Skycoin address (a public key hash) as the "address" of the node. Each node will have an address and you can send a message to the address and the node will receive them. You can put a Skycoin node on your car and drive down the street and as it is connecting and disconnecting from different wifi hotspots, the IP address will change, the networks its connected through will change, but the node will have the same address. It will still be receiving packets as it moves across networks. With IP addresses, connections reset as you change networks. They dont let you just move to the next network if a connection drops.

This means you can take your laptop and move it anywhere and it will have the same address. The address does not change based upon what network you are connected to, the address is associated with the laptop. You can unplug stuff and move it around and always be able to connect to it.

We also did source routing, which means that the host controls the routing path. This means you choose how your packets are routed, not the routers. If you are playing a video game, you want the low latency route and if you are downloading something you want highest bandwidth. Different applications can use different routing in Skywire. The latency is actually lower than latency for TCP/IP because ISPs use "hot potato" routing. There are gaming services that lower your latency by tunneling your traffic through a VPN tunnel to avoid your ISP's hot potato routing. The Skywire meshnet is essentially the same, but for free.

Since we have source routing, if you run a Skycoin public wifi node, no one can trace the traffic running through that node back to you. You cant be sued for someone downloading music on your wifi node. You dont know the destination, the person receiving the data does not know the source and you cant read the contents because its encrypted and everyone is being paid coins for the traffic. If someone DDoS attacks you, they are paying you coins for the bandwidth for the DDoS attack.

There is no reason why an app cannot be built, that rents out storage space on your computer to other people for coins. There are dozens of dropbox clones on github and you just have to add coins. Many of them are federated and allow you to choose a storage provider. You just have to add coins. Its not difficult.

In some sense, coins are becoming like badges. There was a fad a few years ago where people would take anything and try to add badges to it. "I am going to make Groupon, but with badges". Coins are becoming like that. The difference is that if you have a coin, you are liquid from day one. You have a public market. Its like companies being publicly traded as penny stocks from the day they are incorporated, before they have done anything. Some coins are even trading, before they have a coin. MaidSafe is using colorcoins on the Bitcoin blockchain, to sell MaidCoin before the coin exists or anyone knows how it will work. Protoshares is a coin for a coin that doesnt exist yet, but he probably should have used Colorcoins and cut out the miners. So will see an increasing role for colorcoins for coin presales.

Another thing I noticed. MaidSafe is accepting Mastercoin. Mastercoin has done very well. Mastercoin had a massive ICO and the price jumped after the ICO. Everyone made a ton of money. However, Mastercoin is extremely thinly traded. Mastercoin did not have any new users after the ICO, so there was no one to buy out the people who invested in the ICO. No one can sell their Mastercoins without tanking the price. However, now they can convert their Mastercoins into MaidCoins in the MaidSafe ICO.

So I like MaidSafe as an idea. I like messaging, distributed storage and identity. However, some questions such as "Who is MaidSafe aimed at?", "Who will use MaidSafe?", "How will it get users?", "How are SafeCoins secure if they dont use mining?", "What prevents the creations of infinite safe coins?", "Why would people using MafeSafe drive up the price?". I would have designed MaidSafe's economy a bit differently too. People are mining altcoins to sell them for Bitcoins. What if people run MaidSafe to get SafeCoins to sell them for Bitcoins. Someone buys SafeCoins with Bitcoin to buy storage space on MaidSafe and then someone else provides the space and sells the SafeCoins for Bitcoin. There is no net capital inflow into SafeCoin. The price has not changed.
