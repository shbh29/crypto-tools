# To Configure the downloaded openssl from libressl.org
1. ./configure
# if you get an error for not having c compiler install install c compiler by pointing to build-essentials.
2. make # to build the openssl tool from downloaded tar.gz file.
3. make check # to check if all the build tests are passing
4. sudo make install # to install the openssl
5. sudo ldconfig # to link the shared directories.
