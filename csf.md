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


