This is a docker version of [this](https://github.com/Liang-ZX/VectorNet), fixing some bugs and 
organize the necessary compilation and running environment to quickly get started with [VectorNet](https://arxiv.org/pdf/2005.04259.pdf), a trajectory prediction network for autonomous vehicles.


## 1. Prerequist
[ubuntu 20.04](https://releases.ubuntu.com/20.04/)

## 2. Build project
### 2.1 Create directory and clone project
```
cd / && mkdir Vectornet_ws && cd Vectornet_ws
git clone https://github.com/bithuanglq/Docker-VectorNet.git
```

### 2.2 Create docker image from Dockerfile
Create your image (e.g. vectornet:latest).
```
docker build -f Dockerfile -t vectornet .
```

## 3. Running
### 3.1 Create docker container and enter
You can create and run a container with the following command:
```
docker run -it -d --name container_name vectornet /bin/bash
```

And then, if you want to enter the container (to run commands inside the container interactively), you can use the docker exec command:
```
docker exec -it container_name /bin/bash
```

### 3.2 Download dataset
In your host machine, put [Argoverse-forecasting-training-dataset](https://www.argoverse.org/av1.html#download-link) in ___/Vectornet_ws/VectorNet/Dataset/train/___, overwriting _/data_ diretory.
The files in _/data_ is structured data with suffix .csv


### 3.3 Train
```
cd /mnt/VectorNet 
python train.py
```



# Acknowledge
Thanks to this [repo](https://github.com/Liang-ZX/VectorNet), [dataset](https://github.com/argoverse/argoverse-api), and [paper](https://arxiv.org/pdf/2005.04259.pdf).
