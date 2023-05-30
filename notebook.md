# Running the latest AI tools on RunPod
_Note: This list is incomplete. Use at your own risk._

## Table of Contents
1. [Start here](#start-here)
2. [Running the latest AUTOMATIC1111/Stable Diffusion](#running-the-latest-automatic1111stable-diffusion)
3. [Running the latest LLM text2text models](#running-the-latest-llm-text2text-models)
4. [Downloading to your RunPod instance](#downloading-to-your-runpod-instance)  
    a. [from URL link](#from-url-link)  
    b. [from Google Drive](#from-google-drive)

## Start here
1. Go to [RunPod.io](https://runpod.io) and log in.
2. Go to _Templates_ and pick the _RunPod Pytorch 2_ template.
3. Select a pod to start.  
    - 48GB+ VRAM for 13B+ LLMs or hi-res Stable Diffusion pictures.
    - 24GB VRAM for most uses.
4. Set container size to 50GB
5. Start the pod instance.

## Running the latest AUTOMATIC1111/Stable Diffusion
1. Open a web terminal and run the following commands:
```
apt install wget git python3 python3-venv
cd /workspace/
git clone https://github.com/AUTOMATIC1111/stable-diffusion-webui.git
cd stable-diffusion-webui
pip install -r requirements.txt
python install.py
python launch.py --share
```
2. Download/install the following extentions:
  - _start extentions here_

## Running the latest LLM text2text models
```
cd /workspace/
git clone https://github.com/oobabooga/text-generation-webui.git #(or alternatives below)
cd text-generation-webui
pip install -r requirements.txt
git clone https://github.com/PanQiWei/AutoGPTQ
cd AutoGPTQ
pip install .
pip install einops
cd ..
python server.py --share --chat --auto-devices --model llama --autogptq --trust-remote-code
```
Alternative text generation UIs:
- [Honkware/text-generation-webui](https://github.com/Honkware/text-generation-webui) [_[git clone link]_](https://github.com/Honkware/text-generation-webui.git)  
Use with [TheBloke/falcon-40b-instruct-GPTQ](https://huggingface.co/TheBloke/falcon-40b-instruct-GPTQ)
  - Use with a 48GB VRAM GPU. 
  - In the file _text-generation-webui/modules/AutoGPTQ_loader.py_, find the line ```'use_safetensors': use_safetensors,``` and add after it a new line reading ```'trust_remote_code': shared.args.trust_remote_code,```.  
  - Make sure _auto-devices_, _bf16_, and _trust_remote_code_ are checked in the _model_ tab of the web UI.


## Downloading to your RunPod instance

### from URL link
To download a file from a website: ```curl <website_URL> -o <local_filename> -L```  
For example:
```
curl https://civitai.com/api/download/models/51913 -o edge-of-realism.safetensors -L
```

### from Google Drive
1. At Google Drive, set the file for public availability to anyone with the link.
2. Create the following file on your destination, replacing _fileid_ and _filename_ with their values:
```
#!/usr/bin/env bash
fileid="### file id from download URL ###"  #eg, 1AMQ1OndXcTxXwklOGJvK-A5uCGvHR4I7
filename="### local filename ###"
html=`curl -c ./cookie -s -L "https://drive.google.com/uc?export=download&id=${fileid}"`
curl -Lb ./cookie "https://drive.google.com/uc?export=download&`echo ${html}|grep -Po '(confirm=[a-zA-Z0-9\-_]+)'`&id=${fileid}" -o ${filename}
```
3. (optional) At Google Drive, reset the file back to restricted availability 
