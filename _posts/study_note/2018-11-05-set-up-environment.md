---
layout: post
title: "Setting up environment for remote server"
categories: [Study notes]
---

### setup PyTorch with miniconda:
```terminal
curl -o ~/miniconda.sh -O  https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh
chmod +x ~/miniconda.sh
./miniconda.sh
source ~/.bashrc
conda create -n deep_mol python=3.6 numpy mkl ipython jupyter scipy seaborn pandas matplotlib scikit-learn networkx
source activate deep_mol
conda install pytorch torchvision -c pytorch
```

### use tmux:
```terminal
ssh xxx@server_address
tmux new -s mol
source activate environment_name
jupyter-notebook --no-browser --ip=0.0.0.0 --port=8888 --NotebookApp.token='token_name'
```

### Local computer:
```terminal
ssh -N -f -L localhost:8701:localhost:8888 xiaoyu@172.21.32.185
```

### In local browser
Tap *http://localhost:8701*

Put in the token name defined.

### To specify the GPU in the notebook:
```

gpu_id = 1

os.environ["CUDA_DEVICE_ORDER"] = "PCI_BUS_ID"

os.environ["CUDA_VISIBLE_DEVICES"] = str(gpu_id)
```


### To specify the GPU in the terminal:
```
CUDA_VISIBLE_DEVICES=1 python main_script.py
```


### You can check the GPU running with the terminal line:
```
nvidia-smi
```
