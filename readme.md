# PyTorch Docker Env with Jupyter Lab

## Features

- Inherated from [NVIDIA NGC Catalog PyTorch Container](https://ngc.nvidia.com/catalog/containers/nvidia:pytorch).
- PyTroch is organized by conda
- Jupyter Lab is installed and launched by default with port `8888`.

## Known issues and solutions

- By default a docker conatiner only has 48 MB shared memory. To use multi-processes, (for instance, multiple works in PyTroch dataloader), set `shm_size: '64gb'` in the `docker-compose` serveice.
- A [known bug](shm_size: '64gb') bewteen `docker-compose` and `PyCharm` is that the latest `docker-compose` installed from Docker official channel cannot received signals from PyCharm so that the running container can not be stopped.
  - As suggested in the youtrack issue, install `docker-compose` from pip by sudo will overwrite the official `docker-compose` and the pip one actually works with PyCharm for unknown reason.
  - It can be achieved as follows:

  ```bash
  docker-compose --version
  docker-compose version 1.27.4, build 40524192
  sudo pip3 install docker-compose
  docker-compose -v
  docker-compose version 1.29.2, build unknown
  ```
