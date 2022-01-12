
ELK + FileBeat On Docker
=============

* base and reference source: <https://github.com/dalgun/docker-elk>

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
    The file in the container does not change when the file in the host changes.
    This phenomenon does not occur if you directly modify the file with commands such as echo or chmod. It is not reflected only when the file is changed by the running application.
    Someone please fix this problem...
