# Mimic

- "Dashboard v2"
- Centralized configuration management

Note:

In terms of usability improvements, Mimic gave us
- A new dashboard: http://docs.ceph.com/docs/mimic/mgr/dashboard/#mgr-dashboard-overview
  - Angular.JS, inspired by & derived from openATTIC
  - All features of Luminous dashboard
  - username/password auth
  - SSL/TLS
  - RBD & RGW management
  - Config settings browser
- Config options can now be centrally stored and managed by the monitor
  - For initial cluster bootstrap, you can now use DNS service records (SRV)
    rather than specifying MON hosts in ceph.conf
  - and everything else you can `ceph config set` 


# Nautilus

- Placement group autoscaling
- Further dashboard enhancements
- ...

Note:

As I said, the Nautilus release is due out really soon, and will include a bunch more
good stuff:

- PG autoscaling:
  - Because we now have PG merging (as well as PG splitting) we can now
    decrease *or* increase the number of PGs at will.  So you can do this
    by hand, or you can turn on PG autoscaling, and Ceph will try to take
    care of this for you, based on certain storage size targets that you
    can set (see http://docs.ceph.com/docs/master/rados/operations/placement-groups/#autoscaling-placement-groups)
- More dashboard enhancements, including
  - Multiple users/roles, also SSO via SAML
  - i18n & l10n
  - iSCSI and nfs ganesha management
  - Embedded Grafana dashboards
  - A few screenshots follow, just to give some flavour and highlight some
    of the further work since Mimic


<!-- .slide: data-background-image="images/Ceph_Manager_Dashboard_007.png" data-background-size="contain" -->

Note:

Here's the default status screen (on a tiny toy test cluster)


<!-- .slide: data-background-image="images/Ceph_Manager_Dashboard_011.png" data-background-size="contain" -->

Note:
- Mark OSDs up/down/in/out
- Trigger scrubs, deep scrubs
- Set global options (noup/noout/noscrub etc.) and various other settings


<!-- .slide: data-background-image="images/Ceph_Manager_Dashboard_015.png" data-background-size="contain" -->

Note:

The configuration settings editor actually tells you what the configuration
settings mean, and do.


<!-- .slide: data-background-image="images/Ceph_Manager_Dashboard_019.png" data-background-size="contain" -->

Note:

Create, edit, delete storage pools, see various statistics.


# Nautilus

- ...
- Blinky lights
- Orchestrator module(s)

Note:

Back to what else is coming up in Nautilus

- blinky lights (https://pad.ceph.com/p/blinky-lights) is the ability to turn on or
  off the ident and fault LEDs for the disk(s) backing a given OSD, so you can find
  the damn things in your DC.
- blinky lights, and some of the dashboard functionality (notably configuring
  iSCSI gateways and NFS ganesha) means Ceph needs to be able to talk to whatever
  tool it was that deployed the cluster, which leads to the final big thing I
  want to talk about for the Nautilus release, which is the Orchestrator module.


## Orchestrator Module(s)

* Ansible
* DeepSea (Salt)
* Rook

Note:

- There's a bunch of ways to deploy Ceph, and your deployment tool will always know
  more about your environment, and have more power to do things than Ceph itself will,
  but if you're managing Ceph, through the inbuilt dashboard and CLI tools, there's
  things you want to be able to do as a Ceph admin, that Ceph itself can't do.
- Ceph can't deploy a new MDS, or RGW, or NFS Ganesha host.  Ceph can't deploy new OSDs
  by itself.  Ceph can't blink the lights on a disk on some host if Ceph itself has
  somehow failed, but the host is still up.  For these things, you rely on your
  deployment tool, whatever it is.  So Nautilus will include Orchestrator modules for
  Ansible, DeepSea/Salt, and Rook, which allow the Ceph management tools to call out
  to your deployment tool as necessary to have it perform those tasks.  This is the
  bit I'm working on at the moment.


# Octopus?

Note:

Beyond Nautilus, Octopus is the next release, due in a bit more than nine months,
and on the usability front I know we can expect more dashboard and more ochestrator
functionality, but before that...


# Cephalocon 2019

https://ceph.com/cephalocon/barcelona-2019/

19-20 May (+ KubeCon & CloudNativeCon, May 20-23)

CFP closes Feb 1
