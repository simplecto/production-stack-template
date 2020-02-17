# Traefik production configuration

This is the configuration I use to deploy Traefik into production.
It is not necessarily built for massive scale, but it works for a
few websites what receive about 25,000 visits per month on a single
VM with 2 cores and 2 gigs of RAM.

## Deployment checklist

  * Verify that `acme.json` permissions are set to 600. Use command 
    `chmod 600 acme.json` to do that
  * Update the required email in the `docker-compose.yml` file. That is 
    required for LetsEncrypt to work
  * Verify that you want to use the latest protocols and encryption for HTTPS. 
    If you do not want that the follow the instructions outlined below. 
  * By convention we use a separate docker network called `traefik`. You can create
    this network simply by a `docker network create traefik` on the command line.

## acme.json
This is the file Traefik uses to hold the LetsEncrypt certificates needed for
HTTPS. It is required to have file permissions of 600 before startup.

## docker-compose.yml
This is the heart-and-soul of you config. We use the CLI options and Docker 
label approach to configure as much as possible such that it all lives in
one file. However, as as February 2020 Traefik does not support all config
options using this method. 

### what is this external network called "web"?

Good question. By convention all services proxied by traefik will need to connect
over this network which is internal to docker. It is not exposed to the open world.

If it does not already exist on your machine then you can create it using the
`docker network create traefik` command.

It will not be destroyed when bringing traefik down. 

## traefik_conf.yml
This is the only part of the Traefik configuration that must live in an 
external file. In some future release I hope these options can be configured
via docker labels or in command line arguments.


It is included and enabled by default because, "Who would not want the latest
encryption and protocols--am I right?"


Well, just in case you have to support older OS/Browser configurations you can 
disable this. Simply remove the volume bind-mount in the `docker-compose.yml`
file and the command line option `- "--providers.file.filename=/traefik_conf.yml"
`

I wrote more extensively about this here in my blog, [Improve Traefik's HTTPS Encryption with Qualys SSL Labs and testssl.sh](https://www.simplecto.com/improve-traefik-https-encryption-qualys-ssl-labs-testssl-sh/)

## Risk and Gaps

Please see [Risks and Gaps](RISK_ANALYSIS.md)

## Troubleshooting

Watch the logs. Traefik is descriptive in helping you find out what is not working. 