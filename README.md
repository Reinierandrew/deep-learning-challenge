# Selecting applicants to receive charity funding

## Overview
The purpose is to create a binary classifier that can predict  whether applicants will be successful if funded by Alphabet Soup. 
A dataset of 34.000 records was used to train and test the model using various steps to further optimise. These steps inlcude binning and converting categorical data to numerical, using various combinations of: activation  methods, varying number of neurons and deep learning layers and EPOCH's.

## Results
The model targets the `IS-SUCCESSFUL` column using the variables as listed below after the variables `NAME` and `EIN` were removed.

<img width="285" alt="Screenshot 2023-04-26 at 7 48 16 am" src="https://user-images.githubusercontent.com/112833174/234418267-93f592b0-3298-4586-adde-0741ef0e4912.png">

I binned the `APPLICATION_TYPE` into 9 bins (from 17) and  `CLASSIFICATION` was binned into 6 bins (from 71).

All categorical data was then converted to numerical using `pd.get_dummies` and all train and test data was then scaled using `StandardScaler`

I then defined the deep neural net model using 3 layers resulting in a `sigmnoid` output. The first layer uses 80 neurons using the 43 feautures and `relu` for activation.
The second layer has 30 neurons and also uses `relu` for activation.
The final and output layer uses `sigmoid`.

I then compiled the model using `adam` as optimiser to meaure the accuracy and executed the model using 100 EPOCH's which resulted in the following:

<img width="598" alt="Screenshot 2023-04-26 at 8 04 13 am" src="https://user-images.githubusercontent.com/112833174/234418387-c278388a-3261-4e44-a24d-f2ed1f450657.png">


## OPTIMISATION
I ran three instances of optimisation with various variations of binning, neurons, deep layers and activation methods. The results of the first two were similar to the original accuracy.

For the final optimisation I included `NAME` as a variable and binned the single instance applicants. My extensive experience in working with NPO's in Africa is that the name and recognition of an organisation does influence decision making. 

In the model I used 4 layers of up to 400 neurons with the initial layer using `relu` and the three consecutive hidden layers using `leaky relu` and 50 EPOCH's.

<img width="640" alt="Screenshot 2023-04-26 at 8 15 49 am" src="https://user-images.githubusercontent.com/112833174/234418464-239371ff-1a46-461e-9134-1baf8eaff2dc.png">

The result was an accuracy of 80% indicating that the name of the applying organisation does play a role in the success rate.

<img width="608" alt="Screenshot 2023-04-26 at 8 33 05 am" src="https://user-images.githubusercontent.com/112833174/234418587-61f977b7-5228-4618-b33f-5ff6fb3d91e4.png">

## SUMMARY
Using a standard deep learning model achieves an accuracy of <mark>80%</mark> and I expect that number will not change significantly by simply optimising the deep learning model using the variables available without overfitting the model.

A possible alternative would be to use a supervised learning model such as Random Forrest to achieve a better accuracy.
