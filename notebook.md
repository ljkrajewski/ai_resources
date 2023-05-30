# Running the latest AI tools on RunPod
_Note: This list is incomplete. Use at your own risk._

## Start here
1. Go to [RunPod.io](https://runpod.io) and log in.
2. Go to _Template Selection_ and pick _Tensorflow_ template.
3. _coming soon_

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
2. Download the following extentions:
  - _start extentions here_

## Running the latest LLM text2text models
```
cd /workspace/
git clone https://github.com/oobabooga/text-generation-webui.git #(or alternatives below)

```
Alternative text generation UIs:
- [Honkware/text-generation-webui](https://github.com/Honkware/text-generation-webui) [_[git clone link]_](https://github.com/Honkware/text-generation-webui.git)  
Use with [TheBloke/falcon-40b-instruct-GPTQ](https://huggingface.co/TheBloke/falcon-40b-instruct-GPTQ).


## Downloading to your RunPod instance

### from URL link
To download a file from a website: ```curl <website_URL> -o <local_filename> -L```  
For example:
```
curl https://civitai.com/api/download/models/51913 -o edge-of-realism.safetensors -L
```

### from Google Drive:
1. At Google Drive, set the file for public availability to anyone with the link.
2. Create the folloing file on your destination:
```
#!/usr/bin/env bash
fileid="### file id from downoad URL ###"  #eg, 1AMQ1OndXcTxXwklOGJvK-A5uCGvHR4I7
filename="### local filename ###"
html=`curl -c ./cookie -s -L "https://drive.google.com/uc?export=download&id=${fileid}"`
curl -Lb ./cookie "https://drive.google.com/uc?export=download&`echo ${html}|grep -Po '(confirm=[a-zA-Z0-9\-_]+)'`&id=${fileid}" -o ${filename}
```
3. (optional) At Google Drive, set the file to restricted availability 
