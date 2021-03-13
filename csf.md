# Cyber Security Fundamentals Notes
## Week 1
### Lecture Notes

**Assets** : things that need protection and are usually digital, such as files

_Some assets, such as keys and passwords, are important for cyber security but are not stored as files._

**Aspects of asset protection:**
- Confidentiality
- Integrity
- Availability
- Authenticity
- Accountability
- Non\-repudiation

**Confidentiality**

This implies an access control mechanism:
- Users must be identified
- Users are then authenticated
- Users are then authorised to access various assets. The access can be controlled, for example, with read, write and execute permissions.

**Privacy** : the confidentiality of personal information

**Integrity**
- Ensure nothing is lost or deleted either accidently or deliberately
- Make sure nothing is change 

_examples:_
- Use a message digest to detect if a file has been changed
- Use a public key certificate for network communications

**Availability**
- Have capacity to meet demands
- Resources are allocated fairly
- Fault tolerance and recovery from failure

_examples:_
- Keep up\-to\-date backups
- Protect against denial of service attacks

**Authenticity, Accountability, Non\-repudiation**

_Authenticity_
- The document has not been replaced by another one
- The person accessing the system is who they say they are

_Accountability_
- An audit trail is provided
- For example, logging all access to an asset

_Non\-repudiation_
- The author / owner of a document cannot say it was not them

**Threats**
- What are we protecting assets from? Threats
- Different types of asset security are subjects to different threats

_A threat against confidentiality will be different from a threat against availability._

- When protecting an asset, we need to consider all possible threats

_If an attacker thinks of a threat that we have not thought about then they will get through_

There are many different techniques to make sure we have considered all threats:
- Standard lists of threats
- Standard techniques for dealing with them

**Vulnerabilities**
- Different ways of protecting assets lead to different vulnerabilities
- We can check the security of a system in two different ways.

_From the viewpoint of an attacker. What are the attackers goals? How can they achieve them?_

_From the viewpoint of the defender. What are the system’s vulnerabilities?_

- All the vulnerabilities collected together are called the attack surface. As a defender we want to reduce the attack surface

**Protection and Risk**
_Protecting our assets from threats leads to a discussion of risks_
- Protection has a costs
- The value of an asset might be less than the cost of protecting it
- Some forms of protection may be cheaper than others

- Risks involve the probability of something happening, together with the effect of the attack succeeding

_Techniques for dealing with risks:_
- Complete protection prevents the attack from happening
- Reduce the risk, making it less likely
- Mitigate the risk, reduce the effects
- Take out insurance, reduce the cost of rare expensive events
- Liability dumping, someone else pays the cost

**Technical Solutions are Essential**
_Unbreakable encryption to keep secrets and ensure data is not changed_
- The algorithm can’t be broken without the key
- Keys must be kept secret

- Digital signatures to allow legally enforceable contracts so signatures cannot be forged
- Secure message digests to provide document fingerprints without revealing the document content
- Secure protocols to make sure the basic building blocks of encryption signatures and message digests are used correctly _so that it is not possible to bypass the use of a key_

**Human Problems**
- Users may not comply with security policies
- Organisations may develop policies that users find very difficult to use
- Developers may not adhere to security guidelines when building systems
- Regulatory bodies may not provide appropriate policies and rules and then may not enforce them

**socio\-technical systems** : consider people as well as the technical aspects of any system

#### Technical Solutions

**Overview**
- Technical aspects of cyber security use algorithmsto keep information safe
- Different protocolsuse the same algorithms in different ways
- Many protocols solve problems by transforming them into simpler problems
- We will start with the problem of keeping a secret: confidentiality
- We will then consider communicating a secret to someone else

**The Cast**

_It is conventional to use the following characters when describing protocols:_
- Alice, Bob, Carol and Dave have secrets to share
- Eve the eavesdropper tries to find out the secrets and cause other problems
- Trent is a trusted third party

**Keeping A Secret: Memorise**

- We will start with the simplest cyber security problem, keeping a secret
- Our first protocol is to memorise the secret
- This is only appropriate if the secret is fairly short and easy to remember

**Memorise: Threats**

_Forgetting the secret_
- If the probability is high and the value of the secret high then we can mitigate this threat by writing the secret down
- This is the next protocol

_Trickery, such as entering your password in a phishing attack_
- This is a human factors problem

_Coercion, someone forces you to reveal your secret_
- There is a technical solution to this problem: a distress key
- Systems can be set up to take two keys or passwords
- One is the real key, the other produces realistic looking but false information
- This relies on a secret encryption algorithm

**Keeping A Secret: Paper**

_If the secret is too long to remember, the next protocol is to write it down on a piece of paper_
- There is a limit to how long the secret can be
- It can be inconvenient to use if it has to be entered into a computer

_The confidentiality threat relies on the attacker having physical access_
- They can search our home or office

_An availability threat is losing the piece of paper_
- This can be mitigates by backups, making a copy
- All copies now need to be secured
- We must keep track of all copies
- destroy all copies when they are no longer needed

**Paper : Hiding and Safe**

_If the attacker has physical access, this can be mitigated by Hiding in Plain Sight_
- There may be lots of other pieces of paper
- The attacker will have to recognise the secret when they see it
- The attacker will have to know the secret exists
- But we might not be able to find it ourselves!

_A determined search can uncover the secret but it can be expensive in manpower_

_Another protocol is to lock the piece of paper in a safe_
- This uses the simpler protocol: Memorise
- The combination to the safe must be remembered

**Paper: Encryption**

- The secret can be encrypted and written on paper.
- The plain text version must be erased

_A shredder is ineffective:_
- The strips can be reassembled but this is currently very labour intensive
- The strips can be digitised and the document reassembled using jigsaw puzzle algorithms

**Keeping A Secret: Computer File**

- Most documents are prepared on a computer, which introduces a number of vulnerabilities that can be exploited by attackers
- The program used to create the document may make periodic backups, and so there are many different versions of the file that need to be protected
- It is easy to create copies of the file

_Deleted files can be recovered:_
- Deleting a file just puts the blocks making up the file into recycling, to be reused as part of another file later on
- The actual data will still be there until it is overwritten

**Computer File: Hide in Plain Sight**

- This protocol relies on there being a large number of files on the computer e.g document stored in an obscure directory
- It could rely on password access to the computer
- For now, assume an attacker has already gained access to the computer

**Hiding a File: Search Tools**

- The main problem with data on a computer is that an attacker can use automated tools to make the attack
- Data science tools can classify natural language files based on content
- Image files can also be classified
- The attacker can search for specific content, collecting all files matching the search terms

**Hiding a File: External Storage**

- The file can be stored on an external file system such as a USB drive
- The original file on the computer used to prepare it must be erased, also any backups
- The attacker now needs physical access to the storage device
- Once this is achieved, then this becomes the hide in plain sight protocol

**Hiding a File: Steganography**

**Steganography** : secret writing

_In a modern computer setting it means hiding a secret file inside another file:_
- The payload is the secret document
- The cover object is an innocent file with no secret message
- The payload is combined with the cover object to produce the stego object

- Image and video files make good cover objects because they are large files with more precision than is needed
- Special programs are needed to insert and extract the payload

**Steganography: Attacks**

- It is assumed that the original document has been erased
- If the attacker has a file suspected of steganography then there are programs that look for signs that steganography has been used

_A histogram of the colour bytes in an image. Some steganographyalgorithms distort the byte values in a standard way._

- Try a range of standard steganography programs to try and extract the payload
- A more general attack is to distort all images posted to for example, a social media system destroying any possible hidden payload

**Computer File: Encryption**

- An encryption program takes plaintext as input and produces ciphertext as output
- A decryption program takes ciphertext as input and produces plaintext as output
- Decryption must undo encryption
- Encryption followed by decryption must produce the same output as the original input
- The original plaintext document must be erased

_This protocol has a time limited vulnerability: while the plaintext document is in the file system_

**Protocol: Secret Encryption Algorithm**

- The details of the encryption and decryption algorithms are kept secret

_Threat: finding the algorithms_
- The algorithms will be computer programs
- They cannot be encrypted because they must be run on the computer

- This protocol uses the hiding in plain sight protocol for the algorithms

_Threat: guessing the algorithm used_
- Most people cannot invent a good new algorithm
- A running key cipher using a pseudo-random number generator is very common among home-made algorithms

**Protocol: Public Algorithm, Secret Key**

- The encryption and decryption algorithms are public
- Encryption and decryption take an additional parameter, the key
- Knowledge of the algorithm without the key is useless
- The algorithms can be peer\-reviewed for safety
- This protocol then reduces to the the “Keep a Secret” problem for the key

**Attacking Single Key Encryption**

_Ways to attack crypto algorithms:_
- Attacking the algorithm. The algorithm may have flaws that can be exploited
- Attacking the system. This mainly involves trying to find the key, which may be exposed on entry, in transit or in memory
- Brute force attacks when the key length is too short.  This involves trying all possible keys
- Exploiting the entropyof the key space.  Users may choose weak and predictable keys.  A dictionary of common keys is tried

**Problem: Many Secret Documents**

- Users typically have many documents that the want to keep secret
- The standard protocol is to use the same key for all documents

_This is vulnerable if it is possible to find the key from knowledge on one document:_
- The plaintext may also be available for a known plaintext attack
- One of the documents may have a known special structure

- Having many different keys fails for human factor reasons

#### Communicating a Secret

**Problem: Communicating a Secret**

- Alice wants to send secret information to Bob without Eve finding out
- This is usually a confidentiality problem
- It can also be an integrity problem if the messaged is changed before it is forwarded

_It can also be an availability problem:_
- If Eve prevents Bob from receiving the message
- How does Bob know that Alice has sent a message?

**Protocol: Secure Transmission Medium**

- Alice and Bob meet in a secure room or location

_Electronic transmissions are easy to intercept:_
- Transponders can be attached to Ethernet cables and the traffic analysed
- Email is stored and can be analysed later

**Protocol: Hiding in Plain Sight**

- Alice could send Bob an email or phone him

_The large volumes of data mean messages may be ignored:_
- If automated tools do not find them suspicious
- And neither Alice nor Bob is under surveillance

**Protocol: Secure Preparation**

- Alice encrypts the message in a secure area
- It is transmitted by an insecure medium

_We assume that Eve can intercept, see and replace it_

- Bob decrypts the message in a secure area
- Encryption followed by decryption cancel each other out

**Secure Area**

- Don’t put the plaintext on a distributed files system

_It will travel to another computer via an insecure Ethernet cable._

- Watch out for keystroke logging programs and other spyware
- Any computer connected to the Internet can potentially be compromised

_Use a stand-alone computer not connected to anything._

- The encrypted message will have to be transferred to a network-facing computer

**The Encryption Distribution Problem**

- Alice and Bob need to know how to encrypt and decrypt the plaintext
- They must use a compatible method
- They must communicate this information by a different protocol
- They might meet in a secure area

**Protocol: Use a Secret Algorithm**

- Keep the details of the algorithm secret

_This is bad for two reasons:_
- The algorithm designers know the secret and may be physically at risk
- Peer review of a public algorithm reduces flaws

**Protocol: Public Algorithm, Secret Key**

- Details of the encryption and decryption algorithms are public
- They have a parameter, the key, which is kept secret
- Knowledge of the algorithm is useless without the key
- Also called a **one key system** or **symmetric encryption** 

**Key Distribution Problem**

- The encryption distribution problem now becomes the key distribution problem
- The key must also be stored safely, the key storage problem
- The problem of transferring data between Alice and Bob has been transformed into an easier problem: The problem of transferring a key
- The same key can be used for several different communication sessions

#### Common Encryption Algorithms

**Common Single Key Encryption Algorithms**
- **DES** : Data Encryption Standard
- **AES** : Advanced Encryption Standard

_Also consider an erase algorithm_

**DES**

_A block cipher:_
- The data is divided into blocks, each 64 bits long
- The last block may often be short and so is padded to expand it to 64 bits
- This makes a statistical attack harder because it is less likely that two blocks will be the same

_It started as project Lucifer at IBM_
- Several small transformations are repeated one after the other
- Each has a different sub-key, generated from a master key \- using small transformations
- It had a key length of 128 bits

_The NSA (US National Security Agency) modified Lucifer slightly and it was adopted in 1977_
- They reduced the key length to 56 bits, making a brute force attack easier
- It uses very simple operations so that it is fast and easy to implement in silicon

_The NSA did not publish an analysis of its security, encouraging some to think that they had inserted a backdoor_
- No back door has been found but NSA later said that they had changed the algorithm to protect against differential cryptography
- Rival algorithms, such as IDEAL in Europe, were later found to be vulnerable to differential cryptography

**Differential Cryptography** : a branch of study in cryptography that compares the way differences in input relate to the differences in encrypted output

**Breaking DES**

- The short key length of 56 bits makes DES vulnerable to a brute force attack where all keys are tried
- On 29th Jan 1997 the RSA organisation offered a prize of $10,000 to the first person to find the key to some cipher text when they are given 3 blocks of plain text 
- In 1976 Hellman and Diffie estimated that it would cost $20 Million to build a special purpose machine to crack DES in 1 day
- In 1998 The Electric Frontier Foundation built a DES cracker for$250,000.  It could search all possible keys in 9 days
- So DES lasted 20 years before it became easy to crack

