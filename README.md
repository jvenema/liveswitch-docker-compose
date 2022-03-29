# WARNING
This docker compose file is ONLY suited for getting started in a development environment. It is NOT intended for production use! You must handle failover, redundancy, backups, recording, autoscaling, etc, in your production infrastructure and this script does NOT do so. 

# Overview
This is pretty straightforward. It's just a docker-compose file for LiveSwitch. It's not set up for mass scale or health checks yet, just the basic creation of a gateway and media server.

# Prerequisites

docker and docker-compose

# Usage

The usage of this is about as straightforward as the overview.

1. Check out this repo
2. Run `docker-compose up`

That's it. Everything should be running locally. http://localhost:9090/admin to get to the admin page, http://localhost:8080/sync for signalling.

# Running docker as a service
This compose setup can be run as a service using systemd. Systemd does some fun CPU and memory monitoring, so we have to disable all those settings. The service file is in the repository (the .service file), and should be placed in the location noted in the first comment in that file. The location of the docker-compose.yml is specified in the WorkingDirectory setting in the service file.

# Misc notes
After installing on a headless server, sometimes entropy starts to fail, which causes docker-compose to hang with no output. Install haveged (apt install haveged) and this problem goes away.

# What this project does

This compose file creates a LiveSwitch gateway and media server, as well as a redis and postgres instance, and connects everything together. It is a quick and dirty way of getting up and running with a local instance of LiveSwitch for development purposes.