# DebOps for WordPress

"DebOps for WordPress" is a tool created to give anyone in the WordPress community
access to a high-performance WordPress server. It's meant to be easy to use and
require little to no system adminstrator knowledge.

It takes care of everything for you. It's not just installing WordPress. It also takes
care of all the server configuration. It'll handle the setup of:

 * Automatic updates
 * MySQL backups
 * Fail2ban
 * Firewall
 * And a lot more

On top of all that, you'll also have a working WordPress installation using:

* Nginx
* MariaDB
* HHVM
* PHP-FPM (automatic fallback)
* Redis
* WP-CLI
* Varnish (optimized for WordPress)

All that you need to do is type in two command lines.

## Requirements

### Your server

You'll need an Ubuntu server (14.04 LTS version is prefered) that you can connect to
using an SSH key. To configure a server with SSH, please refer to the server creation guide
for your cloud hosting provider.

If there isn't one, please refer to your hosting provider's guide for configuring SSH. You
may also create an issue to create a guide for that specific hosting provider.

### Your computer

In order to use "DebOps for WordPress", you'll need to install Ansible and [DebOps](http://debops.org)
on your computer. You can only install these on MacOS X or Linux.

#### Install pip

The easiest way to install Ansible and DebOps is with [pip](https://pip.pypa.io). If it isn't already
installed, you can install it using one of the following command lines.

On MacOS X:

```bash
sudo easy_install pip
```

On Debian and Ubuntu:

```bash
sudo apt-get install python-pip
```

On Fedora:

```bash
sudo yum install python-pip
```

#### Install Ansible

Due to an [Ansible bug](https://github.com/ansible/ansible/issues/10675), you will need to install a
specific version of Ansible.

```bash
pip uninstall ansible
pip install -Iv https://pypi.python.org/packages/source/a/ansible/ansible-1.9.0.1.tar.gz
```

#### Install DebOps

Installing DebOps is done through pip as well.

```bash
pip install debops
```

For MacOS X users, you'll need to do another step due to another [Ansible bug](https://github.com/ansible/ansible/issues/8555).
Replace `{username}` with your own username.

```bash
ln -s /Users/{username}/Library/Application\ Support/debops /usr/local/share/debops
```

You'll also need to set `/usr/local/share/debops` in your `.debops.cfg` as such:

```ini
data-home: /usr/local/share/debops
```

## Installation

To create a "DebOps for WordPress" project, you just need to:

 1. Get a copy of this repo to your computer.
 2. Make sure that DebOps is up to date by running `debops-update`.

## Configure your first server

Before you can begin configuring your server, you need to create a server for DebOps to configure.

### SSH Key required

DebOps requires that you add an SSH key to connect to your server. It replaces the need for a password
and encrypts all communication with your server.

You can see the [GitHub documentation](https://help.github.com/articles/generating-ssh-keys/) to create
your own. Most provider instructions will also show you how to create and add your SSH key to your server.

### Cloud hosting provider instructions

Here are some detailed instructions to setup your server with specific cloud hosting providers.

#### Digital Ocean

Before you begin, you have to make sure that you've created an [SSH key in Digital Ocean](https://www.digitalocean.com/community/tutorials/how-to-use-ssh-keys-with-digitalocean-droplets). You only need to do this once.

You want to click on `Create droplet` in the Digital Ocean control panel

![Top of the page](https://cldup.com/XgYCnEdxDi-3000x3000.png)

Replace `debops-wordpress` with the name that you want for your server. DebOps will use that name to
store all server specific passwords in the `secret` directory.

![Middle of the page](https://cldup.com/sxP782VXgk-3000x3000.png)

Select a region that fits best for you. You don't need to select anything under `Available Settings`.

![Bottom of the page](https://cldup.com/TbpF9QZJx--3000x3000.png)

The last step is to select your Linux. The default Ubuntu version (14.04 x64) is the best option here. Make
sure to also select an SSH key for the server.

Press `Create Droplet` and wait for your server to come online.

### DNS record

Once your server is created, you'll want to create a DNS record for your server. This isn't
necessary, but the default settings will work better with an address.

### DebOps playbooks

Now that you have your server, it's time to install everything using DebOps. This is only two
command lines, but each of them takes between 5 and 10 minutes.

### Add your server to the host file

First, you'll need to add the address of your new server to the `host` file found in `{project_root}/inventory`.
The server name needs to be added under both the `[all_server]` and `[wordpress]` as such:

```ini
[all_servers]
wordpress.example.com

[wordpress]
wordpress.example.com
```

#### Run the common DebOps playbook

Your first step is to install and configure all essential services. These include iptables, DNS, Postfix,
sshd configuration and much more. You just need to type in this command to get started:

```bash
debops -u root
```

You'll get the following warning almost right away.

```bash
PLAY [Gather default and custom facts] ****************************************

GATHERING FACTS ***************************************************************
The authenticity of host '123.456.78.90 (123.456.78.90)' can't be established.
RSA key fingerprint is 11:eb:57:f3:a5:c3:e0:77:47:c4:15:3a:3c:df:6c:d2.
Are you sure you want to continue connecting (yes/no)?
```

Type `yes` and Enter to continue. This step can take 5-10 minutes. So go grab a coffee or take stretch
while the magic happen.

#### Run the WordPress DebOps playbook

Now, you still don't have a configured WordPres site. You still need to install and configure all
WordPress related services. This is done using this command:

```bash
debops wordpress -u root
```
You don't need to wait for a prompt this time. You can just sit and relax. This step can take 5-10 minutes as well.

### Your server

Once the second script is done, your server will be configured and functional. You can visit your site at
`wordpress.example.com` (replace this with the address you used).

You can SSH to it using the root account:

```bash
ssh wordpress.example.com - l root
```

## Performance tuning

Here are some extra steps you can take to improve the performance and behaviour of your server.

### Recommended plugins

Here are some recommended plugins that you can add to your WordPress installation to improve its
performance further.

#### Varnish Purge Plugin

While Varnish has a solid WordPress configuration, it can't detect when you're making changes to posts.
[This plugin](https://wordpress.org/plugins/varnish-http-purge/) notifies Varnish when you make changes
to existing posts. It'll tell it to purge the relevant pages from the cache. This ensures that visitors
always see the up-to-date post content.

#### Redis Object Cache

Your server comes preconfigured with Redis, but the object cache isn't installed by default. To use the
object cache, you'll need to install [this plugin](https://wordpress.org/plugins/redis-cache/).

#### TinyPNG

Your site might still feel slow even with the best configuration possible. That's because your visitors
still need to download images on your page. If they aren't compressed, this can be an issue that affects
performance. [This plugin](https://wordpress.org/plugins/tiny-compress-images/) takes care of that. It's
[been found](https://www.mattcromwell.com/battle-of-the-image-compression-wordpress-plugins/) to give the
best result in terms of compression.

#### RICG

Even with proper compression, your site might still feel slow on mobile devices. You want to make sure that
you use the right image for the right devices. [This plugin](https://wordpress.org/plugins/ricg-responsive-images/)
will take care of all of that for you.

## Acknowledgements

DebOps is the real cornerstone of this project. This project wouldn't exists without the amazing work done
by [Maciej Delmanowski](https://github.com/drybjed).

A lot of the initial inspiration for the roles came from WPEngine's [Mecury project](https://github.com/wpengine/hgv)
and [the port](https://github.com/zach-adams/hgv-deploy-full) done by [Zach Adams](http://zach-adams.com/).

The [default Varnish configuration](https://github.com/mattiasgeniar/varnish-4.0-configuration-templates) work by
[Mattias Geniar](http://ma.ttias.be/) was critical to get a solid foundation for Varnish in WordPress.
