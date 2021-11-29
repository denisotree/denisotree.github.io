---
title: "Random Passwort on Linux"
date: 2021-11-29T22:55:56+02:00
Description: "How to create random password no linux or Mac OS"
Tags: ["linux", "ubuntu", "mac os", "linux tips"]
Categories: []
featured_image: "/images/it/passwords.jpg"
featured_image_caption: ""
summary: "How to create random password no linux or Mac OS"
DisableComments: true
draft: false
---

Open your terminal

If you use bash type

```
vim ~/.bashrc
```

If you use zsh type
```
vim ~/.zshrc
```

Go to end of file, press `o` and paste string
```
alias passgen="openssl rand -base64 32 | sed 's/[^a-zA-Z0-9]//g'"
```

For exit vim pess `Esc` , then `:x` + `Enter`

Finally, if you need generate random password, just type command `passgen` in your terminal!

Enjoy)