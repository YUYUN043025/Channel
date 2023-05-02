# Set up
Firstly setup NeRF according to original paper readme(environment: nerf)

Secondly setup LLFF according to original paper readme(environment: llff)

# Preparation
First create your own data folder(here we use Channel1) in the nerf_llff_data folder

Next, create a folder named images in the llfftest folder and place the captured images in this folder

Next you need to download the COLMAP software, (address: Release 3.8 - colmap/colmap - GitHub), and then generate poses following the official instruction. Finally we get database.db and the sparse folder

Under the environment "llff", run the following code to get file "poses_bounds.npy":
```
python imgs2poses.py path
```

Where path is the path of your own data(here is the path of Channel1).

Finally, if you face the error:

Mismatch between imgs 0 and poses 55 !!!!
Traceback (most recent call last):

File "run_nerf.py", line 878, in <module>
  
train()
  
File "run_nerf.py", line 544, in train
  
spherify=args.spherify)
  
File "C:\Users\HP\Desktop\nerf-pytorch-master\load_llff.py", line 246, in load_llff_data
  
poses, bds, imgs = _load_data(basedir, factor=factor) # factor=8 downsamples original imgs by 8x
  
TypeError: cannot unpack non-iterable NoneType object

Probably because the functions are not compatible. The solution is to create a new folder images_8 in your data folder(Channel1) and put the eight times downsampled images here.

Below is the command of downsampling:
```
python 8times.py
```
Remember to change the parameter "images_path" and "output_dir"

# Run the new data
Put the directory "Channel1" to directory "nerf_llff_data" and follow the following command:
```
python run_nerf.py --config channel.txt
```
