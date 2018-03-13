# Why Containers
## Demo0
1. Go to https://gitlab.presidio.com/rgomez/docker-presentation-demo0
2. 

## Binds
1. Create a directory.
    - `mkdir my_bindings`
2. Create a file inside the directory.
    - `echo "bind test" >> my_bindings/test.txt`
3. Run a container.
    - `docker run -it --rm -v my_bindings/:/new_vol --name test_bind_1 alpine sh`
4. Inside the container verify the file.
    - `cat new_vol/test.txt`
5. Edit the file.
    - `echo "Another line" >> new_vol/test.txt`
6. Exit the container.
    - `exit`
7. check the file again.
    - `cat my_bindings/test.txt`