**Triple DES**
- A lot had been invested in DES and so efforts were made to improve the way it was used
- The key length can be doubled by using the DES algorithm twice with 2 different keys

_This is vulnerable to a meet\-in\-the\-middle attack_

**meet\-in\-the\-middle attack** : a generic spac\e–time tradeoff cryptographic attack against encryption schemes that rely on performing multiple encryption operations in sequence

- Three key triple DES is not vulnerable and has a key length of 3 * 56 = 168 bits

C = E<sub>K3</sub>\(D<sub>K2</sub>\(E<sub>K1</sub>\(P\)\)\) where E is encryption and D is decryption

_This order is used so that it will work with old data encrypted with just one key._

C = E<sub>K</sub>\(D<sub>K</sub>\(E<sub>K</sub>\(P\)\)\) = E<sub>K</sub>\(P\) as one E D pair cancels out

**Aside: Statistical Attack**

_A statistical attack tries to look for single letter, double letter \(digram\) and triple letter \(trigram\) combinations_
- The frequency in plain text will vary greatly
- This may cause varying frequencies in the cipher text
- This can help the attacker

_Statistical attacks were a serious problem in pre-computer algorithms but modern techniques largely prevent them_
- Compressing before encryption: compressed data looks more random
- The use of block ciphers
- Cipher block chaining and the use of an initialisation vector 

**AES**

- The NIST \(US National Institute for Standards and Technology\) started a search for a replacement for DES once its deficiencies became apparent

_The design of AES was performed in public, unlike DES_
- Entries were invited from around the world
- The algorithms and analysis were made public
- Comments were invited from any organisation

- Applicants were reduced to five for the final evaluation

- This is a block algorithm with block sizes of 128, 192 or 256 bits and key lengths of 128, 192 or 256 bits \- smaller is faster
- It repeats a few simple steps several times in rounds and each round has its own sub-key generated from a master key, just like DES
- The DES decryption algorithm used the same steps as for encryption, just in the reverse order
- It uses simple mathematical operations
- DES used lookup tables to what seemed like random numbers

**The Competition**

- MARS from IBM
- RC6 from RSA Security
- Twofish from Counterpane 
- Serpens from Ross Anderson, Eli Bihan, Lars Knudsen 
- Rjindael from Joan Daemen and Vincent Rjimen 

_The winner, announced in 2000, was Rjindael_

**Cipher Block Chaining**
- A data file will have many blocks, all of which must be encrypted

_A simple way of doing this is to encrypt all the blocks individually_
- This is called using an Electronic Code Book
- It is vulnerable to a statistical attack if the message is long
- If the plain text has an internal structure, this might be reflected in the cipher text
- Two files with the same initial blocks and encrypted with the same key will produce the same cipher text.  Many word processors start each file with the same boilerplate code

_In cipher block chaining, each block of plaintext is xored \(exclusive or\) with the previous block of cipher text before encrypting_
- Regular patterns in the plain text do not appear in the cipher text
- C<sub>i</sub> = E<sub>K</sub>\(C<sub>i-1</sub>⊕P<sub>i</sub>\) where ⊕ is the exclusive or operator

_xor has the useful properties:_
- a ⊕ a = 0
- a ⊕ 0 = a
- x ⊕ y = y ⊕ x

_We can get the equation for decryption by decrypting the encryption equation:_
- D<sub>K</sub>\(C<sub>i</sub>\) = D<sub>K</sub>\(E<sub>K</sub>\(C<sub>i-1</sub>⊕P<sub>i</sub>\)\) = C<sub>i-1</sub>⊕P<sub>i</sub>
- Decryption undoes encryption
- Now xor with the previous cipher text
- C<sub>i-1</sub> ⊕ D<sub>K</sub>\(C<sub>i</sub>\) = C<sub>i-1</sub> ⊕ C<sub>i-1</sub> ⊕ P<sub>i</sub> = 0 ⊕ P<sub>i</sub> = P<sub>i</sub>

**The Initialisation Vector**
- We have to do something different to encrypt P<sub>0</sub> since C<sub>-1</sub> does not exist
- We create a random block called the initialisation vector and use it as C<sub>-1</sub>
- It must be transmitted as plain text with the file so that the file can be decrypted
- If we have many documents all starting with the same blocks, their cipher text will be different because they will have different initialisation vectors

**Erase Algorithm**

- The easiest way to erase the data in a file is to overwrite it with random values before deleting the file
- The blocks are now rescheduled for recycling, but do not contain the original data
- This is easy to do in Java

_It is possible to examine the physical file storage device and several different levels of data_
- Erased data can be recovered, say from the magnetic material

- The technique to beat this is to overwrite with different random data 7 times

# Week 3
### Slides

#### Protocol: Public Key System

_Two different keys are used_

A **public key** is used for encryption:
- Anyone can access this key
- There is no key distribution problem

A **secret key** is used for decryption:
- Knowledge of the public key will not lead to knowledge of the secret key

There is usually a single algorithm:
- Used with the public key encrypts
- Used with the secret key decrypts

#### Authentication Problems

_There is no key distribution problem because the encryption key is public._

There is a **key authentication** problem:
- How does Alice know that the public key is really Bob’s?
- The transmission medium is insecure and so it could be substituted

Also the **message authentication** problem:
- How does Bob know the message is from Alice?
- Anyone can get Bob’s public key to encrypt a message

#### Man in the Middle Attack

- Bob sends his public key to Alice, but it is intercepted by Eve
- Eve sends her public key to Alice, pretending it is Bob’s
- Alice encrypts the plaintext with Eve’s public key \(thinking it is Bob’s\)
- Alice sends the ciphertext to Bob
- Eve intercepts the ciphertext and decrypts it with her secret key
- She reads the plaintext and discovers what Alice has to say
- She encrypts it with Bob’s public key and forwards it to Bob
- Both Alice and Bob are unaware of this attack

#### Problem: Authentication

Secrecy and authentication are nearly equivalent in one key systems:
- Alice must know the secret key to encrypt a message
- She is thus authorised to use it

_If several people share the secret key then it is not possible to determine which of them encrypted the message._

#### Protocol: Public Key Digital Signatures

- Alice encrypts her plaintext document with her secret key, rather than Bob’s public key
- She sends the document, together with the encrypted version, to Bob
- Bob decrypts the encrypted version with Alice’s public key and verifies that they are both the same

_The encryption and decryption operations must cancel each other, no matter which order they are used._

#### Properties of Digital Signatures

- Bob can verify the signature without Alice’s help
- The signature cannot be forged because only Alice knows her secret key
- The signed document in unalterable, except by Alice
- The signature cannot be transferred to another document

#### Secrecy and Authenticity

Signing a document does not make it secure:
- Notice that Eve could also undo the signature and read the document
- She can get Alice’s public key

- Encrypting a document does not guarantee authenticity
- Signing and encrypting a document can provide both secrecy and authentication

#### Public Key Certificates

In many cases the plain text document to be signed contains a public key:
- The signed key plus other information is called a public key certificate
- It is signed by Trent, a trusted third party
- Trent’s public key must also be distributed in a secure way

Bob can distribute his key in a public key certificate \(Provided Alice already has Trent’s public key\).

_This defeats a man in the middle attack._

#### Problem: Authentication without Revelation

- In the preceding example the signed document was the same length as the unsigned document
- This can be inconvenient, especially when many signed documents must be stored

- If just a signature is added, then the contents of the signed document also becomes public knowledge
- It can be seen using the public key to undo the signature

#### Protocol: Message Digest

**Message Digest** : a condensed version of an original document. It is typically around 256 bits long.

It is a unique short description of the original document:
- Like a fingerprint
- The chance of two different documents producing the same message digest is very low

_The algorithm to produce a message digest is sometimes called a hash function._

#### Message Digests and Signatures

- Giving someone a signed copy of a message digest is equivalent to giving them a signed copy of the document
- If the signature needs to be checked then the message digest can be calculated from the original document a second time
- The original message digest can be recovered by removing the signature
- If both the message digests are the same then the signature is valid

#### Public Key Encryption: RSA

- The RSA algorithm is based on number theory

_Its security is based on the difficulty of factoring an integer that is the product of 2 large prime numbers:_
- Some problems, called NP\-Complete problems, are thought to be intrinsically difficult and no quick solution will be found
- Integer factorisation is not one of these
- A fast solution may be found, in which case the RSA algorithm will no longer be any good
- A fast algorithm to prove whether an integer is a prime number or not was found relatively recently

RSA was invented by an English mathematician Clifford Cocks on his first day of working for GCHQ in 1973 but was kept secret until 1997.

#### The RSA Algorithm

- Two random prime numbers p and q are created and kept secret
- Their product, n = p \* q, is calculated and is public
- Its inverse e is calculated and is public: d \* e = 1 modulo \(p\-1\)\(q\-1\)
- This inverse uses modular arithmetic, so that 1/d is still an integer: \(d \* e\) % n = 1 for some n
- If \(p\-1\)\(q\-1\) and dhave a common factor then e does not exist

- The plain text is turned into a series of integers all < n
- The public key is \(e, n\) and the cipher text C = P<sup>e</sup> % n
- The secret key is \(d, n\) and the plain text P’ = C<sup>d</sup> % n
- Some number theory makes sure that P’ = P
- n, d and e are typically 4000 bits long, so it is very slow

The encryption and decryption algorithms are the same, exponentiation.

We can break this algorithm if we can factor large integers:
- We know n and e
- Finding pand q lets us solve the equation for d, the decryption parameter

It is possible to factor quite large integers:
- n, d and e must be quite large
- Hence the algorithm is very slow

#### Guidance on RSA Key Sizes

- 896 bits until 2004
- 1024 bits until 2009
- 1152 bits until 2010
- 1408 bits until 2014
- 1984 bits until 2016
- 2048 bits until 2030
- 3072 bits **beyond** 2030

#### Public Key: Diffie\-Hellman Key Exchange

- The Diffie\-Hellman key exchange uses an exponential algorithm to generate a single key that is shared by two people
- Both parties contribute to the key by sharing information over an insecure communication channel

Each party keeps some information secret.  This secret information is vital to be able to construct the key:
- Each person generates a public and secret number
- They exchange the public numbers

- The key cannot be generated from the public information
- This algorithm forms the basis for session key construction in many internet applications 

#### The D\-H algorithm

Alice and Bob both use two public numbers:
- p, a large prime
- g, a primitive root of p
- Most protocols have a standard set of values to use

Alice and Bob create random numbers, X<sub>A</sub>, X<sub>B</sub> less than p which are their secret keys

They both calculate Y = g<sup>X</sup> % p and exchange them, these are their public keys

Alice calculates K = Y<sub>B</sub><sup>X<sub>A</sub></sup> % p = \(g<sup>X<sub>B</sub></sup>\)<sup>X<sub>A</sub></sup> % p = g<sup>X<sub>A</sub>X<sub>B</sub></sup> % p

_Bob does the same thing and both keys are identical._

#### The Security of D\-H

- g being the primitive root of p means that  Y = g<sup>X</sup> % p has a solution for every value of Y < p
- This equation is called the discrete logarithm problem: Find X given Y and g, p

Number theory shows that this is equivalent to factoring:
- Finding a quick way of factoring numbers will also break D\-H
- Finding a quick way to solve the discrete logarithm problem will also break RSA

The lengths of p, X and Y are similar to the RSA length:
- Very long
- Leading to a slow algorithm

#### Elgamal Public Key Systems

- This system is based on Diffie\-Hellman key exchange

It is just as secure as RSA:
- It is not quite as convenient as RSA
- But it can be used without as license

- It can be used to sign documents
- The maths are slightly more complex
- Elgammal was one of Martin Hellman’s PhD students at Stanford

#### Elliptic Curve Cryptography

- Ellipse: curve with equation x<sup>2</sup> / a<sup>2</sup> +  y<sup>2</sup> / b<sup>2</sup> = 1

_Different values of a nd b give different ellipses._

- Elliptic curves are not ellipses but curves that arise in attempts to find a function for the distance round an ellipse
- General elliptic curve with parameters a and b: y<sup>2</sup> = x<sup>3</sup> +ax + b

#### Elliptic Curve Crypto

- We have a set of all points on the curve
- We define addition of two points by drawing a line connecting the points and finding the third point where this line cuts the elliptic curve
- This produces a cubic equation in x and so in general any line will cut the curve in three points

There are special cases when two of the points are the same:
- The point at infinity is like 0 with normal addition
- A line parallel to the y\-axis that just touches the curve will cut the curve again at infinity

- There are also cases where the line only cuts the curve once

This lets us define an operation that we can call multiplication:

- If A and B are two points on the curve then they define a unique line that goes through them both
- If the 3<sup>rd</sup> point where the line cuts the curve is called C, then we can write: C = A \* B, defining multiplication

- Real number arithmetic is not used because cryptography works better with integers
- Integers mod n or similar approaches are used

#### Advantages of Elliptic Curve Cryptography

- Security using elliptic curves is based on the hardness of a discrete logarithm problem

However the key sizes are much smaller:
- 256 bit ECC provides the same security as 3072 bit RSA
- NSA \(National Security Agency\) uses 384 bit keys

