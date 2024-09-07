---
layout: post
title: "Autoconf in WSL2 with MinGW"
date: 2024-08-19 23:18:30 -0400
categories: jekyll update
tag: autoconf WSL2 MinGW Git-for-Windows Blog Consider it coded!
---

When you install an Ubuntu distro with WSL2 on Windows 11, Ubuntu can see your
Windows files through the Linux path `/mnt/c`. WSL2 Ubuntu also utilizes Linux
packages and applications in your existing Windows installations of MinGW,
usually through the path `/mnt/c/MinGW`. MinGW comes with Git For Windows
installation, for example. I had uninstalled my WSL2 Ubuntu Bionic Beaver and
gone without WSL2 for a long time, trying out full Ubuntu installations on old
laptops. 

Now I'm giving WSL2 another try with Ubuntu Jammy, since over time I haven't 
accumulated that many repos on Ubuntu, they're all on Windows.

Working on installing a server from a repo I have on Windows, I had to run
autoreconf as a preliminary, which immediately failed with the error:

`Can't locate Autom4te/ChannelDefs.pm in @INC (you may need to install the Autom4te::ChannelDefs module) (@INC contains: /mingw/share/autoconf /etc/perl /usr/local/lib/x86_64-linux-gnu/perl/5.34.0 /usr/local/share/perl/5.34.0 /usr/lib/x86_64-linux-gnu/perl5/5.34 /usr/share/perl5 /usr/lib/x86_64-linux-gnu/perl-base /usr/lib/x86_64-linux-gnu/perl/5.34 /usr/share/perl/5.34 /usr/local/lib/site_perl) at /mnt/c/MinGW/bin/autoreconf-2.68 line 40. BEGIN failed--compilation aborted at /mnt/c/MinGW/bin/autoreconf-2.68 line 40.`

What happens is that the autoreconf-2.68 Perl script in your C:\MinGW\bin looks
for the value for key "autom4te_perllibdir" in your perl environment and fails
if that key-value pair hasn't been written. It just means the paths aren't set
up, not necessarily that you don't have the Autom4te package. You'll probably
find do have Autom4te installed in your MinGW if you poke around in
`MinGW\share\autoconf`. Anyway, I went to MetaCPAN to find some
[docs on `@INC`](https://metacpan.org/pod/perlfaq8#How-do-I-add-a-directory-to-my-include-path-(@INC)-at-runtime).
I applied what I found in the documentation as best as I could by running some
Perl commands in the WSL2 terminal, but I can see that the commands didn't
cause any changes that stick. The error persists.

I'm going to keep trying to change the Perl environment.
The [%ENV variable Perldoc](https://perldoc.perl.org/variables/%25ENV) displays
an example script that shows how to set key-value pairs. Also, the
autoreconf-2.68 script's 3rd line gives an example of how to reference the
value for key "autom4te_perllibdir". Enter a perl statement to set a value for
"autom4te_perllibdir" on the command line as follows.
`$ perl -e 'my $dir = "/mnt/c/MinGW/share/autoconf/Autom4te/"; $ENV{"autom4te_perllibdir"} = \$dir'`
That didn't work! 

Well honestly I would want WSL2 to have installations in its Linux root rather
than use MinGW. So how about this, if you find your Linux package on WSL is
sourced from a MinGW installation, just "reinstall" the package with apt.
