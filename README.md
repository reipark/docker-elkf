
ELK + FileBeat On Docker
=============

* base and reference source: <https://github.com/dalgun/docker.git>

## directories and files
---
    .env
        set a ELK_VERSION (7.10.0)

    docker-compose.yml
        docker configurations for services

    elasticsearch
    kibana
    logstash
    filebeat
    sample_log

## description
---
    . ELK with Filebeat on Docker using Docker Compose
        
## command
---
    docker-compose up -d --build
        create docker images and run container

    docker-compose down -v
        stop and remove container

    docker-compose down -rmi all
        stop and remove container and images

    docker logs -f {container_name}
        tailing a log to service

## notice
---
   FileBeat mounts the log file of the host machine inside the FileBeat Docker Container and collects it, but even if the log file of the host machine is changed, the mounted log file inside the container does not change.
If the file is directly modified with commands such as echo or chmod, this does not happen. Only changes made to the file by a running application are not reflected.
Someone please fix this...
