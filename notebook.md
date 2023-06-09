# Running the latest AI tools on RunPod
_Note: This list is incomplete. Use at your own risk._

## Table of Contents
1. [Start here](#start-here)
2. [Running the latest AUTOMATIC1111/Stable Diffusion](#running-the-latest-automatic1111stable-diffusion)
3. [Running the latest oobabooga/text-generation-webui](#running-the-latest-oobaboogatext-generation-webui)
4. [Running Honkware/text-generation-webui](#running-honkwaretext-generation-webui)
5. [Downloading to your RunPod instance](#downloading-to-your-runpod-instance)  
    a. [from URL link](#from-url-link)  
    b. [from Google Drive](#from-google-drive)

## Start here
1. Go to [RunPod.io](https://runpod.io) and log in.
2. Go to _Templates_ and pick the _RunPod Pytorch 2.0.1_ template.
3. Select a pod to start.  
    - 48GB+ VRAM for 13B+ LLMs or hi-res Stable Diffusion pictures.
    - 24GB VRAM for most uses.
4. Set container size to 50GB
5. Open HTTP ports 8080, 7860
6. Start the pod instance.

## Running the latest [AUTOMATIC1111/Stable Diffusion](https://github.com/AUTOMATIC1111/stable-diffusion-webui)
### Method 1: Using Jupyter Notebook
1. After starting a RunPod instance ([see above](#start-here)), open a web terminal and run the following commands:
```
cd /workspace
git clone https://github.com/ljkrajewski/runpod_ai.git
```
2. Open Jupyter Notebook, then run _/workstation/runpod_ai/stable_diffusion-A1111.ipynb_
    - _TODO: write about user-modifiable sections_ 
4. When the "Running on public URL:" line appears, click on the _gradio.live_ link to enter your Automatic 1111 session.

### Method 2: Manual Install
1. After starting a RunPod instance ([see above](#start-here)), open a web terminal and run the following commands:
```
apt install vim wget git python3 python3-venv -y
useradd -U -d /home/user -s /bin/bash user
mkdir /home/user && chown user:user /home/user && chmod 750 /home/user
chown user:user /workspace
su user
cd /workspace
bash <(wget -qO- https://raw.githubusercontent.com/AUTOMATIC1111/stable-diffusion-webui/master/webui.sh)
# <ctrl>-c to stop webui.sh when you get to "Model loaded in..."
cd /workspace/stable-diffusion-webui/
sed -i 's/#export COMMANDLINE_ARGS=""/export COMMANDLINE_ARGS="--xformers --enable-insecure-extension-access --share"/' webui-user.sh
## TODO: check on cmd line flags to allow extentions to run
./webui.sh &
```
2. Download/install the following extentions:
    - [kohya-ss/sd-webui-additional-networks](https://github.com/kohya-ss/sd-webui-additional-networks) ([_git clone link_](https://github.com/kohya-ss/sd-webui-additional-networks.git)) To use LoRA models.  
Instructions: [How to Use LoRA Models with Automatic1111’s Stable Diffusion Web UI](https://www.kombitz.com/2023/02/09/how-to-use-lora-models-with-automatic1111s-stable-diffusion-web-ui/)
    - [Mikubill/sd-webui-controlnet](https://github.com/Mikubill/sd-webui-controlnet) ([_git clone link_](https://github.com/Mikubill/sd-webui-controlnet.git)) Multi-ControlNet  
Instructions: [How to Use ControlNet with Automatic1111’s Stable Diffusion Web UI](https://www.kombitz.com/2023/02/18/how-to-use-controlnet-with-automatic1111-stable-diffusion-web-ui/)  
ControlNet models:
      - [lllyasviel/ControlNet - Hugging Face](https://huggingface.co/lllyasviel/ControlNet/tree/main/models)
      - [lllyasviel/ControlNet-v1-1 - Hugging Face](https://huggingface.co/lllyasviel/ControlNet-v1-1/tree/main)
      - [TencentARC/T2I-Adapter - Hugging Face](https://huggingface.co/TencentARC/T2I-Adapter/tree/main/models)
3. Download any models you want to use.
```
cd /workspace/stable-diffusion-webui/models/Stable-diffusion
curl "https://civitai.com/api/download/models/51913" -o "edge_of_realism.safetensors" -L
```

## Running the latest [oobabooga/text-generation-webui](https://github.com/oobabooga/text-generation-webui)
1. After starting a RunPod instance ([see above](#start-here)), open a web terminal and run the following commands:
```
## Set user interface
export interface='\-\-chat'
#export interface='\-\-notebook'

## Set desired model
export model='anon8231489123/vicuna-13b-GPTQ-4bit-128g'
export switches='\-\-wbits 4 \-\-groupsize 128'
#export model='TheBloke/WizardLM-Uncensored-Falcon-7B-GPTQ'
#export switches='\-\-autogptq \-\-trust-remote-code'

## Install and start the UI
pip install tqdm
apt install zip -y
cd /workspace/
wget https://github.com/oobabooga/text-generation-webui/releases/download/installers/oobabooga_linux.zip
unzip oobabooga_linux.zip

cd /workspace/oobabooga_linux
git clone https://github.com/oobabooga/text-generation-webui.git
cd text-generation-webui
python -m pip install -r ./requirements.txt
python download-model.py $model
cd ..
#sed -i "s/CMD_FLAGS = '--chat'/CMD_FLAGS = '--share $interface $switches'/" webui.py
export OOBABOOGA_FLAGS="--share $interface $switches"
sed -i 's/gpuchoice = input("Input> ").lower()/gpuchoice = "a"/' webui.py
bash start_linux.sh
```
2. _Extentions to install?_

## Running [Honkware/text-generation-webui](https://github.com/Honkware/text-generation-webui)
For running the [TheBloke/falcon-40b-instruct-GPTQ](https://huggingface.co/TheBloke/falcon-40b-instruct-GPTQ) model. [This is why you should care about the Falcon 40b model.](https://huggingface.co/blog/falcon)

1. Start a RunPod instance as described [above](#start-here) with a 48GB VRAM GPU.
2. After starting a RunPod instance, open a web terminal and run the commands above for _oobabooga_, except:
     - replace the _model_ and _switches_ variables with:
     ```
     export model='TheBloke/falcon-40b-instruct-GPTQ'
     export switches=''
     ```
     - add
    ```
    sed -i "s/github.com\/oobabooga\/text/github.com\/Honkware\/text/g" webui.py
    ``` 
    between ```cd /workspace/oobabooga_linux``` and the first ```sed``` command. In other words:
    <pre><code>...
   cd /workspace/oobabooga_linux
   <b>sed -i "s/github.com\/oobabooga\/text/github.com\/Honkware\/text/g" webui.py</b>
   sed -i "s/CMD_FLAGS = '--chat'/CMD_FLAGS = '--share $interface $switches'/" webui.py
   ...</code></pre>
3. In the _model_ tab of the web UI, make sure _auto-devices_, _bf16_, and _trust_remote_code_ are checked.

**NOTE:** Falcon 40b is _extremely_ slow (~0.7 tokens/sec) and needs ~90GB VRAM to run well. A potential alternative is [TheBloke/falcon-7b-instruct-GPTQ].
 ```
 export model='TheBloke/falcon-7b-instruct-GPTQ'
 export switches='--autogptq --trust-remote-code'
 ```

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
cd /workspace/stable-diffusion-webui/models/Stable-diffusion/  #if downloading a checkpoint
#cd /workspace/stable-diffusion-webui/models/Lora  #if downloading a Lora
html=`curl -c ./cookie -s -L "https://drive.google.com/uc?export=download&id=${fileid}"`
curl -Lb ./cookie "https://drive.google.com/uc?export=download&`echo ${html}|grep -Po '(confirm=[a-zA-Z0-9\-_]+)'`&id=${fileid}" -o ${filename}
```
3. (optional) At Google Drive, reset the file back to restricted availability.

----
## Preparing your RunPod instance for development using git and github
Run each line individually.
```
apt update
apt install vim -y
cd ~
ssh-keygen -t ed25519 -f .ssh/runpod -C "Temp runpod key"
cat .ssh/runpod.pub
# Copy the public key above to https://github.com/settings/ssh/new now.

eval "$(ssh-agent -s)"
ssh-add ~/.ssh/runpod
git config --global user.name "Your Name"
git config --global user.email your.email.address@example.com
cd /workspace
git clone git@github.com:ljkrajewski/runpod_ai.git
```
----
Run-Pod Sillytavern/Tavern.AI ([RUN TextGen AI WebUI LLM On Runpod & Colab! Cloud Computing POWER! - YouTube](https://www.youtube.com/watch?v=TP2yID7Ubr4))
```
git pull
pip install -r requirements.txt
 
mkdir repositories
cd repositories
git clone https://github.com/oobabooga/GPTQ-for-LLaMa.git -b cuda
cd GPTQ-for-LLaMa && python setup_cuda.py install
 
 
cd /text-generation-webui
 
pip install scipy
pip install git+https://github.com/mnt4/flask-cloudflared
 
python server.py --port 8080 --chat --auto-devices --model llama --public-api --api
 
May have to run it twice to get the API link from cloudflare. once everything is installed, just run the python script. cntrl c then re run the command.
```
----
Falcon 40B runpod ([FALCON 40B! The ULTIMATE AI Model For CODING & TRANSLATION! - YouTube](https://www.youtube.com/watch?v=WhrdJwEfWZE))
```


cd /text-generation-webui
git clone https://github.com/Honkware/text-generation-webui.git
pip install -r requirements.txt
 
git clone https://github.com/PanQiWei/AutoGPTQ
cd AutoGPTQ
pip install . # This step requires CUDA toolkit installed
 
 
cd /text-generation-webui
 
 
python server.py --share --chat --auto-devices --model llama --autogptq --trust-remote-code
 
# -- No longer needed. Fixed in the current version of text-generation-webui --
#Edit text-generation-webui/modules/AutoGPTQ_loader.py add a new line after line 37:
#'trust_remote_code': shared.args.trust_remote_code,
```
