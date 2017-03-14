# vinegar
A collection of rotten wine-patches.

Should not be used by anyone.


A mental note to myself (ignore if you are not me or is much smarter than me and solved in other way):

In order to install 32-bit libraries in Debian to compile Wine make a i386 deboostrap, install everything inside and compile wine inside it. After satisfying every dependency and compiling Wine get back to the real world. 

<pre>
bruno@Note2:~$ cat /usr/local/bin/wrap32 

LD_LIBRARY_PATH="$LD_LIBRARY_PATH:/usr/lib/x86_64-linux-gnu:/media/1898E4E616F9684B/debian32/usr/lib/i386-linux-gnu:/lib/x86_64-linux-gnu:/media/1898E4E616F9684B/debian32/lib/i386-linux-gnu" LIBRARY_PATH="$LD_LIBRARY_PATH" "$@"
</pre>

Now compile anything using CC="wrap32 gcc" and run any 32-bit using "wrap32 whatever".

<pre>
bruno@Note2:~$ cat /etc/ld.so.conf.d/i386-chroot.conf 
# 386 from chroot
/media/1898E4E616F9684B/debian32/lib/i386-linux-gnu
/media/1898E4E616F9684B/debian32/usr/lib/i386-linux-gnu
/media/1898E4E616F9684B/debian32/lib/i686-linux-gnu
/media/1898E4E616F9684B/debian32/usr/lib/i686-linux-gnu
</pre>

And run ld.so as root.

Debian (till now) won't allow the installation of several packages in parallel for both architectures at the same time.
