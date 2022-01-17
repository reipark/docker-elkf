
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
    FileBeat mounts the log file of the host machine inside the FileBeat Docker Container and collects it,
    but even if the log file of the host machine is changed the mounted log file inside the container does not change.
    If the file is directly modified with commands such as echo or chmod this does not happen.
    Only changes made to the file by a running application are not reflected.
    Someone please fix this...
    
    2021. 01. 17 Update.
    This problem is solved.
    My environment is MacOS, it was a matter of setting options in Docker On Mac.
    (Come to think of it, I should have mentioned the environment called MacOS.)
    If you set it like below in Docker On Mac,
    If the host file is changed, you can check that the file in the mounted container is also changed normally.
    Docker on Mac > Preferences > Genetal > Use gRPC FUSE for file sharing (Uncheck to use the legacy osxfs file sharing instead.)
    You must uncheck the above items. (default is checked)
