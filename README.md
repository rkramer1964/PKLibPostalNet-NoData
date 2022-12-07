# PKLibPostalNet

# Purpose

This is a personal nuget package for LibPostalNet, including data files and support for both windows and linux.

If you want to build your own, you will need to download the data files from:

https://github.com/openvenues/libpostal/releases/download/v1.0.0/parser.tar.gz and decompress them into c:\libpostal

Windows users should be able to use 7-zip for this.

**Users of this package WILL need to reset the libpostal data directory at runtime.  See the [LibPostalNet](https://github.com/mapo80/LibPostalNet) console demonstration
program for how to do this. (snippet below)**

```
                libpostal.LibpostalSetupDatadir(dataPath);
                libpostal.LibpostalSetupParserDatadir(dataPath);
                libpostal.LibpostalSetupLanguageClassifierDatadir(dataPath);

```

# How it was built

## Windows
See the [LibPostal](https://github.com/openvenues/libpostal) project to set up the environment.
Then for the library build:

```
git clone https://github.com/openvenues/libpostal
cd libpostal
cp -rf windows/* ./
./bootstrap.sh
./configure --datadir=/c --disable-sse2
make -j4
make install
```

There were issues reported with SSE, so I disabled it.

## Linux

See the [LibPostal](https://github.com/openvenues/libpostal) project to set up the environment.
Then for the library build:

```
git clone https://github.com/openvenues/libpostal
cd libpostal
./bootstrap.sh
./configure --datadir=`pwd`/libpostal_data --disable-sse2
make -j4
make install
```

**This has my personal build folder on my workstation in the datadir - you WILL need to set the data dir at runtime**
There were issues reported with SSE, so I disabled it.