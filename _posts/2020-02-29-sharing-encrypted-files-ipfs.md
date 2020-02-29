---
layout: post
title: Sharing encrypted files on a private IPFS network in Java
date:       2020-02-29 11:55:19
author:     Utkarsh Gupta
description:    Condensed article on how to privately share files over IPFS network in Java.
keywords:	"ipfs, encryption, encrypted file, java, private"
categories: blog
thumbnail:  key
comments: true
tags:
 - blog
 - tutorial
 - guide
 - ipfs
 - encryption
---

If you're going through this article, I assume you're already familiar with IPFS and are looking for a way to share files publicly or privately over the IPFS network. If you aren't familiar with IPFS yet, I highly recommend you to go through it once and play around with their desktop client for a while to get a better understanding of how it works. There are numerous well-written articles written on the topic, hence decided not to cover IPFS basics in this post. You can start with their [official website](https://ipfs.io/), and then [this article](https://hackernoon.com/understanding-ipfs-in-depth-1-5-a-beginner-to-advanced-guide-e937675a8c8a).

I was working on a blockchain project based upon [Corda Framework](https://www.corda.net/) by R3, wherein it was required to share trade attachment documents privately only with the participating parties. At the time of writing this article, Corda provides the capability of sharing files as attachments but with a limitation (total size of attachments cannot exceed 20MB). Trying to find a workaround to this limitation, I stumbled upon the InterPlanetary File System (IPFS).

Now let's see how do we encrypt the files and share it with other parties. We'll use asymmetric encryption along with symmetric encryption for the purpose. Here are steps to be followed for sharing an encrypted file over the IPFS network:

1. Generate a symmetric key and encrypt the desired file/files using this symmetric key.
2. Share this encrypted file on the IPFS network.
3. Now encrypt this symmetric key (that's generated in step 1) using the public key of the receiver and send it over using a secure medium.
4. The receiver gets this encrypted key and decrypts it using its private key and get the symmetric key.
5. Retrieve the file from the IPFS network and decrypt it using the symmetric key obtained in step 4. Now you'll be able to view the file.

Below is a schematic from this [article](https://medium.com/@mycoralhealth/learn-to-securely-share-files-on-the-blockchain-with-ipfs-219ee47df54c).
![Scematic depicting sharing of an encrypted file on IPFS network](https://miro.medium.com/max/2070/1*yzYjtRViCDeWyhGnVzsUYw.png "Steps to privately share a file on IPFS Network")

> Currently, even if the file is encrypted, we're sharing it with everyone on the public IPFS network. Though nobody would be able to see the contents of the file without having the correct symmetric key, can we also employ a method using which we only share files in a private network where the participants are already verified?
<br/>

This is achieved by creating a private IPFS network by creating a swarm key and distributing the key across nodes that you want to be a part of your private network. I've already created IPFS and Encryption Utility classes in Java, which consists of functions used for encrypting files and sharing them onto the IPFS network. The codes can be directly imported and used in your project. Here's a link to the [gist](https://gist.github.com/UtkarshGpta/db36ebc31b35de59f7b928b5c971a81d).
