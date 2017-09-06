# How to create an Ubuntu singularity container with cufflinks installed

## Install Singularity

### Install Singularity on Ubuntu 16.04

```
ubuntu@laptop:~$ cat /etc/issue
Ubuntu 16.04.3 LTS \n \l

ubuntu@laptop:~$ 
```

Follow the [install instructions](Option 1: Download latest stable release) under the section
_Option 1: Download latest stable release_

### Install Singularity on Ubuntu 17.04

```
ubuntu@laptop:~$ cat /etc/issue
Ubuntu 17.04 \n \l

ubuntu@laptop:~$ sudo apt-get install singularity-container
```

### Create Singularity container

Download the git repository

```
ubuntu@laptop:~$ git clone git@github.com:eriksjolund/cufflinks-ubuntu-singularity-container.git
```

Create an empty Singularity container

```
ubuntu@laptop:~$ singularity create /tmp/container.img
```

Use the file [cufflinks_ubuntu_singularity](cufflinks_ubuntu_singularity) to install Ubuntu 17.04 and cufflinks in the container

```
ubuntu@laptop:~$ sudo singularity bootstrap /tmp/cufflinks-ubuntu1704-container.img /tmp/cufflinks-ubuntu-singularity-container/cufflinks_ubuntu_singularity
```

The bootstrap command took about 3 minutes on my computer.


To run cufflinks execute

```
ubuntu@laptop:~$ singularity exec /tmp/container.img cufflinks --help 2>&1 | head -1
cufflinks: unrecognized option '--help'
ubuntu@laptop:~$   
```

I just realized cufflinks has not yet implemented the "--help" flag, but anyway the cufflinks software is at least running.

