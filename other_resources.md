# Addendum
## Google Colab Tricks
- [Killing a cell to restart runtime](https://stackoverflow.com/questions/53154369/google-colab-how-to-restart-runtime-using-python-code-or-command-line-interf)
```python3
print('Stopping RUNTIME! Please run this cell again.')
from os import kill,getpid
kill(getpid(), 9)
```
- [Stopping on a cell during a 'run all'](https://groups.google.com/g/jupyter/c/ELftSFSiedQ)
```python3
# don't go beyond here with Run All
assert False
```
- Using the GPU
  - **!! [Google Colab - Using Free GPU (tutorialspoint)](https://www.tutorialspoint.com/google_colab/google_colab_using_free_gpu.htm) !!**
  - [Google Colab Free GPU Tutorial (Medium)](https://medium.com/deep-learning-turkey/google-colab-free-gpu-tutorial-e113627b9f5d)
  - [Start Using Google Colab Free GPU (Medium)](https://medium.com/dataman-in-ai/start-using-google-colab-free-gpu-7968acb7ef92#:~:text=Go%20to%20Edit%20%3E%20Notebook%20settings,That's%20it.)

## Alternatives to Google Colab
- [Runpod](https://www.runpod.io/)  
GPU rental with Jupyter Notebook. Not free; starts at $0.20/hour.
  - [How to run Stable Diffusion with no fuss on RunPod](https://blog.runpod.io/stable-diffusion-ui-on-runpod/)
  - [How to Get Really Good Results with Dreambooth](https://blog.runpod.io/how-to-get-really-good-results-with-dreambooth-on-runpod/)

## Other stuff
- [OpenAI/Whisper](https://github.com/openai/whisper)  
Whisper is a general-purpose speech recognition model. It is trained on a large dataset of diverse audio and is also a multitasking model that can perform multilingual speech recognition, speech translation, and language identification.
