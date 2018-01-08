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

### Problems encountered
1. Incorrect gauge of the needle for inserting the gel in the Electrodes
 - ordered the correct gel and the needle from BrainVision
