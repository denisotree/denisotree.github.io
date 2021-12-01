---
title: "How to run Python script on remote server"
date: 2021-11-30T23:38:01+02:00
Description: "How to run Python script on remote server by ssh without registration and sms"
Tags: ["linux", "ubuntu", "mac os", "linux tips", "python", "ssh"]
Categories: []
featured_image: "/images/it/python-remote.jpg"
featured_image_caption: ""
summary: "How to run Python script on remote server by ssh without registration and sms"
DisableComments: true
draft: false
---

All is very-very simple - just run command:

```
ssh {your_login}@{host_or_ip_address} '{path_to_python_env}/bin/python' < {your_script}.py
```

Where `your_login` -> your unix username on remote server, `host_or_ip_address` -> remote server address, `path_to_python_env` -> absolute path to python interpreter or virtualenv bin on remote server and `your_script` -> path to your script on local machine.

After pressing Enter, you need to login to the remote server. If you are allowed to login with a password, enter the password. If you can only log in with an ssh key, make sure your key is registered in the authorized_keys file on the remote server.
