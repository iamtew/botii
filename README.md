# botii - another ii bot

Bash scripts to turn [ii](http://tools.suckless.org/ii/) in to a simple bot.
Inspired and borrowed ideas and tricks from other bots, such as:
- https://github.com/c00kiemon5ter/iibot
- https://github.com/iotku/iibots
- https://github.com/iibot-irc/core
- https://github.com/SwissKid/iibot

# Requirements

- [ii](http://tools.suckless.org/ii/) (the actual IRC client)
- [inotify-tools](https://github.com/rvoicilas/inotify-tools)

## Usage

Any executable files in the `commands` directory will be treated as a command.
For example, place `myscript` in `commands` and invoke it from IRC with a
leading dot, like this: `.myscript`.
Any output will be passed back to the IRC channel. For more details take a look
at `botii_watch` how it works.

## Bot user

It can be wise to create a separate user for the bot and lower the process
limits, this is to avoid fork-bombing your system by misstake.

Bot user:
```
useradd -r -m -d /var/lib/botii -s /sbin/nologin -c 'botii irc bot' botii
```

Bot user limits, `/etc/security/limits.d/99-botii.conf`:
```
botii soft nproc 100
botii hard nproc 200
```

