[![Docker Automated build](https://img.shields.io/docker/automated/jrottenberg/ffmpeg.svg)](https://hub.docker.com/r/joseajp/nuclide-remote/)

# nuclide-remote
Remote nuclide server in a Docker container. You can obtain more information about Nuclide at https://nuclide.io/docs/features/remote/

## Example of use

This Docker image exposes two ports. The `tcp/22` port which is the port used by the SSH server on the container and the `tcp/9090` port which is going to be used as the Nuclide communication port.

These are the basic steps you need to run this image:

- Find the path on your remote server that contains the project you want to open. In this example, it will be `~/projects/test-project`.

- On the remote host start the Docker container:

```
docker run -d -p 9090:9090 -p 9091:22 -v ~/projects/test-project:/projects/test-project --name nuclide-remote joseajp/nuclide-remote
```

- On your local machine, open Nuclide and click the **Try it** button for **Remote Connection** in the quick launch menu.

- Introduce the following parameters:
  - **Username** - `root`
  - **Server** - the address of your server. This can be a domain name based or IP address.
  - **Initial Directory** - the path on your remote server that contains the project you want to open.
  - **SSH Port** - `9091`
  - **Password** - `nuclide`
  - **Remote Server Command** - `nuclide-start-server --port 9090`

> **NOTE**
>
> If you want to access to the container just run this command:
>
>   `docker exec -ti nuclide-remote bash`
>

## License

This repository is licensed under the terms of the MIT [LICENSE](LICENSE).
