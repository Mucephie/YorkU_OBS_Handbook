`code snippet`  


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
 
                   cd (folder name)  
                   Ex. cd 2011-03-14+15 
                   
 7. In your IRAF terminal type:  
 
                   cd IRAF  
                   cl   
    And enter working directory  
    
                   cd (folder name)  
                   Ex. cd 2011-03-14+15 
                   
 8. If you want to check the contents of the directory you are in simply type `ls` (the list command). To check the directory you are in type `pwd`. Backing up a directory is `cd ..` . Lastly, to end an IRAF session, type `logout`.
 9. It is a good idea to keep a record of the statistics of all your images. These can be viewed and saved by typing the following in the IRAF terminal:  
 
                   imstat @object.list >object.stat  
                   imstat @flat.list >flat.stat  
                   imstat @dark.list >dark.stat  
                   
   **Note: Some files will have biases instead of darks. In that case:** 
                   
                   imstat @bias.list >bias.stat  
 10. The preproc transferred into your working directory now needs to be called. To do this first you need to edit ccdproc. You can do this by typing the following into the IRAF terminal **-** a number of packages. **(The different lines signify pressing the enter key.)**  
 
                   noao  
                   
                   imred 
                   
                   ccdred  
 11. ### For the first time user only  
 | `epar ccdproc` epar is the edit parameters command within IRAF. Within the parameters for ccdproc, you need to change all yes to no. To exit out of this program type: `:q` |  
 | ------ |
 12. Now declare the task in your IRAF terminal by the command:  
 
                   task $preproc =./preproc.cl  
     Then to call the task, type: 
     
                   preproc  
     This will complete all your image processing.
 13. From the LINUX terminal, call **ds9** and click 'File' then 'Open' and select the working folder. Open up the first image in your data set. Use your mouse to find the brightest point on your variable star. Once that point is found, click the pixel(pixels are points of light) and a green circle will appear centered at that point/pixel. Do the same for all your comparison stars (surrounding stars used to establish a baseline). You can locate the position of your variable and comparison stars using the marked star fields provided in your stars info binder. **Make sure to mark your variable star first and the comparison stars after that.** The more stars you mark, the more accurate your data will be. The order of the stars you mark must match the given star field. **Be careful not to mark very faint stars.**  
 14. Now you need to save the regions to a file. Within the "region's" menu select **'Save Regions'.** Specify the file name (you should keep it as ds9.reg for ease) and click ok. A dialogue titled 'Save Regions' will appear, change the format from default **ds9 to XY** and click ok. Exit ds9.  
 15. In your LINUX terminal enter command:  
 
                  aimr  
                  
     The program will open in the terminal. Defaults should be sufficient and thus hit return in answer to each query. For example, the first prompt is for _a List of images to examine_ and the default is object.list so you can just hit enter. Answer "n" when prompted for **use alignment parameters file (y/n)?** It will now ask for a list of the region files. The default is again ds9.reg, which again you can just click enter. The rest of the options you can hit enter through as their defaults should be correct.
     **Note: Once the program begins running you will see an output of object names, number of objects found for each image and a hit rate. aimr will look for the target stars in each image.**
     If it does not find all objects (due to realignment or the dome getting in the way), do the following:
       If you have images where stars are visible but not in expected locations, you can redirect IRAF to the location by making additional region files. Those commands follow but it is not recommended you do this unless you are expirienced with data reduction. Better to simply delete the problematic images from object.list.
       Still in the LINUX terminal, open first image that aimr cannot find in ds9. If you can see your star field in that image, click on each star (as done with the first image of the night in step 13) and go to 'Save Region'. This time make sure to change the file name (ex. change ds9.reg to ds91.reg). Next create a file in the working folder called _"alignpars.txt"_ . In this file write where to look for each saved image (must include the first image of the night).
       Example on what to write in the _alignpars.txt_ file:
       
                 @be_lyn.00000025.fits- >ds9.reg (first saved image)
                 -be_lyn.00000052.fits (remove bad frame)
                 @be_lyn.00000099.fits- >ds91.reg (next saved fram)
                 
       Once saved in _"alignpars.txt"_ , run `aimr` again. But this time answr Y when asked **alignment parameters file (y/n)?**  
 16. aimr creates two files, a region file containing all the positions of the stars in each image, and an .opf file. This .opf file needs to be converted into mark files that IRAF can read. This is done using the opf2mark program. To enter this program type the following in the LINUX terminal:
 
                 opf2mark
                 
   Default settings should be as follows (if default is correct hit ENTER):
 


