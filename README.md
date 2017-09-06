# How to create an Ubuntu singularity container with cufflinks installed

__Requirements__: Your computer is running either __Ubuntu 16.04__ or __Ubuntu 17.04__.

## Install Singularity

First install the required packages __debootstrap__ and
__git__ .

```
ubuntu@laptop:~$ sudo apt-get install debootstrap git
```

### Install Singularity on Ubuntu 16.04

```
ubuntu@laptop:~$ cat /etc/issue
Ubuntu 16.04.3 LTS \n \l

ubuntu@laptop:~$ 
```

Follow the [install instructions](http://singularity.lbl.gov/install-linux) under the section
_Option 1: Download latest stable release_

### Install Singularity on Ubuntu 17.04

```
ubuntu@laptop:~$ cat /etc/issue
Ubuntu 17.04 \n \l

ubuntu@laptop:~$ sudo apt-get install singularity-container
```

### Create a Singularity container

Clone this git repository

```
ubuntu@laptop:~$ cd /tmp
ubuntu@laptop:/tmp$ git clone git@github.com:eriksjolund/cufflinks-ubuntu-singularity-container.git
```

Create an empty Singularity container

```
ubuntu@laptop:~$ singularity create /tmp/container.img
```

Use the file [cufflinks_ubuntu_singularity](cufflinks_ubuntu_singularity) to install Ubuntu 17.04 and [cufflinks](http://cole-trapnell-lab.github.io/cufflinks/) in the container

```
ubuntu@laptop:~$ sudo singularity bootstrap /tmp/container.img /tmp/cufflinks-ubuntu-singularity-container/cufflinks_ubuntu_singularity
```

The bootstrap command took about 3 minutes on my computer.


To run cufflinks execute

```
ubuntu@laptop:~$ singularity exec /tmp/container.img cufflinks --help 2>&1 | head -1
cufflinks: unrecognized option '--help'
ubuntu@laptop:~$   
```

I just realized cufflinks has not yet implemented the "--help" flag, but anyway the cufflinks software is at least running.

