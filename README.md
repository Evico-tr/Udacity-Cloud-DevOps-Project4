[![CircleCI](https://dl.circleci.com/status-badge/img/gh/Evico-tr/Udacity-Cloud-DevOps-Project4/tree/master.svg?style=svg)](https://dl.circleci.com/status-badge/redirect/gh/Evico-tr/Udacity-Cloud-DevOps-Project4/tree/master)

## Project Overview

This project about operationalizing a Python flask app `app.py`—that serves out predictions about housing prices through API calls.

Using `sklearn` model that has been trained to predict housing prices in Boston according to several features, such as average rooms in a home and data about highway access, teacher-to-pupil ratios, and so on. The Data set is gotten from the [data source site](https://www.kaggle.com/c/boston-housing). 

## HOW TO RUN THE APP

### Setup the Environment

* Run `make setup` to setup python virtual environment. Just like below
```bash
python3 -m venv ~/.devops
# You should have Python 3.7 available in your host. 
# Check the Python path using `which python3`
source .devops/bin/activate
```
### Installing Dependencies

* Run `make install` to install the necessary dependencies
* Install hadolint with these commands `wget -O /bin/hadolint https://github.com/hadolint/hadolint/releases/download/v1.16.3/hadolint-Linux-x86_64 && chmod +x /bin/hadolint`. This will help lint Dockerfile.
* Install docker using this [link](https://docs.docker.com/engine/install/ubuntu/).
* Install minikube using this [link](). This will help to run Kubernetes locally.

### Testing the source code and Dockerfile
* Run `make lint` to check the source and Dockerfile

### Running the Flask app `app.py`

#### Running the app locally on local Machine:  
* Run `python3 app.py`
#### Running the app in Docker container:
* Run `./run_docker.sh` then run `./make_predicton.sh` to make predictions.
* Run `./upload_docker.sh` to upload the docker image to [docker hub](https://hub.docker.com/).

#### Running the app in Kubernetes:
3. Run `./run_kubernetes.sh` then run `./make_predicton.sh` to make predictions.

## EXPLANATION OF THE FILES IN THE REPOSITORY
### Folder Arrangement
```
.
├── Dockerfile
├── Makefile
├── README.md
├── app.py
├── hadolint
├── make_prediction.sh
├── model_data
│   ├── boston_housing_prediction.joblib
│   └── housing.csv
├── output_txt_files
│   ├── docker_out.txt
│   └── kubernetes_out.txt
├── .circleci
|   └── config.yml
├── requirements.txt
├─- run_docker.sh
├── run_kubernetes.sh
└── upload_docker.sh
```
* `.circleci/config.yml` contains the pipeline config file for cirleci integration.
* `output_txt_files` contains the prediction outputs for docker run and kubernates run after `make_prediction.sh` script was run.
* `app.py` contains the source code of the flask application
* `Dockerfile` contains the configuration for the docker container env. setup
* `Makefile` defines a set of tasks to be executed
* `requirements.txt` contains the dependencies to install