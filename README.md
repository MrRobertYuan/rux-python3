# What's this
This is the congifure and build files helps to run python on RuxOS using cpython

The python execute file and lib files are placed in 'rootfs'. The 'rootfs' is a minimal rootfs for RuxOS in this application using 9pfs.

# How to build

Copy this directory to 'ruxos/apps/c' and change its name to python3

## Dl
Python3 depends on the dynamic loading
config the python args and envs in axbuild.mk


## Quick Start
1. Extract and compile python source and third-party libraries

```sh
chmod +x build.sh
./build.sh
```

2. Copy the musl libc dynamic loader to 'rootfs/lib'

3. Run
change to '/ruxos' directory

run the python terminal
```sh
make A=apps/c/python3 ARCH=aarch64 V9P=y NET=y MUSL=y LOG=off SMP=4 run
```

run the python file
copy python source file into rootfs and config axbuild.mk to:

```txt
app-objs=main.o
ARGS=/bin/python3.11,<souce_path>
ENVS=PYTHONLIB=/lib,PYTHONHOME=/
V9P_PATH=${APP}/rootfs
```