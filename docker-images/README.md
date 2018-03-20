# Container image
## Create an simple image
1. Create a dockerfile:
    - vi dockerfile
2. Inside the file copy:

```
FROM ubuntu
RUN apt-get update
RUN apt-get install figlet
```
3. Save the file.
4. Create the image:
    - `docker build -t figlet .`
5. Verify the image:
    - `docker images`
6. Run the container:
    - `docker run -ti figlet figlet HELLO`

## Create an image with a process to execute
1. Create a dockerfile-cmd:
    - vi dockerfile-cmd
2. Inside the file copy:

```
FROM ubuntu
RUN apt-get update
RUN apt-get install figlet
CMD figlet HELLO
```
3. Save the file.
4. Create the image:
    - `docker build -f dockerfile-cmd -t figlet-cmd .`
5. Verify the image:
    - `docker images`
6. Run the container:
    - `docker run -ti figlet-cmd`

## NGINX image to say HELLO
1. Create a dockerfile-ngix:
    - `vi dockerfile-nginx`
2. Inside the file copy:

```
FROM nginx:1.13-alpine
COPY nginx-conf/index.html /usr/share/nginx/html/
```
3. Save the file.
4. Create a directory.
    - `mkdir nginx-conf`
4. Create an index:
    - echo "HELLO PRESIDIO" >> nginx-conf/index.html
5. Create the image:
    - `docker build -f dockerfile-nginx -t mynginx .`
5. Verify the image:
    - `docker images`
6. Run the container:
    - `docker run -d -P --name web1 mynginx`
7. Find the port:
    - `docker port web1`
8. Use your browser to go to:
    - `http://localhost:<PORT>`

### Don’t lose your container, share it.
1. Login to dockerhub
    - `docker login`
2. Use the correct tag in your container:
    - `docker tag mynginx dockerhub_username/test_nginx:v1`
3. Push your container:
    - `docker push dockerhub_username/test_nginx:v1`
4. Delete your image from your hard-drive.
    - `docker image rm dockerhub_username/test_nginx:v1`
5. Verify the image is not longer present:
    - `docker images`
6. Download the image again:
    - `docker pull dockerhub_username/test_nginx:v1`
