# ConfliBERT-Docker Containerization

Welcome to the how to guide to install a Docker version of ConfliBERT. After completing all the steps below, you will now have a localized version of ConfliBERT without the hassle of building it from scratch. 

## Prerequisites
- **Docker Desktop**: Required for building and running containers. Download from [Docker's official site](https://www.docker.com/products/docker-desktop/).
- **(Optional) Sufficient resources**: While we have a laptop version in production, it is more ideal to run a higher CPU or GPU for larger and faster results.

## Pull The Docker Image
- To install the image, you must utilize the command terminal of your respective OS. The command itself is the same across platforms as this action orginates from Docker Desktop.

```bash
docker pull zawad1879/conflibert:latest
```

## Create a Docker Container

Creating the Docker Container can be achieved in two ways: via your local PC Terminal or Docker Application. While both methods are viable, we recommend the Terminal method as it allows more options to building your container. To elaborate, the Terminal method allows you to construct an image with one of our preset python scripts. These scripts were made to allow either lower spec or non-CUDA capable PCs to run ConfliBERT. That said, even some of the current scripts still require great processing power, so we will break down which script is ideal to use for each level of a computer you have.

**For the GPU/CUDA Variant:**
```bash
docker run --gpus all --name <Add Name> zawad1879/conflibert:latest python3 finetune_data.py --dataset <Add Desired Dataset> --report_per_epoch
```

**For the High CPU Variant:**
```bash
docker run --name <Add Name> zawad1879/conflibert:latest python3 finetune_data_cpu.py --dataset <Add Desired Dataset> --report_per_epoch
```

**For the Low/Laptop CPU Variant:**
```bash
docker run --name <Add Name> zawad1879/conflibert:latest python3 finetune_data_cpu.py --dataset <Add Desired Dataset> --report_per_epoch
```
---
