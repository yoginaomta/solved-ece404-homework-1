Download Link: https://assignmentchef.com/product/solved-ece404-homework-1
<br>
This is an exercise in you assuming the role of a cryptanalyst and trying to break a cryptographic system that consists of the two Python scripts you saw in Section 2.11 in Lecture 2. As you’ll recall, the script EncryptForFun.py can be used for encrypting a message file and the script DecryptForFun.py for recovering the plaintext message from the ciphertext created by the previous script. Both scripts can be found on the ECE 404 Lecture Notes web page (click “download code” for Lecture 2).

With BLOCKSIZE set to 16, the script EncryptForFun.py produces the following ciphertext output for a plaintext message that is a quote from Mark Twain:

3030722b63796c722e62297c226b2639302333257139762a66347d667e7a65286e347a2 3762571333330242d323e24252939676b7575767e7168336d386b323933243f30342633

3a322d7c7f6d796e6568642a776862657f632d6237612b603c223a2f68297f2868236c2 4304b4824306b6244715468164e035d084167390841

all in one line.

You can see the same encrypted output in the file named encrypted.txt on the course website at https://engineering.purdue.edu/ece404/homework.htm The correctly decrypted message should contain “Mark Twain” (without quotation marks).

Your job is to recover both the original quote and the encryption key used by mounting a bruteforce attack on the encryption/decryption algorithms. (HINT: The logic used in the scripts implies that the effective key size is 16 bits when the BLOCKSIZE variable is set to 16. So your brute-force attack needs to search through a keyspace of size only 2<sup>16</sup>.)

To accomplish this, you need to implement the following function in a file named <strong>cryptBreak.py</strong>:

#Arguments:

# ciphertextFile: String containing file name of the ciphertext (e.g. encrypted.txt ) # key_bv: 16-bit BitVector of the key used to try to decrypt the ciphertext.

#Function Description:

# Attempts to decrypt ciphertext contained in ciphertextFile using key_bv and returns the original plaintext as a string

def cryptBreak(ciphertextFile,key_bv):

Keep in mind that what is returned by the above function may or not may not be the correct plaintext since you don’t know the correct key bv. Therefore you will have to brute force all possible key bv values and check the returned string to find the right one.

<h1>Example of Usage</h1>

Below is an example of how the function you implement for this assignment could be used:

import cryptBreak from BitVector import * someRandomInteger = 9999 #Arbitrary integer for creating a BitVector key_bv = BitVector(intVal=someRandomInteger, size=16) decryptedMessage = cryptBreak.cryptBreak(’encrypted.txt’, key_bv) if ’Mark Twain’ is in decryptedMessage:

print(’Encryption Broken!’)

else:

print(’Not decrypted yet’)