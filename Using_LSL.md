# Streaming data from BrainAmp Series amplifier

# Content description


## BrainAmp

This software allows the data coming from the EEG setup to be streamed in a local
network.

Follow these steps:

1. Make sure you are able to view the EEG signals using Recorder. 
Follow step from [here](https://github.com/Neural-Dynamics-Lab-VT/Lab_wiki/blob/master/Brain%20Vision%20Setup.md)
if you have problems.

2. Now, **Stop** monitoring the EEG signals on recoder. As of this writing 
Brain Vision does not allow to both stream and view EEG signals at the 
same time.

3. Enable Remote Data Access (RDA) on the machine that has the Recoder 
software installed (Server). To do this on Recoder: Preferences -> 
Remote Data Access.

4. Now open the BrainAmpSeries App and Set the **Device Number** to **1**, 
**Number of Channels** to **32**, **chunk size** to **3**, 
**Resolution** to **100nV** and **DC Coupling** to **AC**. Don't
check the PolyBox (We might need this later though). Refer [here](https://github.com/sccn/labstreaminglayer/wiki/BrainAmpSeries.wiki)
for more info.

5. Click on the Link button. And, you are done! Well, atleast this part. 
This now would have started streaming data on the lab network with the 
name "BrainAmpSeries-0" and type "EEG", and another one named "BrainAmpSeries-0-Markers"
that holds the event markers.

**Note:**
* Currently, BrainVision Recording software does not allow you to both
stream and view the data. This can be accomplished in a different manner
which is documented later.

* You will not be able to close the BrainAmpSeries App when it is linked and 
transmitting data.

## LabRecorder

* This application can be used at both the client and the server to store the 
streamed data.

* A detailed description of its usage can be found [here](https://github.com/sccn/labstreaminglayer/wiki/LabRecorder.wiki).
Please follow them to be able to read the data stream on your local network.

* The received data can to stored using the Start button on LabRecorder and 
choosing a destination directory.

* The files are stored in XDF format which can be found [here](https://github.com/sccn/xdf).

* The python script in the above repo to read the XDF files.

## Receiving and viewing data using python

Clone [this](https://github.com/sccn/labstreaminglayer/tree/master/LSL/liblsl-Python) repo and follow the
instructions below:

### Receiving data

1.  Navigate to the cloned repo and install the package use `pip install .`

2. The examples directory contains starter code to both send and receive data
over a local network. To receive the data transmitted using the BrainAmp App just
run the `ReceiveData.py` script under the examples directory.

### Viewing it real time

Working on this!
