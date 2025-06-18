 ### Link Stealing Attacks Against Inductive Graph Neural Networks

This repository contains the implementation of link stealing attacks in an inductive graph learning setting, adapted and reproduced from the paper: [Link Stealing Attacks Against Inductive Graph Neural Networks](https://arxiv.org/pdf/2405.05784).

### Setup and Installation

To run this project, you will need to install several Python packages. The instructions below assume you're using Python 3.11.

Step 1: Install Required Libraries
 ```

pip install torch==2.1.0
pip install torchdata==0.6.1
pip install torch_geometric
pip install dgl
pip install tensorflow==2.15.0
pip install graphgallery

```

Step 2: Apply Compatibility Fixes

GraphGallery has some compatibility issues with Python 3.11+. Apply the following patches to fix them:

# Fix deprecated 'Iterable' import
```
sed -i 's/from collections import Iterable/from collections.abc import Iterable/' /usr/local/lib/python3.11/dist-packages/graphgallery/data_type.py

```

# Fix tqdm docstring concatenation issue

```
sed -i 's/tqdm_base.__doc__ + tqdm_base.__init__.__doc__/(tqdm_base.__doc__ or "") + (tqdm_base.__init__.__doc__ or "")/' /usr/local/lib/python3.11/dist-packages/graphgallery/utils/tqdm.py
```

# Baseline Attacks

1. Baseline0 model:
```
python mlp_attack.py --dataset cora --edge_feature all --target_model graphsage --shadow_model graphsage --baseline b0 --lr 0.006 --optim adam --scheduler --gpu -1 --node_only

```

2. Baseline1 model:

```
python mlp_attack.py --dataset cora  --edge_feature all --target_model graphsage --shadow_model graphsage --baseline b1 --lr 0.006 --optim adam --scheduler --gpu -1 --graph_only

```

3. Bseline2 model:
```

python mlp_attack.py --dataset cora  --target_model graphsage --shadow_model graphsage --baseline b2 --lr 0.006 --optim adam --scheduler --gpu -1 --node_graph_both
```
# Other Attacks

1. Attack-0

```
python mlp_attack.py --dataset cora --node_topology 0-hop --edge_feature all --target_model graphsage --shadow_model graphsage --lr 0.006 --optim adam --scheduler --gpu -1
```

2. Attack-1
```
python mlp_attack.py --dataset cora --node_topology 1-hop --edge_feature all --target_model graphsage --shadow_model graphsage --lr 0.006 --optim adam --scheduler --gpu -1
```

3. Attack-2
```
python mlp_attack.py --dataset cora --node_topology 2-hop --edge_feature all --target_model graphsage --shadow_model graphsage --lr 0.006 --optim adam --scheduler --gpu -1
```

4. Attack-3
```
python mlp_attack.py --dataset cora --node_topology 0-hop --edge_feature all --target_model graphsage --shadow_model graphsage --lr 0.006 --optim adam --scheduler --gpu -1 --plus
```


5. Attack-4
```
python mlp_attack.py --dataset cora --node_topology 1-hop --edge_feature all --target_model graphsage --shadow_model graphsage --lr 0.006 --optim adam --scheduler --gpu -1 --plus
```


6. Attack-5
```
python mlp_attack.py --dataset cora --node_topology 2-hop --edge_feature all --target_model graphsage --shadow_model graphsage --lr 0.006 --optim adam --scheduler --gpu -1 --plus
```


7. Attack-6
```
python mlp_attack.py --dataset cora --node_topology 1-hop --edge_feature all --target_model graphsage --shadow_model graphsage --lr 0.006 --optim adam --scheduler --gpu -1 --plus2
```


8. Attack-7
```
python mlp_attack.py --dataset cora --node_topology 2-hop --edge_feature all --target_model graphsage --shadow_model graphsage --lr 0.006 --optim adam --scheduler --gpu -1 --plus2
```


9. Attack-8
```
python mlp_attack.py --dataset cora --node_topology 1-hop --edge_feature all --target_model graphsage --shadow_model graphsage --lr 0.006 --optim adam --scheduler --gpu -1 --all
```

10. Attack-9
```
python mlp_attack.py --dataset cora --node_topology 2-hop --edge_feature all --target_model graphsage --shadow_model graphsage --lr 0.006 --optim adam --scheduler --gpu -1 --all

```
# Experimental Results

![Results Overview](result/results.pdf)

# Citations
```
@article{wu2024link,
  title={Link stealing attacks against inductive graph neural networks},
  author={Wu, Yixin and He, Xinlei and Berrang, Pascal and Humbert, Mathias and Backes, Michael and Gong, Neil Zhenqiang and Zhang, Yang},
  journal={arXiv preprint arXiv:2405.05784},
  year={2024}
}
```

