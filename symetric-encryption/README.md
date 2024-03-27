# symetric algorithm uses same key to encrypt as well as decrypt messages.
# these algorithm apply to a block of message.
# block ciphers are used to apply these algorithms to longer length of message.

#one time pad was first effective set of symetric algorithm
- In One Time Pad, a key of same length of message is used and combined with the message to generate a cipher text.
- This was effective when one key was used to encrypt the one block of message.
- It was not effective to use that many keys for every block of message.
- If same key used for more that one block message then pattern emerge in cipher text that can help give out information from cipher text analysis.
- there was low degree of entropy as per Caude E Shanon.

# Feistal Network was one such popular method with high degree of entropy.
# i.e. change in key is not directly affecting the change in cipher text.
# In this method, the left and right block of message were Ex-OR along with combining Key.
# This operation was reversible, hence could be used as symetric key algorithm.

# DES is one popular implementation of Feistal Networks.
# DES was introduced in 1970s and used a small key size of 56 bits.
# Due to increase in computation power. TripleDES was used that applied DES with three different keys.


# AES was brought from a competition organized by NIST to come up with a symetric encryption that will take place of 3DES.
# AES uses Key numbers as a block and changes the column and row sequence for each state with plain text or cipher text.
# key is a random number of 256, 128 bit.
# sharing these keys with another channel is inconvenient. So, passphrase were better item to remember. And keys can be derived from these passphrase. This is called password based key derivation function (PBKDF2)

# demoed the steps of encryption and decryption using simple AES. and using PBKDF2.
```
$ openssl rand -hex 32
e38b91c5fb087714440ebed9533c4f50d5a91fc68aba7f1f04afb17631f9f702
```
above command generates a 256 bit random number,

```
[ssingh@fedora symetric-encryption]$ echo "keepitsecret" > api_secret.txt
[ssingh@fedora symetric-encryption]$ cat api_secret.txt 
keepitsecret
[ssingh@fedora symetric-encryption]$ openssl -h
openssl:Error: '-h' is an invalid command.

Standard commands
asn1parse         ca                certhash          ciphers           
cms               crl               crl2pkcs7         dgst              
dh                dhparam           dsa               dsaparam          
ec                ecparam           enc               errstr            
gendh             gendsa            genpkey           genrsa            
ocsp              passwd            pkcs12            pkcs7             
pkcs8             pkey              pkeyparam         pkeyutl           
prime             rand              req               rsa               
rsautl            s_client          s_server          s_time            
sess_id           smime             speed             spkac             
ts                verify            version           x509              

Message Digest commands (see the `dgst' command for more details)
md4               md5               ripemd160         sha1              
sha224            sha256            sha384            sha512            
sm3               sm3WithRSAEncryptionwhirlpool         

Cipher commands (see the `enc' command for more details)
aes-128-cbc       aes-128-ecb       aes-192-cbc       aes-192-ecb       
aes-256-cbc       aes-256-ecb       base64            bf                
bf-cbc            bf-cfb            bf-ecb            bf-ofb            
camellia-128-cbc  camellia-128-ecb  camellia-192-cbc  camellia-192-ecb  
camellia-256-cbc  camellia-256-ecb  cast              cast-cbc          
cast5-cbc         cast5-cfb         cast5-ecb         cast5-ofb         
chacha            des               des-cbc           des-cfb           
des-ecb           des-ede           des-ede-cbc       des-ede-cfb       
des-ede-ofb       des-ede3          des-ede3-cbc      des-ede3-cfb      
des-ede3-ofb      des-ofb           des3              desx              
idea              idea-cbc          idea-cfb          idea-ecb          
idea-ofb          rc2               rc2-40-cbc        rc2-64-cbc        
rc2-cbc           rc2-cfb           rc2-ecb           rc2-ofb           
rc4               rc4-40            sm4               sm4-cbc           
sm4-cfb           sm4-ecb           sm4-ofb           

[ssingh@fedora symetric-encryption]$ man openssl
[ssingh@fedora symetric-encryption]$ man openssl
[ssingh@fedora symetric-encryption]$ openssl enc -aes-256-ecb -e -in api_secret.txt -K e38b91c5fb087714440ebed9533c4f50d5a91fc68aba7f1f04afb17631f9f702
$�▒z|Zdco�ң7��[ssingh@fedora symetric-encryption]$ openssl enc -aes-256-ecb -e -in api_secret.txt -K e38b91c5fb087714440ebed9533c4f50d5a91fc68aba7f1f04afb17631f9f702 > api_secret.ec
[ssingh@fedora symetric-encryption]$ xx api_secret.ec 
bash: xx: command not found...
^C
[ssingh@fedora symetric-encryption]$ xxd api_secret.ec 
00000000: 2413 bb1a 7a7c 5a64 636f a6d2 a337 b4e0  $...z|Zdco...7..
[ssingh@fedora symetric-encryption]$ 
[ssingh@fedora symetric-encryption]$ 
[ssingh@fedora symetric-encryption]$ openssl enc -aes-256-ecb -d -in api_secret.ec -K e38b91c5fb087714440ebed9533c4f50d5a91fc68aba7f1f04afb17631f9f702
keepitsecret
[ssingh@fedora symetric-encryption]$ echo "e38b91c5fb087714440ebed9533c4f50d5a91fc68aba7f1f04afb17631f9f702" > shared.key
[ssingh@fedora symetric-encryption]$ 
[ssingh@fedora symetric-encryption]$ 
[ssingh@fedora symetric-encryption]$ openssl -h
openssl:Error: '-h' is an invalid command.

Standard commands
asn1parse         ca                certhash          ciphers           
cms               crl               crl2pkcs7         dgst              
dh                dhparam           dsa               dsaparam          
ec                ecparam           enc               errstr            
gendh             gendsa            genpkey           genrsa            
ocsp              passwd            pkcs12            pkcs7             
pkcs8             pkey              pkeyparam         pkeyutl           
prime             rand              req               rsa               
rsautl            s_client          s_server          s_time            
sess_id           smime             speed             spkac             
ts                verify            version           x509              

Message Digest commands (see the `dgst' command for more details)
md4               md5               ripemd160         sha1              
sha224            sha256            sha384            sha512            
sm3               sm3WithRSAEncryptionwhirlpool         

Cipher commands (see the `enc' command for more details)
aes-128-cbc       aes-128-ecb       aes-192-cbc       aes-192-ecb       
aes-256-cbc       aes-256-ecb       base64            bf                
bf-cbc            bf-cfb            bf-ecb            bf-ofb            
camellia-128-cbc  camellia-128-ecb  camellia-192-cbc  camellia-192-ecb  
camellia-256-cbc  camellia-256-ecb  cast              cast-cbc          
cast5-cbc         cast5-cfb         cast5-ecb         cast5-ofb         
chacha            des               des-cbc           des-cfb           
des-ecb           des-ede           des-ede-cbc       des-ede-cfb       
des-ede-ofb       des-ede3          des-ede3-cbc      des-ede3-cfb      
[ssingh@fedora symetric-encryption]$ ^C
[ssingh@fedora symetric-encryption]$ 





















```
:w


