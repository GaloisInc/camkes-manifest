camkes-manifest
===============
CAmkES is a component platform that provides support for developing and building static 
seL4 systems as a collection of interacting components.  The resulting systems are static, 
meaning that all the components and their connections (and thus all the kernel 
managed resources) are defined at design time and instantiated at system initialisation time.  
It is not possible to change the system (e.g., to create or destroy components or to change 
the connections between components) at runtime.  This CAmkES package includes various example 
systems that can be studied, and individually built and run.

For general instructions on how to use this repository, see [sel4.systems](http://sel4.systems/Download/building).

For general information about CAmkES see [the CAmkES pages on seL4.systems](http://sel4.systems/CAmkES).

For detailed information about CAmkES see documentation in [the camkes-tool repo](https://github.com/seL4/camkes-tool/blob/master/docs/index.md).

Prerequisites, in addition to a standard build system for your target, are:
* The Haskell compiler, ghc
* Haskell libraries missingH, split and data-ordlist
* Python
* Python libraries python-tempita, pyelftools, jinja2 and ply
* which, realpath and the libxml2 utilities.

## Installation and running
Initialize repo with:
```
repo init -u https://github.com/GaloisInc/camkes-manifest -m default.xml -b rust
repo sync
```

and then you can build a simple app for example with:
```
make clean; make x86_simple_defconfig; make silentoldconfig; make
```

and run the resulting image with:
- For 32-bit targets: 
```
qemu-system-x86_64 -m 512 -kernel images/kernel-ia32-pc99 -initrd images/capdl-loader-experimental-image-ia32-pc99 --enable-kvm -smp 2 -cpu Nehalem,+vmx -nographic
```
- For 64-bit targets: 
```
qemu-system-x86_64 -m 512 -kernel images/kernel-x86_64-pc99 -initrd images/capdl-loader-experimental-image-x86_64-pc99 --enable-kvm -smp 2 -cpu Nehalem,+vmx -nographic
```
