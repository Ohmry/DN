# Docker
- [Docker](#docker)
  - [Window OS에서 Docker 설치하는 방법](#window-os에서-docker-설치하는-방법)

## Window OS에서 Docker 설치하는 방법
### Requirement
  1. Installed already docker on windows. if you don't installed read on https://docs.docker.com/docker-for-windows/
  2. Storage using gitlab's data such as logs, data etc. I used Drive D.

### 1. Pull gitlab image on docker hub.
executing command to download gitlab-ce, gitlab community edition.
``` bash
> docker pull gitlab/gitlab-ce 
```

### 2. Create local directory for gitlab.
Windows has problem that permission about folder access. so make directory by docker process shell account, and run docker image by same account.

Create directory. I worked on Windows Powershell with administrator.
``` bash
> cd D:\
> mkdir docker || mkdir gitlab    # Optional, I like this structure.
> cd docker\gitlab

# create gitlab data folders.
> mkdir config
> mkdir data
> mkdir logs

# check these directory all exists.
> dir

Mode       LastWriteTime            Length      Name
----       -------------            ------      ----
d-----     2020-01-26  오후 12:57                config
d-----     2020-01-26  오후 12:55                data
d-----     2020-01-26  오후 12:55                logs
```

### 3. Run gitlab image.
you set location of prompt to directory made by step2. `(ex. D:\docker\gitlab)` then execute command below.
``` bash
> docker run --detach \
    --hostname 127.0.0.2 \  # we connect url using hosts file.
    --name gitlab
    --restart always \      # when docker start, this container always restart.
    --publish 443:443 \
    --publish 80:80 \
    --publish 22:22 \
    --volume config:/etc/gitlab
    --volume logs:/var/log/gitlab
    --volume data:/var/opt/gitlab
    gitlab/gitlab-ce:latest
```


### 4. Check gitlab container status.
You can check gitlab cotainer status using command below. if you can't see this status, gitlab container running is failed.
``` bash
> docker stats

CONTAINER ID        NAME                CPU %               MEM USAGE / LIMIT     MEM %               NET I/O             BLOCK I/O           PIDS
5add6f7b775c        gitlab              2.57%               1.279GiB / 1.943GiB   65.83%              75.9kB / 3.15MB     1.63GB / 91.2MB     277
```


### 5. Enter gitlab with host IP.
Enter to `127.0.0.2` on browser. you can see gitlab page.


### 6. Set hosts file.
you can enter with domain by modify hosts file.

1. Open notepad or editor with administrator.
2. Open hosts file. `(C:\Windows\SysWow64\drivers\etc\hosts)` if x86 `(C:\Windows\System32\drivers\etc\hosts)`
3. Add text like line 10.
    ``` bash    
    1   # localhost name resolution is handled within DNS itself.
    2   #	127.0.0.1       localhost
    3   #	::1             localhost
    4   # Added by Docker Desktop
    5   211.204.117.33 host.docker.internal
    6   211.204.117.33 gateway.docker.internal
    7   # To allow the same kube context to work on the host and the container:
    8   127.0.0.1 kubernetes.docker.internal
    9   # Added by Gitlab on Docker
    10  127.0.0.2 gitlab.laboratory.com 
    11  # End of section
    ```
4. Save file.

### 7. Check connecting domain.
Enter to `gitlab.laboratory.com` on brower. you can see gitlab page.