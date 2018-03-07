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
