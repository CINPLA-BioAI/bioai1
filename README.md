# bioai1
When you log in you enter your uio user place, to install stuff use
`sudo yum install `
Installing from source should be done in 
`/home/username`
You probably have to make that directory as there is no user space made directly on the computer
`sudo mkdir /home/username`
Then one have to alter permissions
`sudo chown -R username:username /home/username`

Storage should not be done in `/home` as there is limited space. Rather use `/mnt/raid1`, this is a 12 GB disk which has raid backup.

To use python you can install with `pip install --user` or make your own virtual environment, `virtualenv` and `virtualenvwrapper` is installed and you only have to add the following to your `.bashrc`

```
# virtualenvwrapper
export WORKON_HOME=/home/username/.virtualenvs
export PROJECT_HOME=/home/username/Devel
source /etc/profile.d/virtualenvwrapper.sh
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

[Use cuda docker with tensorflow](https://www.tensorflow.org/install/docker)

```
docker run -u $(id -u):$(id -g)
```