- NIST \(National Institute for Standards and Technology\) recommended a particular curve that was later found suspect and deprecated by RSA 
- The different elliptic curve called Curve25519 is now popular: y<sup>2</sup> = x<sup>3</sup> + 4866662x<sup>2</sup> + x

#### Public Keys and Elliptic Curves

- Public keys systems based on ECC have been defined
- They can also be used in random number generators
- They can also be used in factoring algorithms

#### More on message digests

**Requirements of Message Digests:**
- Given the message, it is easy to compute the message digest
- Given the message digest, it is hard to compute the message
- Given a message M, it is hard to find another message M' with the same message digest.  Preimage resistance of collisions
- It should be hard to find two random messages M and M' with the same message digest
- This means that message digests must be long enough

#### A Survey of Hash Functions

- Functions to generate message digests are called hash functions

- MD5 was invented by Ron Rivest, 128 bit keys and vunerable to birthday attack

- SHA\-1 was produced by NIST, 160 bit key also vunerable to birthday attack

- SHA\-2 also produced by NIST, with 4 versions:
- SHA\-256 \(or 224\); SHA\-512 \(or 384\) bit
- Secure so far.  Most widely used

- SHA\-3 public competition with adoption in 2012

#### SHA-3 Competition

- Following the success of the AES competition, NIST announced a competition for a message digest, to be called SHA\-3, in November 2007
- 64 entrants were submitted by October 2008

- 51 were accepted for the first round and public scrutiny began
- About 20 were broken

- 14 made it into the second round

5 finalists were announced in December 2010:
- BLAKE
- Grøstl based on AES
- JH
- Keccak
- Skein

- All finalist’s functions were tweaked in response to public analysis
- Winner, announced in October 2012, was Keccak, it was significantly faster than the others
- NIST wanted to change Keccak slightly to trade off security for speed, but backed off because of the climate of mistrust

#### Random Numbers

- A real random number sequence is a sequence of numbers which cannot be repeated if the generator is run again
- A pseudo\-random number sequence looks like a real random number sequence but is repeatable
- A cryptographically secure pseudo\-random number sequence cannot be predicted from knowing some of the numbers in the sequence

#### Generating Real Random Sequences

- Computer Clock: Taking the middle chunk of bits from a very accurate clock

Keyboard Latency:
- Measure the time between successive key strokes, which is quite random
- This is OK for generating short random sequences
- Needs a user to be present to enter the keystrokes

- Using random noise: Measure the time interval between random events such as atmospheric noise being above a certain threshold

#### Pseudo\-Random Sequences

- Pseudo random sequences are sequences that are completely predicable from the starting value
- Their distribution looks random: The frequency distribution of values, pairs of values etc is the same as a random sequence
- They are useful for simulation
- They can sometimes be useful for encryption, but care must be taken

#### Problems with PRNG: Netscape

- In 1996 two Computing students discovered a flaw in Netscape’s PRNG that enabled them to easily brake SSL

_SSL_ : Secure Sockets Layer, used for internet security

At that time, the USA government viewed crypto products as munitions and prevented their exports to non Americans:
- The USA SSL key length was 128 bits, which would take a long time to break with a brute force attack
- Export versions had a key length of 40 bits, which would require 2<sup>40</sup> ≈ 10<sup>12</sup> attempts
- Just about anyone could break the export version with a brute force attack

- A random number generator was called 4 times to generate the key
- The weakness was in the way the initial seed was chosen: It was based on the process number, the parent process number and the time in milliseconds
- Communications were initiated by one party sending a random number and the other replying with the encrypted version
- Just 10<sup>6</sup> attempts were needed to break both the USA and export versions of Netscape SSL
- It took 25 seconds on a standard PC of the time

#### Dual\_EC\_DRBG

- This stands for Dual Elliptic Curve Deterministic Random number Generator

In 2007 NIST issued a new cryptographically secure random number generator standard with 4 algorithms:
- The recommended, and default, algorithm was Dual\_EC\_DRBG
- It was recommended by NSA

_It was an order of magnitude slower than the others._

#### Crypto 2007 Conference: Aug 2007

- Dan Shumow and Niels Ferguson from Microsoft demonstrated that the algorithm had some secret parameters that were used to derive the public parameters
- These secret parameters could be used to recover all the internal workings of the PRNG from 32 bytes of output
- Prominent figures in the crypto community at the times, such as Bruce Schneier, recommended that Dual\_EC\_DRBG should not be used
- This lead to doubts about all the curves recommended by NIST and the adoption of the different curve25519

#### OpenSSL

- This is an open source library of crypto implementations
- The user could choose between several different pseudo\-random number generators
- A coding bug discovered in December 2013 meant that it was impossible to actually choose Dual\_EC\_DRBGas the random number generator
- There were no bug reports, and so no one had actually used it

#### NIST and RSA

- The RSA organisation used Dual\_EC\_DRBG in its product Bsafe as the default, on recommendation from the NSA, starting in 2004
- In September 2013 NIST strongly recommended that Dual\_EC\_DRBG no longer be used
- RSA then also recommended that it not be used

## Week 3
### Slides
#### Man in the Middle Attacks

* **All public key systems** are vulnerable to a man in the middle attack
* If Alice and Bob are communicating, then Eve has to make sure that all communications go through her
* If Bob is sending his public key to Alice then Eve grabs it and replaces it with her own public key
* When Alice sends an encrypted message, encrypted with what she thinks is Bob’s public key, Eve grabs it and decrypts it, since it was really encrypted with her public key
* She can alter it, encrypt it with Bob’s public key, and send it to Bob

#### Public Key Certificate

* A public key certificate is a document that contains a public key, the owners ID and other application specific information
	* It has been signed by Trent, a trusted third party
* **Attack**: Eve creates a fake certificate that pretends to contain Bob’s public key, but actually contains her public
	* Eve cannot sign it because she does not have Trent’s secret key
	* Trent must keep his secret key secret
	* There must be a mechanism for Trent to revoke their public key and issue new certificates if their secret key is compromised
* **Attack**: Eve asks Trent to sign her public key certificate, pretending to be Bob
	* Trent must verify the owner’s ID before signing the certificate.
	* The certificate must contain the owner’s ID as well as the public key
* **Attack**: Eve sets up her own certifying authority
	* In practice, there are many certifying authorities, not just one Trent
	* There must be a higher organisation to certify certifying authorities
* Alice must already have Trent’s public key so that she can unlock the certificate.
	* This is called a master key
	* Getting this should be an easier problem than getting Bob’s public key

#### Certificate Chains

* It is possible to have several layers of public key certificates
* Trent’s public key can be distributed as part of a public key certificate signed by a national certifying authority
* Alice just has to have the correct public key for the national certifying authority
	* An even easier problem to solve
	* She uses it to get Trent’s public key from Trent’s certificate
	* She uses Trent’s public key to get Bob’s public key from Bob’s certificate
* The certifying authority’s key can be embedded in hardware.
	* Tamper resistant or tamper evident

#### Chip and PIN

##### Context

* Chip and PIN cards have a chip embedded in the card to allow programs to run on the card
	* They are called ICC or Integrated Circuit Cards
	* They are also called smart cards
	* Old style cards just contained a magnetic strip
* They are part of the EMV standard
	* Europay, Mastercard, Visa
	* Europay became part of Mastercard in 2002
* They use a public key infrastructure

* Smart cards have been introduced to combat fraud
* Implementing chip and PIN cost around £1 billion
* The chip addresses counterfeit fraud where cards are cloned
	* It verifies the card
* The PIN combats signature fraud by verifying the cardholder
* Other advantages include not having to store signed copies of card vouchers

#### Liability Shift

* Starting from 2005, the liability for fraudulent transactions at the point of sale shifted from the bank to the retailer if the retailer is not using chip and PIN
* On the other hand, if the bank does not support chip and PIN then they will be liable for losses
* This changed on 1<sup>st</sup> November 2009, when the banks had to prove that the customer was at fault when money was taken from an account
* This was a result in failures of the Chip and PIN system

#### Failures

* In 2006 Shell petrol stations were attacked
	* Their implementation of the protocol allowed customer data to beleaked and around £1 million was stolen from their customers
* In October 2008, PIN terminals were targeted during their manufacture in China, again leaking customer data
* A man in the middle attack was successfully demonstrated in 2009

#### Operations Provided

* The card can be authenticated by a terminal in two ways:
	* **Static Data Authentication** – magnetic strip
	* **Dynamic Data Authentication**  – chip on card
* Transactions and messages can be authenticated using a signed message digest
	* This is called an application cryptogramor a message authentication code \(MAC\)
* Transactions and messages can be secured by encryption
	* This is single key encryption after the user has been verified
* PIN encryption at point of entry \(optional\)
	* Signing a transaction is the alternative

#### Algorithms Used

* Algorithms
	* 3\-DES, RSA, SHA\-1 \(Secure Hash Algorithm 1\)
	* Possibly new algorithms in the future \(e.g. ECDSA\) Elliptic Curve Digital Signature Algorithm
* Mechanisms
	* RSA digital signatures and public key certificates
	* Card unique 3\-DES keys, derived from Master Keys
	* Unique session keys for encryption and MAC

#### EMV Public Key Certificates

**Components**

* Certificate core
	* General information about the user and the application
* Public Key
	* User’s public key \(including remainder\)
	* EMV formatting
* Message digest
	* Message Digest of data
* Signature by a Trusted Third Party

#### Public Key Certificate Validation

* The public key of the Trusted Third Party \(who signed the certificate\) is used to decrypt the certificate, thus revealing the data
* The EMV formatof the revealed data \(header, trailer, certificate format\) is checked
* The message digest of the revealed data is calculated and check that it is the same as the message digest in the certificate
* The public key exponent and modulus, \(e, n\) is extracted from the revealed data
* The public key remainder found on key certificates is an optimisation parameter designed to speed up the calculations
	* RSA exponential calculations are slow

#### Parties to the Transaction

* Payment System **Certifying Authority**: the trusted third party in charge of the whole process
* The Issuer: a bank
* Card associated with a customer
	* **Primary account number**: the 16 digit number on the card
* Acquirer: the merchant selling something to the customer
* The Card terminal

#### Static Data Authentication

* A Certifying Authority public key certificate is stored in the terminal in unsigned form
	* Protected against change, tamper resistent
* A bank public key certificate, signed by the Certifying Authority is stored on the card
* Static Data on the magnetic strip includes:
	* Primary account number
	* Application Expiry Date
	* Bank parameters
* Static Data Authentication is used to make sure that that certain data elements on the card have not changed since the card was issued

**See CHIP AND PIN WEEK 3 FOR STATIC DATA AUTH DIAGRAMS**

#### Dynamic Data Authentication

* Dynamic data authentication provides authenticity and integrity of the Card
* Allows detection of unauthorised alteration of Card data after the card has been personalised
* Prevents replay attacks and Card counterfeiting
* Dynamic data authentication involves a Terminal **unpredictable number** \(UN\) or \(nonce\) and calculations on the Card
	* The UN is signed by the card’s secret key
* 3 public / secret key pairs are used in this certificate chain

**See CHIP AND PIN WEEK 3 FOR DYNAMIC DATA AUTH DIAGRAMS**

#### What Happens in Detail

* Power up the chip and negotiate the communications protocol
	* There will be different versions of the protocol
* Process the list of EMV payment applications supported by the chip, for example, credit and debit
	* Give a choice to the cardholder or ask for their confirmation
* Select the chosen application and read the relevant information from the chip
* Validate the chip data using the public key infrastructure
* Check the PIN
	* If the PIN operations time out then check the signature
* Decide whether to approve off\-line, go on\-line or decline, based on floor limits, type of transaction, success of PIN, expiry dates, etc
* The chip is given the opportunity to override this decision
* If the transaction goes on\-line then additional chip data is sent to the bank
	* The bank uses this data to verify the card.  The data is signed by the cards secret key
	* The bank sends additional data, signed with its secret key.  The card uses this to verify the bank
	* Part of the response from the bank can be a script which is processed by the chip.  This can disable the chip if stolen, unblock the PIN, etc
* The chip is asked if it wants to override the decision to approve or decline the transaction
* The transaction takes place
* The chip is powered down

#### Chip and PIN is Broken

* Murdoch, Drimer, Anderson and Bond demonstrated a flaw in the Chip and PIN protocol in 2009
* They were able to use a card without knowing the PIN in a man in the middle attack
	* They used several cards, entering a PIN of 0000 each time, in their department canteen at the University of Cambridge with the knowledge and permission of the management
* They used the offline PIN verification protocol where the PIN was verified by the card and not the bank
* They built a man\-in\-the\-middle machine with a laptop and special hardware that cost $200

#### The Authentication Protocol

* There are two actors: Card and Terminal
* The following dialog takes place after some preliminaries: 
* Card → Terminal: Get the PIN from the user and send it to me
* Terminal → Card \-  either:
	* Here is the PIN
	* Or user verified without PIN \(signature, etc\)
	* Or transaction rejected
* Card → Terminal \(if PIN provided\) \- either: 
	- PIN OK
	- Or PIN INCORRECT, try for _x_ more times

#### The Man in the Middle

* The man in the middle sits between the card and the terminal, relaying message without changing them until the card asks the terminal to get the PIN
* MIM then receives the PIN but does not pass it on to the card.  Instead it sends the following messages:
	* MIM → Card: user verified without PIN
	* MIM → Terminal: PIN OK
