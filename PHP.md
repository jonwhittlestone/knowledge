# PHP #

- [Phalcon](Phalcon)
- [LaravelRefreshers](LaravelRefreshers)
- [LaravelBotMan](LaravelBotMan)
- [debuggingphp](debuggingphp)
- [LaravelAPIUdemy](LaravelAPIUdemy)
- [LaravelAtSonin](LaravelAtSonin)


----
- Run PHP 5.6 CLI app with docker image
    
    # build the image from the Dockerfile
    ▶ docker image build .
    # Run from out new image (no need for a volume or working directory but just to demonstrate)
    ▶ docker run -it --rm -v "$PWD":/usr/src/myapp -w /usr/src/myapp ef36a97f035b vendor/bin/phpunit app/tests/Import/Formats/HazarbuzExchangeLtd/MainFormatTest.php

----
