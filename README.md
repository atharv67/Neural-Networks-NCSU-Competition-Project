# Neural-Networks-NCSU-Competition-Project
Competition Project for CSC 591-Neural Networks course at NCSU
## Introduction
Humans naturally develop walking capability that is energy efficient, stable, environment adaptive, and robust. Lower limb amputations, unfortunately, disrupt this ability; individuals with lower limb amputations usually depend on prosthetic devices to restore the basic walking function. Lower-limb robotic prosthetics can benefit from context awareness to provide enhanced comfort and safety to the amputee. In this work, we aim to develop a terrain identification system based on inertial measurement units IMU streams collected from the lower limb. The system for a prosthetic leg uses visual and inertial sensors though, but we are willing to observe if terrain identification without the visual data is viable. With such information, the control of a robotized prosthetic leg can be adapted to changes in its surrounding.
## Dataset
Data will consist of at several sessions from 6 different subjects including IMU data from a sensor on the leg of a participant, and the labels come from annotations of terrain type from a synchronized data stream. We only make use of the IMU data for this project. This work is inspired by this research project: https://research.ece.ncsu.edu/aros/paper-tase2020-lowerlimb/:
The dataset has folders for each session for a particular subject. Each of these folders have a 
- X data file with xyz reading of accelerometer and xyz reading of gyroscope.
- X timestamps
- Y labels
- Y timestamps
The y readings are at 10Hz and X readings are at 40Hz.
## Methodology
- Firstly we load the data.
- For combining the X and y dataframes, we create a 4 y records for each y in the data to compensate for the difference in frequencies while taking a reading.
- For making the data suitable to input for an RNN, we use 30 as a window size and combine 30 X records. For the y label, we use the mode of these 30 records.
- We then create an Bi-directional LSTM network and tune hyperparameters to get the best result.
- To handle the class imbalance, we assign different class weights to adjust our loss function.
- The code for this is present in [C3.ipynb](https://github.com/atharv67/Neural-Networks-NCSU-Competition-Project/blob/main/C3.ipynb).