* The terminal then proceeds with the transaction, which is logged as ‘Verified by PIN’
* The card also concludes that the user has been authenticated

#### Flaws the Made the Attack Possible

* The user can be verified in two different ways by two different devices:
	* Card verifies PIN
	* Terminal verifies signature
* The Terminal Verification Results \(TVR\) data format catered for many different failure modes but only 1 success mode
	* It did not report on which method had been successful
* The protocol allowed many different verification protocols
	* The terminal relied on the success code from the card without knowing any details
* The conversation between the Card and terminal is not authenticated, allowing a man\-in\-the\-middle attack
* These are fundamental flaws which are difficult to fix

#### Network Security Using Public Key Certificates

#### TLS

* TLS stands for Transport Level Security
	* The current protocol for internet communication
* It replaced SSL, Secure Sockets Layer
	* A number of flaws of SSL were discovered over time

#### Handshake Protocol

* Client\(C\) and Server\(S\)
	* C → S: Give me a secure connection
* S → C: Use these algorithms
	* Here is my public key certificate
* C → S: Here is an Unpredictable Number \(UN\) encrypted with your public key

* The certificate contains the server's name and public key
	* It is encrypted with the secret key of a Certifying Authority \(CA\)
	* The client already has the public key of this CA
	* As a master certificate
* Both the client and the server use UN to generate session keys for bulk encryption of data
	* Using AES or 3DES
* If the server is genuine then it knows the server secret key and so can decrypt UN
	* If it is not genuine then it cannot get the UN
	* It cannot encrypt / decrypt traffic with the client

#### Alternative Handshakes

* If the server does not have a certificate signed by an authority that the client has a master certificate for then an alternative has to be used
* The most common is to use Diffie\-Hellman.  This is then vulnerable to a man in the middle attack
* If the client and server connect regularly then they may use the same D\-H generated key
* It is more secure if they use an Ephemeral D\-H key: a new key is generated for each session
* If a connection between a client and a server will be used regularly then the connection parameters can be set up in advance
	* Use pre-shared keys \(PSK\) or a secure remote password \(SRP\) \(such as Kerberos\)

#### Man in the Middle \(MiM\) Attacks

* A MiM attack can be prevented by using public key certificates, provided the certifying authority is secure
	* If the CA is compromised then an attacker can forge their own certificates
* There are a number of CA's, many of which are weak
* The weakness of a MiM attack is that it must take place at a given time and between just 2 parties, a given client and server
	* But it can be automated
* This provides scope for preventing a MiM attack:
	* Certificate pinning
	* Certificate perspectives

#### Certificate Pinning

* Obtain a trusted version of the server certificate and then compare it with the one provided for each session
* In many cases the client will treat the certificate obtained during the first visit to a site
* If a different one is subsequently provided, then a MiM is probably taking place

#### Certificate Perspectives

* Use a third party, a notary, to obtain a server certificate from a different IP address
* The MiM attack will probably not be taking place simultaneously on two different connections to the server
* It is likely that the two certificates will be different if a MiM attack is taking place
* Several different certificates from different notaries can be used for added security

## Week 4
### Slides

#### Secret Writing

* Steganography is a form of hiding in plain sight
	* The word steganography is made up of two Greek words meaning secret writing
* A secret payloadis hidden inside an innocuous looking cover object, producing a stego object
* The payload itself can be encrypted for additional security
* In the past steganography involved modifying physical objects \(or people!\) in an undetectable way
	* Now it involves modifying electronic objects

#### Text Example

* The payload, a short piece of text, can be converted into a bit string
* The cover object, a longer text document, can be modified by adding a space to the end of the next line if the next bit is a 1
* There must be a way of indicating the end of the payload, perhaps by terminating it with a NULL character \(8 zeros\)
* The stego object will look the same as the original cover object
	* The added space at the end of some lines will not be visible when reading the document

#### Detecting Steganography

* Text documents with extra spaces at the ends of some lines would look suspicious
	* Provided steganography was suspected
	* The analysis would have to be digital
	* There might be another reason for the spaces, such as a birthday attack
* If the original cover document were publicly available, such as the file dracula.txt, then the stego version of dracula.txt would be longer
	* Steganography would be easy to detect

#### Attacking Steganography

* The payload could be removed if the stego object was processed to remove all blank spaces at the end of each line
* This could be done as a preventative measure on allemails if steganography was suspected
* This would prevent communications via steganography but would not recover the payload
* This approach may not detect if steganography has been used, depending on how it was implemented
* The aim of this attack is to prevent communications
* The extra spaces could be put in the middle of lines
* A word may or may not be misspelt in each sentence

#### Steganography with Images

* Text files have limited capacity and are only good for hiding small payloads
* Image files are much larger and are commonly exchanged
* There is much more spare capacity to hide secret information
	* In a picture of my dog playing in the snow for example
* There are many different image file formats, which can cause problems for steganographers

#### Image Pixels

* Image files contain header information and then the pixels
	* The header information is usually quite precise, with little spare capacity
* The bulk of the file is made up of pixels
	* Each pixel will typically contain three colour components: red, green and blue
	* Each colour component is typically 8 bits long, with 256 different possible values
* The following slides show the bit planes for the green colour component of an image
	* Each pixel is either  1 or 0

#### Least Significant Bit \(LSB\)

* The least significant bit of each colour component is often quite random
* Replacing it with a different value will often not be noticed
* Replacing all the least significant bits with bits from the payload will usually result in an image that looks the same as the cover image
	* This gives a payload capacity of 1/8<sup>th</sup>\(12.5%\)
* Replacing bit 1 with bits from the payload can often work as well, giving a 25% carrying capacity
* The possible capacity is quite large
	* Hide an image in another image

#### Problems with LSB

* The example cover image is quite good because the colours changequite rapidly over all of the image
* Most pictures will have areas where the colour doesn’t change very much
	* Sky, furniture, machines
	* The pixel values do not change very much
* Replacing the LSB with random rapidly changing values is then quite noticeable

#### Bit Plane Complexity Segment \(BPCS\)

* A bit plane is a black and white image created by taking one bit, say green bit 3, from every pixel in the image
* The previous example showed all 8 bit planes from the green colour segment of all the pixels in the image
	* There will be another 8 red and 8 blue bit planes, for a total of 24
* In this algorithm, each bit plane is divided into small segments8 pixels long and 8 pixels high
	* Each segment contains 64 bits
* A 1024 x 1024 image will have 128 groups of 8 pixels in each direction, with 128 x 128 = 16,384 segments per bit plane
* 4 bit planes gives a total of 24 \* 16,384 =  393,216 segments

#### Complex Segments

* In some segments the bits from neighbouring pixels will be distributed fairly randomly. They are called complex segments
	* Most segments in the Bit 0 example
	* They can be replaced with payload bits without anyone noticing
* In other segments the bits from neighbouring pixels don’t change very much
	* Many segments in the Bit 5 example
	* They should not be replaced with payload bits
* The BPCS algorithm only replaces complex segments

#### What is Complex?

* Complexity essentially measures how often neighbouring bits in asegment change value
* For each row in a segment \(there are 8 rows\)
	* Count the number of times the pixels change value
	* Maximum value is 7, eg 10101010
* Do the same for each of the 8 columns
* The maximum number of changes is 2 x 8 x 7 = 112
* The complexity of a segment C = number of actual changes / 112
* Define a threshold value T, which is a parameter of the algorithm
* If C \> T then the segment is complex

#### Recovering the Payload

* The embedding algorithm looks through all the segments in order
	* If the segment is complex enough then it is replaced by payload bits
	* Non\-complex segments are not changed
* The extraction algorithm also looks through all the segments in the same order
	* If the segment is complex then it must contain payload bits
	* If it is not complex then it could be part of the cover image
	* It could also be a non\-complex part of the payload
* Thus non\-complex payload segments must be made complex for the extraction algorithm to work

#### Conjugation

* If a payload segment is not complex then all its bits are xored with a chess board pattern:  
10101010  
01010101  
10101010  
01010101  
10101010  
01010101  
10101010  
01010101  
* This is called a conjugated segment
* It can be shown that: Complexity \(segment\) + Complexity \(conjugated segment\) = 112
* Thus if T < 0.5, then conjugating a non\-complex segment will always produce a complex segment

#### Conjugation Map / End of Payload

* We still need to detect if a payload segment was conjugated or not
	* 1 bit per segment
* Assume the image is 1024 x x1024 then it contains 393,216 segments
* Assume 128k \(to keep the maths simple\) of the segments are complex and contain payload segments
* Then the conjugation map contains 128k bits, one per segment
	* This can be stored in 2k extra segments

#### Conjugation Map / End of Payload

* We also need to know when we have reached the end of the payload
* We can pre\-process the payload, calculating its length and conjugating non\-complex segments as necessary, producing the conjugation map
* The conjugation map and payload length can be added to the start of the payload
* In our example, this will add 2k segments to the front of the payload
	* They will also need to be conjugated, producing a super\-conjugation map
* In our example, the super\-conjugation map will be 32 segments long
	* The recursion will eventually stop

#### Conjugation Bit

* Alternatively, the length can be added to the front of the payload
* The payload is divided in 63 bit segments
	* Every segments only contains 63 bits of data
	* The other bit, say bit 0, is either 1 or 0, depending in whether the segment was conjugated or not
* This is easier to implement but also easier to detect with a digital examination of the file
	* One bit position in each segments has an odd distribution of values

_The BPCS algorithm can achieve a capacity of between 25% and 50% without visual detection._

#### Image Types

* Most images are compressed before being communicated
* A lossless compression preserves the pixel values
	* The exact values can be recovered by decompressing
	* Common lossless algorithms are .png and .gif
* A lossy compression looses information
	* The exact pixel values cannot be recovered
	* Common lossy algorithms are .jpg
* Steganography with lossy algorithm is harder, but can be done

#### Encrypted Payload

* The payload could be encrypted first for added security
* The techniques described here work with any bit string, whether encrypted or not
* The encryption and steganography could be done with two separate products
* Alternatively, keyed steganographic products take a key as a parameter and do both the encryption and steganography

#### Steganalysis

* Attacks on steganography can have several goals:
	* Recover the payload
	* Replace the payload
	* Destroy the payload
* A visual attack looks at images to see if they show signs of containing a hidden payload
	* Steganography techniques are specifically designed to make this attack difficult
* If you have the original image then digital pixel comparisons can be made

#### Histograms

* A histogram counts the number of pixels with a given value and displays them as a graph
* Histograms of natural images tend to be smooth
* Histograms of BPCS stego images tend to have a valley, with lower counts, around the complexity threshold
* Histograms of LSB stego images tend to have some spikes around multiples of 8 bits

#### Digital Watermarks

* Digital watermarks are added to images
	* Sometimes they are visible but are often invisible
* They are used to show ownership or otherwise identify images
* They use techniques similar to steganography
* The main attack is to try and remove the watermark

#### Content Protection

* Digital content is easy to copy
	* CD, DVD, BlueRay, digital downloads etc.
	* Sound, video and software
* One person can pay for the content and distribute it to others who do not pay
* A company can sell fake media for a much lower price
	* A CD / DVD costs in the region of 20 – 30 pence to make
* Techniques based on single and public key encryption have been created to prevent these attacks

#### Content Protection Challenges

* The user should not have to enter the encryption key
	* Otherwise the product would be unusable
* So the key must be encrypted and stored in the hardware / software and hidden from the user
* The actual encryption key will often be stored in the computer memory while the playing application is running
	* Making it vulnerable to other running programs
* Audio and video hardware must eventually get the content in unencrypted form to play it
	* Specialist hardware / software can then capture this information
	* As can using a microphone / video camera

#### Audio Cassette Tapes

* Audio cassette tapes recorded music on magnetic tapes
* They were the next step after vinyl records
* Copying tapes was easy
	* Most cassette tape players had two decks to make copying easier
	* It was possible to make mix tapes
	* \. \. \. Or make a copy for a friend
	* The protection was a warning notice: don’t make illegal copies
* Many legal attempts were made to stop the sale of these devices
	* These failed because some copying was legal
* Several countries introduced a tax on blank media that went to the music industry

### MP3

* Use of proprietary compression formats that contained copy protection mechanisms
	* DRM, digital rights management
* There was strong customer rejection, exacerbated by the Sony Rootkit problem
	* On first play of the CD on a computer, malware was secretly added to the computer to interfere with all CD copying
	* It also phoned home with the user’s general listening habits
	* The operating system was modified to hide these additional files
	* which also provided cover for any other malware to hide
	* The Sony Rootkit software apparently used other people’s code, illegally, without a license!

#### DVD

* Uses CSS \(Content Scrambling System\) based on encryption
* Used 40 bit keys
	* In 1996, when it was developed, the USA government did not allow export of any encryption device with greater security
* There were 5 regions, each with different encryption keys, to support differential pricing
	* Players and DVDs only worked in one region
* Each hardware manufacturer \(about 400 of them\) had their own set of 5 keys which were hardcoded in their players
* Each DVD contained all the allowed keys
	* A rogue manufacturer could have their key revoked
	* Their key would not be added to future DVDs

#### Breaking CSS

