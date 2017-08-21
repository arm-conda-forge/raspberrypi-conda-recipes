About
-----
A repository of conda recipes for the RaspberryPi. All build (armv6l) distributions are available on binstar at:

https://anaconda.org/RaspberryPi

A selection of armv7l distributions (generated for building opencv3) are currently available at:

https://anaconda.org/microsoft-ell

Installing conda on the RaspberryPi
-----------------------------------
### RaspberryPi 0 (armv6l)
Currently there is an old-ish Miniconda installer for the RaspberryPi at http://repo.continuum.io/miniconda/Miniconda-3.5.5-Linux-armv6l.sh. The channel URL schema has changed since then, so accessing the `raspberrypi` channel won't work unless you manually update conda. 

To manually update conda for armv6l to 3.19.0:
1. Run the 3.5.5 Miniconda installer
2. `wget https://anaconda.org/RaspberryPi/conda/3.19.0/download/linux-armv6l/conda-3.19.0-py27_0.tar.bz2`
3. `conda install conda-3.19.0-py27_0.tar.bz2`
4. `conda --version` should now show 3.19.0.
5. Last but not the least, since this was a manual update, the old version of conda (3.5.5) is not automatically removed. To simulate that, rename the .json metadata file. Otherwise, conda will uninstall itself when you call `conda install`, rendering the environment useless.
   ```
   cd ~/miniconda/conda-meta
   mv conda-3.5.5-py27_0.json conda-3.5.5-py27_0.json.old
   ```
6. From here, you can install packages from the RaspberryPi channel and build your own packages, 

To update conda-build:
```
conda install -c raspberrypi conda-build
```

To install Python 3:
```
conda install -c raspberrypi python=3
```
 
### RaspberryPi 2 and 3 (armv7l)
For RaspberryPi 3, use: http://repo.continuum.io/miniconda/Miniconda3-latest-Linux-armv7l.sh. The `RaspberryPi` channel only contains armv6l packages that were built sometime back. 

```
wget http://repo.continuum.io/miniconda/Miniconda3-latest-Linux-armv7l.sh
chmod +x Miniconda3-latest-Linux-armv7l.sh
./Miniconda3-latest-Linux-armv7l.sh
<follow prompts to install, select `yes` when prompted to prepend the install location to PATH>
source ~/.bashrc
conda install conda-build
```

More recently, the `microsoft-ell` channel has added a subset of packages.  If you need more packages, it's fairly straightfoward to build your own (see the next section).

Building packages
-----------------
Refer to the Anaconda documentation on how to build and upload packages: http://conda.io/docs/build_tutorials/pkgs2.html

To build a specific package, e.g. opencv3
```
cd recipes
<Ensure you are *not* within a conda environment>
conda-build opencv3
```
