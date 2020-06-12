# petibear/tgconnectbox

Telegram bot to perform selected operations on UPC Connect Box (Compal CH7465LG) with.
This is a dirty (docker image) wrapper around [python-connect-box](https://github.com/home-assistant-ecosystem/python-connect-box) that allows passing commands only in one pre-defined telegram chat.

# Usage:

## Prerequisites

1. Get a Telegram bot, get its `token`, contact the bot and find out the `chat_id` of your common conversation
    * a new bot is created contacting the `@BotFather` bot
    * `chat_id` can be found investigating `https://api.telegram.org/bot[token]/getUpdates`
2. Create your own `config.yaml` out of `config_template.yaml`, set the `token`, `chat_id` and `host` and `password` to the Connect Box router


## Docker

Launch the docker image `petibear/tgconnectbox` mounting your folder with with `config.yaml` to the `/config` volume. Need to be launched from a host that can see both telegram and the router.

Linux
```shell
docker run --rm  -v path/to/config/folder/:/config petibear/tgconnectbox
```

WSL2
```shell
docker run --rm  -v c:/path/to/config/folder/:/config petibear/tgconnectbox
```

| Parameter | Type | Function |
| :----: | --- | --- |
| `/config` | volume | folder in which `config.yaml` is searched|

## Linux
Install the prerequisites (see `requirements.txt`), put your confit to `./config/config.yaml` and launch with `python3 app.py`.

_Note_: [python-connect-box](https://github.com/home-assistant-ecosystem/python-connect-box) needs to be installed from a git location for now using `pip install git+https://github.com/home-assistant-ecosystem/python-connect-box.git`

# Commands
Supported commands:

* `/help`
* `/status` - get status
* `/devices` - get the list of active devices
* `/downstream` - get downstream details
* `/upstream` - get upstream details
* `/temperature` - get temperature
* `/ipv6f` - show IPv6 filters
* `/ipv6f i` - toggle enable/disable of the i-th IPv6 filter

# Acknowledgements
Thanks to @fabaff, the author of [python-connect-box](https://github.com/home-assistant-ecosystem/python-connect-box)