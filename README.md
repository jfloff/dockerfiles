# Dockerfiles

Collection of Dockerfiles for various uses

  * [Dockerfile.RStudio](#rstudio)
  * [Dockerfile.Jekyll](#jekyll)
  * [Dockerfile.PlayFramework](#playframework)


## RStudio
Runs RStudio server, which is available via browser.

Builds [rocker/hadleyverse](https://github.com/rocker-org/hadleyverse), which extends `rocker/rstudio`, and provides `rmarkdown`, `knitr`, `pandoc`, and latex tools for authoring papers and presentations in the RStudio environment. Also provides popular packages by Hadley Wickham such as `ggplot2`, `dplyr`, `tidyr`, `devtools`, `httr`, and others.

##### Running
```shell
docker run --rm -v "$(pwd)":/home/r -w /home/r -p 8787:8787 -e ROOT=TRUE -ti rocker/hadleyverse
```

Browse to `https://<docker-ip>:8787` so you can view the *RStudio*. Log in using:
```
username: rstudio
password: rstudio
```

You can get your `docker-ip` at:
```shell
docker machine ip default
```

Launch an *R* terminal session instead of using *RStudio*:
```shell
docker run --rm -v "$(pwd)":/home/r -w /home/r -it rocker/hadleyverse /usr/bin/R
```

Launch plain bash session:
```shell
docker run --rm -v "$(pwd)":/home/r -w /home/r -it rocker/hadleyverse /bin/bash
```

##### More info
* [R and Docker together](https://benmarwick.github.io/UW-eScience-docker-for-reproducible-research/#18)
* [rocker/rstudio docker image](https://github.com/rocker-org/rocker/wiki/Using-the-RStudio-image)


## Jekyll
Runs Jekyll blog generator, which is available via browser.

Builds [jekyll/jekyll:builder](https://github.com/jekyll/docker), which is targeted at building  Jekyll sites.

##### Running
```shell
docker run --rm --label=jekyll --volume=$(pwd):/srv/jekyll \
  -it -p $(docker-machine ip `docker-machine active`):4000:4000 \
    jekyll/jekyll:builder
```

Browse to `https://<docker-ip>:8787` so you can view your generated site. You can get your `docker-ip` at:
```shell
docker machine ip default
```

##### More info
* [jekyll/jekyll:builder](https://github.com/jekyll/docker)


## Play Framework
Builds [dordoka/play-framework](https://github.com/dordoka/play-framework) docker image for Play Framework.

##### Running
```shell
docker run --rm -it -v "$(pwd)/<app>:/home/play/Code" -p 9000:9000 -p 9999:9999 -p 8888:8888 dordoka/play-framework
```

Once inside the shell run:
```shell
activator run
```

## License
[MIT License](LICENSE)