* Makers had little incentive to keep their keys secret
	* The keys were inside their players
	* Making them tamper resistant is expensive
	* An attacker just needed to find one key
* A PC is an open platform and so driver code can be obtained
	* Obfuscating the code was not a serious impediment
	* Once the CSS algorithm was published, anyone could break it
* CSS did not allow Linux to play DVDs
	* Depriving Linux users of access to DVDs resulted in a lot of talented computer guys trying hard to break the encryption
	* Forcing Linux users to switch to Windows does not work!
* CSS was broken in 1999, 3 years after it became available
	* An application that allowed DVDs to be played on Linux machines was published
* Flaws in the implementation meant that the effective key length was 16 bits
* It could be broken in about 1 minute by a 2000 era PC

#### HDCP

* High bandwidth Digital Content Protection
* This is an Intel product. Devices that play HD videos must obtain a license and pay an annual fee
* Devices
	* Must not be designed to copy
	* Must not transmit video signals to non\-HDCP devices
	* Must frustrate attempts to beat encryption
* Functionality
	* Authenticate playing devices
	* Encrypt transmitted data
	* Revoke compromised keys

#### How HDCP Works

* Each device has its own
	* Secret information: 40 x 56\-bit keys
	* Public information: A 40\-bit Key Selection Vector \(KSV\) with 20 1\-bits and 20 0\-bits
	* The HDCP organisation provided these numbers to the manufacturers

#### HDCP: Bulk Encryption Keys

* During communication, devices exchange their public KSVs
* Each device uses the other’s KSV to xor together all the 56\-bit keys where there was a 1\-bit in the KSV
	* 20 out of 40 keys were used
	* The HDCP organisation used secret information when handing out the device public and secret information to make sure that both transmitter and receiver are the same
* This 56\-bit key is used to encrypt and decrypt the data using DES
* If a device is compromised, the corresponding KSV is added to a revocation list, which is signed by the authorities and burned on all new media

#### HDCP: Mutual Authentication

* Once the devices have exchanged KSV’s and generated their keys, the transmitting device creates a 64\-bit unpredictable number \(UN\) and sends it to the receiver
* The receiver creates a 16\-bit value based on UN and its version of the key
	* Like a 16\-bit message digest!
	* It sends it to the transmitter
* The transmitter creates its own version of the 16\-bit number based on the UN and its version of the key
* If they match then communication starts

#### HDCP: Adoption and Attacks

* 2000: invented
* 2001: Crosby et al. Showed how to break HDCP in a paper at ACM\-CCS8
* 2004: adopted in USA
* 2005: adopted in EU
* All devices marketed as HD ready must used HDCP
* Microsoft Vista and Win 7 use HDCP for graphics cards and monitors
* 2010/11: Master keys published on the internet
	* Around 6 years after adoption

#### How HDCP was Broken

* HDCP used a custom algorithm!
* The reason was to make it easier to implement in hardware
	* The custom algorithm used less than 10,000 gates
	* A system using RSA and other standard algorithms would use about 30,000 gates
* The weakness of the algorithm was adding the 20 keys \(using xor\), with the 20 being chosen by the KSV value
	* This is like a system of linear equations

#### Back to HDCP 

* The same principle works if we use xor instead on \+/\-
* There are 40 unknowns to find
	* The HDCP organisation’s secret information used to make sure the public and secret keys of each device are compatible
* We can find them if we have the secret information from 40 different devices
	* Provided they are all linearly independent
	* In practice, if we have 50 device keys then there is a 99.9% chance that 40 of them are linearly independent
* Once we have this information we can rip any DVD

#### AACS: Advanced Access Content System

* Adopted in 2006 to protect Blu\-ray and HD DVD systems
* Each individual player has a set of 128 AES keys, which are combined in a similar way to HDCP
	* The algorithm can’t be broken by the linear equation trick
* It has a similar revocation scheme
* It uses a ‘traitor tracing’ technique
	* Many video segments have digital watermarks that can only be decoded by one of the keys in a player
	* Analysis of pirated content will reveal the keys used, which can be revoked

#### AACS: Breaking This System

* In late 2006 / early 2007 a programs were published that could break the encryption and copy the file to a hard drive, so long as a valid key was provided
	* Less than a year after adoption
* Processing keys were found by analysing the computer memory while it was playing a Blu\-ray file
	* This is an inherent weakness of all such systems
* The keys were widely published on the internet. For a while the consortium played whack\-a\-mole to take down any site mentioning the key using the DMCA \(Digital Millennium Copyright Act\)

#### Encrypting Microsoft Word Documents

* Up until Office 2007 the key length was 40 bits, making it easy to break with a brute force attack and even easier with a dictionary attack
	* It used a proprietary algorithm, usually a bad idea
* Office 2007 – 2016 used AES with a 128\-bit key, which is usually secure
* Office 2016 uses AES with a 256\-bit key, which is even more secure
* The user can choose shorter and more memorable keys with these products, making them less secure

#### Encrypting USB Sticks

* Modern USB sticks will use good encryption but there have been some failures in the past
	* Usually because of a proprietary algorithm
* SySS Hack on SanDisk Cruzer devices in 2009
	* The software module that processed the key always sent the same magic bitstring to the drive to unlock it!
	* Bypassing the key checking part of the software and replaying the magic sequence unlocked the device
* In 2017 a generic device with a fingerprint scanner did something similar, sending an ID of the fingerprint to the device controller
	* The attack involved physically opening the USB device and connecting two pins to send the ID of the first recorded fingerprint

#### Secret Splitting 

* Let us imagine that we have a secret that we cannot entrust to just one person, but want to split between two people
* Both people are needed to reconstruct the message
* We cannot just give half the bits to each person
	* It would make it easier for one person to make a brute force attack to recover the other person’s half
* The secret is usually a password
* This is authentication requiring more than one person

* The following protocol lets the boss Sam split the secret message Mbetween two underlings Alice and Bob
* Sam obtains a truly random bit string R, the same length as M
* Sam calculates P = M ⊕ R, gives P to Alice and R to Bob
* The message can be reconstructed as P ⊕ R = M ⊕ R ⊕ R = M
* This technique cannot be broken by cryptographic techniques, since R is a one time pad

#### Splitting Between More Than Two People

* This technique is easily generalised to more than two people
* Let us split the secret between Alice, Bob, Carol and Dave
* Sam provides three random bit strings, R, S and T
* The fourth string is P = M ⊕ R ⊕ S ⊕ T
* The four strings are distributed to the four underlings
* The original message is recovered by P ⊕ R ⊕ S ⊕ T = M

#### Limitations of this Protocol

* The boss has absolute power and can hand out rubbish if he wants
* All pieces of the encrypted message are necessary
* If Alice falls under a bus then the secret is lost

#### Secret Sharing

* It is possible to split a secret up into n pieces so that it can be recovered with only m of the pieces, with m < n
	* This is called a threshold scheme
* With a \(3,4\) threshold scheme, the secret can be divided into 4 pieces and given to Alice, Bob, Carol and Dave
	* Only three of them \(any three\) are needed to recover the secret
	* If Alice falls under a bus then the secret is recoverable
	* but if Bob is away at the time then Carol and Dave cannot recover the secret by themselves
* The individual pieces are called shadows

#### Lagrange Interpolation Scheme 

* This scheme is based on the numerical solution of linear equations
* Integers are used to avoid the problem of rounding errors that arise when using real numbers
* Naturally, the integers are calculated mod p, so that division produces an integer answer
* The shadows are calculated using a polynomial of the appropriate degree
* If 2 shadows are needed to construct the key then the appropriate polynomial is a line which has two unknown coefficients a and b

* The algorithm when 2 shadows are needed:
* Chose a prime number p which is larger than the number of shadows \(n\) and the largest secret
	* Prime pmust be handed out along with the shadows and made public
* Chose a random number < p for the coefficient a
	* It is only used to generate the shadows and is discarded after the shadows are calculated
	* It must be kept secret
* The coefficient bis the secret message M
* This produces the polynomial y\(x\) = a \* x + b \(mod p\)

* The shadows are calculated by evaluating the polynomial at n different random values of x
* Each shadow is the three numbers \(x, y\(x\), p\)
* Since the linear equation has two unknown coefficients aand b, any two shadows can be used to find them
	* They generate two linear equations, which can be solved for the two unknowns a and b
* We want b, which is the secret M

## Week 5
### Slides 
#### Passwords
* The standard way of protecting access to a computer is by issuing a user name and password
* The computer does not need to store the passwords, just the result of a one way function operating on a password
	* An encrypted password, like a message digest
* Each time a user logs on, the password is entered and the encrypted version of the entered password compared with the value stored in the database
* This theoretically means that there is not a problem if the encrypted password file is stolen
	* The initial versions of UNIX made the password file publicly readable

#### Password Entropy

* There is a problem if the passwords are similar to English text
* In this case we must consider the entropy of the password space, rather than the theoretical maximum number of passwords
* There are 95 printable ASCII characters, so the entropy per character is
	* log<sub>2</sub>\(95\) ≈ 6.5
	* This is the maximum entropy, assuming each character is equally likely
* So the theoretical entropy of an 8 character password is 52 \(8\*6.5\)
	* In theory, there are 2<sup>52</sup> different passwords

* If we assume that the passwords are more like English then there will be fewer different passwords
* If we use the redundancy in English to calculate the entropy, we must use the experimental rate of the language, which is \~1.5
	* The entropy of each character is roughly 1.5
	* Leading to an entropy of 8 \* 1.5 = 12 bits
	* This is about 4 thousand choices
* The actual entropy will be more than this when different cases and also digits can be used
	* It will still be a lot fewer than 52 bits

#### Dictionary Attacks

* A dictionary attack is a form of brute force attack
* It is an offline attack, and is used on a copy of the password file
* A dictionary of possible passwords is constructed and the corresponding encrypted passwords calculated
* They are compared with the password file, and any matches mean that a password has been compromised
* It costs just as much to test a large number of passwords as a single password
* If there are 1000 passwords to test, then someone will almost certainly have chosen an insecure password
	* Typically, about 30% of the passwords can be obtained

#### David Klein’s Dictionary

* One of the early dictionaries
	* Variations on user’s name, initials and login name: 130 choices
	* Men’s and women’s names: 16,000
	* Places, names of famous people, numbers, vulgar phrases, keyboard patterns, etc: 60,000
	* Various permutations from the previous list: 1,000,000
	* Capitalisations from the previous list: 4,000,000
* If we type “common password lists” into a search engine we will get a large number of lists, ranging in size from 10k to 10M

#### Salt

* A salt value \(random string\) is added to a password before encryption and stored in the password file along with the encrypted password
* This does not make it harder to crack a given password
	* The salt string is publically available
* The dictionary attack cannot be run against all the passwords in a password file together, since they all have individual salt values which must be appended to each password
* In UNIX, the salt string consists of 2 ASCII characters, which adds 13 bits \(2\*6.5\) to the entropy when conducting a bulk dictionary attack
	* A factor of around 8,000

#### Pass Phrases

* Generating really random passwords will foil a dictionary attack, but the passwords can be hard to remember
* One way round this is to make the password very long, a pass phrase
* This is then fed into a function that generates a 64 bit password
* This password is then used as before
* This is useful as a front end to Linux, which has 8 byte passwords, which are rather short
* As a rule of thumb, one letter in the pass phrase will generate 1.5 bits in the password
	* This is a similar entropy argument to earlier

#### Graphical Passwords

* It is easier to remember complex information in visual form
* Recognition Based
	* Recognise it when you see it again
* Recall Based
	* Remember and recreate the image at login
* Locimetric
	* Remembering with visual clues
	* Remember points in an image

#### Passface – A Recognition Based System

* On registration
	* Choose several different faces that you will recognise again
* On login
	* Presented with several screens, each with 16 faces
	* Recognise a face on each screen
* Can’t choose relatives or friends – social engineering attack
* People are not very good at recognising faces when chosen from pictures
* Does not work well in practice

#### Draw a Secret \(DAS\)

* People remember what they have drawn because of the creative effort involved
* On registration
	* Draw a simple shape
* On login
	* Draw the same shape again
* Can you really remember an earlier drawing
	* Usually too simple to be memorable

#### ClickPoints - Locimetric

* Click on points in a picture
* Must get the order right
* How close is close enough?
* In practice people choose from a small set of points, even in a complex picture
* Does not work well.

#### Recognising Doodles

* Make the drawing more complex and hence more memorable
* On registration
	* Draw several doodles
* On login
	* Recognise your doodles amongst distractors, similar to passface
* You are likely to remember your doodles because of the creative effort
* They are personal but probably not open to a social engineering attack
* There can be a problem with distractors that are similar
	* Many people might choose to draw a similar doodle

#### Filtering Distractors for Doodle Passwords

#### Starting Point

* One of us ran a web site for older users 
* They did not want another text password
* Asking them to draw a doodle as a password was more memorable because 
	* The drawing was personal
	* They also recalled the drawing process
	* Visual and action\-planning memory invoked

#### Adding a New User

* They draw 4 black and white doodles which are digitised
* 15 distractors for each doodle are chosen from existing passwords

#### Login

* On login they choose their doodle in a 4x4 grid for each of 4 screens
* The random positioning is different each time

#### Problems With Simple Doodles

