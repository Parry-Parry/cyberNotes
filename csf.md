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
- Each has a different sub-key, generated from a master key
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

- Three key triple DES is not vulnerable and has a key length of 168 bits

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

- This is a block algorithm with block sizes of 128, 192 or 256 bits and key lengths of 128, 192 or 256 bits
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