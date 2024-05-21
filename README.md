# Spark Docker Container 

Welcome to the Docker Spark-Python Setup repository! This repository is designed to provide you with a ready-to-use Docker environment for running Apache Spark along with Python.

## What`s Inside?

* **Dockerfile** A Dockerfile that sets up an environment with Apache Spark and its dependencies, as well as Python.
* **docker-compose.yml**A docker-compose file that orchestrates the setup of master, worker and history server.
* **entrypoint.sh** A bash file which contain entry point for master, worker and history server.
* **requirements.txt** Python requirements for Spark setup.
* **spark-defaults.conf** Default Spark configurations.

## Prerequisites

Before you begin, ensure you have the following installed on your system:

* Make 
* Docker
* Docker Compose

## Quick Start

1. **Clone the Repository:**
```bash
git https://github.com/CaCuCkA/spark-init.git
cd spark-init
```

2. **Build the Docker Image:**
```bash
make build
```


3. **Run Spark Cluster:**
``` bash
make run-scaled SPARK_WORKERS=number_of_workers
```

## Documentation
The project is designed to allow user interaction primarily through a Make interface, simplifying the experience and abstracting away from low-level coding.

* **Build Docker image.** Builds the Docker containers using `docker-compose`. This command uses the cache from previous builds to speed up the build process.
    ```bash
    make build
    ```

* **Build Docker image with no cache.** Builds the Docker containers without using any cache, ensuring that all the layers are freshly built.
    ```bash
    make build-nc
    ```

* **Build Docker image with no cache and progress.** Builds the Docker containers without cache and displays detailed progress output. This is useful for debugging during the build process.
    ```bash
    make build-progress
    ```

* **Stop Docker Image.** Stops and removes the containers, along with their associated volumes. This helps ensure a clean state before starting a new session.
    ```bash
    make down
    ```
* **Simple project run.** First, ensures a clean environment by taking down any existing containers, then starts the containers as defined in the docker-compose file. This command is useful for running the application in an interactive mode.
    ```bash
    make run
    ```

* **Project run with multiple workers.** Similar to the `run` command, but scales the number of Spark worker containers according to the `SPARK_WORKERS` environment variable. This is useful for testing scalability.
    ```bash
    make run-scaled
    ```
* **Silent project run.** Runs the containers in detached mode, allowing them to run in the background. This is useful for long-running services.
    ```bash
    make run-d
    ```

* **Submit task to Spark.** Executes a Spark job by submitting it to the Spark master container. The `app` variable should be set to the path of the Spark application you want to run.
    ```bash 
    make submit app=<app_name>
    ```