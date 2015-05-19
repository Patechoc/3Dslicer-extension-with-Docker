# 3Dslicer-extension-with-Docker
This is a demo to run, test, build extensions and package your own variant of 3DSlicer right from the latest released version (currently Slicer 4.4).

## How it works?

- [3DSlicer](http://www.slicer.org/) is built and compiled from source (with [CMake](http://www.cmake.org/)), and the result is stored on [DockerHub as a Docker image](https://registry.hub.docker.com/u/patrickmerlot/3dslicer-docker-image/).
- This image is pulled and we can run it or extend it locally within Docker.
- On top of that, [Wercker](http://wercker.com/) allows us to automate the test and deployement for every single 'push' made to this repository.

While Docker guarantees reliability and reproducibility without waiting for most of the dependencies and the code source to compile, Wercker alows continous delivery of your applications, by testing and reporting on every single modification your push to the repository (and [even locally](http://blog.wercker.com/2015/05/15/Introducing-local-development.html)... hot topic!).