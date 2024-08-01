# docker-mullvadvpn

Run mullvad-cli in a docker container (docker-compose)

## How to run it
> Please don't forget to read [this](#architecture).

My objective was to get a mullvad-cli app to run in a docker container, and even
better, to get it to run with docker compose.
To run this, will have to build the image of the container using the following commands:
- `cd docker-mullvadvpn`, (original project by [gvkhna](#original-project), a bit edited)
- `docker build --rm -t <your_image_name> .` (I personally used `docker build --rm -t coton_mullvad .`)

Now that you have your image, you can run it as a solo container (just copy the `compose.yml` file parameters in the command line you'll use),
or use the docker compose method.
- `cd ..` (this project root),
- `docker compose up -d`

> If you named your image differently, edit the `compose.yml` file in consequence.

It is unlikely this project will be more documented or continued, but please enjoy
reading the configuration files. If it does help you, let me know with a star ;)

> Sadly, the --privileged (or privileged: true) seem to be necessary for `mullvad-daemon.service` to start correctly in the container.
> It's a huge [security flaw](https://docs.docker.com/reference/cli/docker/container/run/#privileged), but if you're here it's because you
> are trying to achieve a difficult thing, so bear with it or do better.

## Architecture
Please take a look at the [Dockerfile](docker-mullvadvpn/Dockerfile) and change the
mullvad ".deb" package you download to reflect your architecture.
The current Dockerfile is set up for macOS 14.5

## Original project
This project is based on the work of [gvkhna](https://github.com/gvkhna/docker-mullvadvpn/)
which I thank.
Sadly, his project is archived as did not work as some external updates seem to have broken it.
