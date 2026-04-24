# CloudStream: Cloud-Native Microservices Application

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
![Python 3.9](https://img.shields.io/badge/Python-3.9-green.svg)

CloudStream is a scalable, cloud-native streaming platform designed to demonstrate modern DevOps methodologies. The project implements a RESTful microservice architecture with automated CI/CD pipelines, containerization, and cloud orchestration.

## Installation & Setup

```bash
source bin/setup.sh
```
This will install Python 3.9, make it the default, modify the bash prompt, create a Python virtual environment, and activate it.

After sourcing it, your prompt should look like this:

```bash
(venv) theia:project$
```

## Useful commands

Under normal circumstances, you should not have to run these commands. They are performed automatically at setup but may be useful when things go wrong:

### Activate the Python 3.9 virtual environment

You can activate the Python 3.9 environment with:

```bash
source ~/venv/bin/activate
```

### Installing Python dependencies

These dependencies are installed as part of the setup process, but should you need to install them again, first make sure that the Python 3.9 virtual environment is activated and then use the `make install` command:

```bash
make install
```

### Starting the Postgres Docker container

The labs use Postgres running in a Docker container. If, for some reason, the service is not available, you can start it with:

```bash
make db
```

You can use the `docker ps` command to make sure that Postgres is up and running.

## Project layout

The code for the microservice is contained in the `service` package. All of the tests are in the `tests` folder. The code follows the **Model-View-Controller** pattern with all of the database code and business logic in the model (`models.py`), and all of the RESTful routing on the controller (`routes.py`).

```text
├── service         <- microservice package
│   ├── common/     <- common log and error handlers
│   ├── config.py   <- Flask configuration object
│   ├── models.py   <- code for the persistent model
│   └── routes.py   <- code for the REST API routes
├── setup.cfg       <- tools setup config
└── tests                       <- folder for all of the tests
    ├── factories.py            <- test factories
    ├── test_cli_commands.py    <- CLI tests
    ├── test_models.py          <- model unit tests
    └── test_routes.py          <- route unit tests
```

## Data Model

The Account model contains the following fields:

| Name | Type | Optional |
|------|------|----------|
| id | Integer| False |
| name | String(64) | False |
| email | String(64) | False |
| address | String(256) | False |
| phone_number | String(32) | True |
| date_joined | Date | False |

## Features & DevOps Integration

* **RESTful API:** Full CRUD operations for stream resource management.
* **TDD:** Developed using Test-Driven Development with over 95% code coverage.
* **CI/CD:** Automated testing and linting via GitHub Actions.
* **Containerization:** Fully Dockerized services for consistent environments.
* **Orchestration:** Deployment ready for Kubernetes/OpenShift.

## Local Kubernetes Development

This repo can also be used for local Kubernetes development. It is not advised that you run these commands in the Cloud IDE environment. The purpose of these commands is to simulate the Cloud IDE environment locally on your computer. 

At a minimum, you will need [Docker Desktop](https://www.docker.com/products/docker-desktop) installed on your computer. For the full development environment, you will also need [Visual Studio Code](https://code.visualstudio.com) with the [Remote Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) extension from the Visual Studio Marketplace. All of these can be installed manually by clicking on the links above or you can use a package manager like **Homebrew** on Mac or **Chocolatey** on Windows.

Please only use these commands for working stand-alone on your own computer with the VSCode Remote Container environment provided.

1. Bring up a local K3D Kubernetes cluster

    ```bash
    $ make cluster
    ```

2. Install Tekton

    ```bash
    $ make tekton
    ```

3. Install the ClusterTasks that the Cloud IDE has

    ```bash
    $ make clustertasks
    ```

You can now perform Tekton development locally, just like in the Cloud IDE lab environment.

## Author
**Shivam Kumar**
* Computer Science & Engineering Student
* [LinkedIn] (https://www.linkedin.com/in/em-shivam-17a869257?utm_source=share&utm_campaign=share_via&utm_content=profile&utm_medium=android_app).

---
*Developed as a Cloud-Native capstone Project - 2026*
