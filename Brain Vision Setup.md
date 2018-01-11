# Notes from discussion with Jonathan from Brain Vision

## 12.23.2017

### Instructions to create the setup
1. Connect the BrainAmp to the battery with the circular connector attached to both ends
2. Connect the BrainAmp to the BUA (BrainVision USB 2 PC Adapter) using the fiberoptic cable.
3. Connect the BUA to the PC using the USB.
4. Connect the BrainVision USB security stick to the PC to ensure the licenses work.
5. Connect the control box to the BrainAmp using the FRC(Flat Ribbion cable)
6. Connect the control box to the Electrodes using another FRC.
7. Make sure the  ground and reference electrodes are connected seprately on the control box.

### Problems encountered
1. Battery was not charged
  - Solved later by charging the battery
2. The control box was not booting on the USB power via PC.
  - Solved later using AA batteries instead. (Downside to this is we might not be able to use the stimulation or the event channel yet!!!)

## 1.4.2018

### Powering up the setup
1. Connect the electrodes to the cap.
 - Green ones go to the green locations in the cap(those are the first 32 channels in the control box, it can later be expanded using the yellow inputs in the control box t upto 64.)

2. Switch the power.
3. Open the BrainVision Recorder App and create a workspace.

### Creating a workspace
1. Create a new workspace
2. Hardware Filters - use them judiciously so as to negate anti-aliasing effects. DO NOT over-filter the input as this can be done in the later stages of the data pre-processing. It may introduce temporal shifts in the data.
3. Software Filters - Do not use too many filters on the raw data, instead apply filters on the display data which is not saved.

### Other Misc Points
1. Electrode Position file can be uploaded which contains the electrode position data which can be found on the BrainVision website.
2. Lab Streaming Ware  - Check this out to view the live data feed from the amp.

### Additional Pointers while creating a workspace
1. Change resolution in the edit workspace window. The resolution also determines the voltage range.
2. Can do DC recording by setting the lower cutoff in the mater setting.
3. USB URL: localhost:1947/int/devices.html
4. Software filters:

         * Filters data when it is recording. (Avoid this when possible)

         * Available when editing workspace

         * Notch Filter: 60Hz

         * High Cutoff Filter: 40Hz

         * Low Cutoff filter: Freq -> 0.2 Hz

         * Segment filters can be used to segment data on the fly.

### Problems encountered
1. Incorrect gauge of the needle for inserting the gel in the Electrodes
 - ordered the correct gel and the needle from BrainVision

## 1.9.2018
1. Jonathan sent the .bref file for the electrode position referencing in the Recorder.
2. Sent the actiCAP software for recognizing the active electrodes on Google Drive.



### workspace editing
1. Go to config->preferences and check the actiCAP electrodes checkbox.
2. save the .bref in the workspace folder.

### Misc Notes
1. The software package has a few montages and workspaces which might be useful later on...

### Applying the gel and connecting the Electrodes
1. Put on the cap and make sure it is secure.
2. Fill the syringe with the gel. Try to avoid air bubbles.
3. insert the syringe in the electrode till the tip touches the bottom.
4. Move the syringe while holding the electrode with the left hand. Move it in circles to remove the hair from the base of the electrode. (Very Important STEP)
5. Fill the ref, ground and channel 1 first.
6. Checking Impedances

  a. On the Software

  b. Using the Control box

    i. Click on the 'Z' button to put it in the impedance mode.

  Red - High Impedances

  Yellow - Almost there

  Green - Woohoo!

7. Fill the gel in the gap with a slight hand movement.

** The gel hardens ~ 5 mins.

** Make sure the Gel is cleaned after the usage or it will harden!


### Problems encountered
1. Recorder has stopped working for some reason!
  - Reinstalled on another system. There was an error with the driver.

## Using Brain Vision Analyzer

1. Save the EEG data by starting a recording and then stopping it using BrainVision Recorder

![alt text](./Images/saveRecording.png)

2. Open Analyzer and create a new workspace from File -> New

3. Create new folders for 'Raw Files', 'History Files' and 'Export Files'

4. Place the generated Raw files (.eeg (Actual Data), .vhdr(Header file containing the references to the other files) and .vmrk(marker files)) from Recorder in step in the 'Raw Files' directory from step 3

5. (Optional) Re-open the workspace to view the files if they are not visible in the primary window.

6. Double click the raw file to view it in the Analyzer.

## Export as .EDF+ format

Go to export -> EDF and generate a EDF file for the recorded data.

## Reading the file from python

We are using python package 'mne' for exploring the data.

1. add the package to your env using instructions given [here](https://github.com/mne-tools/mne-python)

2. We are using the following two formats of the data

  a. .edf - > `mne.io.read_raw_edf()`

  b. .vhdr (contains .eeg + .vmrk) - > `mne.io.read_raw_brainvision()`

  ** .vhdr contains the links to the .eeg and .vmrk file in it. Hence we read this in the python.

  More on those functions [here](https://martinos.org/mne/stable/manual/io.html)
