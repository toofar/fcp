SSH/SCP are to slow. Use netcat instead.

Uses ssh to bootstrap a netcat (actually nc) pipe so you don't get limited by
ssh. On my direct ethernet link at home I get ~70 MB/s compared to ~20 MB/s
with scp.

You can transfer files to and from local and remote hosts or from a remote
host to a different remote host (assuming they have a route to each other).
Can also do local to local copies but it isn't particularly functional.

Multiple source paths are not currently supported.

Requires tar, basename, dirname, cat, nc and any dest/source host and
additionally find on the source host and getopt on the controlling host.

    Usage: fcp [-c] [-p portno] [--] [srchost:]srcpath [[dsthost:]dstpath]
    
    Copy files between hosts on a network. Uses tar and netcat (nc) for
    transferring data and ssh for setting up the transport.
    `dstpath` defaults to the current directory, use "-" to get a tarball on
    stdout.
    
    Options:
      -c         Tell tar to use gzip compression.
      -p portno  Port used by netcat. Defaults to 4365.

Released under the zlib license: http://opensource.org/licenses/Zlib
