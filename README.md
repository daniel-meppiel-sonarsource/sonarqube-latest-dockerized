# sonarqube-latest-dockerized

This project allows you to run the latest version of SonarQube with a PostgreSQL database, accompanied by a Jenkins server.
Both SonarQube and Jenkins are behind a Nginx reverse proxy and can be accessed via 2 different Ngrok tunnels.

## Prerequisites

You will need [Docker](https://docs.docker.com/get-docker/) and [Docker Compose](https://docs.docker.com/compose/install/) installed and running in your machine.
You will also need a [Ngrok](https://ngrok.com) account and 2 endpoints configured. 

## Configuration

1. Make sure you have 2 Ngrok endpoints ready for use, one for SonarQube and one for Jenkins.
2. Create a `.env` file in the project root and set `NGROK_AUTH_TOKEN=<your_ngrok_auth_token>`.
3. Modify the `ngrok.yml` file. For each of the tunnels, set the `subdomain` value to your Ngrok subdomain, and the `host_header`value to your Ngrok tunnel URL.
4. Modify the `/reverse_proxy/nginx/nginx.conf` file: for each of the two server blocks, set the server_name to your Jenkins and SonarQube Ngrok endpoints respectively.

## Run it with Docker Compose

To run the services, use the following command:

`docker-compose up`
