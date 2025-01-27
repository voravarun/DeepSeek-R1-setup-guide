# DeepSeek-R1-setup-guide to use GPU
This is a guideline to setup deepseek-r1 running on the local gpu with interactive chatbox.</br>
- The OS: Window 10
- GPU: Nvidia RTX 3090 </br>

Note: This guideline does not include the installation of CUDNN and CUDA Toolkit

## Installation
### Install Ollama
1. Install [Ollama](https://ollama.com/) on your PC
2. Choose the deepseek-r1 to install from this website https://ollama.com/library/deepseek-r1 </br><strong>My recommendation is 32b</strong> if you want to have another version you can also choose them from the list up to your choice.
3. run the following script in the cmd
```bashscript
ollama run deepseek-r1:32b
```
4. When you finish the model installation go to your Ollama folder </br>
<i>This is my Path: C:\Users\ADMIN\AppData\Local\Programs\Ollama</i></br>
Then coppy the <strong>cublas64_11.dll cublasLt64_11.dll and cudart64_110.dll</strong> from your CUDA Toolkit folder to this folder</br>
<img src="img\OllamaFolder.png">

5. Set up the System Environment Variable by adding your folder path.
<img src="img\EnvSetup.png">
<img src="img\EnvSetup2.png">
<img src="img\EnvSetup3.png"> </br>

6. run the following script in the cmd
```bashscript
ollama serve
```
You will see the cmd showing like this.
```bashscript
C:\Users\ADMIN>SET CMDSTAN=C:/Users/ADMIN/miniconda3\Library\bin\cmdstan\

(base) C:\Users\ADMIN>ollama serve
2025/01/27 18:03:12 routes.go:1187: INFO server config env="map[CUDA_VISIBLE_DEVICES: GPU_DEVICE_ORDINAL: HIP_VISIBLE_DEVICES: HSA_OVERRIDE_GFX_VERSION: HTTPS_PROXY: HTTP_PROXY: NO_PROXY: OLLAMA_DEBUG:false OLLAMA_FLASH_ATTENTION:false OLLAMA_GPU_OVERHEAD:0 OLLAMA_HOST:http://127.0.0.1:11434 OLLAMA_INTEL_GPU:false OLLAMA_KEEP_ALIVE:5m0s OLLAMA_KV_CACHE_TYPE: OLLAMA_LLM_LIBRARY: OLLAMA_LOAD_TIMEOUT:5m0s OLLAMA_MAX_LOADED_MODELS:0 OLLAMA_MAX_QUEUE:512 OLLAMA_MODELS:C:\\Users\\ADMIN\\.ollama\\models OLLAMA_MULTIUSER_CACHE:false OLLAMA_NOHISTORY:false OLLAMA_NOPRUNE:false OLLAMA_NUM_PARALLEL:0 OLLAMA_ORIGINS:[http://localhost https://localhost http://localhost:* https://localhost:* http://127.0.0.1 https://127.0.0.1 http://127.0.0.1:* https://127.0.0.1:* http://0.0.0.0 https://0.0.0.0 http://0.0.0.0:* https://0.0.0.0:* app://* file://* tauri://* vscode-webview://*] OLLAMA_SCHED_SPREAD:false ROCR_VISIBLE_DEVICES:]"
time=2025-01-27T18:03:12.352+07:00 level=INFO source=images.go:432 msg="total blobs: 7"
time=2025-01-27T18:03:12.352+07:00 level=INFO source=images.go:439 msg="total unused blobs removed: 0"
time=2025-01-27T18:03:12.353+07:00 level=INFO source=routes.go:1238 msg="Listening on 127.0.0.1:11434 (version 0.5.7)"
time=2025-01-27T18:03:12.354+07:00 level=INFO source=routes.go:1267 msg="Dynamic LLM libraries" runners="[cpu_avx2 cuda_v11_avx cuda_v12_avx rocm_avx cpu cpu_avx]"
time=2025-01-27T18:03:12.354+07:00 level=INFO source=gpu.go:226 msg="looking for compatible GPUs"
time=2025-01-27T18:03:12.355+07:00 level=INFO source=gpu_windows.go:167 msg=packages count=1
time=2025-01-27T18:03:12.355+07:00 level=INFO source=gpu_windows.go:183 msg="efficiency cores detected" maxEfficiencyClass=1
time=2025-01-27T18:03:12.355+07:00 level=INFO source=gpu_windows.go:214 msg="" package=0 cores=16 efficiency=8 threads=24
time=2025-01-27T18:03:12.533+07:00 level=INFO source=gpu.go:334 msg="detected OS VRAM overhead" id=GPU-f2012a31-4047-98c1-f0d3-038cd8357e42 library=cuda compute=8.6 driver=12.6 name="NVIDIA GeForce RTX 3090" overhead="189.4 MiB"
time=2025-01-27T18:03:12.535+07:00 level=INFO source=types.go:131 msg="inference compute" id=GPU-f2012a31-4047-98c1-f0d3-038cd8357e42 library=cuda variant=v12 compute=8.6 driver=12.6 name="NVIDIA GeForce RTX 3090" total="24.0 GiB" available="22.8 GiB"
```
### Install ChatBox
7. Install [ChatBox](https://chatboxai.app/en)
8. Open Chatbox and go to the Settings. Choose the Model section and select Ollama.</br> <i>Note: you can check the API Host from the previous bash script in the cmd showing <strong>OLLAMA_ORIGINS</strong></i>
<img src="img\chatboxSet.png">

9. Ask something on your Chatbox to see if it answer back. If it is then go to the next step.
10. Run this script in your cmd. If you see something like this congratulation! 
```bashscript
C:\Users\ADMIN>ollama ps
NAME               ID              SIZE     PROCESSOR    UNTIL
deepseek-r1:32b    38056bbcbb2d    23 GB    100% GPU     4 minutes from now
```

