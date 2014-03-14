---
layout: postsen
title: "Is Homebrew the missing package manager for OS X?"
date: 2010-05-10 13:38
categories:
- en
---

Once upon a time, in OSX land, there were three package managers: fink (the old one inspired by debian's apt); macports (inspired by FreeBSD's ports); pkgsrc (the ancient one which is originally for netBSD but works everywhere). There also was a port of gentoo portage for osx. And recently appeared homebrew, subtitled "The missing package manager for OS X" or "MacPorts driving you to drink? Try Homebrew!". So obviously, it tries to be a macports replacement in a place where macports is not the only reigning package manager.



As I used macports and got involved in its development by writing portfiles, I got interested in how homebrew may be better. So I read the [homebrew website](http://mxcl.github.com/homebrew/) and began comparing:



>Homebrew is the easiest and most flexible way to install the UNIX tools Apple didn't include with OS X.
>
>     $ brew install wget

Not really easier than `port install wget`



> Packages are installed into their own isolated prefixes and then symlinked into /usr/local.

Compare this to macports where packages are installed into their own isolated prefixes and then hardlinked into /opt/local. So it boils down to hardlink versus symlink?



> Just extract the tarball and straight away you have a working Homebrew installation.

Lies, one also need to install Xcode and launch a ruby script. In macports, you also have to install Xcode but not to extract the tarball as there are mpkgs...



> Create new Homebrew packages in seconds.
> 
>     $ brew create http://foo.com/bar-1.0.tgz
> 
> Created /usr/local/Library/Formula/bar.rb

Nice. There exists an automatic scripts for creating perl portfiles, but as far as I know nothing for simple classical packages. Well it is true that `port cat wget > Portfile; $EDITOR Portfile` is not that difficult.  




> Easily adapt Homebrew formula to your needs. And since it's all Git underneath your changes are merged automatically with upstream updates.
> 
>     $ brew edit wget # opens in TextMate!

Or you could easily adapt portfiles to your needs. And since it's all svn underneath your changes are merged automatically with macports updates.

    $ port edit wget # opens in your favorite editor





> Homebrew formula are simple Ruby scripts:
> 
>     require 'formula'
>     
>     class Wget < Formula
>       homepage 'http://www.gnu.org/wget/'
>       url 'http://ftp.gnu.org/wget-1.12.tar.gz'
>       md5 '308a5476fc096a8a525d07279a6f6aa3'
>     
>       def install
>         system "./configure --prefix=#{prefix}"
>         system 'make install'
>       end
>     end

Whereas Portfiles are simple tcl scripts which in easy cases are just a list of keys/values.

    PortSystem 1.0
    name            clive
    version         0.4.5
    description     A console line client for livejournal.
    long_description      This is a console UNIX client for updating weblogs. \
                          It is designed to be used interactively or as a \
                          UNX-style filter on the command line.
    maintainers     nomaintainer
    categories      net
    platforms       darwin 
    homepage        http://sourceforge.net/projects/ljclive/
    master_sites    sourceforge:ljclive
    checksums       md5 1ed5e499501e6af761d56727b49aa273
    depends_lib     port:libiconv


> Homebrew complements OS X. Install your gems with gem, and their dependencies with brew.

And be ensnared in a mess of conflicting files, some installed by your package manager, some by gems/cpan/python, some by you. A mess from which you won't know what you may safely remove. Or choose to use a serious package manager. Also, I would like to know if homebrew checks that programs indeed install in /usr/local and do not leave things in uncalled places.



So in the end, unless if I was thinking in ruby, macports is still better for me, and even if beaten in ease of use, pkgsrc stays the reliable one. But in the end, Everybody is reinventing the wheel of the package manager. I'm aware that macports does not always behave as wanted. I agree that pkgsrc is not as easy as osx users need. I know that fink is sometimes lagging and I'm sure that homebrew with its 770 recipes is far from being as wide as macports with its 6865 ports and so much from debian and its more than 30000 packages.
