# Analysis of Super Resolution in Image De-Oldification
Trained an image colorization model from scratch using conditional GAN architecture where the generator is a dynamic UNet (UNet with ResNet18 backbone) and the discriminator is a block of conv->BN->Relu. Implemented and analyzed two pipelines involving blur image colorization  followed by super resolution and blur image super resolution followed by colorization, where for implementing super resolution two different architectures are considered, ESRGAN and Real ESRGAN.

## Datasets:

Training/Validation -> COCO dataset (downloaded in code) 8000/2000

Test -> Kaggle Dataset: [Image Super Resolution](https://www.kaggle.com/datasets/adityachandrasekhar/image-super-resolution)
        and [Super Image Resolution](https://www.kaggle.com/datasets/akhileshdkapse/superimage-resolution).

### Directory Format:

    .
    ├── colorized_images
        ├── LR_fake             #Low resolution images colorization outcomes
        ├── LR_real_bw          #Low resolution *L channel images
        ├── LR_real_rgb         #Low resolution RGB images (orignal images considered while testing)
    ├── ESRGAN_Results
        ├── colortosuper        #LR -> Color -> Super Outcomes
        ├── LRtosuper           #LR -> Super Outcomes
        ├── super_bw            #Super Resolution Outcomes *L channel
        ├── super_rgb           #Super Resolution Outcomes RGB
        ├── supertocolor        #LR -> Super -> Color Outcomes
    ├── experiments
        ├── pretrained_models
            ├── RealESRGAN_x4plus.pth #Downloaded in Code
    ├── models
        ├── (All downloaded weights for ESRGAN will come here)
    ├── realesrgan #As provided
    ├── RealESRGAN_Results
        ├── colortosuper
        ├── LRtosuper
        ├── super_bw
        ├── super_rgb
        ├── supertocolor
    ├── test_data
        ├── LR          #Low Resolution test data from Kaggle
    ├── color.pt
    ├── VizWiz_Data_val
    ├── ColorizationESR.ipynb
    ├── ColorizationRealESR.ipynb
    ├── inference_realesrgan.py
    ├── res18-unet.pt
    └── RRDBNet_arch.py

## Overall Architecture for Colorization:
![image](https://user-images.githubusercontent.com/83297868/167446032-4893d3f5-c4f2-4475-9c2c-963b1c6b026d.png)

## Conditional GAN Generator (UNet with ResNet18 backbone) Architecture:
![image](https://user-images.githubusercontent.com/83297868/167445547-38e9d3a7-c417-4ae6-a024-cc0b7c72c9b1.png)

# Models Proposed:
### Model Pipeline 1:
![image](https://user-images.githubusercontent.com/83297868/167445812-25b81278-28e1-472b-beed-6575d86776b6.png)

![image](https://user-images.githubusercontent.com/83297868/167446170-b47b0135-25e3-48a7-909e-3e46a4abc320.png)

### Model Pipeline 2:
![image](https://user-images.githubusercontent.com/83297868/167445917-04a20c2f-60e7-41d3-bf56-f9778aa785ac.png)

![image](https://user-images.githubusercontent.com/83297868/167446230-43dfa364-a9e0-441f-9316-6e93866232f7.png)

# Outputs:

### Changes in output with each pipeline
![ALL](https://user-images.githubusercontent.com/83297868/167447882-0c8710b4-0df4-46fd-984a-2d27f06269f2.gif)

### Pipeline 2 Outcome for structured images with ESRGAN and RealESRGAN
![Face](https://user-images.githubusercontent.com/83297868/167447963-36015ab9-4666-424c-b360-20a5220ddf56.gif)

### Pipeline 2 Outcome for non-structured images with ESRGAN and RealESRGAN
![Nature](https://user-images.githubusercontent.com/83297868/167449476-ee6972fb-73b7-4fae-9b33-63ea305f4467.gif)

### Outcomes from different pipelines:
![image](https://user-images.githubusercontent.com/83297868/167447262-63143694-b0c8-4229-b86d-636d886ce42d.png)

# *Miscellaneous*
### Outcomes of the trained colorization model on COCO dataset
![image](https://user-images.githubusercontent.com/83297868/167439459-11ac5972-33df-4f8e-bd45-9fc9ab68603a.png)
![image](https://user-images.githubusercontent.com/83297868/167439481-21ff8bde-bb32-4083-93ed-047862184ee2.png)
![image](https://user-images.githubusercontent.com/83297868/167439504-32e11b46-8c0f-4530-ab90-d36da5b8d79f.png)
![image](https://user-images.githubusercontent.com/83297868/167439522-92654c34-462b-4d59-b11d-62d8a5dfee22.png)
![image](https://user-images.githubusercontent.com/83297868/167439548-0617fc73-1a71-4311-bf13-111a2069c7ed.png)
![image](https://user-images.githubusercontent.com/83297868/167439576-853e722f-8b5e-40ba-aefc-5faa56f8a0fb.png)
![image](https://user-images.githubusercontent.com/83297868/167439594-9d71c1bc-3ddf-495f-a4c4-e845ccef566f.png)
![image](https://user-images.githubusercontent.com/83297868/167439621-402049eb-ca28-44dd-bd3d-5e05b4a9e72f.png)


