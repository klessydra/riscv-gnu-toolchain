RISC-V GNU Toolchain with the Klessydra Instruction Extensions
===================================================

This README provides instructions on how to install and build the RISC-V GNU-compiler Toolchain with the Klessydra instruction extensions. This extension enables the execution of vector operations in SIMD/MIMD fashion inside the [Klessydra Vector Coprocessing Unit (VCU)](https://github.com/klessydra/pulpino-klessydra). For more information on how to use these instructions, please refer to the [Klessydra Technical Manual](https://github.com/klessydra/pulpino-klessydra/blob/master/doc/Klessydra/Klessydra%20Technical%20Manual%20v11.1%20May%202020.pdf).

##  Installation
To install the RISC-V toolchain with Klessydra instruction extension, please follow the steps below:
   1. Clone this repository to your local machine:     
   
     git clone https://github.com/klessydra/riscv-gnu-toolchain
     
   2. Run the configure script replacing **"/path/to/install"** with the path where you want to install the toolchain: 
   
     ./configure --prefix=/path/to/install --with-arch=rv32ima --with-abi=ilp32  
     
   3. Build the toolchain:
     
     make
     
   4. Copy the riscv-gnu-toolchain/**make_link.sh** script into the **bin** directory of the installed toolchain:

     cp make_links.sh </path/to/install>/bin  
       
   5. Make the script executable:  
   
     chmod +x /path/to/install/bin/make_links.sh
     
   6. Run the script to create symbolic links:  

    ./path/to/install/bin/make_links.sh
         
## Usage
   To use the RISC-V toolchain with Klessydra instruction extension, simply add the **bin** installation directory to your PATH environment variable. For example, if you installed the toolchain to **/opt/riscv-klessydra**, add the following line to your **.bashrc** file:    
   
    export PATH=$PATH:/opt/riscv-klessydra/bin  
    
Now if you want to test the toolchain, execute the commands as such in a terminal: klessydra-unknown-elf-... (e.g. klessydra-unknown-elf-gcc -c file.c -o file.o)
    

