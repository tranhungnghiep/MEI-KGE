# MEI: Multi-partition Embedding Interaction

This implements the MEI knowledge graph embedding method in the paper [Multi-Partition Embedding Interaction with Block Term Format for Knowledge Graph Completion](https://arxiv.org/abs/2006.16365) (ECAI 2020). MEI unifies several recent state-of-the-art KGE models and provides an optimal efficiency-expressiveness solution. The code is optimized for high performance in PyTorch and demonstrates several important techniques in KGE.

Knowledge graph embedding methods (KGE) aim to learn low-dimensional vector representations of entities and relations in knowledge graphs. The models take input in the format of triples (h, t, r) denoting head entity, tail entity, and relation, respectively, and output their embedding vectors as well as solving the link prediction task. For more information, please see our paper.

## Installation
- Clone the repository to your local machine: `git clone https://github.com/tranhungnghiep/MEI-KGE/`
- Go to the repository directory: `cd MEI-KGE/`
- Install required packages, you may install in a separate environment: `pip install -r requirements.txt`
- Go to the source directory: `cd src/`

## How to run
The following commands contain optimal hyperparameters for MEI.

On WN18RR:
```shell script
python main.py --seed 7 --config_id "rep" --gpu 0 --model MEI --in_path ../datasets/wn18rr/ --out_path ../result/ --check_period 5 --K 3 --Ce 100 --Cr 100 --reuse_array torch1pin --sampling kvsall --loss_mode softmax-cross-entropy --batch_size 1024 --max_epoch 1000 --opt_method adam --amsgrad 0 --lr 3e-3 --lr_scheduler exp --lr_decay 0.99775 --lambda_ent 0.0 --lambda_rel 0.0 --lambda_params 0.0 --label_smooth 0.0 --constraint "" --to_constrain "" --lambda_rowrelnorm 0.0 --droprate_w 0.0 --droprate_r 0.0 --droprate_mr 0.0 --droprate_h 0.71 --droprate_mrh 0.67 --droprate_t 0.0 --norm bn --n_w 0 --n_r 0 --n_mr 0 --n_h 1 --n_mrh 1 --n_t 0 --n_sepK 1
```
On FB15K-237:
```shell script
python main.py --seed 7 --config_id "rep" --gpu 0 --model MEI --in_path ../datasets/fb15k-237/ --out_path ../result/ --K 3 --Ce 100 --Cr 100 --reuse_array torch1pin --sampling 1vsall --loss_mode softmax-cross-entropy --batch_size 1024 --max_epoch 1000 --opt_method adam --amsgrad 1 --lr 3e-3 --lr_scheduler exp --lr_decay 0.99775 --lambda_ent 0.0 --lambda_rel 0.0 --lambda_params 0.0 --label_smooth 0.0 --constraint "" --to_constrain "" --lambda_rowrelnorm 0.0 --droprate_w 0.0 --droprate_r 0.0 --droprate_mr 0.0 --droprate_h 0.66 --droprate_mrh 0.67 --droprate_t 0.0 --norm bn --n_w 0 --n_r 0 --n_mr 0 --n_h 1 --n_mrh 1 --n_t 0 --n_sepK 0
```
On YAGO3-10:
```shell script
python main.py --seed 7 --config_id "rep" --gpu 0 --model MEI --in_path ../datasets/YAGO3-10/ --out_path ../result/ --K 5 --Ce 100 --Cr 100 --reuse_array torch1gpu --sampling 1vsall --loss_mode softmax-cross-entropy --batch_size 1024 --max_epoch 1000 --opt_method adam --amsgrad 1 --lr 3e-3 --lr_scheduler exp --lr_decay 0.995 --lambda_ent 0.0 --lambda_rel 0.0 --lambda_params 0.0 --label_smooth 0.0 --constraint "" --to_constrain "" --lambda_rowrelnorm 0.0 --droprate_w 0.0 --droprate_r 0.0 --droprate_mr 0.0 --droprate_h 0.1 --droprate_mrh 0.15 --droprate_t 0.0 --norm bn --n_w 0 --n_r 0 --n_mr 0 --n_h 1 --n_mrh 1 --n_t 0 --n_sepK 0
```

## Results


## How to cite
If you found this code or our work useful, please cite us.
- *Hung Nghiep Tran and Atsuhiro Takasu. [Multi-Partition Embedding Interaction with Block Term Format for Knowledge Graph Completion](https://arxiv.org/abs/2006.16365). In Proceedings of the European Conference on Artificial Intelligence (ECAI), 2020.*  
  ```
  @inproceedings{tran_multipartitionembeddinginteraction_2020,
    title = {Multi-{Partition} {Embedding} {Interaction} with {Block} {Term} {Format} for {Knowledge} {Graph} {Completion}},
    booktitle = {Proceedings of the {European} {Conference} on {Artificial} {Intelligence}},
    author = {Tran, Hung Nghiep and Takasu, Atsuhiro},
    year = {2020},
    pages = {833--840},
    url = {https://arxiv.org/abs/2006.16365},
  }
  ```
- *Hung Nghiep Tran and Atsuhiro Takasu. [MEIM: Multi-partition Embedding Interaction Beyond Block Term Format for Efficient and Expressive Link Prediction](). In Proceedings of the International Joint Conference on Artificial Intelligence (IJCAI), 2022.*  
  ```
  @inproceedings{tran_meimmultipartitionembedding_2022,
    title = {{MEIM}: {Multi}-partition {Embedding} {Interaction} {Beyond} {Block} {Term} {Format} for {Efficient} and {Expressive} {Link} {Prediction}},
    booktitle = {Proceedings of the {Thirty}-{First} {International} {Joint} {Conference} on {Artificial} {Intelligence}},
    author = {Tran, Hung Nghiep and Takasu, Atsuhiro},
    year = {2022},
    pages = {2262--2269},
  }
  ```

## See also
- AnalyzeKGE, preliminary experiments and analysis: https://github.com/tranhungnghiep/AnalyzeKGE
- MEIM-KGE, MEI iMproved beyond block term format: https://github.com/tranhungnghiep/MEIM-KGE
- KG20C, a scholarly knowledge graph benchmark dataset: https://github.com/tranhungnghiep/KG20C
