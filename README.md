# DOCKER COMMANDS
- `docker images`
    - lists all available images

- `docker run <image> [command]`
    - where
        - `<image> = <repository:tag>`
            - 'latest' will be used by default for tag name
        - `[command]` is an optional command tu run for deployed container
    - DESCRIPTION: spins up a container from image and runs it
    - OPTIONS
        - `--rm` - remove container when 'command' will stop execution
        - `-i` - run container in the interactive mode
        - `-t` - creates pseudo TTY that attaches stdin and stdout. Always used in conjunction with -i
            - use 'exit' command to stop container
        - `-d` - run container in the 'detouched' mode
            - containers will start in the backgeround and will stop when the process that has created container will stop
        - `-p <host_port>:<container_port>` - maps port of the host to container's port
        - `--name` - sets the name for container (otherwise it will be generated by docker). Is a good option in debugging scenarios
    - EXAMPLES
        - `docker run -it <image>`
        - `docker run <image> -p 3000:80`
            - maps container's 80 port to host's 3000

    - QUESTIONS
        - is container still running if deployed in non-interactive mode and command has finished execution?
            - no
        - how to preserve files created within specific interactive container session?
            - `commit` container as a new image (this will save writable I/O layer). See `docker commit`

- `docker stop [OPTIONS] <container>`
    - stops running container
    - OPTIONS
        `-t [sec]` - forcely stop container after specified amount of seconds

- `docker ps`
    - DESCRIPTION: lists all running containers.
    - OPTIONS
        `-a` - list all containers (running and  stopped ones)

- `docker commit <container> <repository:tag>`
    - saves container to the image

- `docker inspect <container_id>`
    - DESCRIPTION: will show low-level information about container or image (network settings is a commonly used section)

- `docker logs <container_id>`
    - here is a deep dive into docker logging: https://www.level-up.one/deep-dive-into-docker-logging/
