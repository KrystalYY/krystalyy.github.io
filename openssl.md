# Openssl

## SSL

SSL(Secure Socker Layer) -> TLS (Transport Layer Security), cryptographic **PROTOCOL** designed to provide communications security over a computer network. It is based on TCP and transparent to application layer protocols.

### Underlying techniques:
* **Asymmetric cryptography**
* **Digital signature**: verify the authenticity of digital messages or documents (hash + payload => digest => encrypt with private key => send => receiver decrypt with public key <- compare -> dogest <= hash + payload)
* **Digital cerfiticate**: prove the ownership of a public key (has digital signature of CA (certificate authority))

### How SSL protects security?
* **Authenticate server**

When client sends request to certain site A 
1. server replies the **digital certificate** that contains the public key of A => we know the authenticated public key that belongs to A
2. then client uses that public key to encrypt request message, only the real server with the corresponding private key can decrypt the message => we are sure the server is the real server for site A

* **Prevent eavesdropping**

When client sends request to certain site A 
1. the 1st request contains a random number C1
2. server reply contains a random number F (and the **digital certificate**)
3. the 2nd request contains a random number C2 encrypted with the public key
4. only the authenticated server which has the private key can decrypt and get the C2 
5. both sides have C1, C2 and F => generate a symmetric encryption key from these 3 numbers and use it for later communication (asymmetric cryptography consumes much more energy)

(step 1 - 4 are the same as step 1 - 2 of **Authenticate server**)

* **Ensure data integrity**

When client sends request to certain site A
1. when server replies the **digital certificate**, it is signed by CA, so the integrity of **digital certificate** is ensured
2. during later communication, the symmetric encryption ensures data integrity


## OpenSSL

An open source, C library of SSL protocol, it contains 3 parts:
* `libcrypto`: cryptographic library
* `libssl`: implementation of all TLS protocol
* `openssl`: command line tool

## Lets Encrypt

Make it possible to set up an HTTPS server and have it automatically obtain a browser-trusted certificate, without any human intervention. 

1. runs a certificate management agent on the server
2. agent proves to the CA that the web server controls a domain (domain validation via different approaches)
3. agent signs a given nounce with private key to prove that it controls the key pairs (authorized key pair).
4. CA verifies, uses the authorized key pair to send request to issue/revoke the certificate
