# StackGAN

- PyTorch implementation of the paper [StackGAN: Text to Photo-realistic Image Synthesis with Stacked Generative Adversarial Networks](https://arxiv.org/pdf/1612.03242v1.pdf) by Han Zhang, Tao Xu, Hongsheng Li, Shaoting Zhang, Xiaogang Wang,   Xiaolei Huang, Dimitris Metaxas.
- We use BERT embeddings for the text description instead of the char-CNN-RNN text embeddings that was used in the paper implementation.
<img src="examples/framework.jpg" width="850px" height="370px"/>

## Pretrained model
- [Stage 1](https://drive.google.com/drive/folders/14AyNcu7oZJe2aMevynAbYIpMKN7I3yHT?usp=sharing) trained using BERT embeddings instead of the orignal char-CNN-RNN text embeddings


<!-- ### TODO:

- [ ] Clean the code and document code + README.md
- [ ] Check for bugs
- [ ] Try overfitting stage-1 
- [ ] Try overfitting stage-2
- [x] Train stage-1 locally
- [ ] Figure out the training by searching for loss OR
- [ ] Clone the repo and compare stage-1 results (make a script to do this)
- [ ] Train stage-2
- [ ] Upload bert embeddings
- [ ] Make repo public

### After public:
- [ ] Compare different embeddings (cnn-rnn, skip, bert)
- [ ] Document the training process  

 -->

## Paper examples
Examples for birds (char-CNN-RNN embeddings), more on [youtube](https://youtu.be/93yaf_kE0Fg):
![](examples/bird1.jpg) <br>
![](examples/bird2.jpg) <br>
![](examples/bird4.jpg) <br>
![](examples/bird3.jpg) <br>

--------------------------------------------------------------------------------------------
Examples for flowers (char-CNN-RNN embeddings), more on [youtube](https://youtu.be/SuRyL5vhCIM):
![](examples/flower1.jpg) <br>
![](examples/flower2.jpg) <br>
![](examples/flower3.jpg) <br>
![](examples/flower4.jpg) <br>

## Dataset
Check README.md in `/input`

## Generating BERT embeddings of annotations
```bash
cd input/src
python3 bert_emb.py  
```

### Training
```bash
cd src
```
Option 1: CLI args training (src/args.py)
```bash
python3 train.py --TRAIN_MAX_EPOCH 10 
```
Option 2: yaml args training (cfg/s1.yml and cfg/s2.yml)
```bash
python3 train.py --conf ../cfg/s1.yml

mkdir ../old_outputs
mv ../output ../old_outputs/output_stage-1

python3 train.py --conf ../cfg/s2.yml

mv ../output ../old_outputs/output_stage-2
```
To load the tensorboard
```bash
tensorboard --logdir=../output 
```


### Citing StackGAN
If you find StackGAN useful in your research, please consider citing:

```
@inproceedings{han2017stackgan,
Author = {Han Zhang and Tao Xu and Hongsheng Li and Shaoting Zhang and Xiaogang Wang and Xiaolei Huang and Dimitris Metaxas},
Title = {StackGAN: Text to Photo-realistic Image Synthesis with Stacked Generative Adversarial Networks},
Year = {2017},
booktitle = {{ICCV}},
}
```

**Follow-up work**

- [StackGAN++: Realistic Image Synthesis with Stacked Generative Adversarial Networks](https://arxiv.org/abs/1710.10916)
- [AttnGAN: Fine-Grained Text to Image Generation with Attentional Generative Adversarial Networks](https://arxiv.org/abs/1711.10485) [[supplementary]](https://1drv.ms/b/s!Aj4exx_cRA4ghK5-kUG-EqH7hgknUA) [[code]](https://github.com/taoxugit/AttnGAN)

**References**

- Generative Adversarial Text-to-Image Synthesis [Paper](https://arxiv.org/abs/1605.05396) [Code](https://github.com/reedscot/icml2016)
- Learning Deep Representations of Fine-grained Visual Descriptions [Paper](https://arxiv.org/abs/1605.05395) [Code](https://github.com/reedscot/cvpr2016)