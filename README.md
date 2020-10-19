# Docker

<https://hub.docker.com/>

works via *Linux Namespaces*
therefore docker needs some form of Linux to run

## VSCode Docker Extension

ms-azuretools.vscode-docker

---

## Activate Virtualization on Windown 10 *Home*

> When using PRO und up Edition just use Hyper-V.
>
> 1. ### With Home you need to make sure virtualization is active in BIOS
>
> > In my case it's intel virtualization
>
> 2. ### download the [Docker Desktop for Windows with using the WSL 2 backend for Wondows Home](https://hub.docker.com/editions/community/docker-ce-desktop-windows/)
>
> > [You can find more information here](https://docs.docker.com/docker-for-windows/install-windows-home/)
>
> 3. ### Enable the Windows Subsystem for Linux
>
> the next steps can be found here: <https://docs.microsoft.com/en-us/windows/wsl/install-win10>
>
> > ```PowerShell
> >  dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
> > ```
>
> 4. ### Update to WSL 2
>
> #### Requirements
>
> > - For x64 systems: Version 1903 or higher, with Build 18362 or higher.
> > - For ARM64 systems: Version 2004 or higher, with Build 19041 or higher.
> > - Builds lower than 18362 do not support WSL 2. Use the [Windows Update Assistant ](https://www.microsoft.com/software-download/windows10) to update your version of Windows
> >   To check your version and build number, select Windows logo key + R, type winver, select OK. (Or enter the ver command in Windows Command Prompt). Update to the latest Windows version in the Settings menu.
>
> 5. ### Enable Virtual Machine feature
>
> Before installing WSL 2, you must enable the Virtual Machine Platform optional feature.
> Open PowerShell as Administrator and run:
>
> > ```PowerShell
> >  dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
> > ```
>
> Restart your machine to complete the WSL install and update to WSL 2.
>
> 6. ### Download the Linux kernel update package
>
> - Download the latest package:
>
> > [WSL2 Linux kernel update package for x64 machines](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi)
>
> - Run the update package downloaded in the previous step. (Double-click to run - you will be prompted for elevated permissions, select ‘yes’ to approve this installation.)
>
> Once the installation is complete, move on to the next step - setting WSL 2 as your default version when installing new Linux distributions. (Skip this step if you want your new Linux installs to be set to WSL 1).
>
> 7. ### Set WSL 2 as your default version
>    Open PowerShell as Administrator and run this command to set WSL 2 as the default version when installing a new Linux distribution:
>
> > ```PowerShell
> > wsl --set-default-version 2
> > ```
>
> 8. ### Install your Linux distribution of choice
>
> - Open the [Microsoft Store](https://aka.ms/wslstore) and select your favorite Linux distribution.
>
> The following links will open the Microsoft store page for each distribution:
>
> > - [Ubuntu 16.04 LTS](https://www.microsoft.com/store/apps/9pjn388hp8c9)
> > - [Ubuntu 18.04 LTS](https://www.microsoft.com/store/apps/9N9TNGVNDL3Q)
> > - [Ubuntu 20.04 LTS ](https://www.microsoft.com/store/apps/9n6svws3rx71)
> > - [openSUSE Leap 15.1 ](https://www.microsoft.com/store/apps/9NJFZK00FGKV)
> > - [SUSE Linux Enterprise Server 12 SP5](https://www.microsoft.com/store/apps/9MZ3D1TRP8T1)
> > - [SUSE Linux Enterprise Server 15 SP1 ](https://www.microsoft.com/store/apps/9PN498VPMF3Z)
> > - [Kali Linux ](https://www.microsoft.com/store/apps/9PKR34TNCV07)
> > - [Debian GNU/Linux ](https://www.microsoft.com/store/apps/9MSVKQC78PK6)
> > - [Fedora Remix for WSL ](https://www.microsoft.com/store/apps/9n6gdm4k2hnc)
> > - [Pengwin ](https://www.microsoft.com/store/apps/9NV1GV1PXZ6P)
> > - [Pengwin Enterprise ](https://www.microsoft.com/store/apps/9N8LP0X93VCP)
> > - [Alpine WSL ](https://www.microsoft.com/store/apps/9p804crf0395)
>
> - From the distribution's page, select "Get".
>
> 9. ### Set up a new distribution
>
> The first time you launch a newly installed Linux distribution, a console window will open and you'll be asked to wait for a minute or two for files to de-compress and be stored on your PC. All future launches should take less than a second.
>
> You will then need to [create a user account and password for your new Linux distribution](https://docs.microsoft.com/en-us/windows/wsl/user-support) .
>
> CONGRATULATIONS! You've successfully installed and set up a Linux distribution that is completely integrated with your Windows operating system!
>
> ### Install Windows Terminal (optional)
>
> Windows Terminal enables multiple tabs (quickly switch between multiple Linux command lines, Windows Command Prompt, PowerShell, Azure CLI, etc), create custom key bindings (shortcut keys for opening or closing tabs, copy+paste, etc.), use the search feature, and custom themes (color schemes, font styles and sizes, background image/blur/transparency). [Learn more ](https://docs.microsoft.com/en-us/windows/terminal).
>
> [Install Windows Terminal ](https://docs.microsoft.com/en-us/windows/terminal/get-started).
>
> ### Set your distribution version to WSL 1 or WSL 2
>
> You can check the WSL version assigned to each of the Linux distributions you have installed by opening the PowerShell command line and entering the command (only available in Windows Build 18362 or higher): `wsl -l -v`
>
> ```PowerShell
> wsl --list --verbose
> ```
>
> To set a distribution to be backed by either version of WSL please run:
>
> ```PowerShell
> wsl --list --verbose
> ```
>
> Make sure to replace <distribution name> with the actual name of your distribution and <versionNumber> with the number '1' or '2'. You can change back to WSL 1 at anytime by running the same command as above but replacing the '2' with a '1'.
>
> Additionally, if you want to make WSL 2 your default architecture you can do so with this command:
>
> ```PowerShell
> wsl --set-default-version 2
> ```
>
> This will set the version of any new distribution installed to WSL 2.
>
> ### [Troubleshooting installation](https://docs.microsoft.com/en-us/windows/wsl/install-win10#troubleshooting-installation)


## Commands

------------

<https://gist.github.com/bradtraversy/89fad226dc058a41b596d586022a9bd3


When useing bash use `winpty` infront of each command

run the nginx web server on port 80

```PowerShell
docker container run -it -p 80:80 nginx
```

show all running containers

```PowerShell
docker container ls 
```

or

```PowerShell
docker ps 
```

show all container (even not running ones)

```PowerShell
docker container ls -a
```

show all images

```PowerShell
docker images  
```

`docker container run -detach -port <localmachine-port:container-port> --name <name> <image>`

`-d` option indicates that we want to run the containers in the background and get our terminal back.

```PowerShell
docker container run -d -p 80:80 --name mynginx nginx
```

force remove a running Container

`docker container rm <name> -force`

```PowerShell
docker container rm mynginx -f
```


enter Container

```PowerShell
docker container exec -it mynginx bash
```

will return the root@. Enter `ls` to show content.

webroot in debian (nginx enviroment) is under `usr/share/nginx/html`

```PowerShell
cd usr/share/nginx/html
```

`ls` to show content.

exit container

```PowerShell
exit
```

remove all Containers


```PowerShell
docker rm $(docker ps -ap) -f
```

map areas of the container to you local file system via a "Volume/BindMount"

adding a new container with a **BindMount** 
`-v <URL of local machine>:<URL of container>` 

shortcut for current directory:

- bash: `$(pwd)`
- cmd: `%cd%`
- PowerShell: `${PWD}`

```PowerShell
docker container run -d -p 8080:80 -v $(pwd):/usr/share/nginx/html --name nginx-website nginx 
```

> ## Dockerfile
>
> Dockerfile reference: <https://docs.docker.com/engine/reference/builder/>
>
> <https://docs.docker.com/develop/develop-images/dockerfile_best-practices/>
>
>
> create a `Dockerfile` inside your workspace
>
> We get everthing that comes from the latest version of enginx
>
> ```Dockerfile
> FROM nginx:latest
> ```
>
>define workdirectory in the container
>
> ```Dockerfile
> WORKDIR /usr/share/nginx/html
> ```
>
> copy all to all (all the filex from our local dir to the workdir)
> ```
> COPY . .
> ```

### docker image build

build image and push to docker account

`docker image build -t <Accountname>/<Imagename> .`

`.` referse to the folder we are in

```PowerShell
docker image build -t cinnadev/nginx-website .
```

### build an local image from the repo

```PowerShell
docker container run -d -p 8082:80 cinnadev/nginx-website 
```

### Docker Login

```PowerShell
docker login
```

### push Image to Docker Repository

```PowerShell
docker push cinnadev/nginx-website
```

## **Node Mongo Project**

### create the Dockerfile

asterix will include both package files . package.json and package-lock.json
`*` = wildcard

```Dockerfile
COPY package*.json
```

`RUN` commands aftge copy the package.json to install npm packages

```Dockerfile
RUN npm install
```

next copy everything else over

```Dockerfile
COPY . .
```

expose the port we will run on

```Dockerfile
EXPOSE 3000
```

execute cmd command to start the node server

```Dockerfile
CMD ["npm", "start"]
```

### create the docker-compose.yml

version of docker compose

```yaml
version: '3'
```

#### define 2 Services 

    app 
    mongo

```yaml
services: 
    app:
        container_name: docker-node-mongo
        restart: always
        build: .
        ports:
            - '80:3000'
    mongo:
        container_name: mongo
        image: mongo
        posts:
            - '27017:27017':
```

- app is builded from the current dir `bulid: .` and will run on port 80 local 3000 in conatainer 

- mongo is an mongo image and runs on port 27017 local as well as in the container

#### link mongo container to the app

```yaml
services: 
    app:
        container_name: docker-node-mongo
        restart: always
        build: .
        ports:
            - '80:3000'
        links:
            - mongo
    mongo:
        container_name: mongo
        image: mongo
        posts:
            - '27017:27017'
```

## Terminology

---------------

<https://docs.docker.com/glossary/>


- container:

> A container is a runtime instance of a docker image.
A Docker container consists of
>
>    - A Docker image
>    - An execution environment
>    - A standard set of instructions
>
> The concept is borrowed from Shipping Containers, which define a standard to ship goods globally. Docker defines a standard to ship software.
>`To help you grasp the nuance, think of an image as a class, and of a container as an instance of that class.`

- Dockerfile:

> A Dockerfile is a text document that contains all the commands you would normally execute manually in order to build a Docker image. Docker can build images automatically by reading the instructions from a Dockerfile.

- image:

> In an image, a layer is modification to the image, represented by an instruction in the Dockerfile. Layers are applied in sequence to the base image to create the final image. When an image is updated or rebuilt, only layers that change need to be updated, and unchanged layers are cached locally. This is part of why Docker images are so fast and lightweight. The sizes of each layer add up to equal the size of the final image.

- namespace:

> A Linux namespace is a Linux kernel feature that isolates and virtualizes system resources. Processes which are restricted to a namespace can only interact with resources or processes that are part of the same namespace. Namespaces are an important part of Docker’s isolation model. Namespaces exist for each type of resource, including net (networking), mnt (storage), pid (processes), uts (hostname control), and user (UID mapping). For more information about namespaces, see Docker run reference and Isolate containers with a user namespace.

- repository:

> A repository is a set of Docker images. A repository can be shared by pushing it to a registry server. The different images in the repository can be labeled using tags.

Here is an example of the shared nginx repository and its tags.

- volume:

> A volume is a specially-designated directory within one or more containers that bypasses the Union File System. Volumes are designed to persist data, independent of the container’s life cycle. Docker therefore never automatically deletes volumes when you remove a container, nor will it “garbage collect” volumes that are no longer referenced by a container. Also known as: data volume
>
> There are three types of volumes: host, anonymous, and named:
>
> - A host volume lives on the Docker host’s filesystem and can be accessed from within the container.
>
> - A named volume is a volume which Docker manages where on disk the volume is created, but it is given a name.
>
> - An anonymous volume is similar to a named volume, however, it can be difficult, to refer to the same volume over time when it is an anonymous volumes. Docker handle where the files are stored.