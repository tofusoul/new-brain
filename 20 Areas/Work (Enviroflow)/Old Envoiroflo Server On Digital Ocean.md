# INFO

- Fedora 39
- Hosted on Digital Ocean
- 170.64.169.74 

# Server setup:

- rabbitmq

- Python 3.10.8:

- setup with this info <https://tecadmin.net/how-to-install-python-3-10-on-centos-rhel-8-fedora/>


sudo dnf install wget yum-utils make gcc openssl-devel bzip2-devel libffi-devel zlib-devel wget <https://www.python.org/ftp/python/3.10.8/Python-3.10.8.tgz> tar xzf Python-3.10.8.tgz cd Python-3.10.8 sudo ./configure --with-system-ffi --with-computed-gotos --enable-loadable-sqlite-extensions sudo make -j \$ sudo make altinstall

```
#+END_SRC
```
- Python 3.11 is installed by default it seems

- setup new user <https://www.digitalocean.com/community/tutorials/initial-setup-of-a-fedora-22-server>

- also remember to chance ssh policy to allow password

- <https://www.digitalocean.com/community/tutorials/how-to-configure-ssh-key-based-authentication-on-a-linux-server#how-to-copy-a-public-key-to-your-server>

- <https://www.digitalocean.com/community/tutorials/how-to-set-up-timezone-and-ntp-synchronization-on-ubuntu-14-04-quickstart>
