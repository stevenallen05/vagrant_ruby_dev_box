### My Vagrant/Ansible dev box setup

#### Requires:
 * Vagrant
 * Ansible

#### Provides:
 * Postgresql
 * Redis
 * RabbitMQ
 * rbenv w/ ruby-build default-gems plugins
 * nodenv w/ node-build plugin
 * DNS-over-TLS to cloudflare
 * Nordvpn
 * Krypt.co for SSH key management
 * Unison sync between `~/host_home/gits` and `~/gits`
 * Mailhog
 * Ngrok
 * Git bash prompt from https://github.com/magicmonty/bash-git-prompt

#### Config

```bash
# Make config.yml
$ cp config.yml.example config.yml
# Set your config variables
$ vim config.yml
```

# Warning

I won't help you fix this if you break it.
