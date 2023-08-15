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
  
      (maybe grab a snack while this is occurring, takes more than a couple of minutes)
      ```
        conda install -c conda-forge tensorflow
        conda install -c anaconda hdf5=1.8.17
        conda install -c anaconda theano
        conda install -c conda-forge keras=2
      ```
    * Download the source files for the benchmarks
        ```
        git clone https://github.com/ECP-Candle/benchmarks
        ```
3. Connect to UVA Eduroam Network or UVA Anywhere VPN
      - steps to download this VPN can be found:
        - Linux: https://www.rc.virginia.edu/userinfo/linux/uva-anywhere-vpn-linux/
        - Mac and Windows: https://virginia.service-now.com/its/?id=itsweb_kb_article&sys_id=f24e5cdfdb3acb804f32fb671d9619d0
          
  
4. Log into Rivanna:
   ```
   ssh $USER@rivanna.hpc.virginia.edu
   ```
  
6. Log into Biihead node (if using biihead2, replace 1 below with 2)
   ```
   ssh $USER@biihead1.bii.virginia.edu
   ```

5. Run the Pilot1 benchmarks (have not yet done Pilot2 and so on)

   ** More information about Pilot1 Benchmarks can be found in my github page **
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
7. Should produce success, if not email me at esf3xw@virginia.edu with questions




   
