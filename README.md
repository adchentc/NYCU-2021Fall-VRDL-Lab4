# NYCU_VRDL_Super_Resolution


## <div align="center">Abstract</div>

This repository is a assignment in NYCU VRDL. In this assignment, we are only allow to use 291 HR images for training and 14 LR images are for the inference. Our main task is to turn low-resolution image to high-resolution image and has to beat the baseline which PSNR score is 27.4162. The best experiment result that we achieved the goal with IMDN model which we referenced the code in [IMDN](https://github.com/Zheng222/IMDN) and got PSNR 27.8949 in the final submission.

## <div align="center">Proposed Approach</div>
<p>
<!--    <a align="center" target="_blank"> -->
   <img width="850" src="https://github.com/adchentc/NYCU_VRDL_Super_Resolution/blob/main/proposed.png"></a>
</p>

## <div align="center">Usage</div>

### Dependencies
  - Python 3.8.10
  - PyTorch 1.10.0

### Checkpoints

You can download our model weight [HERE](https://drive.google.com/file/d/1xn91pdAP7HgM8-iz8JHglvxcedF8qJqi/view?usp=sharing)

### Training
  - Clone the repository from [Zheng222](https://github.com/Zheng222/IMDN)
  ```
  $ git clone https://github.com/Zheng222/IMDN
  ```
  - Download [Dataset](https://drive.google.com/file/d/1DLMvJTKJYNqc-qsU_MVfuMDSGWl4DEGL/view?usp=sharing)
  - Convert png file to npy file
  ```
  python scripts/png2npy.py --pathFrom /path/to/DIV2K/ --pathTo /path/to/DIV2K_decoded/
  ```
  - Run training x2, x3, x4 model
  ```
  python train_IMDN.py --root /path/to/DIV2K_decoded/ --scale 2 --pretrained checkpoints/IMDN_x2.pth
  python train_IMDN.py --root /path/to/DIV2K_decoded/ --scale 3 --pretrained checkpoints/IMDN_x3.pth
  python train_IMDN.py --root /path/to/DIV2K_decoded/ --scale 4 --pretrained checkpoints/IMDN_x4.pth
  ```
  
### Testing
  - Run testing
  ```
  python test_IMDN.py --test_hr_folder Test_Datasets/Set5/ --test_lr_folder Test_Datasets/Set5_LR/x3/ --output_folder results/Set5/x3 --checkpoint checkpoints/IMDN_x2.pth --upscale_factor 3
  ```
