# Setpoint Energy Savings Calculator

## install
```
sudo apt install libcurl4-openssl-dev libssl-dev
pip install -r requirements.txt
```

# run
# local
gunicorn main:app --reload

# docker
docker build . -t energy-calc

docker run --rm --name energy-calc -e PORT=3000 -p 3000:3000 energy-calc

# access docker shell
docker exec -it energy-calc bash

# check exists
docker image ls

# gcloud

gcloud builds submit --tag gcr.io/pfolio-deploy-1/energy-calc

gcloud run deploy --image gcr.io/pfolio-deploy-1/energy-calc --platform managed --port=3000

```




## cloud build api
```
CREDENTIALS:
-> Application Data
Usin Defaults

```

## config
```
# test locally
python main.py

# docker test

```

An online tool for fast energy saving estimations of expanded temperature ranges.

## Project Objective

Develop an interactive online calculator to provide estimations of potential energy savings based on expanded temperature deadbands. More information about the tool can be found [here](https://cbe.berkeley.edu/research/setpoint-energy-savings-calculator/)

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

### Prerequisites

Python 3 installed on your machine.

If you do not have Python installed on your machine you can follow [this guide](https://wiki.python.org/moin/BeginnersGuide/Download)

### Installation

This guide is for Mac OSX, Linux or Windows.

1. **Get the source code from the GitHub repository**
```
$ git clone https://github.com/CenterForTheBuiltEnvironment/energy-calc.git
$ cd comfort_tool
```
2. **Create a virtual environment using the following command:**

On Linux and MAC ` $ python3 -m venv venv `

On Windows ` py -3 -m venv venv `

3. **Activate the virtualenv:**

On Linux and MAC ` $ . venv/bin/activate `

On Windows ` venv\Scripts\activate `

Your shell prompt will change to show the name of the activated environment.

4. **Install Python dependencies**

The dependencies of the comfort tool are all contained in *requirements.txt*. 
Install them all using:
`$ pip install -r requirements.txt`

6. **Run the tool locally**

Now you should be ready to run the tool locally.
`python3 energycalc.py`

Visit http://localhost:5000 in your browser to check it out. 
Note that whenever you want to run the tool, you have to activate the virtualenv first.

### Versioning
When you release a new version of the tool you should first use `bumpversion` to update the version of the tool. You can use the following command:
```cmd
bumpversion patch  # alternatively you can use minor or major instead of patch
```

## Deploy to Google Cloud Run

You need to have [gcloud](https://cloud.google.com/sdk/docs/install) installed on your computer. A short guide on how to deploy on Google Cloud Run can be found [here](https://youtu.be/FPFDg5znLTM).

First make sure you that gcloud is up-to-date and that you are logged in with the right account.
```text
gcloud components update
gcloud auth list
```

```text
gcloud run deploy energy-calc --source . --platform managed  --project=cloud-run-install --allow-unauthenticated --region=europe-west2
```

```testlocal
# testing locally
PORT=8080 && docker run -p 9090:${PORT} -e PORT=${PORT} cloud-run-source-deploy```