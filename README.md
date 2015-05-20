# 3Dslicer-extension-with-Docker
This is a demo to run, test, build extensions and package your own variant of 3DSlicer right from the latest released version (currently Slicer 4.4).

## How it works?

- [3DSlicer](http://www.slicer.org/) is built and compiled from source (with [CMake](http://www.cmake.org/)), and the result is stored on [DockerHub as a Docker image](https://registry.hub.docker.com/u/patrickmerlot/3dslicer-docker-image/).
- This image is pulled and we can run it or extend it locally within Docker.
- On top of that, [Wercker](http://wercker.com/) allows us to automate the test and deployement for every single 'push' made to this repository.

While Docker guarantees reliability and reproducibility without waiting for most of the dependencies to be installed and the code source to compile, Wercker allows continuous delivery of your applications, by testing and reporting for every single push to the repository (and [even locally after any file modification saved](http://blog.wercker.com/2015/05/15/Introducing-local-development.html)... hot topic!).

## Getting started

### Running 3Dslicer
To run Slicer on your machine.
Pull the Docker image, i.e. the source code of 3Dslicer already built and compiled:

```shell
$ sudo docker pull patrickmerlot/3dslicer-docker-image
```

and run the image (as an interactive Docker container), which is like entering a virtual environment where 3Dslicer is already installed from source and ready to run:

```shell
$ sudo docker run -t -i patrickmerlot/3dslicer-docker-image /bin/bash
...
$ bash-4.2# ls
...
$ bash-4.2# /myProject/Slicer/Slicer-SuperBuild-Debug/Slicer
...
$ exit
```

### Test 3Dslicer

### Modify/Extend 3Dslicer

### Package your variant

## Setting up your own Automation-driven development

- Create a new repository on GitHub. To avoid errors, do not initialize the new repository with README, license, or gitignore files. You can add these files after your project has been pushed to GitHub.
- Clone this repository and push it to your own Github/Bitbucket account.

```shell
$ git clone https://github.com/Patechoc/3Dslicer-extension-with-Docker.git
$ cd 3Dslicer-extension-with-Docker
```

- At the top of your GitHub repository's Quick Setup page, click to copy the remote repository URL.
- In Terminal, add the URL for the remote repository (<remote repository URL>, e.g. https://github.com/Patechoc/myNewSlicerExtension.git) where your local repository will be pushed.

```shell
$ git remote rm origin
$ git remote add origin <remote repository URL>
```

- Push the changes (or simply this clone untouched) from your local repository to GitHub.

```shell
$ git push origin master
```

- Sign up/Log in to your [Wercker account](https://app.wercker.com/)
- Register your Github account in the Settings if not already done
- Create a new application and follow the steps (Select a repository, ...) until you clicked on "Finish"
- In your new application, change the Wercker version to 5 ("Ewok"). In "Settings" > "Infrastructure stack", select "Infra Stack 5"/"Ewok". This allows Wercker to pull Docker images.
- You are done! Now every time you will "push" to your Github repo, Wercker will test your code following the steps detailled in wercker.yml