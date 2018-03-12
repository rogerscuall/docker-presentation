# Container Networks
## Publish all ports
1. Run the command:
    - `docker run -d -P --name web2 nginx`
2. Find the ports mapping.
    - `docker port web2`
3. Open a browser to `http://0.0.0.0:<PORT>`

## Create container networks:
1. Create a new network:
    - `docker network create my_test`
2. Create a container in the new network:
    - `docker run -d -P --name web3 --net my_test nginx`
3. Create another container:
    - `docker run -ti --rm --name test_node --net my_test alpine ping web3`
4. Did we configure name resolution?
    - `docker run -ti --rm --name test_node --net my_test alpine cat /etc/resolv.conf`
