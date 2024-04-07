# llvm17.0.6-Installation
Few instructions to manually install LLVM 17.0.6 on Ubuntu Linux 22.04.4 LTS. This installation will let you easily build a solid structure to create your own IR passes.

## Folder Structure
Create this folders structure inside a ```ROOT``` folder.
```bash
ROOT -
      |
        - BUILD/
        - INSTALL/
        - SRC/
        - TEST/
        - setup.sh
```
### setup.sh
After creating the folder structure create this simple script. This will export the tools folder to let your installation coexist with other versions of LLVM installed on your system.
```bash
#!/bin/bash
ROOT=<ypur_intallation_root>
export PATH=$ROOT/INSTALL/bin:$PATH 
```
Run this script when you need to run tools from your personal installation of LLVM -- ```(ROOT)$ . setup.sh``` 

## Installation
### Download Source and Setup
1. Download the Source Code (_tar.gz_) inside $ROOT/SRC -- [Source Code](https://github.com/llvm/llvm-project/releases/tag/llvmorg-17.0.6).
2. Extract files - ```tar -xvzf llvm-project-llvmorg-17.0.6.tar.gz```
3. Place extracted files correctly
```bash
(ROOT/SRC)$ mv -r llvm-project-llvmorg-17.0.6/* .
(ROOT/SRC)$ rm -r llvm-project-llvmorg-17.0.6 llvm-project-llvmorg-17.0.6.tar.gz
```
4. Move into **BUILD** folder for next steps - ```cd $ROOT/BUILD```
### Configuration
Run the following command inside **BUILD** folder
```bash
cmake -G "Unix Makefiles"
  -DCMAKE_BUILD_TYPE=Release
  -DCMAKE_INSTALL_PREFIX=$ROOT/INSTALL
  -DLLVM_ENABLE_PROJECTS="clang"
  -DLLVM_TARGETS_TO_BUILD=<host>
 
  $ROOT/SRC/llvm/
```
**NOTES:** 
1. The _host_ parameter depends on your machine architecture -- use ```X86``` for x86 and x86_64 machines
2. The best option for developmen purposes would be to configure the installation with the ```-DCMAKE_BUILD_TYPE=Debug``` option, which would make the tools debuggable. However this involves increasing the size of the BUILD/INSTALL tree to over 100 GB.
### Compiling and Install
```bash
make -j2 && make install
```
**NOTE:** The ```-j``` option indicates the use of multiple cores, this will increase the use of RAM.  Check that the indicated number of cores does not result in RAM overloading.
### Documenation
You can consult the [official LLVM documentation](https://llvm.org/docs/GettingStarted.html#getting-started-with-llvm) for more specific information about installing and running LLVM.
