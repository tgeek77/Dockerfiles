# marias-arm
ARMHF build of the official MariaDB image

# changes from official build

The official MariaDB(x86) build is based on the official Debian image but uses DEB's for the actual server from a third party repository. There are only 32 and 64-bit builds of those DEB's and not ARM builds. I'm too lazy at this point to compile my own packages from source so instead my image uses the images from the Debian repository.

Please see https://hub.docker.com/_/mariadb/ for help on how to use the image.
