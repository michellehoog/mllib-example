# MLLib and MLFlow Example

An example notebook using the [UCI Machine Learning Repository's heart disease dataset](https://archive.ics.uci.edu/ml/machine-learning-databases/heart-disease/). 

To run the notebook you will need 
* pyspark, and
* mlflow,
 
or run the notebook from a docker container. I've used the docker image [jupyter/pyspark-notebook](https://hub.docker.com/r/jupyter/pyspark-notebook).

## Installation on Mac

`brew cask install homebrew/cask-versions/adoptopenjdk8`  
`brew install apache-spark`  
`pip install mlflow[extras]`  

## Docker

Get the docker image using `docker pull jupyter/pyspark-notebook`.  

This image does not contain MLflow. You will need to run the container and install it before running the notebook. To open a terminal for the container:  

`docker exec -it sparkbook bash`  

Then install MLflow: `pip install mlflow[extras]`.  

Finally, you can run your container with the command: 

`docker run -d --name sparkbook -p 8881:8888 -p5000:5000 -v "$PWD":/home/jovyan/work jupyter/pyspark-notebook start.sh jupyter lab --LabApp.token=''`

Jupyter Notebook is exposed on port 8881 and MLflow on port 5000.  

The container's folder `/home/jovyan/work` will be mapped to whichever folder you ran the `docker run` command from (`$PWD`).  

**Note**: To view MLflow UI when it is running on a Docker container, explicitly pass the host when you start your UI: `mlflow ui --host 0.0.0.0`.

Stop the container with `docker stop sparkbook`.  
