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
Run this script when you need to run tools from your personal installation of LLVM -> ```(ROOT)$ . setup.sh``` 
