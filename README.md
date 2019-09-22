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
 * goenv
 * DNS-over-TLS to cloudflare
 * Nordvpn
 * Krypt.co for SSH key management
 * Unison sync between `~/host_home/gits` and `~/gits`
 * Mailhog
 * Ngrok
 * ZSH w/ powerlevel9k (tweak in `config.yml`)

#### Config

```bash
# Make config.yml
$ cp config.yml.example config.yml
# Set your config variables
$ vim config.yml
```

# Warning

I won't help you fix this if you break it.
