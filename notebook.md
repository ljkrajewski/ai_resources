To run latest AUTOMATIC1111 in RunPod:
1. In RunPod, deploy a _RunPod Stable Diffusion v1.5+v2_ template
2. Open a web terminal and run the following commands:
```
cd /workspace/stable-diffusion-webui
git pull
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

To download from Google Drive:
1. At Google Drive, set the file for public availability to anyone with the link.
2. Create the folloing file on your destination:
```
#!/usr/bin/env bash
fileid="### file id from downoad URL ###"  #eg, 1AMQ1OndXcTxXwklOGJvK-A5uCGvHR4I7
filename="### local filename ###"
html=`curl -c ./cookie -s -L "https://drive.google.com/uc?export=download&id=${fileid}"`
curl -Lb ./cookie "https://drive.google.com/uc?export=download&`echo ${html}|grep -Po '(confirm=[a-zA-Z0-9\-_]+)'`&id=${fileid}" -o ${filename}
```
