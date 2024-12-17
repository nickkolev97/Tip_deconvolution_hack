Hackathon submission (17/12/2024) for tip deconvolution.

Aim: To fix tip artefacts in AFM images such as blunt tip and double tip.

Dataset: We are using the same dataset as in the "afm_imperfect_probe.ipynb" notebook. This is a single AFM scan of size ___nm?
An artificial dataset is then created to mimic blunt tips. The blunt tip image is made by convolving the original image with a gaussian
whose center and standard deviation are parameters chosen by the user. In our case, we randomly select these parameters from a uniform
distribution between [0.2,0.8) for the standard deviation (the tip radius), and the x and y offset of the gaussian center (with [0.2,0.8) 
being in units of pixels). We did not have time to try and do the double tip too. We realise that using a single AFM image will cause major overfitting
but training a more robust model we could apply to more data that still showed good results wasn't realistic within this timeframe. 

Solution: Our main focus were autoencoders. We tried a variety of different sizes and depths, mainly basing it off this paper (ref). We 
also tried some different loss functions, most notably a combination of MAE loss and SSIM loss, equally weighted. We compare the results of a few of the different
models by using their SSIM score compared to the original, uncorrupted image. In addition, we also used gwyddion's tip estimation and surface reconstruction function
on two images and we compare these to the autoencoders too.

