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


BUT Asymmetric encryption has its own security flaws:

## Man in the Middle Attack
Normally, the browser computer notifies the webserver that it wants to send data. Instead, a hacker comes in the middle and acts as a webserver and has a private key and a public key just like the server. The hacker receives the notification intended to the server and sends back the public key to the computer. The computer thinks the public key is from the server.

The computer encrypts its symmetric key using the public key and sends it back to the server. Instead, the hacker intercepts this data (encrypyted symmetric key). The hacker then decrypts it using his private key. Now the hacker has the symmetric key from the computer. The computer sends its sensitive data encrypted by the symmetric key and the hacker views this encrypted sensitive data and can obtain it easily and decrypts it using the symmetric key already acquired and the sensitive data is exposed.

To deal with Man in the Middle Attacks, we need to ensure the public key is from the server and not the hacker. We do that with **Certificate Authority**

## Certificate Authority (How it works)
Certificate Authority is a 3rd party entity that is trusted by browsers. They are very few worldwide.

The web server has its private key aand public key and also does the certificate authority.

The browser computer notifies the webserver it wants to send sensitive data (email, password). Instead of the server sending its public key back to the computer, it sends it to the Certificate Authority. The Certificate Authority creates a certificate which is a text files containing the following basic information;
1. Who is being issued the certificate (facebook web server)
2. Issuerers of the Certificate Authority
3. The server public key

The Certificate Authority encrypts the server public key using its Certificate Authority private key and the result is an encrypted server public key. All this is inside the certificate. Just when the server public key was encrypted by the Certificate Authority private key, we say that the Certificate Authority signed this certificate. The Certificate Authority now sends the certificate back to the server. The server sends this certificate back to the computer.

The computer needs to validate if the server public key is coming from the server not from anyone else. The computer now looks at who issued this certificate by checking at its details and it requests for the public key of the issuerer of the certificate. The public key is then used to decrypt the encrypted server public key (signature). If the decrypted server public key equals the server public key, then the computer/browser is sure the public key came from the server.

Then the process we discussed for asymmetric encryption is repeated and data is transferred securely

## Chain of Trust
As mentioned earlier, there are few Certificate Authorities worldwide and if their private keys are compromised, hackers can steal very sensitive information from users of big companies.

To harden the security of these private keys, there are intermediate Certificate Authorities that sit between the servers and the Root Certificate Authorities. Instead of servers reaching the Root CA's, they must pass through these Intermediate CA's who also have their public and private keys and the same process we discussed is repeated. This is to verify if the 'CA' can be trusted and its signature is verified by the Intermediate CA, the Intermediate CA's signatures is verified by the Root CA's private key. The Root CA verifies its signature by its own key. 
 
## References
1. https://youtu.be/EnY6fSng3Ew?si=Dsx7d95dtH23gldq
