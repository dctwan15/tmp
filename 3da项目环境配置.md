3da项目环境配置

本文档说明3d diffusor actor的项目环境配置，包括代码环境和推理时仿真环境

1. 安装系统依赖（仿真环境视频流转发用，**4090上有显示器应该不需要这一步**）

   ```
   sudo apt install libxcb-ra xorg xvfb x11-apps x11-utils x11-xserver-utils libx11-xcb1 libxcb-util1 libxcb-xinerama0 libxcb-render0 libxcb-shape0 libxcb-shm0 libxkbcommon-x11-0 libdbus-1-3 libxcb-xinerama0 libxkbcommon-x11-0 libxcb-icccm4 libxcb-image0 libxcb-keysyms1
   ```

   可能有一些依赖在安装过程中会出现问题，可以先跳过这些出问题的依赖，把能装上的依赖先装上

2. 项目环境

   ```shell
   # 创建虚拟环境 (diff: python3.9)
   conda create -n 3da python=3.9
   
   # 安装cuda和pytorch环境 (diff: pytorch==2.0.0, pytorch-cuda=11.8)
   conda install pytorch==2.0.0 torchvision==0.15.0 torchaudio==2.0.0 pytorch-cuda=11.8 -c pytorch -c nvidia
   
   # 安装剩余的依赖
   pip install diffusers["torch"]
   
   # diff: cu118, cp39
   pip install dgl==1.1.3+cu118 -f https://data.dgl.ai/wheels/cu118/dgl-1.1.3%2Bcu118-cp39-cp39-manylinux1_x86_64.whl
   
   pip install packaging
   pip install ninja
   
   # 下载文件安装：flash_attn-2.5.9.post1+cu118torch2.0cxx11abiTRUE-cp39-cp39-linux_x86_64.whl
   # 下载链接：https://github.com/Dao-AILab/flash-attention/releases?page=3
   # diff: cu118, cp39
   pip install flash-attn==2.5.9.post1 --no-build-isolation
   
   pip install -r requirements.txt
   ```

   requirements.txt文件内容如下

   ```
   git+https://github.com/openai/CLIP.git
   numpy==1.23.5
   pillow
   einops
   typed-argument-parser
   tqdm
   transformers
   absl-py
   matplotlib
   scipy
   tensorboard
   opencv-python
   blosc
   setuptools==57.5.0
   beautifulsoup4
   bleach>=6.0.0
   defusedxml
   jinja2>=3.0
   jupyter-core>=4.7
   jupyterlab-pygments
   mistune==2.0.5
   nbclient>=0.5.0
   nbformat>=5.7
   pandocfilters>=1.4.1
   tinycss2
   traitlets>=5.1
   ```

   

   安装PyRep和RLBench，按照官网过程即可

   

   

