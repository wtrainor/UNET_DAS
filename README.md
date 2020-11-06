# UNET_DAS
Codes for running UNet on RTM images seen in Jreij, S., Trainor-Guitton, W., Morphew, M., and Lim Chen Ning, I., 2021, The Value of Information from Horizontal Distributed Acoustic Sensing Compared to Multicomponent Geophones via Machine Learning: Journal of Energy Resources Technology, v. 143, doi: https://doi.org/10.1115/1.4048051.

U-net for fault detection below the Brady National Laboratory
Quickstart guide by Michael Morphew (May 2019), modified by W. Trainor-Guitton (Nov 2020). The generated .npy are available upon request (wtrainor@gmail.com, too big to put on github).

DATA PREPROCESSING
Step 1. Run your simulation in Mio, generating many hh files
Step 2. Copy your data over to a new folder for safety, then run copy_files.bash to create the @hh binary files
Step 3. Place the NotebookReadsInHeaderBinarydata.ipynb notebook and the read_in_rsf.py files into the directory with all the hh and @hh files
Step 4. Edit the jupyter notebook with your preferred output names for the .npy files that the notebook spits
Step 5. Run the notebook and generate the .npy files that will be used by the notebook.  There should be four: geophone, DAS, combined, and fault labels
Step 6. (optional) The Data_Checker.ipynb notebook can be used to compare data files and plot data to ensure that your data is what you think it is

RUNNING UNET
Step 1. Start the Unet_Faults.ipynb notebook
Step 2. Run the imports and definition cells
Step 3. Edit the data = and labels = cell to import your data and labels
Step 4. Run the rest of the cells up to the callbacks cell, editing model parameters as you desire (adding data augmentation, changing dropout, etc.)
Step 5. Change the ModelCheckpoint argument to name your model
Step 6. Change your batch size and epochs in the results = ... cell (epochs should be 50-100 to ensure training stabilizes)
Step 7. Run the results = ... cell to perform the training
Step 8. Run the rest of the notebook to plot your training and testing results

RESTARTING AN OLD MODEL
Step 1. Start the Unet_Faults.ipynb notebook
Step 2. Run the notebook up to and including the model initiation cell (model = create_unet())
Step 3. Skip the next couple cells as those cells perform the training
Step 4. Uncomment and edit the model.load() cell to load in the weights you want.
Step 5. Run the rest of the notebook as normal.

RUNNING UNET-CV
Step 1. Run the notebook as you would the Unet_Faults notebook up until the K fold split cell (the big cell that performs CV)
Step 2. Change the ModelCheckpoint argument to name your models generated from each fold
Step 3. Run the rest of the notebook up until the last cell.
Step 4. Change the name of the CSV file that saves the CV statistics to your preferred file name
