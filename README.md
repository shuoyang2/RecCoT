# RecCoT
The source code is for the paper: "RecCoT: Enhancing Recommendation via Chain-of-Thought"

# Requirements
torch == 2.6.0

torchvision == 0.21.0

torchaudio == 2.6.0

transformers == 4.51.2 

peft == 0.14.0 

deepspeed == 0.16.4 

vllm == 0.8.3 
# Preparation
The datasets used in the paper can all be downloaded from this 
[official website](https://amazon-reviews-2023.github.io/).
# Usage
1)CoT Generation.

```
sbatch CoT.sh
```
2)Pretrain the smaller model

First, run save.sh to get the data, then run pretrain.sh to obtain the pre-trained model. 
```
sbatch save.sh
sbatch pretrain.sh
```
After that, run save_cls.sh to get the Cache_Store(You need to modify the content in the utils\config.py to obtain results for different datasets. Also, change the ckpt_path in SaveClsModel class within the trainer.py of that directory to point to your trained model.).
```
sbatch sace_cls.sh
```
3）Down-streaming RecSys
```
sbatch RecCoT.sh
```