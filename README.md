# YorkU_OBS_Handbook
The York University Allan I. Carswell observatory Handbook is a guide for assisting in research at the observatory.

The Allan I. Carswell Observatory Handbook
=======

## Using the telescope for research


## Data reduction on Delphinius 
 1. Open two (2) terminals (ctrl + alt + t). One will be for LINUX and the other for IRAF.
 2. In the LINUX terminal type `cd ./IRAF` (or simply `cd IRAF`)
 3. Locate the raw data of the night you want to reduce from the Data Reduction folder on your desktop called 'Preformatted_RESEARCH_DATA'
 4. Copy your nights data into your 'IRAF' working folder located in your home directory. There is many ways to do this but it is suggested you use the "Copy to" command and keep the same name of the night's data. eg 2017-10-17+18 (mkdir may also be needed. mkdir is a terminal command to make a new directory.)
 5. Then copy **prepro.cl~** and **coords.dat** into your working folder. They are located in a folder called 'Scripts' in your home directory. Make sure you are using the correct prepro.cl ("~" for using bias images vs "" when using darks: for the STXL ccd we are not taking darks)
 6. In your LINUX terminal type (you should be in the IRAF directory) enter the working directory (your night of data):  
                   `cd (folder name)`  
                   `Ex. cd 2011-03-14+15`  
 7. In your IRAF terminal type:  
                   `cd IRAF`  
                   `cl`  
                   And enter working directory  
                   `cd (folder name)`  
                   `Ex. cd 2011-03-14+15`  
 8. If you want to check the contents of the directory you are in simply type `ls` (the list command). To check the directory you are in type `pwd`. Backing up a directory is `cd ..` . Lastly, to end an IRAF session, type `logout`.
 9. It is a good idea to keep a record of the statistics of all your images. These can be viewed and saved by typing the following in the IRAF terminal:  
                   `imstat @object.list >object.stat`  
                   `imstat @flat.list >flat.stat`  
                   `imstat @dark.list >dark.stat`  
                   **Note: Some files will have biases instead of darks. In that case:**  
                   `imstat @bias.list >bias.stat`  
 10. The preproc transferred into your working directory now needs to be called. To do this first you need to edit ccdproc. You can do this by typing the following into the IRAF terminal **-** a number of packages. **(The different lines signify pressing the enter key.)**  
                   `noao`  
                   `imred`  
                   `ccdred`  
 11.


