#cowsay example

#https://realpython.com/python-versions-docker/

#https://runnable.com/docker/python/dockerize-your-python-application

#check installation

docker run hello-world

#Build your own docer image, put following to Dockerfile

FROM ubuntu

RUN apt update && apt install -y cowsay

CMD ["/usr/games/cowsay", "Docker cool"]

#build an image from your Dockerfile

docker build -t cowsay .

#-t: tag your image with name cowsay
#. : Current directory as build context for your image, it should contain Dockerfile

#run Cocker image

docker run --rm cowsay

#--rm: to cleanup the container after use

#list your images

docker images

#list containers 

docker ps -a

#delete contaner or image

docker rm id

#To play with REPL

docker run -it --rm python:3.6

#Setting up py env, put following commands to Dockerfile

FROM python:3.6-slim
RUN python -m pip install \
       parse \
       realpython-reader

#--slim: for being slim, --alpine etc

#build and run docker file

docker build -t rp .

docker run -it --rm rp

#Start containerthat run custom commands

docker run --rm rp realpython

#There are two general ways to run scripts like this in your Docker container:

#Mount a local directory as a volume in the Docker container.
#Copy the script into the Docker container.

#Mounting and running python script with python image

docker run --rm -v /home/skycam/docker_stuffs/docker_for_ml/py_file_run:/app rp python /app/headlines.py

#Copy script to Docker container

#Dockerfile
FROM python:3.7.5-slim
WORKDIR /usr/src/app
RUN python -m pip install \
        parse \
        realpython-reader
COPY headlines.py .
CMD ["python", "headlines.py"]




    
    