* Many users choose simple doodles, such as stick men or smileys
* In this case there is a reasonable probability that one of the distractors is a similar simple doodle drawn by someone else

#### Biometrics

* Fingerprints
	* Can be lifted from anything you touch. Easy for someone else to acquire them
	* Fingerprint readers can have trouble with dirty / oily fingers
	* Fingerprints for manual workers can wear away
	* Fake fingers are quite easy to create
	* Fingerprint readers find it easier to read ‘fake fingers’ correctly
	* Owners of fingerprint based systems, eg some cars, can be in danger of loosing a finger!

* Biometric authentication should be monitored to prevent faking
	* Someone there to detect the use of a fake finger
* Biometric information is fixed public knowledge
	* You can’t choose a new biometric if the old one is compromised
* The most common biometric is a photo
* Easily checked by a human
* Automatic facial recognition is not very good, but improving

#### False Positives and Negatives

* False positive – wrongly say that the biometrics match
	* Let someone break in
* False negative – wrongly say the biometrics don’t match
	* Wrongly exclude someone
* The false positive / false negative ratio can often be adjusted
* Biometric should not be used for identification because of the false negative problem
	* Use an alternative form of identification and use biometrics to authenticate it
* Use multifactor authentication
	* Token \(what you have\) and biometric \(what you are\)

#### False Positives and Rare Events

* Mass screening is often proposed to detect rare events
	* Detect a rare form of cancer
* No technique is perfect, there will be some false positives and false negatives
* Example, a screening system has a 1% false positive and a 1% false negative rate
* It is looking for a 1 in a million cancer
* If your test is positive, what is the probability that you have the cancer?
	* It is not 99%!
* The false positive rate may be small, but if the events we are looking for are rare then most positives we find are false

#### Remote Authentication

* A user is sitting at a client computer but wants to log in to another computer \(a server\) connected to the client
* The client could transmit the password to the server, letting the server authenticate the user
* This is dangerous, since the network is insecure
* The client could authenticate the user and then connect the user to the server
* This could be a danger to the server, since it must trust the remote authentication performed by the client
* The server could send the password to the client in the clear, letting the client authenticate the user

#### Authentication Over a Network

* There are the 3 approaches, with decreasing levels of trust
	* Each client macine authenticates users. Each server enforces a security policy based on the user’s ID
		* The server assumes the client machines are genuine and trusts them to authenticate users
	* The client systems must authenticate themselves to servers, but the servers trust the clients to authenticate the users
	* The user must prove identity to each server. Each server provesidentity to the clients

#### Kerberos

* Kerberos is a trusted third\-party authentication product used by LINUX and Microsoft Windows
* It provides secure network authentication, allowing access to different services on the network
* Originated with MIT project Athena
* The mythical Kerberos was a three headed guard dog, and the Kerberos protocol provides three levels of protection
	* Authentication at the start of a network connection
	* Authentication of each message
	* Encryption of each message
* It uses single key encryption

#### Gradual Explanation

* We will approach Kerberos in several steps
* Each step will solve a problem found in the previous step
* This will help to explain each part of Kerberos
* The Kerberos actors are:
	* User \(U\)
	* Client \(C\) machine, interacts with the user
	* Server \(S\) machine, provides a service
	* Authenticator \(A\), authenticates users
	* Ticket Granting Service \(T\) 

#### A Simple Protocol

* We do not want each server to have to authenticate every user
	* The user would have to keep entering their password
* We have a dedicated process, an authentication server \(A\) to do this
	* It knows the passwords of all users
	* It shares a different secret key with each server \(S\), set up in the initialisation phase
* In the following protocol, IP is a network address, P is a password and K a key
	* C \-\> A:  ID<sub>C</sub>, P<sub>C</sub>, ID<sub>S</sub>
	* A \-\> C:  Ticket = KS\[ID<sub>C</sub>, IP<sub>C</sub>, ID<sub>S</sub>\]   
	* C \-\> S:  ID<sub>C</sub>, Ticket

* In this scenario Crequests the users password \(P<sub>C</sub>\) and the service required \(ID<sub>S</sub>\) from the user and sends this information to A
* Achecks that the password is correct and that the user is allowed to use S.  If this is OK then it sends a Ticket
* The Ticket is encrypted with K<sub>S</sub>, S’s key and can only be opened by S
* C sends the Ticket and the user’s ID to S
* Schecks that the correct user is calling from the correct IP address and has a ticket for the correct sever \(itself\)
* There are two problems with this protocol:
	* The password is sent in the clear
	* The user must enter a password every time a service is used

#### Solving These Problems

* The password transmission problem is solved by creating a user key K<sub>U</sub> based on the users password
	* Both C and A know the user’s password and can generate this key
	* They can then communicate securely
* The second problem is solved by creating a new “Login” service, called a Ticket Granting Service \(T\)
	* The user gets a Ticket for T when he logs in
	* T will issue Tickets for different S’s when needed

#### Better Protocol

* When the user logs in
	* C \-\> A:  ID<sub>C</sub>
	* A \-\> C:  K<sub>U</sub>\[Ticket<sub>T</sub>\]
* First use for each new service
	* C \-\> T:  ID<sub>C</sub>, ID<sub>S</sub>, Ticket<sub>T</sub>
	* T \-\> C:  Ticket<sub>S</sub>
* Each time a service is used
	* C \-\> S:  ID<sub>C</sub>, Ticket<sub>S</sub>
* Ticket<sub>T</sub> = K<sub>T</sub>\[ID<sub>C</sub>, IP<sub>C</sub>, ID<sub>T</sub>, Timestamp<sub>1</sub>\]
* Ticket<sub>S</sub> = K<sub>S</sub>\[ID<sub>C</sub>, IP<sub>C</sub>, ID<sub>S</sub>, Timestamp<sub>2</sub>\]
* A timestamp is actually a time interval, with start and stop times

* The first ticket is encrypted with the users key \(K<sub>U</sub>\)
	* The user is prompted for their password, and only the user and A knows this
	* The key is generated from the password and unlocks Ticket<sub>T</sub>
* The client keeps Ticket<sub>T</sub> and uses it whenever a new type of service is requested
* The client keeps all the other tickets to be used whenever each service is used
* The timestamps are needed to prevent replay attacks

#### More Problems

* If the lifetime of the timestamp is too short then the user has to continually type in their password to create a new ticket when the old one expires
* If the lifetime of the timestamp  is too long, the system is vulnerable to a replay attack
	* A different user session on the same client machine can use a ticket that has not yet expired to access a service
	* Thus T and S must be able to prove that the person using a Ticket is the person who was issued with the Ticket
* The servers must also authenticate themselves to the user
	* An attacker could insert a false server

#### Authenticators

* Problem 2 is solved by A providing a secret piece of information to both C and T inside the ticket
	* C can then prove to T that it is the same client session as the one given the Ticket
	* This secret information is a session key K<sub>CT</sub>, for use between C and T
* When the user logs in
	* A \-\> C:  K<sub>U</sub>\[K<sub>CT</sub>, ID<sub>T</sub>, Ticket<sub>T</sub>, Timestamp<sub>1</sub>\]
	* Ticket<sub>T</sub> = K<sub>T</sub>\[K<sub>CT</sub>, ID<sub>C</sub>, IP<sub>C</sub>, ID<sub>T</sub>, Timestamp<sub>2</sub>\]
	* The client is told the session key and the validity of the Ticket
* When the user requests a service
	* C \-\> T:  ID<sub>S</sub>, Ticket<sub>T</sub>, Authenticator<sub>C</sub>
	* Authenticator<sub>C</sub> = K<sub>CT</sub>\[ID<sub>C</sub>, IP<sub>C</sub>, Timestamp<sub>3</sub>\]
* The authenticator proves that the request is coming from the same client session that was granted the Ticket, since it is encrypted with the session key

#### Server Authentication

* When the user requests a service
	* T \-\> C:  K<sub>CT</sub>\[K<sub>CS</sub>, ID<sub>S</sub>, Timestamp<sub>4</sub>, Ticket<sub>S</sub>\]
	* T sends back a session key between the client and server, together with a server Ticket, which also contains the session key

* C \-\> S:  Ticket<sub>S</sub>, Authenticator<sub>C</sub>
* The client creates another authenticator and sends it to the server, together with the ticket
* S \-\> C:  K<sub>CS</sub>\[Timestamp \+ 1\]
* The server adds 1 to the timestamp and sends it back, encrypted with the session key
	* Adding one to the timestamp shows that the server was able to open the authenticator and was not replaying a previous ticket
	* Similar to the use of unpredictable numbers in other protocols

#### Timestamps

* The timestamps rely on time being synchronised over all machines
* Network time protocols can be insecure, and so this could be a weakness, allowing a replay attack
* Timestamps have a fixed lifetime, and represent a period of time, not a time instant
* They can’t be exact because of network delays etc.
* This makes the system vulnerable to a quick replay attack, while the timestamp is still valid
* The servers should keep a table of all current tickets to foil this
	* They no longer need to remember tickets whose timestamps have expired

#### Software Weaknesses

* The client key is based on their password, with all of the usual vulnerabilities in that area
* The machine running the Kerberos processes must be secure, since the keys are stored in an internal database on that machine
* The machine administering this database must also be secure
* An attacker must be prevented from replacing the Kerberos processes with ones of their own devising
	* This is similar to login emulators
* The protocol has to be implemented correctly
	* This is usually checked with a software validation suite

### Week 6
#### Web Security

* The web is basically a client server application running over a network
	* The security techniques mentioned so far are all applicable
* The web does however have its own peculiar security issues
* The web is a highly visible front end to many corporations, government agencies and public bodies
	* Reputations can be damaged if web servers are subverted
* Web browsers are easy to use, web servers are relatively easy to configure and web content is easy to develop

#### Problems Specific to the Web

* The underlying software is very complex and may hide potential security flaws
* There are many new and upgraded systems that may have been installed correctly but are vulnerable to attack
* Casual and untrained users commonly manage web based servers
* Web servers can be exploited as launching pads into the entire corporate network
* A large number of ‘zombie’ machines can be used to make an attack

#### Web Page Security

* We will start by considering two different ways that IP packets can be encrypted
	* Transport and tunnel mode
* We then have a quick overview of HTTP
* Finally we will first look at ways in which web pages can be attacked
	* Look at the top 10 security vulnerabilities

#### Security at the IP Layer

* It is transparent to the application software in higher levels
	* All packets are encrypted, regardless of application generating and consuming them
	* Users do not need to be trained in security matters
* It can be implemented in a firewall
	* Internal traffic is not encrypted and so does not incur the performance penalties
* It can be implemented on an individual basis
	* Useful for offsite workers
* Can be used in a subnet for sensitive applications

#### Transport or Tunnel Modes of Operation

* An IP packet has two parts
	* Payload: the data being carried
	* Header: origin, destination and other information
* Transport Mode
	* Protection is provided for the IP payload but not the IP header
* Tunnel Mode
	* Protection is provided for the entire IP packet, including the header
	* It is the payload of an outer IP packet, using transport mode
	* It is useful for transport in the outside world from one firewall to another, hiding traffic analysis

#### Services Provided

* Connectionless Integrity because it is at the IP level
* Authentication using a signed message digest
	* In transport mode the payload is authenticated
	* In tunnel mode the origin and destination are authenticated
* Confidentiality through encapsulated security payload
	* In transport mode the payload is confidential
	* In tunnel mode the origin and destination are confidential
* The connection details are similar to TLS

#### HTTP

* HTTP is the basic protocol for the WWW
* A client makes a request to a server
* It is a stateless protocol
	* Each transmission between a client and server is independent
	* The server only deals with the immediate request, it does not remember any of the previous ones
	* The protocol does not identify a session, it just deals with a collection of transmissions
	* The application must provide session information to tie together related  transmissions
* There is no built in encryption

#### GET

* A GET command is sent by a client and requests a named resource
	* GET /images/logo.png HTTP/1.1
	* Give me the file called /images/logo.png using HTTP version 1.1
* There is a mechanism for sending information at the same time that is insecure but is often used
	* GET /images/logo.png?user=ron HTTP/1.1
	* This sends the value of the parameter user
* The GET message is sent in the header part of the IP packet
	* The header also contains the address of the server
	* It must sent in the clear to be delivered

#### POST

* POST sends information to the server
	* POST /images/logo.png HTTP/1.1
* The file and also any parameters are now sent in the body of the IP packet
* The body can be encrypted using transport mode in IPSEC

#### COOKIES

* Cookies are files sent from the server to the client and stored on the clients machine
* They are mainly used to maintain a session
	* The cookie is stored on the client machine in the first transmission of the session
	* It uniquely identifies the session
	* This cookie is then sent back in the body of the subsequent GET commands
* Cookies can also be used to track users

#### OWASP Top Ten Security Risks

* Open Web Application Security Project
	* An online community providing free resources to help web security
1. Injection
2. Broken Authentication 
3. Sensitive Data Exposure 
4. XML External entity XXE 
5. Broken Access Controls
6. Security Misconfiguration 
7. Cross Site Scripting XSS 
8. Insecure Deserialisation 
9. Using Components with Known Vulnerabilities 
10. Insufficient Logging and Monitoring

#### Injection

