# Jet Image Classification:

This project served as my MSc thesis at the **Indian Institute of Technology, Delhi**, under the supervision of *Professor Abhishek M. Iyer*, Department of Physics. The objective was to utilize ML techniques to analyze particle collisions at the Large Hadron Collider and detect anomalies.

## Data:
The project works on the classification of image data. These simulated images are called *Jet images*, which represent collimated sprays of particles resulting from the particle collisions. The task was to employ several Machine Learning classification techniques to categorize the Jet images into two distinct classes: Signal and Background events.

An example of Jet images is given below:
![JET](/Images/JET.png)

## Algorithm 1: Principal Component Analysis (PCA)
The first ML algorithm employed was [PCA](/Jupyter_Notebooks/PCA.ipynb), a dimensionality reduction technique. This method follows from the Eigenfaces method of facial recognition. It enables the comparison of images based on their proximity in this reduced feature space. The **accuracy** achieved on the test set was an impressive **98.04%**.


## Algorithm 2:  Convolutional Neural Networks (CNNs)
Transitioning to CNNs, we used deep learning in image analysis. The CNN architecture we modeled is shown in the image below:
![CNN](Images/Cnn12.jpg)

We trained the algorithm on two different datasets:

1. [Dataset 1](/Images/Datasets/Dataset_100.zip): This was a balanced dataset of 100 images of each class, resulting in a total of *200 images* of dimensions (480, 640, 3). The accuracy achieved by the [CNN model](/Jupyter_Notebooks/CNN100.ipynb) on the test set after training for 40 epochs was **77.4%**. The ROC curve is shown below.
![ROC100](/Images/roc100.png)

2. [Dataset 2](/Images/Datasets/Dataset_200.zip): This was also a balanced dataset of 200 images of each class, resulting in a total of *400 images* of dimensions (369, 369, 3). The accuracy achieved by the [CNN model](/Jupyter_Notebooks/CNN200.ipynb) on the test set after training for 38 epochs was **92.5%**. The ROC curve is shown below.
![ROC200](/Images/roc200.png)


# Image Preprocessing:

To further increase the accuracies of classification, the project pivoted to better [pre-processing techniques](/Jupyter_notebooks/Preprocessing.ipynb) on the images. A methodology for reconstructing images from recorded data was used which was formulated as an optimization problem. The optimization was achieved by the **Gradient Descent Algorithm**.

This method was implemented using two Python libraries: *Numpy and Autograd*. The results were compared with another preprocessing algorithm called **'Weiner Filter Recovery'**. Mean Signal and Background images after employment of these images are shown below:
![MeanImages](/Images/ALL.png)

To quantify the separation of classes after pre-processing, the *Bhattacharya Distance* was calculated between the mean Signal and mean Background images. The results were:
1. Weiner: 0.279
2. **Autograd: 0.332**
3. Numpy: 0.151 

To further test efficiency, the preprocessed images were run through the CNN to determine changes in accuracy. The unprocessed images gave an accuracy of *41.2%*. The processed images gave the following accuracies:
1. **Autograd: 76.2%**
2. Numpy:  62.5%

Therefore, it was concluded that the preprocessing done by *Autograd* was the most *useful in classification*.


# Large Hadron Collider Dataset:

At the culmination of this project, the algorithms were applied to the *real Large Hadron Collider data* available on the CERN website: [Photon data](https://cernbox.cern.ch/remote.php/dav/public-files/AtBT8y4MiQYFcgc/SinglePhotonPt50_IMGCROPS_n249k_RHv1.hdf5) and [Electron data](https://cernbox.cern.ch/remote.php/dav/public-files/FbXw3V4XNyYB3oA/SingleElectronPt50_IMGCROPS_n249k_RHv1.hdf5). The two classes in this dataset corresponded to **Electrons** and **Photons**, real-life examples of signal and background events. The dataset contained **40,000 images** of dimensions (32,32,2) each, the two channels representing Energy and Time. An example image of this dataset is given below:
![EnergyTime](/Images/Energy-Time.png)

The [Jupyter Notebook](/Jupyter_Notebooks/CNN_EP_model.ipynb) for this portion of the project shows three CNN models developed for this dataset. The model which gave the *best accuracy* had the following architecture:
![CNN_EP](/Images/3rd_CNN.jpg)

The accuracy achieved was **67.3%**.

