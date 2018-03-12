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
