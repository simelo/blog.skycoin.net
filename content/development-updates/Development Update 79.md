+++
title = "Development Update #78"
tags = [
    "Development",
]
date = "2015-08-24"
categories = [
    "Development Updates",
]
description = "Release notes highlighting the current development behind Skycoin."
+++

I have switched the peer list to json instead of csv and am merging in the blacklist and peer lists.

The new peer list format looks like.

![](http://i.imgur.com/MtJrUwL.png)

This is first step to adding new fields to the peer list state and renabling PEX (peer-exchange). Fake peers were being spammed when we were using DHT for peer-discovery. This meant it could take up to two minutes to find a valid peer and begin downloading the blockchain. Under the new protocol, a peer will only be announced to peers if they have a port that is open for incoming connections. This will decrease the time to find other peers further.

The peer blacklist conditions were turned down, because it was being triggered by China's firewall and by abnormal networking conditions. A peer would get blacklisted for an hour if they made a connection attempt and the firewall dropped the connection before the introduction packet was received by the other side. Black list conditions were reduced and now clients are not blacklisted until they send invalid data.

II am adding periodic blockchain saving every 20 seconds, right now, which should fix the windows bug. This should have been pushed a while ago, but was pushed to wrong branch.

I might do quick change to the client to show block height at bottom of the screen and to show connection count.
