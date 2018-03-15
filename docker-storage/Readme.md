# Container Storage
## Volumes
1. Create a volume.
    - `docker run -ti --rm -v new_vol --name test_volume alpine sh`
2. Check the new volume inside the container.
    - `df -h`
3. Create a file on that volume.
    - `echo 'this is a test' >> /new_vol/test.txt`
4. Create another container with same volume.
    - **USE ANOTHER SESION** **NOT POSSIBLE ON PLAYWITHDOCKER**
    - `docker run -it --rm --volumes-from test_volume --name test_volumne_1 alpine sh`
5. Verify the file created in the other container exist.
    - `cat /new_vol/test.txt`

## Binds
1. Create a directory.
    - `mkdir my_bindings`
2. Create a file inside the directory.
    - `echo "bind test" > my_bindings/test.txt`
3. Run a container.
    - `docker run -it --rm -v $PWD/my_bindings:/new_vol1 --name test_bind_1 alpine sh`
4. Inside the container verify the file.
    - `cat new_vol1/test.txt`
5. Edit the file.
    - `echo "Another line" >> new_vol1/test.txt`
6. Exit the container.
    - `exit`
7. check the file again.
    - `cat my_bindings/test.txt`
