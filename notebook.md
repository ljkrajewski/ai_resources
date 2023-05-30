# Running the latest AI tools on RunPod

1. Go to [RunPod.io](https://runpod.io) and log in.
2. Go to _Template Selection_ and pick _Tensorflow_ template.
3. 

## Running the latest AUTOMATIC1111/Stable Diffusion
2. Open a web terminal and run the following commands:
```
cd /workspace/
git clone stable-diffusion-webui
cd stable-diffusion-webui
pip install -r requirements.txt
apt install wget git python3 python3-venv
python install.py
python launch.py --share
```

To download a file from a website: curl _website_URL_ -o _local_filename_ -L  
For example:
```
curl https://civitai.com/api/download/models/51913 -o edge-of-realism.safetensors -L
```

## Running the latest LLM text2text models
```
cd /workspace/
git clone https://github.com/oobabooga/text-generation-webui.git #(or alternatives below)

```
Alternative text generation UIs:
- [Honkware/text-generation-webui](https://github.com/Honkware/text-generation-webui) [_[git clone link]_](https://github.com/Honkware/text-generation-webui.git)  
Use with [TheBloke/falcon-40b-instruct-GPTQ](https://huggingface.co/TheBloke/falcon-40b-instruct-GPTQ).


## To download from Google Drive:
1. At Google Drive, set the file for public availability to anyone with the link.
2. Create the folloing file on your destination:
```
#!/usr/bin/env bash
fileid="### file id from downoad URL ###"  #eg, 1AMQ1OndXcTxXwklOGJvK-A5uCGvHR4I7
filename="### local filename ###"
html=`curl -c ./cookie -s -L "https://drive.google.com/uc?export=download&id=${fileid}"`
curl -Lb ./cookie "https://drive.google.com/uc?export=download&`echo ${html}|grep -Po '(confirm=[a-zA-Z0-9\-_]+)'`&id=${fileid}" -o ${filename}
```
