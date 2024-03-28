## Block ciphers are used for longer message to provide diffusion.
1. Defussion hides the patterns in the input text to reflect patterns in the output text.
2. Defussion is not confusion as stated by Calaude E Shannon. Complicating relationship between input text and cipher text is Difussion. Complicating relationship between Key and Cipher text is confusion. We earlier saw One Time Pad offers no confusion. So a change in key can cause related change in cipher text. And using same key for different message would reveal information in Cipher text.

### Different Modes of Operations and their names:
1. CBC - Cipher Block Chaining. Offers diffusion and parallel decryption. However, encryption cannot be parallelized. Plaintext of each block is Ex-ORed with Cipher Text of previous block.
2. OFB - Ouput Feedback - This is used when hardward capabilities are limited. Its operations are called Stream Ciphers. This does not provide high degree of Difussion. It is simple to implements. IV and Key are combined to generate a cipher text then Ex-ORed with plain text.
3. ECB - Electronic Code Book. This simply encrypts with key and plaintext. Offers no Defusion.
4. CFB - Cipher Feedback. Cipher text of previous block is fed to encryption of next block with key and output is Ex-ORed with the plain text.

#### Modes of Operations are chosen based on requirements.
1. Some are Self Synchronizing. Meaning they can recover the part of original text even if some of the Cipher Text is garbled.
2. Parallel Decyption is provided by CBC.
3. Some are usefule for only hardware encyption like OFB. These are called Stream Ciphers.

- Stream Ciphers provide less defussion in comparision to block Ciphers.

## Example:
*Encryption CBC:*
```
openssl enc -aes-256-cbc -e -in image.bmp -pbkdf2 > image.enc
```

*Decryption CBC*:
```
openssl enc -aes-256-cbc -d -in image.enc -pbkdf2 > decrypted.bmp
```

## Initialization Vector - IV.
1. To start with a defusion, a random number of integer is used. We call it initialization Vector.
2. IV is saved in a plain text along with the cipher text to use while decryption.
3. IV is similar to salt. As IV does provide any advantage to be know to attacker.
4. Not Using IV will enable identifying patterns in initial block of plain text encryption.
5. It is important to use separate IV with different encryptions. Otherwise, it will reveal statistical information to attacker.


