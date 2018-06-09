---
layout: post
title: "Run Jupyter Notebook on Aliyun ECS"
date: 2018-06-09 08:29:00 +0800
summary: run jupyter notebook on aliyun ecs
slug: run-jupyter-notebook-on-aliyun
categories: python aliyun
---

_Problem_

You want to deploy Jupyter Notebook on your Aliyun ECS

_Solution_

Install Python and Jupyter. Add a new rule to security group (Inbound + Port number). Type "ipython" at the command line, it will start an interactive shell where you can set the login password for Jupyter

```python
ln [1]: from notebook.auth import passwd
ln [2]: passwd()
Enter password: # enter the password
Verify password: # enter it again
Out[2] 'sha1:******' # copy this string
```

Create Jupyter config file
```bash
jupyter notebook --generate-config
nano ~/.jupyter/jupyter_notebook_config.py
```

Modify the config file
```config
c.NotebookApp.ip = '*'
c.NotebookApp.password = u'sha1:****'
c.NotebookApp.open_browser = False
c.NotebookApp.port = <port_number>
```

Back to the command line and start Jupyter notebook
```bash
Jupyter Notebook &
```

Open a web browser, navigate to `http://<ip_address>:<port_number>`, enter the password and you can start using Jupyter notebook.



