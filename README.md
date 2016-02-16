# Dockerfiles

Collection of Dockerfiles for various uses

  * [Dockerfile.RStudio](#rstudio)

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
docker run --rm -it --user docker rocker/hadleyverse /usr/bin/R
```

Launch plain bash session:
```shell
docker run --rm -it --user docker rocker/hadleyverse /bin/bash
```

##### More info
* [R and Docker together](https://benmarwick.github.io/UW-eScience-docker-for-reproducible-research/#18)
* [rocker/rstudio docker image](https://github.com/rocker-org/rocker/wiki/Using-the-RStudio-image)

## License
[MIT License](LICENSE)
