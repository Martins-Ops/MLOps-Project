
# Operationalize a machine learning microservice API

[![CircleCI](https://dl.circleci.com/status-badge/img/gh/Martins-Ops/MLOps-Project/tree/main.svg?style=svg)](https://dl.circleci.com/status-badge/redirect/gh/Martins-Ops/MLOps-Project/tree/main)

This Project puts in operation a python flask application which was built with sklearn model API, its main function is to operationalize the microservice to serve out predictions about housing prices through API calls.

The project makes use of [Docker](https://www.docker.com) in containerizing the application and service orchestration using [Kubernetes](https://kubernetes.io) in deploying the containerized application.

The Status Badge showing **PASSED** above is pulled from CicleCI integration.
[CicleCI](https://circleci.com) defines an automated testing environment which indicates that the code has passed all lint tests. The circleci uses a yaml file which can be found in the .circleci directory of the repository

## Running the Python Script

- Create a Python Virtual Environment.
```bash
python3 -m -venv [nameofenv]
```
- Source the virtual environment to activate it.
```bash
source [nameofenv]/bin/activate
```

Now we have  created a Virtual environment which has python and its packages installed.
Next install the packages required to run the application in **requirements.txt** of the repository.
> `pip install --upgrade pip &&\ pip install -r requirements.txt`

### Running Web app (app.py)

The following command runs the web app from the relevant files present in the repository.
- Run the Dockerfile present in the repository
```bash
./run_docker.sh
```
- Test the application by making predictions
```bash
./make_prediction.sh
```

#### Files in the repository

- **.circleci**
This directory contains a config.yml file which creates a virtual environment and passes lint test on the project code
- **model_data**
This directory contains files used in the flask app to get required data for prediction
- **output_txt_files**
This directory contains the log files after making predictions with `./make_prediction.sh`
- **app.py**
This is a python flask app containing the code for the microservice
- **Dockerfile**
The Dockerfile contains all the commands a user could call on the command line to build the docker image.
- **make_prediction.sh**
A bash script files used in making API call to the microservice by sending a request
- **Makefile**
The Makefile includes instructions on environment setup and lint tests, it install dependencies in the requirements.txt and executes the files in the virtual environment using the command `make`
- **requirements.txt**
The requirements.txt file contains the application required to run the web application
- **run_docker.sh**
A bash script that executes commands to build docker image, list the images in the environment and run the docker image.
- **run_kubernetes.sh**
A bash script that executes commands to run the containerized app on kubernetes using `kubectl`, list the running pods and forward the container port to a host port
- **upload_docker.sh** 
A bash script that executes commands to create a docker path using the format `docker ID/image name`, tag the docker image and finally push it to dockerhub.
