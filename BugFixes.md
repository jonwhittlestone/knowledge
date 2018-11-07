# Common bug fixes

----

Uncomment lines 209 - 212 when compiling Python from source in `Modules/Setup`

    SSL=/usr/local/ssl
    _ssl _ssl.c \
            -DUSE_SSL -I$(SSL)/include -I$(SSL)/include/openssl \
                    -L$(SSL)/lib -lssl -lcrypto
                    
Once that's done, do ./configure, make, and make install again and it should work.

----
