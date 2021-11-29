---
title: "How to use ssh config"
date: 2021-11-30T00:38:38+02:00
Description: "How to setup alias in ssh by native config"
Tags: ["linux", "linux tips", "ssh"]
Categories: []
featured_image: "/images/it/ssh-config.jpg"
featured_image_caption: ""
summary: "How to setup alias in ssh by native config"
DisableComments: true
draft: false
---

By default SSH use native config file `~/.ssh/config` without extension.

How to use it:

```
Host {alias}
    HostName {host name or ip address}
    User {username}
#   Port {port} - optional
#   IdentityFile {path/to/ssh-private-key} - optional
#   Compression {yes or no} - optional
#   ConnectTimeout {time in seconds} - optional
```

For example your `~/.ssh/config` file:

```
Host host1
    HostName api.host.com
    User root
```

You could to connect to your host with command:

```
ssh host1
```
