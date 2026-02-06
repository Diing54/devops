---
title: "HTTP/HTTPS,SSL/TLS and CA"
date: 2026-02-06
tags: ["security","web"]
---

*Date: 2026-02-06*
{{< tags >}}

## Intro
## HTTP/HTTPS
Hypertext Transfer Protocol (HTTP) ---> Protocol used by browsers to communicate with web servers.

Hypertext Transfer Protocol Secure (HTTPS) ---> Encrypts this communication

## Scenario
When on a browser and lets say you want to sign in to your facebook account, your login details (email, password) ,must be sent to facebook servers so that you can be authenticated to login to your account. Login details are compressed to JSON format and then converted to binary language which computers understand. This data is then transmitted over the internet to reach the facebook servers. It can either be transmitted through electrical signals/light signals or any other means such as radiowaves for wireless connections.This data can be collected by anyone that intercepts your network. This is why HTTP is not secure.

## HTTPS
To fix this we use HTTPS. HTTPS secures this data using encryption. Different encryption algorithms can be used. A random string of characters is then produced that makes no sense if the data is intercepted by any hacker. The same key used to encrypt data can also be used to decrypt it.

When this encrypted data arrives at the facebook servers, they can't just decrypt it because the servers don't have the private key.

We can opt to send both this encrypted data and its private key so that the web servers can decrypt it but its still not secure because a hacker can intercept this network and obtain both the encrypted data and the private key to decrypt this data. So sending the private key over the network is dangerous.

## Asymmetric Encryption
The solution to the above problem is Asymmetric encryption.

The encryption discussed above was symmetric encryption where encryption and decryption is done using the same private key. (This is not recommended as discussed)

Asymmetric encryption is when there are 2 keys; a public key and a private key. Public key is used to encrypt the data and private key is used to decrypt it or the other way around.

Asymmetric encryption can be utilized to send data between 2 machines

The server hosts both the public key and private key. Public keys don't need to be secure, they can be accessed by anyone in the world. The private keys should remain private to the server.

Before a browser sends data (email, password) for our facebook login, the server is first notified, and it sends back a public key to the browser computer. So the browser computer has this public key and also it has a key it will perform symmetric encryption later. So the public key received by the computer is used to encrypt the key that was already in the computer and it is sent over the network to the server. A hacker who intercepts this network can obtain the data but can't do anything with it since the private key that can decrypt it is only at the web server. The server decrypts the data and now both the server and the computer have the symmetric key they can utilize to transfer data securely. 
## References
1. https://youtu.be/EnY6fSng3Ew?si=Dsx7d95dtH23gldq
