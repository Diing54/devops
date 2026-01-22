
2025-02-15 22:53

Level : #child 

Tags : [[linux]] ,[[security]] 

# openssh
OpenSSH (Open Secure Shell) is a free, open-source toolset that allows for secure remote login and other secure network services over an insecure network i.e. the internet. It encrypts all traffic during a session and guarantees the integrity of data transfer
1. sshd - The OpenSSH server daemon
2. ssh - Short form for secure shell, provides a secure channel to the command shell on the remote system
3. scp - secure copy, for encrypted file transfer
4. sftp - secure file transfer protocol, provides file access
5. ssh-copy-id - a program for installing your public key to a remote SSH server's authorized_keys file
6. ssh-keyscan - finds and collects public host keys on a network, saving time of looking for them manually
7. ssh-add - adds your identities to the authentication agent, ssh-agent
8. sshfs - Allows you to mount a remote filesystem using sftp
9. ssh-agent - a program that securely manages and stores your SSH private keys in memory, making it easier to authenticate with remote servers without repeatedly entering passphrases. This allows you to authenticate with SSH servers once and then use that authentication for multiple connections without needing to re-enter your key's passphrase

OpenSSH supports different types of authentication;

**Password authentication** - Uses your LInux login and password to authenticate. Simplest but vulnerable when your SSH session is infected with a keylogger which can capture your credentials.

**Public key authentication** - This authenticates with your personal SSH public keys. You need to create and distribute your public keys and you can login only from machines that hold your private key

**Passphrase-less authentication** - Public key authentication without a passphrase. Useful for automated services like scripts and cron jobs

There are two different uses for authentication keys: host keys, which authenticate computers, and public keys, which authenticate users. SSH keys come in pairs, private and public. Transmissions are encrypted with the public key and decrypted with the private key, a brilliantly simple scheme. You can safely distribute your public keys as much as you want, while you must protect your private key and not let anyone else have it. 

Server and client are defined by the direction of the transaction. The server has the SSH daemon running and listening for connection requests, and the client is anyone logging in to this machine via SSH.

sudo ssh-keygen -A

ssh-keygen: generating new host keys: RSA DSA ECDSA ED25519

server’s private host keys are owned by root, read-only

public keys, which are owned by root, read-write for root, and read-only for everyone else

Now take a look at /etc/ssh/sshd_config. When you change this file(Uncomment the options you want to use or change.), reload sshd to load your changes:
$ sudo systemctl reload sshd.server

Any port scanner will find your open ports, and attackers will attempt brute force
password cracking. Attackers still target the default SSH port 22 the most. Changing the port won’t reduce this risk very much, but it should reduce the number of entries in your log files. When you use alternate port numbers, first look in /etc/services to find unused ports, and then record the ports you use in this file.

Public key authentication is very strong and cannot be brute-forced like password logins (see Recipe 12.7). The trade-off is less convenience, as you can log in only from machines that have your private key.




## References
