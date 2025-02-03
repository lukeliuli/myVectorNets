# vectornet生成condaEnv
-  参考 https://github.com/Liang-ZX/VectorNet 
-  

## 基本命令
- conda create -n vectornet python=3.7
- pip install torch==1.1.0 -f https://download.pytorch.org/whl/cu90/torch
    - or  pip install torch==1.1.0+cu90 torchvision==0.3.0+cu90 -f https://download.pytorch.org/whl/torch_stable.html
    - or  pip install torch==1.1.0 https://download.pytorch.org/whl/cu90/torch
    - or  wget https://download.pytorch.org/whl/cu90/torch-1.1.0-cp37-cp37m-linux_x86_64.whl
- pip install torchvision==0.3.0 -f https://download.pytorch.org/whl/cu90/torchvision
- apt install cmake -y && apt install libgl-dev -y
- cd argoverse_api 
- pip install -e .
    - 中间会出现错误，把sklearn变为scikit-learn
- pip install   tensorboard==2.11.2 \
                tqdm \
                future
- cp functional.py /root/miniconda3/envs/vectornet/../python3.7/site-packages/torchvision/transforms/
     - or cp functional.py functional.py 的环境中
- cd vectorNet
    - pip install -r requirement.txt
- 其余就是看train.py 把下载argo数据库房在dataset文件夹中
- python train.py

# docker 生成 vectornet镜像
-  参考 https://github.com/bithuanglq/Docker-VectorNet
## 基本命令
- 修改 argoverse_api下的setup.py 中sklearn 为scikit-learn
- 进入docker-vectorNet目录中运行docker build -f Dockerfile -t vectornet .
- 如果成功，按照docker-vectorNet里面的README.md运行其他指令
    - 其中运行容器的指令改为 docker run -it -d --name vectornet -v /train_data_path:/mnt/vectorNet/Dataset vectornet /bin/bash
    - or docker cp forecasting_train_v1.1.tar.gz vectornet:/mnt/vectorNet/Dataset ,然后解压生成train目录
# 注意
1. 所有步骤的框架和细节都在 https://github.com/bithuanglq/Docker-VectorNet  和 https://github.com/Liang-ZX/VectorNet 中
2. vectornet_condaenv.tar 为conda vectornet环境的整体打包
3. vectornetCondaEnv.yaml 为conda vectornet环境的配置
4. 