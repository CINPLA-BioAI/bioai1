# bioai1
Storage should not be done in `/home` as there is limited space. Rather use `/media/storage`, this is a 12 TB disk which has raid backup.

To use python you can install with `pip install --user` or make your own virtual environment, `virtualenv` and `virtualenvwrapper` is installed and you only have to add the following to your `.bashrc`

```
# virtualenvwrapper
export WORKON_HOME=~/.virtualenvs
export VIRTUALENVWRAPPER_PYTHON=/usr/bin/python3
export VIRTUALENVWRAPPER_VIRTUALENV=/home/username/.local/bin/virtualenv
source /home/username/.local/bin/virtualenvwrapper.sh
```

Install CUDA 18.04 docker image

```
add-apt-repository main
apt install software-properties-common
apt install dkms build-essential
apt install ubuntu-drivers-common
ubuntu-drivers devices
ubuntu-drivers autoinstall
```

```
docker run -it <image/tag> bash
docker commit docker_id new/name
docker attach docker_id
```
[docker in another drive](https://www.guguweb.com/2019/02/07/how-to-move-docker-data-directory-to-another-location-on-ubuntu/)

[install docker](https://docs.docker.com/engine/install/ubuntu/)
[install nvidia-docker](https://github.com/NVIDIA/nvidia-docker)
[Use cuda docker with tensorflow](https://www.tensorflow.org/install/docker)



[Use docker without sudo](https://docs.docker.com/engine/install/linux-postinstall/)

[Tensorflow docker images](https://hub.docker.com/r/tensorflow/tensorflow/)
devel-gpu uses python 3.6
```
docker run -u $(id -u):$(id -g) --gpus all -it tensorflow/tensorflow:latest-gpu-py3 bash
```
[run tensorflow docker jupyter remotely](https://medium.com/@lucasrg/using-jupyter-notebook-running-on-a-remote-docker-container-via-ssh-ea2c3ebb9055)

Use `tensorflow/tensorflow:latest-gpu-py3`

```
docker run --gpus all -it --rm -v "$(realpath ~/projects):/projects" -p 8888:8888 lepmik/tensorflow:latest-gpu-py3
docker run --gpus all -it -v "$(realpath ~/projects):/projects" lepmik/tensorflow:latest-gpu-py3 bash
```
in the docker:
```
cd projects
jupyter lab --ip 0.0.0.0 --port 8888 --allow-root
```
## PyTorch
https://ngc.nvidia.com/catalog/containers/nvidia:pytorch
https://docs.nvidia.com/deeplearning/frameworks/pytorch-release-notes/running.html#running

```
docker pull nvcr.io/nvidia/pytorch:21.05-py3
docker run --gpus all -it --rm nvcr.io/nvidia/pytorch:21.05-py3 bash
```
