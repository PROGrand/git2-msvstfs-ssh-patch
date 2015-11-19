# git2-msvstfs-ssh-patch
libgit2 for Visual Studio 2015 ssh public/private key enabler
==================================

This patch for 'libgit2' allows usage of SSH public/private keys pair with ssh
repositories (such as gitolite) in Visual Studio 2015. Key-pair
can be produced by ssh-keygen utility included in "Git For Windows"
toolset. Fork uses keys stored in %USERPROFILE%\.ssh folder.

Compilation instructions are described in http://randomswdev.blogspot.it/2015/07/adding-ssh-support-to-visual-studio.html

in short:

* obtain cmake 3.3.0, python 2.7.10, libssh2 1.6.0
* unpack libgit2-src.zip from VisualStudio2015 destination folder.
* perform: <pre>cd c:\dev\libgit2
mkdir build && cd build
cmake -DEMBED_SSH_PATH=C:/dev/libssh2 -DSTDCALL=ON ..
</pre>

Above instructions allows generic SSH usage, and following patching command establishes %USERPROFILE%\.ssh\id_rsa file support.
<pre>$ patch src/transports/ssh.c < ssh.c.patch
</pre>
