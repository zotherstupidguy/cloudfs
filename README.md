
cloudfs: Cloud virtual filesystem and block device
By Benjamin Kittridge. Copyright (C) 2013, All rights reserved.

You can contact me at bysin@bysin.net


Requirements
----
1. Linux >2.6

2. libfuse


How it works
----
Cloudfs creates an object filesystem or block device on top of
popular cloud storage services.  This filesystem can only be
accessed with cloudfs only.  It also supports transparent encryption
and zlib compression. As of right now, I only have support
for Amazon S3, but plan on adding others in the future.


Compiling
----
1. Run ./config.sh && make

2. Copy bin/cloudfs to /usr/sbin/

3. Copy bin/cloudfs.conf to ~/.cloudfs.conf

4. Edit ~/.cloudfs.conf


Command-line options
----
Listing volumes:
	cloudfs --list
	
Create a new volume:
	cloudfs --volume [volume] --create
	
Mounting the volume:
	cloudfs --volume [volume] --mount [directory]
	
Unmounting the volume:
	cloudfs --volume [volume] --unmount [directory]
		or
	umount [directory]
	
Deleting the volume:
	cloudfs --volume [volume] --delete


Tips and tricks
----
If you're going to use rsync with cloudfs, you'll see an improvement in
performance if you specify the " --inplace " flag with rsync. This
flag is not required, but highly recommended.

For automated scripts, you can add the " --force " flag to prevent
prompting.

You can't mount the same bucket twice at the same time for writing,
but you can use the " --readonly " flag to mount a bucket in read-only
mode.

