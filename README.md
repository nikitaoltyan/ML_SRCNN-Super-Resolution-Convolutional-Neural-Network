# ML_SRCNN-Super-Resolution-Convolutional-Neural-Network
Implementation of SRCNN architecture using Deep Learning and PyTorch

**Members** : <a href="https://github.com/nikitaoltyan">Nikita Oltyan</a>, <a href="https://github.com/arseniyzu">Arseniy Zubenya</a>

## Description

This project aims to improve image quality (image debluring) with the use of SRCNN model. The below image briefly explains the output we want:

<p align="center">
<img src="./assets/output_example.JPG">
</p>


## Table of Content

* [Dataset](#dataset)

* [Model](#model)

* [PSNR Function](#psnr_function)

* [Results](#results)

* [Dependency](#dependency)

* [References](#references)


## Dataset <a name="dataset"></a>

The dataset contains:

**13056 train images (256x128)**

**3200 val images (256x128)**

You can find a whole lot of image dataset mainly used for super-resolution experimentation in this public <a href="https://drive.google.com/file/d/1QI3MvHTxFzwZfF1xdgJv0EJqB91yAzMG/view?usp=sharing">Google Drive folder</a>.

**All examples of training and validation data are groped into one picture with a good quality one on the left side and a poor quality on the right.**

<p align="center">
<img src="./assets/train_example.JPG">
</p>

Below the line you can find a story of an idea of that dataset and how we get that data.

---

After brief examination of our task we decided that there wasn’t any easy way of implementing Super Resolution for any image of any object we want.

We decided to concentrate our efforts on improving quality of skyline pictures. This is a common problem for a millions of traveling people – they often zoom horizon, trying to take their best pictures of sunsets/city skylines/historical sites.

```sh
# The quality of original images was decreade by Image function.
size = 1024, 1024
file_path = "some/file/path"
image = Image.open(file_path)
new_image= image.resize(size, Image.ANTIALIAS)
    
save_path = "some/new/file/path"
new_image.save(save_path, optimize=True, quality=20)
```

We’ve started with dataset of skyline pictures taken by Nikita from his flat using digital slr but they were too big for any existing models: 3024x4032 pixels.

So we resized them into 1024x1024, bet it still was too big and expensive for resources:

<p align="center">
<img src="./assets/original_image_example.JPG">
</p>

So we tried to crop them into batches of 16 pieces with 256x256 size each but is was hopeless. That gave us an 4000 items dataset that wasn’t enough, especially in difficult parts where sky and buildings are together. The pixelation didn’t disappear, but blur was added.

<p align="center">
<img src="./assets/wrong_working_example.jpg">
</p>

In the final stage of data preparing we changed “RGB” color channels into “L” (black and white) and divided original images into batches of 64 pieces with 128x128 size each. That’s how we get our dataset that now available.

<p align="center">
<img src="./assets/test_images_stack.png">
</p>

## Model <a name="model"></a>

## PSNR Function <a name="psnr_function"></a>

## Results <a name="results"></a>

## Dependency <a name="dependency"></a>

## References <a name="references"></a>
