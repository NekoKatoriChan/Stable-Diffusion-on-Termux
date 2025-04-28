# What's this?
A script that install Stable Diffusion cpp on Android as simple as possible (Use at your own risk)

## Why?

I don't know, eh, if you encounted common issue, please scrool down to see `Troubleshooting`

# Installation 

### 🐧💥Ez Installation (Pre-complied, CPU)

```
bash <(curl -s https://raw.githubusercontent.com/NekoKatoriChan/Stable-Diffusion-on-Termux/main/install)

```

### 💀💧Compatibility Installation (CPU)

```
bash <(curl -s https://raw.githubusercontent.com/NekoKatoriChan/Stable-Diffusion-on-Termux/main/install-comp)

```

### Vulkan?
Not yet, cuz most phone can't compatible when running it with Vulkan!


# 🍊 Quick Guide

If you're too lazy to read this, use `sd-ez` instead.

```
usage: ./bin/sd [arguments]

arguments:
  -h, --help                         show this help message and exit
  -M, --mode [MODEL]                 run mode (txt2img or img2img or convert, default: txt2img)
  -t, --threads N                    number of threads to use during computation (default: -1)
                                     If threads <= 0, then threads will be set to the number of CPU physical cores
  -m, --model [MODEL]                path to full model
  --diffusion-model                  path to the standalone diffusion model
  --clip_l                           path to the clip-l text encoder
  --clip_g                           path to the clip-l text encoder
  --t5xxl                            path to the the t5xxl text encoder
  --vae [VAE]                        path to vae
  --taesd [TAESD_PATH]               path to taesd. Using Tiny AutoEncoder for fast decoding (low quality)
  --control-net [CONTROL_PATH]       path to control net model
  --embd-dir [EMBEDDING_PATH]        path to embeddings
  --stacked-id-embd-dir [DIR]        path to PHOTOMAKER stacked id embeddings
  --input-id-images-dir [DIR]        path to PHOTOMAKER input id images dir
  --normalize-input                  normalize PHOTOMAKER input id images
  --upscale-model [ESRGAN_PATH]      path to esrgan model. Upscale images after generate, just RealESRGAN_x4plus_anime_6B supported by now
  --upscale-repeats                  Run the ESRGAN upscaler this many times (default 1)
  --type [TYPE]                      weight type (f32, f16, q4_0, q4_1, q5_0, q5_1, q8_0, q2_k, q3_k, q4_k)
                                     If not specified, the default is the type of the weight file
  --lora-model-dir [DIR]             lora model directory
  -i, --init-img [IMAGE]             path to the input image, required by img2img
  --control-image [IMAGE]            path to image condition, control net
  -o, --output OUTPUT                path to write result image to (default: ./output.png)
  -p, --prompt [PROMPT]              the prompt to render
  -n, --negative-prompt PROMPT       the negative prompt (default: "")
  --cfg-scale SCALE                  unconditional guidance scale: (default: 7.0)
  --skip-layers LAYERS               Layers to skip for SLG steps: (default: [7,8,9])
  --skip-layer-start START           SLG enabling point: (default: 0.01)
  --skip-layer-end END               SLG disabling point: (default: 0.2)
									 SLG will be enabled at step int([STEPS]*[START]) and disabled at int([STEPS]*[END])
  --strength STRENGTH                strength for noising/unnoising (default: 0.75)
  --style-ratio STYLE-RATIO          strength for keeping input identity (default: 20%)
  --control-strength STRENGTH        strength to apply Control Net (default: 0.9)
                                     1.0 corresponds to full destruction of information in init image
  -H, --height H                     image height, in pixel space (default: 512)
  -W, --width W                      image width, in pixel space (default: 512)
  --sampling-method {euler, euler_a, heun, dpm2, dpm++2s_a, dpm++2m, dpm++2mv2, ipndm, ipndm_v, lcm}
                                     sampling method (default: "euler_a")
  --steps  STEPS                     number of sample steps (default: 20)
  --rng {std_default, cuda}          RNG (default: cuda)
  -s SEED, --seed SEED               RNG seed (default: 42, use random seed for < 0)
  -b, --batch-count COUNT            number of images to generate
  --schedule {discrete, karras, exponential, ays, gits} Denoiser sigma schedule (default: discrete)
  --clip-skip N                      ignore last layers of CLIP network; 1 ignores none, 2 ignores one layer (default: -1)
                                     <= 0 represents unspecified, will be 1 for SD1.x, 2 for SD2.x
  --vae-tiling                       process vae in tiles to reduce memory usage
  --vae-on-cpu                       keep vae in cpu (for low vram)
  --clip-on-cpu                      keep clip in cpu (for low vram)
  --diffusion-fa                     use flash attention in the diffusion model (for low vram)
                                     Might lower quality, since it implies converting k and v to f16.
                                     This might crash if it is not supported by the backend.
  --control-net-cpu                  keep controlnet in cpu (for low vram)
  --canny                            apply canny preprocessor (edge detection)
  --color                            Colors the logging tags according to level
  -v, --verbose                      print extra info
```

# Troubleshooting

If you encountered `permission denied`, copy and paste command to Termux

```
chmod +x $PATH/sd
chmod +x $PATH/sd-ez
```


## 📌 Credit

This project is inspired by the work of [leejet](https://github.com/leejet/stable-diffusion.cpp), who created the original stable-diffusion.cpp repository.
The installer scripts have been made easier to use and customized for Termux, based on this great work.
