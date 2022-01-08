# Denoising-Autoencoders

Due to advancement in technology we might have a large amount of the data but there is always concern about the usability. For example, in medical images like X-rays, MRI, CT scans, Ultrasound, etc., when original images are put in the paper, the quality degrades, due to which the accuracy of the decision model degrades. These images are susceptible to noise.

Image denoising is required to suppress noise from noise-contaminated images,and hence, is an important preprocessing step in image analysis. There are many different techniques and methods which can be used for performing denoising such as applying Median, Gaussian, Average, Bilateral Filters, etc. However, they don't necessarily perform well in denoising images without losing much information and hence, an algorithm is needed that can outperform all the other methods that have been proposed.

 ![image](https://user-images.githubusercontent.com/68664921/148658793-b59db98d-ec9b-4535-9b57-341600302a3f.png)
 
 ## Overview
- Import Key libraries, dataset and visualize images
- Perform image normalization, pre-processing, and add random noise to images
- Build an Autoencoder using Keras with Tensorflow 2.0 as a backend
- Compile and fit Autoencoder model to training data 
- Assess the performance of trained Autoencoder using various KPIs 

## Prerequisites
- Basic programming experience in python
- Basic understanding of Tensorflow
- Working knowledge of Machine Learning and Deep Learning

## Understanding the theory 

### Autoencoder Intuition
Autoencoders are a type of Artificial Neural Networks that are used to perform a task of data encoding (representation learning).
Autoencoders use same input data for input as well as output, crazy right?

![image](https://user-images.githubusercontent.com/68664921/148659340-ad7b260d-e8ca-4ed1-b972-3e7a30920278.png)


### Code Layer
Autoencoders work by adding a bottleneck in the network.
This bottleneck forces the network to create a compressed (encoded) version of the original input.
Autoencoders work well if correlations exist between input data and (performs poorly if all the input data is independent).


![image](https://user-images.githubusercontent.com/68664921/148659354-d7018490-b242-47d6-a69d-5a02127dafa2.png)

### Math behind Autoencoder
Encoder: ``` h(x) = sigmoid (W * x + b) ```

Decoder: ``` x̂ = sigmoid (W* * h(x) + c) ```

![math](/img/AutoencoderDenoising3.png)

### Reconstruction Error
Autoencoders objective is to minimize the reconstruction error which is the difference between the input X and the network output X̂. 

![reconstruction](/img/AutoencoderDenoising4.png)



Autoencoders dimensionality reduction (latent space) is quite similar to PCA (Principal Component Analysis) if linear activation functions are used.


 ## Possible Approaches

Traditional approaches for performing denoising include methods like 

1. **Gaussian blur**: In Gaussian Blur operation, we take a pixel as the average value of its neighboring pixels. The Gaussian filter is a non-uniform low pass filter that removes the high-frequency components and details.
2. **Average blur**: During this operation, the image is convolved with a box filter. In this process, the central element of the image is replaced by the average of all the pixels in the kernel area.
3. **Median blur**: The Median blur operation is resembling the other averaging methods. Here, the middle element of the image is replaced by the median of all the pixels in the kernel dimension. This operation processes the edges while extracting out the noise.
4. Bilateral filter: The Bilateral Filter alters the intensity of each and every pixel with a weighted mean of intensity values from neighboring pixels to obtain an edge-preserving and noise-reducing smoothing effect.

To measure the quality of the obtained images using different approaches and compare them with our method, we use what is known as the **PSNR (Peak signal-to-noise ratio)**. It is the ratio between the original noiseless image and the error in the image that is first corrupted and then denoised using the particular algorithm. The higher the PSNR value, the better the quality of the reconstructed image as it has a higher **Signal Noise ratio**. 

## Methodology-

### Introduction of noise for creating training set-
In order to create the training set, we purposely corrupt the images by adding noise to them stochastically with a random normal distribution having a mean of 0 and standard deviation of 1 with a multiplying factor of 0.07 as the dataset by default contains images without noise. This is done to stimulate the noise which can occur in medical images due to the reasons mentioned in the previous section. The dataset is a compilation of CT scan images meant for studying COVID-19, but we are using it for the purpose of demonstrating denoising.

### Denoising using Autoencoder

- Autoencoder is a type of unsupervised learning technique that uses artificial neural networks for the task of representation learning. An autoencoder is made up of two parts-
- Encoder- It accepts the input data and maps it to a latent space, which is a compressed form of the data, using deterministic mapping. 
- Decoder- It accepts the latent space representation and then maps it back into reconstruction, which has the same shape as the input data using similar mapping.

In other words, the autoencoder seeks to-
Accept input data (corrupted medical images in this case)
It then internally compresses the data into a hidden space representation
Finally, it tries to reconstruct the original data from that hidden representation.

## Installing

A step by step series of examples that tell you how to get a development env running

### Step 1
Download the prerequisites from the ``` requirements.txt``` file.

``` pip install -r requirements.txt ```

### Step 2
Open ``` jupyter notebook ``` on your local host or you can use Google Colab too.

### Step 3
Follow the steps in the notebook if you want to train your own or you can simply run the notebook in this repo.

## Output

This is a side-by-side comparison of the input images with added noise and the reconstructed output from the network.

![output](/img/AutoencoderDenoising5.png)


## References to study in detail about related topics
* [Autoencoders](https://towardsdatascience.com/applied-deep-learning-part-3-autoencoders-1c083af4d798)
* [Deep Learning](https://www.datacamp.com/community/tutorials/deep-learning-python)
                       
