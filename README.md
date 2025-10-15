# ConfliBERT-Docker Containerization

Welcome to the how to guide to install a Docker version of ConfliBERT. After completing all the steps below, you will now have a localized version of ConfliBERT without the hassle of building it from scratch. 

## Prerequisites
- **Docker Desktop**: Required for building and running containers. Download from [Docker's official site](https://www.docker.com/products/docker-desktop/).
- **(Optional) Sufficient resources**: While we have a laptop version in production, it is more ideal to run a higher CPU or GPU for larger and faster results.

## Pull The Docker Image
- To install the image, you must utilize the command terminal of your respective OS. The command itself is the same across platforms. Currently, we have two available images.
- 
**For CPU-only (Mac/PC without NVIDIA GPU):**
```bash
docker pull ashtone/conflibertcpu:latest
```

**For GPU (PC with NVIDIA GPU):**
```bash
docker pull ashtone/conflibertgpu:latest
```

## Create a Docker Container

Creating the Docker Container can be achieved via your local PC's Terminal. Currently, an image can be constructed with one of our preset python scripts. These scripts were made to allow either lower spec or non-CUDA capable PCs to run ConfliBERT. That said, even some of the current scripts still require great processing power, so we will break down which script is ideal for each level of a computer you have.

**For the GPU/CUDA Variant:**
```bash
docker run --gpus all --name <Add Name> <Image Version> python3 finetune_data.py --dataset <Add Desired Dataset>
```

**For the CPU Variant:**
```bash
docker run --name <Add Name> <Image Version> python3 finetune_data_cpu.py --dataset <Add Desired Dataset>
```

**For the Low/Laptop CPU Variant:**
```bash
docker run --name <Add Name> <Image Version> python3 finetune_data_cpu_low.py --dataset <Add Desired Dataset>
```
---

If you wish to see the progress of the finetuning per epoch, you can add "--report_per_epoch" to the end of your command.

## Datasets

If you do not have a dataset of your own set up, we have a number of preset datasets. These include:
- 20news.json
- BBC_News.json
- BBC_News_Demo.json
- IndiaPoliceEvents_docs.json
- IndiaPoliceEvents_sents.json
- insightCrime.json
- re3d.json
- satp_relevant.json

The details of each dataset can be found here (under "Evaluation Datasets"): https://github.com/eventdata/ConfliBERT/blob/main/README.md

If you wish to alter the config file of a dataset, I recommend to reference the readme file within the "configs" folder of the Main ConfliBERT GitHub Repo: https://github.com/eventdata/ConfliBERT/blob/main/configs/readme.md
