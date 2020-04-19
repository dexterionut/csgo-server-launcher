## About
CS:GO Dedicated server dockerized

## Environment variables

* `TZ` : The timezone assigned to the container (default `UTC`)
* `PUID` : csgo-server-launcher user id (default `1000`)
* `PGID` : csgo-server-launcher group id (default `1000`)

And also the following environment variables to edit the .env file

* `IP` (default `$(sudo dig -4 +short myip.opendns.com @resolver1.opendns.com)`)
* `PORT` (default `27015`)
* `GSLT`
* `STEAM_LOGIN` (default `anonymous`)
* `STEAM_PASSWORD` (default `anonymous`)
* `CLEAR_DOWNLOAD_CACHE` (default `0`)
* `API_AUTHORIZATION_KEY`
* `WORKSHOP_COLLECTION_ID` (default `125499818`)
* `WORKSHOP_START_MAP` (default `125488374`)
* `MAXPLAYERS` (default `18`)
* `TICKRATE` (default `64`)
* `EXTRAPARAMS` (default `-nohltv +game_type 0 +game_mode 1 +mapgroup mg_active +map de_inferno +sv_lan 0`)

## Volumes

* `/var/steamcmd/games/csgo` : CSGO root folder
* `/home/steam/Steam` : Steam folder for logs, appcache, etc...

## Usage

### Docker Compose

Docker compose is the recommended way to run this image. Edit the compose and env files with your preferences and run the following command :

```bash
$ docker-compose up -d
$ docker-compose logs -f
```

## Upgrade image

You can upgrade this image whenever I push an update :

```bash
docker-compose pull
docker-compose up -d
```

## Notes

### Update CSGO

If you use compose, you can update CSGO by using the updater.yml :

```bash
$ docker-compose down              # stop csgo
$ docker-compose -f updater.yml up # start updater
$ docker-compose up -d             # start csgo
```
