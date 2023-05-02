# Set up
Firstly setup NeRF according to original paper readme(environment: nerf)
Secondly setup LLFF according to original paper readme(environment: llff)
The directory "channel1" includes poses generated under the environment "llff"

# Run the new data
Put the directory "channel1" to directory "nerf_llff_data"
and follow the following command:
```
python run_nerf.py --config  
```
