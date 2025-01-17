# New Documentation

1. VPN for Rivanna (UVA) (add more here about downloading it etc)
   cms rivanna vpn connect
   
3. Check out code
   ```
   cd /scratch/$USER
   git clone git@github.com:claragrimmelbein/mlcommons.git
   cd mlcommons/benchmarks/uno/target/rivanna
   ```

4. Log into biihead2 (explain set up for biihead informal)
   ```
   ssh b2
   cd mlcommons/benchmarks/uno/target/rivanna
   make image
   ```
   * now have uno.sif
  
5. run simply slurm ( make sure file in right location, directory names correct, variables, etc)
   ```
   sbatch simple-singularity.slurm
   ```
     
   
   
   




# Steps to Run CANDLE Uno for Rivanna Users:

1. Make sure you have Python 3.7 or higher; very important to stay up to date else you will have troubles
   
       
2. Next, you will need to download some things onto your computer to set up the Python environment
    * BEFORE DOWNLOADING, MAKE SURE YOUR COMPUTER HAS ENOUGH STORAGE (or else ...)
    * Anaconda Installer:
        * Via GUI ( I prefer this way, but can also do it via command line: see https://docs.anaconda.com/free/anaconda/install/ )
        * Mac os: https://www.anaconda.com/download#macos
        * Other: https://www.anaconda.com/download#downloads
        * Run to check if proper installation occurred or if you have it previously installed:
            ```
            conda list
            ````
    * Install additional modules not shipped with Anaconda:
  
      (maybe grab a snack while this is occurring, takes more than a couple of minutes, on second thought you could eat a multiple course meal in this time period)
      ```
        conda install -c conda-forge tensorflow
        conda install -c anaconda hdf5=1.8.17
        conda install -c anaconda theano
        conda install -c conda-forge keras=2
      ```
      * Another way of installing Tensorflow:
        ```
        pip install tensorflow
        ```

         If troubles with grpcio wheel, do the following
        ```
        python -m pip install --upgrade pip
        pip install wheel && GRPC_BUILD_WITH_BORING_SSL_ASM="" GRPC_PYTHON_BUILD_SYSTEM_RE2=true GRPC_PYTHON_BUILD_SYSTEM_OPENSSL=true GRPC_PYTHON_BUILD_SYSTEM_ZLIB=true pip install grpcio
        ```
        
    * Download the source files for the benchmarks
        ```
        git clone https://github.com/ECP-Candle/benchmarks
        ```
        * Double check for:
            * p1b1_baseline_keras2.py
            * p1b2_baseline_keras2.py
            * p1b3_baseline_keras2.py
          
4. Download Uno Data (13.21 GB)
   ```
   wget http://ftp.mcs.anl.gov/pub/candle/public/benchmarks/Pilot1/uno/top_21_auc_1fold.uno.h5
   ```
      
6. Connect to UVA Eduroam Network or UVA Anywhere VPN
      - steps to download this VPN can be found:
        - Linux: https://www.rc.virginia.edu/userinfo/linux/uva-anywhere-vpn-linux/
        - Mac and Windows: https://virginia.service-now.com/its/?id=itsweb_kb_article&sys_id=f24e5cdfdb3acb804f32fb671d9619d0
          
  
7. Log into Rivanna:
   ```
   ssh $USER@rivanna.hpc.virginia.edu
   ```
  
8. Log into Biihead node (if using biihead2, replace 1 below with 2)
   ```
   ssh $USER@biihead1.bii.virginia.edu
   ```

9. Run the Pilot1 benchmarks (have not yet done Pilot2 and so on)

   ** More information about Pilot1 Benchmarks can be found on my GitHub page **

   * May be wise to just start with P1B1, this is the baseline implementation
     ```
     cd Pilot1/P1B1
     python p1b1_baseline_keras2.py
     ```

   * Else:




   ```
    pushd benchmarks/Pilot1/P1B1/
    python p1b1_baseline_keras2.py
    popd

    pushd benchmarks/Pilot1/P1B2/
    python p1b2_baseline_keras2.py
    popd

    pushd benchmarks/Pilot1/P1B3/
    python p1b3_baseline_keras2.py
    popd
   ```
11. Should produce success, if not, email me at esf3xw@virginia.edu with questions








August 15, 2023     
References: 
   * https://github.com/ECP-CANDLE/Benchmarks
   * https://github.com/grpc/grpc/issues/24677
      





   
