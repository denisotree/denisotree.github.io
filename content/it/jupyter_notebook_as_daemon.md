---
title: "Setting up jupyter notebook as daemon"
date: 2020-09-24T16:33:08+03:00
Description: ""
Tags: ["jupyter"]
Categories: []
featured_image: "/images/it/jupyter.jpg"
featured_image_caption: ""
summary: "How to install and configure Jupyter notebook like a service at your Linux server"
DisableComments: true
draft: false
---

## Jupiter Notebook Installation

Install Jupyterlab, using pip package manager

```
pip install jupyterlab
```

Next, install notebook

```
pip install notebook
```

Now, you can start Jupyter notebook with command **jupyter notebook**

## Create virtualenv kernel

In order not to get side effects when installing packages for your laptop, we will do it inside the virtual environment.

Install module **virtualenv** if you have not it

```
pip install virtualenv
```

Create your environment

```
virtualenv [-p {path_to_python_bin}] .venv
```

For activate virtual environment us the next command

```
. .venv/bin/activate
```

Install new jupyter kernel

```
python -m ipykernel install --user --name=.venv
```

## Configurate daemon startup

Generate Jupyter notebook config file

```
jupyter notebook --generate-config

>> jupyter config: path/to/jupyter_notebook_config.py
```

Use your favorite text editor for change this config like here

```
c.NotebookApp.ip = '0.0.0.0'
c.NotebookApp.open_browser = False
c.NotebookApp.port = 8888
```

Set password for your notebook

```
jupyter notebook password
```

Next, we will create system daemon file

```
vim ~/.config/systemd/user/jupyter.service
```

And insert next rows

```
[Unit]
Description=Jupyter Notebook

[Service]
Type=simple
PIDFile=/run/jupyter.pid
ExecStart=/home/{username}/.local/bin/jupyter-notebook --config=/home/{username}/.jupyter/jupyter_notebook_config.py
User={username}
Group={groupname}
WorkingDirectory=/abspath/to/your/working/directory
Restart=always
RestartSec=10

[Install]
WantedBy=multi-user.target
```

Enable and start daemon

```
systemctl --user enable jupyter.service
```

```
systemctl --user daemon-reload
```

```
systemctl --user restart jupyter.service
```

## Check notebook

In your browser go to address **{your_server_name}:4242**

![Password window](/images/it/jupyter-password.jpg "")

Enter your password and will see this window

![Welcome window](/images/it/jupyter-welcome.jpg "")

Press "New" button and choose **.venv** like your base kernel. Now you can use all modules, you install in **.venv** environment.

Enjoy!