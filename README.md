# Octagon
An Optimized Library for the Octagon Abstract Domain

#Requirements:
  Make sure you have latest version of APRON library installed. The APRON library can be downloaded from
    http://apron.cri.ensmp.fr/library/
  
#Compiling:

    Download the source and follow the instructions below.
    Copy the "src" folder into the directory containing APRON so that the path to new folder is: APRON_PATH/src
    Go to the "APRON_PATH/src" folder and open the Makefile
   
   If your machine supports Intel's vector intrinsics, and you would like to use vectorized operators for dense type,
      
     specify -DVECTOR for IS_VECTOR and "-m64", "-march=native" for AFLAGS in Makefile
      	If your machine only supports SSE specify the option DSSE in DFLAGS
     otherwise comment it out and it will use scalar instructions for Dense type.
      
   Specify -DTHRESHOLD=value, for example -DTHRESHOLD=0.75 in DFLAGS. The Threshold lies between 0 and 1 and controls switching between dense and decomposed types (operators). The analysis will switch     
   from decomposed to dense as soon as sparsity is below the threshold. A larger value of threshold favors dense whereas smaller favors decomposed types(operators).

   If you want to record timing information for different octagon operators, specify DTIMING in DFLAGS.
      Run "make", it will generate "liboptoct.so" and "liblinkedlistapi.so" libraries.
      
#Installing:
    Specify the install directory in APRON's "Makefile.config" file.
    Run "sudo make install"
    
#Using in Static Analyzer

  Java:
	
      Copy the files in "java_interface" directory into APRON_PATH/japron/apron
      Replace the Makefile in APRON_PATH/japron directory with the Makefile in "java_interface" directory.
      run "make" in the APRON_PATH/japron
      run "sudo make install" to install the updated "libjapron.so" file.
      Initialize the APRON Manager as:
        man = new OptOctagon();
      
  C++:
      
      Copy the files in "C++ interface" directory into APRON_PATH/apronxx
      Replace the Makefile in APRON_PATH/apronxx directory with the Makefile in "C++ interface" directory.
      run "make" in the APRON_PATH/japron
      run "sudo make install" to install the updated "libjapron.so" file.
      Initialize the APRON Manager as:
        man = new opt_oct_manager();
