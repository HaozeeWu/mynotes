# mynotes
## 更改unbuntu python版本

> 安装anaconda，选择合适的版本，在虚拟环境中安装对应的torch

    wget https://repo.anaconda.com/archive/Anaconda3-2019.10-Linux-x86_64.sh

## 终端显示光标

    echo -e "\033[?25h"

## 创建conda环境

    conda create --name my_env python=3.7

## pip 源

    pip install pipenv -i https://pypi.tuna.tsinghua.edu.cn/simple https://pypi.mirrors.ustc.edu.cn/simple
    pip install scipy==1.2.1 -i https://pypi.tuna.tsinghua.edu.cn/simple

## &#x20;pip安装torch

    pip install torch==1.8.1+cu111 torchvision==0.9.1+cu111 torchaudio==0.8.1 -f https://download.pytorch.org/whl/torch_stable.html --default-timeout=1000

## pip下载超时

    pip --default-timeout=1000

## 服务器后台运行

    nohup python -u train_denoise.py --args_file params.json > train_20230308.log 2>&1 &
    nohup python -u test.py > test.log 2>&1 &

## 查看后台运行的所有进程

    ps -aux 
    ps aux |grep python #python进程

## 关闭进程

    kill -9 [进程id]

    >jobs

    >fg %1

    >ctrl +C

## 双卡启动命令

    nohup python -u -m torch.distributed.launch --nproc_per_node=2 train_double.py > log/train2023_0413_test1.log 2>&1 &