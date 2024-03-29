# Text-to-Image Generation

## Colab Notebooks

- [__How To Use Stable Diffusion XL (SDXL 0.9) On Google Colab For Free (YouTube)__](https://www.youtube.com/watch?v=s2MQqmv6yAg)
  - [[Tutorial] How To Use Stable Diffusion SDXL Locally And Also In Google Colab (GitHub)](https://github.com/FurkanGozukara/Stable-Diffusion/blob/main/Tutorials/How-To-Use-Stable-Diffusion-SDXL-Locally-And-Also-In-Google-Colab.md)
- [https://github.com/TheLastBen/fast\-stable\-diffusion](https://github.com/TheLastBen/fast-stable-diffusion/blob/main/fast_stable_diffusion_AUTOMATIC1111.ipynb) 
  - Google Colab Stable Diffusion notebook (coming)
  - [Google Colab Dreambooth notebook](https://colab.research.google.com/github/TheLastBen/fast-stable-diffusion/blob/main/fast-DreamBooth.ipynb)
 [Alternative GC Dreambooth notebook](https://colab.research.google.com/github/ShivamShrirao/diffusers/blob/main/examples/dreambooth/DreamBooth_Stable_Diffusion.ipynb)
- [How to Use Stable Diffusion to Generate Images (CPU)](https://colab.research.google.com/drive/1NA8XytvxOT841JtaTao896Gm_SFT66N4?usp=sharing&ref=assemblyai.com#scrollTo=6yCG-zQL9ByF)  
Run Stable Diffusion without a GPU, but takes 8 minutes to generate a 512x512 image while being a memory hog.
- [How to Use Stable Diffusion to Generate Images](https://colab.research.google.com/drive/1uWCe41_BSRip4y4nlcB8ESQgKtr5BfrN?usp=sharing)  
Installing Stable Diffusion on Google Colab (so you can have a GPU).

## Models
- [Segment Anything Model (SAM)](https://github.com/facebookresearch/segment-anything)  
Produces high quality object masks from input prompts such as points or boxes, and it can be used to generate masks for all objects in an image.
- [Hugging Face](https://huggingface.co/)
  -  [runwayml/stable-diffusion-v1-5](https://huggingface.co/runwayml/stable-diffusion-v1-5/tree/main)  
_v1-5-pruned.safetensors_ is recommended for training models.
- [Civitai](https://civitai.com/)  
Repository of Stable Diffusion models including:
  - [Set of photorealistic models to browse](https://civitai.com/tag/photorealistic)
  - Best models (IMO):
    - [Reliberate](https://civitai.com/models/79754/reliberate) _[[Download link]](https://civitai.com/api/download/models/84576)_  
    Good with [LowRA](https://civitai.com/models/48139/lowra) _[[Download link]](https://civitai.com/api/download/models/63006)_ and [Detail Tweaker](https://civitai.com/models/58390/detail-tweaker-lora-lora) _[[Download link]](https://civitai.com/api/download/models/62833)_ LoRAs.
    - [Level4](https://civitai.com/models/17449/level4) _[[Download link]](https://civitai.com/api/download/models/25295)_
    - [ChilloutMix](https://civitai.com/models/6424/chilloutmix) _[[Download link]](https://civitai.com/api/download/models/11745)_ Warning: NSFW content.
    - [Protogen x3.4 (Photorealism)](https://civitai.com/models/3666/protogen-x34-photorealism-official-release) _[[Download link]](https://civitai.com/api/download/models/4048)_
    - [Universal photorealistic model with style palette](https://civitai.com/models/16916/universal-photorealistic-model-with-style-palette) _[[Download link]](https://civitai.com/api/download/models/19969)_
    - [Edge Of Realism](https://civitai.com/models/21813/edge-of-realism) _[[Download link]](https://civitai.com/api/download/models/51913)_
    - [Uber Realistic Porn Merge (URPM)](https://civitai.com/models/2661/uber-realistic-porn-merge-urpm) _[[Download link]](https://civitai.com/api/download/models/15640)_
    - [Flat-2D Animerge](https://civitai.com/models/35960/flat-2d-animerge) _[(Download link)](https://civitai.com/api/download/models/91560)_
- VAE: [gemasai/vae-ft-mse-840000-ema-pruned](https://huggingface.co/gemasai/vae-ft-mse-840000-ema-pruned/tree/main)

## Training/Tutorials/Etc.
- __[The guide to fine-tuning Stable Diffusion with your own images](https://tryolabs.com/blog/2022/10/25/the-guide-to-fine-tuning-stable-diffusion-with-your-own-images)__  
** Includes therory, recomendations from their Discord community, and a good workflow for producing best txt2image, image2image, or inpainting results. Best read so far. **
- [Prompt Muse channel - YouTube](https://www.youtube.com/@promptmuse)  
Focuses on using graphic AI.
- [Aitrepreneur channel - YouTube](https://www.youtube.com/@Aitrepreneur)  
Covers LLM and graphic AI. Generally includes instructions for local installation (but only for Windows :P).
- [Why everyone else's Stable Diffusion Art is better than yours (Checkpoint, LoRA and Civitai) - YouTube](https://www.youtube.com/watch?v=GBYD-CyTt7w)
- ["Borrow" Any Pose For Your AI Art! (Easy Tutorial) - YouTube](https://www.youtube.com/watch?v=p57iJeqGEoo)
- [Perfect hands in Stable Diffusion AI - YouTube](https://www.youtube.com/watch?v=IPmxnMTFVtY)  
Hands are a problem even with the best of prompts. This walks you through using the PoseX and Depth Library extentions to fix them.
- [Stable Diffusion - Better Fine Details with a new VAE! (Variational Autoencoder) - YouTube](https://www.youtube.com/watch?v=QFFQi5Jd4I4)
- [cloneofsimo/lora-training](https://replicate.com/cloneofsimo/lora-training)  
LoRA model trainer with presets for faces, objects, and styles. Read the introduction/how-to [here](https://replicate.com/blog/lora-faster-fine-tuning-of-stable-diffusion).
- [__Textual Inversion Tutorial - Embeddings and Hypernetwork basics and walkthrough (YouTube)__](https://www.youtube.com/watch?v=Ep4T8fyy2LE)

## AI Enhancers/Upgraders
- [8 Best Free Online AI Photo Enhancer Tools in 2023](https://www.perfectcorp.com/consumer/blog/online-photo-editing/photo-enhancer-online-tools)
- [Top 10 Free Online AI Image Upscalers in 2023](https://www.media.io/image-upscaler-tips/online-ai-image-upscaler.html)
- [ComfyUI Infinite Upscale - Add details as you upscale your images using the iterative upscale node (YouTube)](https://www.youtube.com/watch?v=t3lT_04A9j0)

## Negative prompts
- basic negative prompt
```
out of frame, lowres, text, error, cropped, worst quality, low quality, jpeg artifacts, ugly, duplicate, morbid, mutilated, out of frame, extra fingers, mutated hands, poorly drawn hands, poorly drawn face, mutation, deformed, blurry, dehydrated, bad anatomy, bad proportions, extra limbs, cloned face, disfigured, gross proportions, malformed limbs, missing arms, missing legs, extra arms, extra legs, fused fingers, too many fingers, long neck, username, watermark, signature,
```
- (much) bigger stable diffusion negative prompt
```
(((deformed))), blurry, bad anatomy, disfigured, poorly drawn face, mutation, mutated, (extra_limb), (ugly), (poorly drawn hands), fused fingers, messy drawing, broken legs censor, censored, censor_bar, multiple breasts, (mutated hands and fingers:1.5), (long body :1.3), (mutation, poorly drawn :1.2), black-white, bad anatomy, liquid body, liquidtongue, disfigured, malformed, mutated, anatomical nonsense, text font ui, error, malformed hands, long neck, blurred, lowers, low res, bad anatomy, bad proportions, bad shadow, uncoordinated body, unnatural body, fused breasts, bad breasts, huge breasts, poorly drawn breasts, extra breasts, liquid breasts, heavy breasts, missingbreasts, huge haunch, huge thighs, huge calf, bad hands, fused hand, missing hand, disappearing arms, disappearing thigh, disappearing calf, disappearing legs, fusedears, bad ears, poorly drawn ears, extra ears, liquid ears, heavy ears, missing ears, old photo, low res, black and white, black and white filter, colorless, (((deformed))), blurry, bad anatomy, disfigured, poorly drawn face, mutation, mutated, (extra_limb), (ugly), (poorly drawn hands), fused fingers, messy drawing, broken legs censor, censored, censor_bar, multiple breasts, (mutated hands and fingers:1.5), (long body :1.3), (mutation, poorly drawn :1.2), black-white, bad anatomy, liquid body, liquid tongue, disfigured, malformed, mutated, anatomical nonsense, text font ui, error, malformed hands, long neck, blurred, lowers, low res, bad anatomy, bad proportions, bad shadow, uncoordinated body, unnatural body, fused breasts, bad breasts, huge breasts, poorly drawn breasts, extra breasts, liquid breasts, heavy breasts, missing breasts, huge haunch, huge thighs, huge calf, bad hands, fused hand, missing hand, disappearing arms, disappearing thigh, disappearing calf, disappearing legs, fused ears, bad ears, poorly drawn ears, extra ears, liquid ears, heavy ears, missing ears, old photo, low res, black and white, black and white filter, colorless, (((deformed))), blurry, bad anatomy, disfigured, poorly drawn face, mutation, mutated, (extra_limb), (ugly), (poorly drawn hands), fused fingers, messy drawing, broken legs censor, censored, censor_bar, multiple breasts, (mutated hands and fingers:1.5), (long body :1.3), (mutation, poorly drawn :1.2), black-white, bad anatomy, liquid body, liquid tongue, disfigured, malformed, mutated, anatomical nonsense, text font ui, error, malformed hands, long neck, blurred, lowers, low res, bad anatomy, bad proportions, bad shadow, uncoordinated body, unnatural body, fused breasts, bad breasts, huge breasts, poorly drawn breasts, extra breasts, liquid breasts, heavy breasts, missing breasts, huge haunch, huge thighs, huge calf, bad hands, fused hand, missing hand, disappearing arms, disappearing thigh, disappearing calf, disappearing legs, fused ears, bad ears, poorly drawn ears, extra ears, liquid ears, heavy ears, missing ears, (((deformed))), blurry, bad anatomy, disfigured, poorly drawn face, mutation, mutated, (extra_limb), (ugly), (poorly drawn hands), fused fingers, messy drawing, broken legs censor, censored, censor_bar, multiple breasts, (mutated hands and fingers:1.5), (long body :1.3), (mutation, poorly drawn :1.2), black-white, bad anatomy, liquid body, liquidtongue, disfigured, malformed, mutated, anatomical nonsense, text font ui, error, malformed hands, long neck, blurred, lowers, low res, bad anatomy, bad proportions, bad shadow, uncoordinated body, unnatural body, fused breasts, bad breasts, huge breasts, poorly drawn breasts, extra breasts, liquid breasts, heavy breasts, missingbreasts, huge haunch, huge thighs, huge calf, bad hands, fused hand, missing hand, disappearing arms, disappearing thigh, disappearing calf, disappearing legs, fusedears, bad ears, poorly drawn ears, extra ears, liquid ears, heavy ears, missing ears,
```
