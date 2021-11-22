# Status: unmaintained

As much as I'd like, I currently don't have the time or energy to support this project at this time. The goal of this project was to make a good WordPress server available to everyone. The mission continues with [Ymir](https://ymirapp.com). 

Otherwise, there are a lot of good server management tools for WordPress now. If you're looking for something free, you should take a look at [Sail](https://sailed.io/). It's only on DigitalOcean though. Otherwise, you can take a look at paid tools like [Gridpane](https://gridpane.com) (which was inspired by this project) and [SpinupWP](https://spinupwp.com).

---

![DebOps for WordPress](https://cldup.com/7ODJOzazxd-3000x3000.jpeg)

# DebOps for WordPress

"DebOps for WordPress" is a tool that gives anyone in the WordPress community
access to a fast and secure WordPress server. It's meant to be easy to use and
require little to no system administrator knowledge.

It takes care of everything for you. It does more than just install WordPress for you. It
also takes care of all server configuration and maintenance tasks.

All that you need to do is type in three commands (after installation) and wait for the magic to happen.

## Documentation

Please refer to the [wiki](https://github.com/carlalexander/debops-wordpress/wiki) for full documentation,
examples and other information.

## Installation

*If you've never used DebOps or Ansible before, please refer to the "[Installation](https://github.com/carlalexander/debops-wordpress/wiki/Installation)" page of the wiki.*

To create a "DebOps for WordPress" project, you just need to:

 1. Get a copy of this repo to your computer.
 2. Make sure that DebOps is up to date by running `debops-update`.

## Usage

*If you've never used DebOps or Ansible before, please refer to the "[Configuring your server](https://github.com/carlalexander/debops-wordpress/wiki/Configuring-your-server)" page of the wiki.*

To configure a server, you need to add it to the `hosts` file in the `inventory` folder
under both the `[debops_all_hosts]` and `[wordpress]`.

```ini
# inventory/hosts

[debops_all_hosts]
wordpress.example.com

[wordpress]
wordpress.example.com
```

Once that's done, you just need to run three commands. Each of them can take several minutes to run.

```bash
$ debops bootstrap -u root
$ debops
$ debops wordpress
```

## Acknowledgements

DebOps is the real cornerstone of this project. This project wouldn't exists without the amazing work done
by [Maciej Delmanowski](https://github.com/drybjed).

A lot of the initial inspiration for the roles came from WPEngine's [Mecury project](https://github.com/wpengine/hgv)
and [the port](https://github.com/zach-adams/hgv-deploy-full) done by [Zach Adams](http://zach-adams.com/).

The [default Varnish configuration](https://github.com/mattiasgeniar/varnish-5.0-configuration-templates) work by
[Mattias Geniar](http://ma.ttias.be/) was critical to get a solid foundation for Varnish in WordPress.
