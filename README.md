# ELM_Bring_up_Petalinux
This repo will include ELM bring up tests for GEM,I2C, and  Petalinux Based tests

# Getting Started:-
### Using HTTPS:-
``` git clone --recursive https://github.com/bkushal26/ELM_Bring_up_Petalinux.git```

#### Using SSH-
``` git clone --recursive git@github.com:bkushal26/ELM_Bring_up_Petalinux.git```

## Git Repo Structure for GEM1:-

#### myproj
Working Vivado project saved in this folder (Vivado 2019.1)

### petaProj
*Working Petalinux project saved in this folder. 
1. Includes HDF sourced from `myProj/<project_1.sdk` directory.
2. Configured macb Driver in kernel Configuration.
3. Configured `iperf3` application. 
	3.1- in your <project_dir>/project-spec/meta-user/recipes-core/images/petalinux-image.bbappend add the following line:
	```IMAGE_INSTALL_append = " iperf3"```(be aware of the extra space)
	3.2  in ```petalinux-config -c rootfs``` -> user packages, enable iperf3
	
### tcl
This folder contains tcl file which needs to be sourced when starting from scratch

###shellScripts
This folder includes shell scripts to automate the tests.
1. ping_iperf_client.sh-To be sourced on Board by- ``` sh ping_iperf_clinet.sh ```
2. ping_iperf_slient.sh-To be sourced on Host PC by- ``` sh ping_iperf_server.sh ```
 


## Create a new project from scratch:
1. check the current working directory has 'tcl' folder.
2. Launch Vivado (2019.1)
3. In Vivado Tcl Console run :```source tcl/psddr.tcl```

## List of Commands useful-
1. To check the usb port status- ``` dmesg | grep ttyUSB```
2. To launch serial terminal- ```screen /dev/ttyUSB? 115200```
3. Petalinux Project related -
	3.1 Create PetaLinux Project:- ```  petalinux-create --type project --template <PLATFORM> --name <PROJECT_NAME> ```
	3.2 Initialize PetaLinux Project (for custom hardware only):- ``` petalinux-config --get-hw-description=<path-to-directory-containing-hardware description-file> ```
	3.3 Configure the Linux Kernel:- ```petalinux-config -c kernel ```
	3.4 Configure the Root Filesystem:- ```petalinux-config -c rootfs ```
	3.5 Build the System:- ```petalinux-build ```

## 

