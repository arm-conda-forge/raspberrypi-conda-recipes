About
-----
A repository of conda recipes for the RaspberryPi. All build distributions are available on binstar at:

https://anaconda.org/RaspberryPi

A selection of armv7l distributions (generated for building opencv3) are currently available at:

https://anaconda.org/microsoft-ell

If you already have conda installed on the RaspberryPi (via the miniconda installer or otherwise), simply add the
raspberrypi channel and run ``conda update --all``.

To use custom channels, do:
conda config --add channels channelname

Installing conda on the RaspberryPi
-----------------------------------
Currently there is an old-ish Miniconda installer for the RaspberryPi at http://repo.continuum.io/miniconda/Miniconda-3.5.5-Linux-armv6l.sh. The channel URL schema has changed since then, so accessing the `raspberrypi` channel won't work unless you manually update conda. 

To manually update conda for armv6l to 3.19.0:
1. Run the 3.5.5 Miniconda installer
2. wget https://anaconda.org/RaspberryPi/conda/3.19.0/download/linux-armv6l/conda-3.19.0-py27_0.tar.bz2
3. conda install conda-3.19.0-py27_0.tar.bz2
4. From there, you should be able to consume packages from the RaspberryPi channel, i.e. `conda install -c raspberrypi foo`

For RaspberryPi 3, use: http://repo.continuum.io/miniconda/Miniconda3-latest-Linux-armv7l.sh.

A more up to date self extracting installer will be made available in due course (in this repo).

Building packages
-----------------
Refer to the Anaconda documentation on how to build and upload packages: http://conda.io/docs/build_tutorials/pkgs2.html
