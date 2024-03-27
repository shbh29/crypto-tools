# to compute hash use below command:
cat kafka-3.7.0-src.tgz | openssl dgst -sha512

# Information Theory
Claude E Shanon
# Ralph Merkesh and Damgard designed a theory that combining states will generate a collusion free compression algorithm
MD5 was based on this algorithm.
later in 2018 research found that compression algorithm needs 2^18 iterations to find the hash collusion for MD5.

#SHA1 was also researched to find a to detect a collusion.

#SHA2 is also based on Ralph Merkle and Damgard theory. 
# unfortunatly, this algorithm is suceptible for for keep computing has problem to get the same hash.
# as a solution most algorithm perform a last step as doFinal, where the drop some part of hash from calculation to save from further continuing hash calculation. 
# This has proved to be effective for now.

#NIST organized a compition to come up with new family of secure hash algorithm.
SHA-3 family developed by 4 guys moved away from Ralph Merkle and Damguard theory and used some high number of internal states and bits.
This algorthm is not widely adopted because SHA-2 family has proven to be effective for now.

# Hashing applications are found in JWT Tokens
a secret is used by issuer to obtain an Hash out of the payload and header.
the obtained has is then combined with another secret to derive a signature.

# password are widely used application of Hash.
1. password should never be stored in a plain text. Doing this gives immediate access to user password compromising user information.
2. simply hashing the password and storing in the database open up on a password directory hash.This kind of attack compares the hashes of common passwords used to the obtained access of database containing passwords.
3. to avoid the problem of password hashing directory, password concatinated with a salt before calculating hash.
4. additionally to be able to update the algorithms and iterations of hashing, we can maintain the Algorithm ID and update the algorithm ID with any new algorithm use and updating the no. of iterations.

