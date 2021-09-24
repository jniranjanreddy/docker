# What is difference between COPY and ADD.
According to the Dockerfile best practices guide, we should always prefer COPY over ADD unless we specifically need one of the two additional features of ADD.

COPY - 99% of the time you should be using COPY
     COPY doesn't support <src> with URL scheme.
     COPY doesn't unpack compression file.
  
ADD - add recommended only below conditions
    ADD http://someserver.com/filename.pdf /var/www/html   # URL's
    ADD http://example.com/big.tar.xz /usr/src/things/     # Tar files
    
 he ADD directive will automatically expand tar files into the image file system. While this can reduce the number of Dockerfile steps required to build an image, it may not be desired in all cases
############################################

  
  # What is difference between CMD and Entrypoint
  
  ENTRYPOINT: 
     The ENTRYPOINT specifies a command that will always be executed when the container starts.
  
  CMD: 
     The CMD specifies arguments that will be fed to the ENTRYPOINT
