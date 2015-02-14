puppet-serf
===========

## Description
Configure a [Shorewall](https://shorewall.net/) firewall.

=======

Overview
--------

The Shorewall module provides an interface for installing and running the
Shorewall firewall management system, including control over many of its
diverse configuration files and assurance that Shorewall is activated on the
node.

Examples
--------

Classes
-------

## Class `shorewall`

This is the main class in the module it ensures that the Shorewall package is
installed and provides header boilerplate for many of the configuration files.
It also ensures that Shorewall is running.

### Parameters

#### `ipv4` (boolean)

Enables IPv4 firewalling. Default: `true`

#### `ipv6` (boolean)

Enables IPv6 firewalling. Default: `false`

#### `ipv4_tunnels` (boolean)

Control whether or not the module will manage the `tunnels` configuration file
for IPv4. Default: `false`

#### `ipv6_tunnels` (boolean)

Control whether or not the module will manage the `tunnels` configuration file
for IPv6. Default: `false`

#### `ip_forwarding` (boolean)

Sets the value of the `IP_FORWARDING` setting in
[`shorewall.conf`](http://shorewall.net/manpages/shorewall.conf.html)

#### `traffic_control` (boolean)

Enables control over the `tcinterfaces` and `tcpri` configuration files and
also sets the value of the `TC_ENABLED` setting in
[`shorewall.conf`](http://shorewall.net/manpages/shorewall.conf.html) to
`Simple` when true and `Internal` when false. This feature of the module is
incomplete. Default: `false`

#### `maclist_ttl` (number)

Sets the value of the `MACLIST_TTL` setting in
[`shorewall.conf`](http://shorewall.net/manpages/shorewall.conf.html) 

#### `maclist_disposition` (string)

Sets the value of the `MACLIST_DISPOSITION` setting in
[`shorewall.conf`](http://shorewall.net/manpages/shorewall.conf.html)

#### `log_martians` (boolean)

Sets the value of the `LOG_MARTIANS` setting in
[`shorewall.conf`](http://shorewall.net/manpages/shorewall.conf.html)

#### `route_filter` (boolean)

Sets the value of the `ROUTE_FILTER` setting in
[`shorewall.conf`](http://shorewall.net/manpages/shorewall.conf.html)

#### `blacklist` (string array)

## Class `shorewall::simple`

This class is wrapper around the more complicated and flexible `shorewall` class. It is designed to handle the special case of a system with just two zones, the local system and everything else. The class automatically declares all interfaces and allows specific ports to be opened to outside traffic.

### Parameters

#### `ipv4` (boolean)

Enables IPv4 firewalling. Default: `true`

#### `ipv6` (boolean)

Enables IPv6 firewalling. Default: `false`

#### `inet` (string)

Sets the name of the zone that contains "everything else." Default: `inet`

#### `ipv4_tunnels` (boolean)

Control whether or not the module will manage the `tunnels` configuration file
for IPv4. Default: `false`

#### `ipv6_tunnels` (boolean)

Control whether or not the module will manage the `tunnels` configuration file
for IPv6. Default: `false`

#### `default_policy` (string)

Sets the disposition for packets that do not match a rule for an open port. Must be one of `DROP`, `REJECT`, or `ACCEPT`. Default: `REJECT`

#### `open_tcp_ports` (integer array)

An array of the TCP port numbers that will be open to incoming traffic. Default: `[ '22' ]`

#### `open_udp_ports` (integer array)

An array of the UDP port numbers that will be open to incoming traffic. Default: `[]`

Defines
-------

## Define `shorewall::blacklist`

### Parameters

## Define `shorewall::config`

### Parameters

## Define `shorewall::host`

### Parameters

## Define `shorewall::iface`

### Parameters

## Define `shorewall::init`

### Parameters

## Define `shorewall::mark`

### Parameters

## Define `shorewall::masq`

### Parameters

## Define `shorewall::policy`

### Parameters

## Define `shorewall::port`

### Parameters

## Define `shorewall::proxyarp`

### Parameters

## Define `shorewall::routestoppped`

### Parameters

## Define `shorewall::rule`

### Parameters

## Define `shorewall::tunnel`

### Parameters

## Define `shorewall::zone`

### Parameters

Platform Support
----------------

This module is known to work on:

* Ubuntu 14.04 Trusty Tahr
* Ubuntu 12.04 Precise Pangolin
* Debian 7.x wheezy
* Raspbian

Pull requests enabling use of the module on additional platforms are welcome.

Author
------

Nate Riffe <inkblot@movealong.org>