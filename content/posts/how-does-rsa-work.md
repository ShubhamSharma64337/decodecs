+++
date = '2025-01-04T22:11:02+05:30'
draft = false
title = 'How Does Rsa Work'
math = true
+++

## Why RSA works?
Prime Factrization, yes, it is the reason RSA algorithm works. Finding our prime factors of 15 or 21 is easy, but for very large numbers, there is still no algorithm which can find out the factors in polynomial time. So even though some algorithm might be able to find out the factors, but it will take it years to do so *(Until Quantum Computers are ready to be used)*.

## Step 1
The first step in the RSA process is to choose two Prime Numbers sufficiently large enough to make it difficult to detect them from their product. For the purpose of simplicity, we will consider the numbers to be 5 and 7.  
Let us name them *p* and *q*.  

\[p=5, \ q=7\]

## Step 2
Now we need to find out another number which is the product of the previously chosen primes. Let us name it *n*  
\[n = 5 \times 7 = 35\]  

## Step 3
One more thing we need to find is the number of whole numbers upto n, which are coprime to n. A quick formula to find this value say \(\phi\) is

\[\phi=(p-1)(q-1)=(4\times6)=24\]

## Step 4
After Step 3, we have the following four values   

\[p=5,\ q=7,\ n=35,\ \phi=24\]  

These four quantities are all we need to find out the encryption and decryption keys.

So let us find our encryption key:

The way to find encryption key e is to choose an e such that it is coprime to both \(n\) and \(\phi\), 

\[1 < e < \phi\]  

## Step 5
Finally, we need to find the decryption key with the following equation -  

\[ d \times e\mod\phi = 1\]  

We usually use values of d larger than \(\phi\). There may be many possible values of \(d\) which satisfy this equation. You just need to choose the one you like.

## Step 6  

Now you can make the finalized encryption keys as a pair of e and n or d and n  

\[E = (e,n)\ and \ D = (d,n)\]

## Step 7  
To convert any message into cipher text, you convert each character into its corresponding ASCII value(let it be \(a\)) and use the following expression to find cipher value \(C\)  

\[C = a^e \bmod n\]

Later, to obtain the decrypted character value (let it be \(D\)), use the following expression  

\[D = c^d \bmod n\]

## End Notes  

One important thing about RSA is that it is not typically used to encrypt the actual payload or message, but to encrypt the Symmetric Cipher Key. The reason is that RSA is a resource intensive algorithm. An algorithm like AES256 is used to encrypt the data and receiver's public RSA key is used to encrypt the Symmetric AES256 Key. Both the AES256 encrypted data and RSA encrypted Symmetric Key is then sent to the receiver. The receiver decrypts the RSA encrypted Symmetric key with his/her private key and then uses the Symmetric Key to decrypt the Payload. As the size of Symmetric Key is comparatively smaller, the Encryption-Decryption process takes much lesser time.

That is all for now. As I learn more about RSA, I will update the blog accordingly.
