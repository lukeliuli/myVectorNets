FROM python:3.7.16

LABEL "Author"="Liqun Huang"
LABEL "Email"="2728679381@qq.com"

USER root
WORKDIR /root

RUN apt update && \
    mkdir .pip && cd .pip && touch pip.conf && \
    apt install vim -y && \
    echo "[global]" >> pip.conf && \
    echo "index-url = https://pypi.tuna.tsinghua.edu.cn/simple" >> pip.conf 

WORKDIR /mnt

RUN mkdir argoverse_api VectorNet
COPY argoverse_api ./argoverse_api
COPY VectorNet ./VectorNet
COPY README.md ./

RUN cd /mnt/VectorNet 
RUN apt install cmake -y && apt install libgl-dev -y
RUN pip install -e /mnt/argoverse_api 
RUN pip install torch==1.1.0  \
                torchvision==0.3.0 \
                tensorboard==2.11.2 \
                tqdm \
                future

COPY functional.py /usr/local/lib/python3.7/site-packages/torchvision/transforms/

CMD [ "/bin/bash" ]
