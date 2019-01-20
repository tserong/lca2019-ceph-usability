## Distributed storage is easier now

Usability from Ceph Luminous to Nautilus

* * *

Tim Serong | [tserong@suse.com](mailto:tserong@suse.com)

linux.conf.au 2019

Note:

At LCA 2018, Sage Weil presented ["Making distributed storage easy: usability
in Ceph Luminous and beyond"](https://www.youtube.com/watch?v=GrStE7XSKFE).
I'm here today to present somewhat of a sequel to that talk, covering the
changes we've made in the meantime, and what's still coming down the track.


# The Story So Far

Note:

Once upon a time, there was Ceph...  But if I tell the whole story,
I won't have any time left for this talk, so you should probably watch
[A Gentle Introduction to Ceph](https://www.youtube.com/watch?v=5xoYFGkFTkM)
(LCA 2016 Geelong sysadmin) before listening to the rest of what I'm about
to say. 


## Ceph is Awesome

* Object, block and file storage
* Scale-out, no SPOF
* "Self-managing"

Note:

Ceph provides object, block and file storage in a single, horizontally scalabe
cluster, with no single points of failure.  It's Free and Open Source software,
it runs on commodity hardware, and it tries to be self-managing wherever possible,
so it notices when disks fail, and replicates data elsewhere, it does background
scrubbing, it tries to balance data evenly across the cluster.  But you do still
need to actually administer it.


## Ceph is Hard

Note:

This leads to one of the first points Sage made this time last year: Ceph is
Hard.  Status display and logs were traditionally difficult to parse visually,
there were lots of configuration options, tricky authentication setup, difficulty
figuring out number of placement groups, the fact that you had to do everything
with a CLI, unless you had a third-party GUI.


### ~~Ceph is Hard~~
## Ceph was Hard

Note:

I'd like to be able to flip this point to the past tense, because a bunch of
those things were already fixed in the Luminous release (August 2017); status
display and logs were cleaned up, a balancer module was added to help ensure
data is spread more evenly, crush device classes were added to differentiate
between HDDs and SSDs, a new in-tree web dashboard was added (although it was
read-only, so just cluster status display, no admin tasks), plus a bunch of
other stuff.  http://ceph.com/releases/v12-2-0-luminous-released/

But we can't go all the way to saying it "was hard", because that might imply
that *everything* is now easy...


### ~~Ceph is Hard~~
### ~~Ceph was Hard~~
## Ceph is Easier Now

Note:

...so until we reach that frabjous day, I'm just going to say that Ceph
is easier now, and it will continue to get easier in future.


## Ceph is Easier Now

Note:

Last LCA we were half way through the Mimic development cycle, and at the time
the major usability enhancements planned included:

- centralised configuration management
- slick deployment in Kubernetes with Rook
- Vastly improved dashboard based on ceph-mgr and openATTIC
- PG merging

We got some of that stuff done for Mimic, which was released in June 2018
https://ceph.com/releases/v13-2-0-mimic-released/ and more of it is coming
in the Nautilus release, which is due out very soon.