* Users provide commands to application that are expecting data
* The data is being processed by a script that mixes commands and user supplied data
* Many scripting languages, such as SQL, can be fooled into treating part of the user supplied information as a command
* They will be running on the server with the authorisation of the server ‘user’, often administrator
* They can access and return sensitive information

#### SQL Injection

* Many systems pass SQL queries to a database subsystem
* The queries are often constructed from user input
* These queries will contain meta\-characters which can be misused by an attacker
* In this first example, we are using a database called Usr that stores user names and passwords in columns called UserName and Password
	* Our login page will get the relevant information from the user and store it in the variables user and pass

* We then construct a query string in Java and use it to access the database  
```
String Query = "SELECT * FROM Usr "
+ "WHERE UserName='" + user +"' "
+ "AND Password='" + pass + "'"; 
```  
* If the input text was user = ron and pass = abcdefgh then the query submitted to the database would be:  
```
SELECT * FROM Usr WHERE UserName='ron' AND 
Password='abcdefgh'
```  
* On the other hand, if the input text was user = ron' and pass was empty, the generated SQL would be:  
```
SELECT * FROM Usr WHERE UserName='ron' –-' AND 
Password=''
```  
* The –\- introduces a SQL comment, which invalidates the password check, provided there is a user called ron
* This attacks only works if we know the user name, which is not usually as secret as the password

* The problem is not the –\- comment in SQL
* The problem is in the Java program which has allowed the metacharacter 'to be entered as data
* When SQL parses its query, it used the first ' to switch from command mode to data mode
* The second 'switches back to command mode, and so on
* This has allowed us to enter commands as data
* This is a tricky problem because ' can be a valid part of a name

#### Blind SQL Injection

* The previous example worked because we knew \(or guessed\) the structure of the database and names of the columns
* If we did not know this we can still get some information by trying different queries
	* Telling if they worked or not would provide some information
	* Error messages may tell us something

#### Command Injection

* Linux uses a command language called bash to run commands
* Scripts \(programs\) can be written to run common sequences
* These scripts can use variables to make them more general
* These variables can contain malicious code

```
finger $useruser='ron; 
rm –rf *'
```

#### Never Trust User Supplied Input

* Check user input before including it in a command script
* This can be difficult because there are so many things to check

#### Broken Authentication

* Poor implementation can compromise passwords, letting users havemore permissions than they should
* Example, a login page that allows a large number of attempts to guess a password

#### Password Problems: Users

* Good passwords are hard to remember
	* Weak passwords are vulnerable to a brute force attack
* Many accounts, all requiring passwords encourages password reuse
	* Create an app that people would want to use and collect user names and passwords
	* Try the user names and passwords on sensitive sites such as internet banking
* Password rotation and complexity requirements result in users forgetting their passwords and having to reset them
	* This often requires the user to provide weaker information such as their mother’s maiden name

#### Password Problems: Systems

* The system may have weak password storage
	* Store as plain text
	* Use unsalted hashes
	* Use a weak hash algorithm such as MD5/SHA1
* Solutions
	* Use 2 factor authentication
	* Log authentication failures and monitor the logs

#### Sensitive Data Exposure

* Sensitive data should only be accessible to authorised users
* Some data is not protected and can be seen by unauthorised users
* It should be encrypted and stored in computers behind a firewall

* Some web sites use security by obscurity, where sensitive pages are not protected by a login process
* If the attacker can guess the page URL then they can access the page

#### Hidden Fields in Forms

* Another technique that relies on security by obscurity is to putsensitive information in hidden fields of forms
	* The hidden field does not show up on the web page
	* But it can be seen if the html for the web page is examined
* This is often used for session management
	* If the field is changed then a session associated with a different user can be accessed

```
<form action=blah.jsp method=“post”>
<input type=“hidden” name=“sessid” value=“123”/>
</form>
```

#### XML External Entity

* XML is a hierarchical data file format
* Data can come from inside the server via an external entity reference
* This might expose sensitive data
	* General information gathering
* It is also possible to achieve remote code execution

#### Broken Access Control

* Login into a system lets the user run programs on the machine
* Access controls decide what they are allowed to do
	* Example, access only that user’s files
* If the access controls are not implemented properly then the user might be able to do more than they should
* This can lead to privilege escalation

* Main problems
	* Incorrect implementation
	* User provided data is used without sufficient checks
* Solutions
	* Disable directory listings
	* Log access failures and trigger alerts

#### Security Misconfiguration

* Not setting the security up properly
* Insecure default configurations
* Error messages containing sensitive information
* Not patching or upgrading systems

#### Cross Site Scripting XSS

* Data provided by the client is a script \(EG javascript program\) that is run in the victim’s browser
	* With potentially admin privileges
* Can hijack user sessions

_If the script can be stored on the server then the script can be run later, potentially with another user’s privileges._

#### Insecure Serialisation

* Some programming languages, eg Java, allow complex data structures to be stored in their binary form \(serialisation\) and then restored to binary form \(deserialised\)
* This is more efficient but also allows for malicious data objects that exploit the deserialisation mechanism
* It can also apply to objects with internal structure such as cookies
* Cookies are often used to obtain serialisation
* They are stored on the client machine and so can be modified by a malicious client

#### Using Components with Known Vulnerabilities

* Components are parts of an application, such as libraries, frameworks and software modules
* They are often stores as separate files \(.dll for example\) and loaded when needed by the application
	* They can thus be replaced without having to replace the application
* They run with the same privileges as the application

#### Insufficient Logging and Monitoring

* Logs record programs that run and actions taken
	* They can be enabled or disabled
	* If they are disabled then malicious activity will not be recorded
* If logs are kept then they need to be monitored to detect any attacks in a timely manner

## Week 7

#### Network Layers

* Data Link Layer
	* Medium Access Control \(MAC\) addresses
	* Cable or WiFi
* Network Layer
	* Internet Protocol \(IP\) addresses
	* Address Resolution Protocol \(ARP\)
* Transport Layer
	* Ports
* Application Layer
	* Domain Name Server \(DNS\)

#### Data Link Layer: Cable

* Connects individual devices, typically via ethernet: IEEE 802.3
* Each device has a MAC address for its Network Interface Controller
	* 48 bit, 6 groups of 2\-hex digits eg 00:24:E8:95:7A:9E
* First 24 bit organisationally unique identifier \(OUI\)
	* Dell: 00\-14\-22 \(Dell has more than one\)
* Second 24 bits Network Interface Controller \(NIC\) specific
* Special addresses
	* FF:FF:FF:FF:FF:FF special, broadcast
	* 01: . . . Special, multicast \(restricted broadcast\)

* Communication via an ethernet frame \(packet\)
	* Destination MAC address
	* Source MAC address
	* Payload
	* Checksum

#### Data Link Layer: WiFi

* Individual devices connected by WiFi: IEEE 802.11
* There are additional frame types
	* Management
	* Control
	* Data
* MAC address of the Access Point \(AP\) is included in the frame header

#### WiFi Security

* Packets are constrained to cables \(and packet sniffers\) in a connection\-based network
* In a wireless network anyone can listen if, provided that are in range
	* Important information MUST BE encrypted
* Wireless Equivalent Privacy \(WEP\) has been broken
	* Never use
* WiFi Protected Access \(WPA\): 2003
	* Different 128\-bit key per packet
	* Master key
	* Intermediate produce, better than WEP but still flawed

* WPA2: 2006
	* Uses AES
	* Uses pre\-shared keys, which allow brute force cracking. Key Reinstallation AttaCK \(KRACK\)
* The attack forces the devices involves to reuse the same key for several different messages
	* If one of the messages is know then the packet key can be recovered
	* Known plaintext attack
* It can be fixed by a software update

* WPA3: proposal 2018
	* Designed to fix the problem shown up by the KRACK attack

#### Network Layer

* IPV4: 32 bit addresses
	* 4 x 8\-bit decimal values eg 192.168.56.1
* IPV6: 128 bit addresses
* Special addresses
	* 127.0.0.1  local machine
	* 255.255.255.0  subnet mask \(24 bit subnet\)
* IP packets
	* Destination address
	* Source address
	* Payload
	* Checksum

#### Address Resolution Protocol \(ARP\)

* A device has the IP address of the packet destination and wants to find the MAC address of the device that has this IP address
* Example
	* CA:FE:CO:FF:EE:00 has received the packet with IP address 192.168.0.1 and wants to know who to send it to
	* Who has 192.168.0.1 : sent to FF:FF:FF:FF:FF:FF \(everyone\)
	* Answer: 192.168.0.1 is at FE:ED:DE:AD:BE:EF : sent to CA:FE:CO:FF:EE:00

#### Types of Attack

* Switch Downgrading: ARP or MAC flooding
* ARP Poisoning

#### Switch Downgrading : MAC Flooding

* A switch will:
	* Receive a MAC frame
	* Use the IP and port number to find the destination MAC
	* Forward the frame
* The switch maintains an internal table of IP addresses, port numbers and the MAC addresses of the associated devices
	* It builds the table dynamically by observing the traffic
	* The table has a finite size
* What happens when the table is full?
	* Some destinations will not be in the table
	* These frames will be broadcast rather than sent to the destination

#### The Attack

* The attacker sends lots of frames with different addresses
* This will fill up the table, forcing the switch to start broadcasting frames
* The implications
	* The traffic can be monitored since it is being broadcast
	* The increased traffic reduces performance

#### ARP Poisoning

* The aim of this attack is not to fill up the table but to insert incorrect values
* Remember that a machine that receives an ethernet frame not in the table will ask around to find out who to forward the packet to
* It can receive different replies, since the IP protocol does not depend on a specific route. It is connectionless
* The machine will then decide which route to take
* The attacker will send a large number of responses saying that it can forward the packet, hoping it will be chosen
* The aim is for all this traffic to be routed via the attacker, who can then forward it onwards
	* Man in the middle attack

#### Transport Layer

* Sits on top of IP and connects applications
* Each IP address has 64k ports, addressed by 16\-bit integers
	* Well known ports have 10\-bit addresses, port numbers < 1024
	* 1024 to 49151 registered for particular applications
	* 49152 to 65535 are public ports
* Each application connects to a specific port
	* 20 \(data\), 21 \(control\) FTP
	* 80 HTTP

#### TCP/UDP

* UDP Single packet transmission
	* Delivery not guaranteed
* TCP a sequence of packets
	* Guaranteed delivery
	* Will be delivered in order
* Both connect to ports at an IP address

#### Application Layer

* Domain Name Server \(DNS\)
* Connects text network addresses to IP addresses

#### DNS Poisoning

* /hosts file on the local computer is the first point of contact in the Domain Name Server process
	* C:\\Windows\\System32\\Drivers\\etc\\hosts
* If the name is not there then the process searches further afield
* This can be use as an add blocker by redirecting advert serving and monitoring IP addresses to 127.0.0.1 \(local host\)
	* Code trying to refer to these addresses will be sent to the hostmachine, which does not have them
	* They will not be displayed
* This approach can also be used for censorship

#### Sockets: Transport Layer Security

* Used to be called Secure Sockets Layer
* A socket connects two applications with a 'pipe'. First used in UNIX.
* Data can be transmitted in both directions.  Data arrives at thedestination in the same order that it was put into the pipe.
* Exceptions can jump the queue
* The pipe typically runs across the internet, connecting an application on one computer with an application on another
	* Typically a browser connects to a server

#### TLS Summary

* Public key certificates are used if the client has a public key certificate of the certifying authority that signed the server public key certificate
* Diffie\-Hellman is used to create ephemeral  keys is there are no certificates available
* Certificate pinning and perspectives are used to try and foil a man in the middle attack

#### Bulk Data Transmission

* It typically uses either AES or 3DES
* It typically uses cipher block chaining \(CBC\)
* It can be useful to transmit single bytes as soon as they are available rather than waiting to collect blocks
* Counter Cipher Mode \(CCM\) and Galois Counter Mode \(GCM\) are common stream ciphers, transmitting bytes when they become available

#### Resumed Sessions

* If a connection is likely to be used for several sessions then the server can send a session ID or a session ticket \(similar to a Kerberos ticket\) during the initial handshake
* If the client is given a session ID then when they want to resume the session they just present the ID
	* The server searches through its collection of current session ID's and checks that the client state \(IP address etc\) is the same
	* If it is the same then it returns the same session ID, otherwise it returns a different one
* A session ticket contains the client state in an encrypted form
	* The server then doesn't need to store all the possible client states itself, but recovers them from the ticket when it is presented

#### Forward Secrecy

* A client\-server session has forward secrecy if the communications remain secret even if the handshake parameters become compromised
* If all the AES session keys are generated from the initial handshake parameters and then reused for subsequent communications, then
	* All communications in the past \(if they have been recorded\) and future will be compromised
* The best way to achieve forward secrecy is to use ephemeral D\-H to calculate the session keys
* A new random key is generated for each session

#### Denial of Service \(DOS\) Attacks

* Exploit system weaknesses
	* Ping of death using the network enquiry ping command
	* Teardrop, sends mangled IP packets and exploits a bug in the code that reassembles them
	* Smurf attack relies on a poorly configured network.  Sends a packet to the broadcast address and the machine amplifies it by sending it to everyone else
* Computationally intensive calculations
	* Diffie\-Hellman calculations in SSL or IPSec

