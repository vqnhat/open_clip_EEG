# open_clip_EEG
EEG classification with CLIP style contrastive learning

## Dataset
Access the processed EEG tensor dataset via this [Goole drive link](https://drive.google.com/drive/folders/1U9HKXpRc9HqQFgzcqXDek-fL1GzOufel?usp=sharing). Ensure you download and place the data in your designated data directory before starting the training process.

## Usage
```
pip install -r requirements.txt
```

Launch the training script using torchrun. Here is an example command for a single node:

```
torchrun --nproc_per_node 1 -m open_clip_train.main --train-num-samples 10968539 --dataset-type EEG --batch-size 40 --precision amp --workers 0 --fold 1 --model ViT-H-14 --pretrained ../weights/ViT-H-14/open_clip_pytorch_model.bin --dataset "../data/EEG-BasedBCIClassification/2. BCI-ABSB/ABSB-4D/BCI_ABSB_SubjectB_2LR_4D.mat" --max_EEG_channel 62
```

Command Arguments

`----dataset-type`: define the EEG data type

`--fold`: Select the dataset subset to validate, the remaining data will be used as the training data

`--max_EEG_channel`: maximum supported EEG channels number in the training data

`--dataset`: path to the EEG tensor data. List of supported training data:

&emsp;&emsp;- Data Set IVa for the BCI Competition III

&emsp;&emsp;&emsp;`1. BCI-III/Tensor-form/4D-7-Channel/BCI_IV_al_4D_7Channels.mat`

&emsp;&emsp;&emsp;`1. BCI-III/Tensor-form/4D-7-Channel/BCI_IV_aw_4D_7Channels.mat`

&emsp;&emsp;&emsp;`1. BCI-III/Tensor-form/4D-7-Channel/BCI_IV_ay_4D_7Channels.mat`
             
&emsp;&emsp;- ABSP BCI dataset

&emsp;&emsp;&emsp;`2. BCI-ABSB/ABSB-4D/BCI_ABSB_SubjectA_2LR_4D.mat`
        
&emsp;&emsp;&emsp;`2. BCI-ABSB/ABSB-4D/BCI_ABSB_SubjectB_2LR_4D.mat`
             
&emsp;&emsp;- Single Trial Recognition for the Jiaotong EEG motor imagery dataset

&emsp;&emsp;&emsp;`3. BCI-JP/4D/BCI_JP_sub1_4D.mat`
        
&emsp;&emsp;&emsp;`3. BCI-JP/4D/BCI_JP_sub2_4D.mat`
        
&emsp;&emsp;&emsp;`3. BCI-JP/4D/BCI_JP_sub3_4D.mat`
        
&emsp;&emsp;&emsp;`3. BCI-JP/4D/BCI_JP_sub4_4D.mat`
        
&emsp;&emsp;&emsp;`3. BCI-JP/4D/BCI_JP_sub5_4D.mat`

`--pretrained`: path to the pretrained CLIP weights

## Acknowledgments
We gratefully acknowledge [mlfoundations](https://github.com/mlfoundations) for providing the original [OpenCLIP](https://github.com/mlfoundations/open_clip) training code, which serves as the foundation for this repository.
