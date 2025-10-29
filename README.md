# ConfliBERT-Docker Containerization

Welcome to the how to guide to install a Docker version of ConfliBERT. After completing all the steps below, you will now have a localized version of ConfliBERT without the hassle of building it from scratch. 

## Prerequisites
- **Docker Desktop**: Required for building and running containers. Download from [Docker's official site](https://www.docker.com/products/docker-desktop/).
- **(Optional) Sufficient resources**: While we have a laptop version in production, it is more ideal to run a higher CPU or GPU for larger and faster results.

## Pull The Docker Image
- To install the image, you must utilize the command terminal of your respective OS. The command itself is the same across platforms. Currently, we have two available images.
  
**For CPU-only (Mac/PC without NVIDIA GPU):**
```bash
docker pull ashtone/conflibertcpu:latest
```

**For GPU (PC with NVIDIA GPU):**
```bash
docker pull ashtone/conflibertgpu:latest
```

## Create a Docker Container

Note: In order to see the results, **you must run Docker Desktop as adminstrator**.

**For the GPU/CUDA Variant & Output via Windows Command Line:**
```bash
docker run --gpus all --name confliBertGPU -v "%cd%/../outputs:/app/outputs" ashtone/conflibertgpu:latest python3 finetune_data.py --dataset BBC_News_Demo
```

**For the CPU Varian & Output via Windows Command Line:**
```bash
docker run --name confliBertCPU -v "%cd%/../outputs:/app/outputs" ashtone/conflibertcpu:latest python3 finetune_data_cpu.py --dataset BBC_News_Demo
```

**For the Low/Laptop CPU Variant & Output via Windows Command Line:**
```bash
docker run --name confliBertLaptop -v "%cd%/../outputs:/app/outputs" ashtone/conflibertcpu:latest python3 finetune_data_cpu_low.py --dataset BBC_News_Demo
```

**For the GPU/CUDA Variant & Output via MacOS/Linux/Windows Powershell:**
```bash
docker run --gpus all --name confliBertGPU -v "$(pwd)/../outputs:/app/outputs" ashtone/conflibertgpu:latest python3 finetune_data.py --dataset BBC_News_Demo
```

**For the CPU Varian & Output via MacOS/Linux/Windows Powershell:**
```bash
docker run --name confliBertCPU -v "$(pwd)/../outputs:/app/outputs" ashtone/conflibertcpu:latest python3 finetune_data_cpu.py --dataset BBC_News_Demo
```

**For the Low/Laptop CPU Variant & Output via MacOS/Linux/Windows Powershell:**
```bash
docker run --name confliBertLaptop -v "$(pwd)/../outputs:/app/outputs" ashtone/conflibertcpu:latest python3 finetune_data_cpu_low.py --dataset BBC_News_Demo
```

After running the container, you should find the results in one of two places:
  - For Windows, it can be found in C:\Users\outputs.
---

If you wish to see the progress of the finetuning per epoch, you can add "--report_per_epoch" to the end of your command.
```bash
docker run --gpus all --name confliBertGPU -v "%cd%/../outputs:/app/outputs" ashtone/conflibertgpu:latest python3 finetune_data.py --dataset BBC_News --report_per_epoch
```

## Datasets

If you do not have a dataset of your own set up, we have a number of preset datasets. These include:
- 20news
- BBC_News
- BBC_News_Demo
- IndiaPoliceEvents_docs
- IndiaPoliceEvents_sents
- insightCrime
- re3d
- satp_relevant

The details of each dataset can be found here (under "Evaluation Datasets"): https://github.com/eventdata/ConfliBERT/blob/main/README.md

If you wish to alter the config file of a dataset, I recommend to reference the readme file within the "configs" folder of the Main ConfliBERT GitHub Repo: https://github.com/eventdata/ConfliBERT/blob/main/configs/readme.md