#### DDOS

* Distributed denial of service attacks
	* Vast number of attackers overwhelm victim 
	* Exhaust system resources, or
	* Exhaust bandwidth
* Assemble a botnet of compromised PC’s
	* They respond to an attack command

#### Direct Attacks

* The most common attack is SYN flooding using a fake From address
* SYN asks for a connection
	* The victim responds to the From address with SYN\-ACK and waits with a half open connection
	* There will never be a reply because the From address is fake
	* The victim will usually wait and send several SYN\-ACK packets before giving up
	* The aim is to exhaust the number of half open connections
* One preventative method is for the two parties to exchange cookies, a relatively fast operation, before starting to open a connection

#### Reflector Attacks

* Internal internet nodes such as routers and servers are innocently used to launch the attack
* Packets requiring a response are sent to the routers and other internet infrastructure with a forged From address of the victim
* The routers sends legitimate responses to the victim
* The victim is overwhelmed with normal packets
* Routers are usually induced to send SYN\-ACK packets
* They can be recognised as bogus
* The aim is to overwhelm the bandwidth

#### Detect and Filter

* Victim detects an attack
* Requests that the attacking source packets are filtered by the ISP
	* How can the victim get information to the ISP when the network is overloaded?
	* Phone call or alternative network
* There will be false positives and false negatives
* The normal packet survival rate can become quite low
* IP traceback is a good idea that doesn’t always work
	* Stopped at firewalls
	* Reflector attacks come from a legitimate source
* IP hopping and proxies can defend against a DDOS attack

#### Firewalls

* Firewalls are used to monitor incoming and outgoing packets, looking for threats
* They used rules to decide if traffic is allowed to pass
* They are usually placed on gateway machines to control access to an internal network
	* Can use tunnel mode outside

#### Defence in Depth

* We provide more than one firewall, as in the example below
* The Web Server is in a DMZ \(demilitarised zone\)
	* It has partial protection
	* Full protection is behind the second firewall

#### Proxy Service

* All connections to the Internet are routed through the firewall
* Checking for allowed access is centralised
* Common content is only cached once
* Logs are all in one place for ease of monitoring

#### Packet Filtering

* The packets are checked against a set of rules to determine if a packet should pass
* Check on the requested service \(using port number and machine\)
	* Only some ports are allowed \(eg those related to HTTP\)
* Check the packet source
	* Black list – ban these sites
	* White list – only allow these sites
* Deep packet inspection
	* Check the content
	* Has privacy implications

#### Stateful Inspection

* Just check key parts of the packet and apply a matching algorithm
	* Port and protocol
* The administrator can define rules
* Rules can use past experience from previous connections to the site, as well as previous packets of the current connection

### Examples

* A rule may state that if too many files are being read by a specific IP address then that IP address is blocked
* All access to certain domain names can be blocked
	* This can be bypassed by using IP addresses directly
* It is possible to create rules for certain protocols
	* IP, TCP, UDP
	* HTTP, FTP
	* ICMP \(Internet Control Message Protocol\)
	* SMTP \(Simple Mail Transport Protocol\)
	* SNMP \(Simple Network Management Protocol\)
	* Telnet \(Remote execution\)

* Specific words and phrases
	* Deep packet inspection will check words with a list of forbiddenwords and block any packet containing any of these words
* Some ports, eg FTP \(21\) will only be available on one internal machine
* Disable source routing
	* The internet is connectionless, but a packet may specify the exact route that it will take
	* This can be forged to make it appear that the information came from a trusted source

#### Example Rule

```
src ip: any; dst ip: webserver; dst port: 80; protocol: tcp
```

* This rules allows:
	* Packets to come from anywhere
	* Only go to the webserver 
	* Only use port 80 \(HTTP\)
	* Only use the TCP protocol

#### Next Generation Firewalls \(NGFW\)

* These provide additional functionality
* Integrated intrusion prevention
* Application awareness and control
* Are threat focussed

#### Intrusion Detection

* Network traffic, rather than single packets, is examined to see if an attack is underway
* It can be signature based
	* Check with a database of known attacks
	* Recognise them by their ‘signature’
	* Will not recognise a novel attack
* Anomaly detection
	* AI, typically machine learning, looks for non-standard situations and tries to classify them as an attack or just normal variation
* In both cases, sysadmins are notified if an attack is suspected
	* AI is not good enough to be fully trusted 

#### Intrusion Prevention

* Will detect an intrusion as before
* In this case the firewall can take action without waiting for a sysadmin to initiate it

#### Application Awareness and Control

* Threat focussed
	* Know which assets are most at risk and add this to context information
	* Deciding on what to do depends on the potential damage
* Cleanup after an event
* Retrospective security
	* Be aware of a recent event and be on the lookout for it to happen again

#### Virtual Private Network \(VPN\)

* It uses tunnel mode IPSEC
* The user’s computer will run the VPN application, which puts the whole of the IP packet, including the header, as an encrypted payload in an outer packet
* The outer packet is delivered to the VPN provider’s computer
	* Gateway to a company network
	* Computer in another country
* Results travel in reverse
* You appear to be using the VPN provider’s computer
	* You can appear to be in a different country to bypass censorship

#### Heartbleed

* This is an attack based on a poorly designed feature in a commonlibrary to implement TLS and SSL, OpenSSL
* This library has a ping command for seeing if a server is alive
* The client sends a 'are you alive' message to a server
* The server replies by sending a dump of a portion of RAM to prove that it is alive
* This dump will typically contain passwords and other sensitive information in an easily recognisable form
* This feature has now been removed, but older implementations will have to be upgraded

#### Security of a Web Based Application

* We will look at the security threats and possible counter-measures of a typical 4 level web based application.  The four levels are:
	* Client
	* Web Server
	* Application Server
	* Database and other specialist facilities
* Each level has its own security problems and solutions, as do the three types of communications between the levels
* We will discuss each area in turn, considering threats and countermeasures

#### Threats : Client

* The client machine is outside our control
	* We expect the client to use a standard browser, but oponents cangenerate their own hand crafted HTTP requests if they decide to attack us
* Failure to logout
	* This would allow access to user related information
	* While not strictly our problem, we can take measures to limit any damage from this mistake by the user
* Browser Cache
	* The browser may well cache pages or cookies in case they are needed again
	* These cached pages will be in the user's file system, where someone else can access them
* Downloadable Information
	* Any code that runs on the client can be seen
	* This can provide insight into the internal workings of our systems
	* This has implications for intellectual property rights
	* ID numbers may also be used to guess at the URLs of internal webpages, the structure of requests, and so on

#### Countermeasures : Client

* Remove Meaning from Client Side Code
	* C1: Client side code should not contain any comments and should also be obfuscated as much as possible
	* C2: No business logic should appear in client side code, which should only deal with presentation issues
* Avoid Caching
	* C3: Set page expiration to immediate so that the browser will not cache the page.  Unfortunately the back button will no longer take us back to these pages
	* C4: Don't use permanent cookies.  Transient in memory cookies can be used to record session information, but can still be seen by anyone with access to memory
* Field Validation
	* C5: Length validation of all input from the client, to prevent buffer overflow attacks
	* C6: Content validation of all data from client, to make sure that it is in the correct format.  This would also deal with special characters such as & and <
	* C7: Use message digests on all round trip information such as ID numbers to detect tampering and replay attacks
* Avoid In Clear Information
	* C8: Do not use HTTP GET command, use POST instead
	* C9: Encrypt HTTP body using TLS
	* C10: Reference numbers are only valid during the session, and do not contain any meaningful information
	* C11: Hidden fields can be used to record session information, but they can also have security weaknesses
		* An attacker can save a page, change a hidden field value and then replay that page
		* Do not use hidden fields

#### Threats : Web Server

* The web server is under our control, but there are still many attacks that we need to protect against
* Exploiting Vulnerabilities of Server Software
	* Servers such as IIS have a number of well known vulnerabilities,and so we need to make sure that all the patches are up to date
	* New vulnerabilities come to light from time to time, and so we need to keep up to date with the literature and relevant web sites
* Caching of Sensitive Information
	* This is less of a problem on the server, but session related information might still be cached

* Denial of Service Attacks
* Impersonation of Users
* Replay Attack
	* The replay may be a login request or a payment request, for example
* Hosting an Onward Attack
	* The structure of the internal domain can be discovered, allowing an enemy to attack it
* Cross Process Contamination
	* Information destined for one process may be sent to another
	* This can happen when we use components and web services

#### Countermeasures : Web Server

* C12: No Direct Access to Business Data.  This access is achieved at the process server level
* C13: Session Timeout, Protect against users who leave while still logged in
* C14: Null Memory After Use, Memory that has not been nulled is similar to a cache
* C15: Session Management, Correctly identify which session any client activity belongs to

#### Threats : Process Server

* The process server processes requests from the web server
	* It can be attacked from a compromised web server or another machine masquerading as a web server
	* We thus need to defend in depth
* Illegitimate Request
	* If the format of a valid request is known and authentication has been bypassed
* Denial of Service
	* This would typically be from a single web server machine, and sonot as series as a DDOS attack
* Illegitimate Components
	* Some parts of the system might have been replaced, either by a successful attack or by an insider attack

#### Countermeasures : Process Servers

* C16: User Authentication
	* This is where the user authentication takes place, since it is more secure than the web server
	* Avoid root users, Each user will have just the permissions they require and no more
* C17: Authorisation Checks
	* Make sure that the user is authorised to undertake the requests they are making
* C18: Password Re\-entry
	* Ask user to re\-enter password at crucial stages to verify that they are who we think they are
* C19: Stateless Components
	* If a component based system, such as CORBA, COM or .NET is used, then make sure that each component does not retain any information that could be used when they are next invoked, typically by a different process
	* In object oriented terminology: they do not have instance variables
* C20: Component Certification
	* All components are signed to certify that they are genuine
* C21: Web server authentication

#### Threats : Database and Other Services

* The database is where we keep all of our persistent information
	* A lot of damage can be done if it is compromised
* Illegitimate Requests
	* The database will respond to any well formed query from any machine with the appropriate access rights
* Internal Attack from someone inside our organisation
	* Database tools such as Query Analyser and Enterprise Manager may be used to compromise data
	* Other parts of the system may also be vulnerable to an internal attack, but an attack on the database would be especially bad

#### Countermeasures : Database

* C22: Access Controls.  Only certified components can access the database
* C23: Use of Stored Procedures
	* Make it difficult to construct ad\-hoc queries, although usually there must be a mechanism to allow some ad\-hoc queries
* C24: Encrypted Columns
	* Some columns are encrypted
	* Only secure components can access them
	* All access to them would be via stored procedures

#### Threats : Connections Between Computers

* The client machines, web servers, process servers and database servers are all connected, and the connections are all vulnerable
* Disclosure to Packet Analysers
	* Packet analysers are placed next to communication cables and record all of the packets passing to and fro, reassembling them into streams

#### Threats : Client \- Web Server Link

* The connection between the client and the web server is outside our control, being part of the WWW.  This causes several potential problems
* Proxy Server Caches
	* The connection between a client and a server will pass through several nodes, such as an ISP or a corporate gateway
	* These nodes may well cache the information on the way
	* This cached information is potentially available to others
* Spoof Web Sites \(Phishing\)
	* The customer must be confident that they are connecting to our web site and not a spoof site
* Information Sent in The Clear
	* The HTTP header for all HTTP packets is never encrypted.  This includes the URL
	* The GET method of parameter passing adds parameters as part of the URL, and, as such, they are communicated in the clear
	* The POST method of passing parameters uses the HTTP packet body, and so can be encrypted

#### External Safeguards

* C25: Firewalls
	* A typical hardware architecture will have two firewalls.  The first one filters all non\-HTTP traffic to the web server.  The other makes sure that only the web servers can access the process server
* C26: Intrusion Detection
	* There are third party products that can detect any unusual activity and alert an administrator
	* Tamper detection can be achieved with message digests
* C27: Physical security of critical components

#### Email Problems

* There are security implications if our system accepts inbound email, and generates outbound email
* Impersonation
* Denial of Service
	* Email bombs may be sent
* Viruses and Executable Attachments
	* This threat will cause us problems if our system is affected
	* Our reputation will suffer if we send out infected emails
* Spam Relay
	* Our email server may be taken over as a spam relay and become blacklisted, preventing us from sending legitimate emails
	* This would also damage our reputation
* Security of Mail Content
	* Encryption of email is not widespread and distribution of encrypted email relies on encryption facilities at each end
	* We cannot assume that our customers will use encrypted email

#### Countermeasures : Email

* C28: Web Based Mail.  Provide our own web based email, which we can ensure is encrypted
* C29: Check for Viruses, Both on inbound and outbound email
* C30: Verify that the SMTP header is valid
* C31: Configure email system securely, making sure it cannot be used as a relay

#### Installation and Configuration Issues

* There are a number of issues involved when we install our system at a customer’s site
	* Caused by customers or our own technical staff
* Revealing Secrets
	* We may need special permissions and IDs when we set up the system
	* We must make sure that these are not revealed
* Installation of Illegitimate Components
	* Components designed to compromise security may be installed alongside or in place of regular components
* Security can be compromised when a system is reconfigured

#### Countermeasures – Installation and Configuration

* C32: Physical Security



