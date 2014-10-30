# DO Install Button

This is an **experimental** installer for getting apps running quickly on DigitalOcean.

This tool is written by DO fans, and is not affiliated with DigitalOcean Inc.

## Make your app installable with this tool

Add a file named `app.yml` to the root of your project on GitHub, like so:

```yaml
name: OneBody
image: ubuntu-14-04-x64
min_size: 1gb
config:
  #cloud-config
  users:
    - name: onebody
      groups: sudo
      shell: /bin/bash
      sudo: ['ALL=(ALL) NOPASSWD:ALL']
  packages:
    - git
  runcmd:
    - cd /home/onebody && git clone git://github.com/churchio/onebody.git && cd onebody && bash build/ubuntu/14.04/provision.sh
```

Then add markup like the following to your README.md file:

```markdown
[![Install on DigitalOcean](http://installer.71m.us/button.svg)](http://installer.71m.us/install?url=https://github.com/churchio/onebody)
```

## Run this tool yourself

```
git clone git@github.com:seven1m/do-install-button.git
cd do-install-button
cp config.yml{.example,}
# edit config.yml appropriately
bundle
rackup
```

## Copyright

Copyright 2014 Tim Morgan. See LICENSE file in this directory.