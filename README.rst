speedtest-cli
=============

Command line interface for testing internet bandwidth using
speedtest.net

Installation
------------

::

        ## If migrating from prior bintray install instructions please first...
        # sudo rm /etc/apt/sources.list.d/speedtest.list
        # sudo apt-get update
        # sudo apt-get remove speedtest
        ## Other non-official binaries will conflict with Speedtest CLI
        # Example how to remove using apt-get
        # sudo apt-get remove speedtest-cli
        $ sudo apt-get install curl
        $ curl -s https://raw.githubusercontent.com/codding-nepale/speedtest-cli/main/script.deb.sh | sudo bash
        $ sudo apt-get install speedtest
::

Usage
-----

::

    $ speedtest -h
        Speedtest by Ookla is the official command line client for testing the speed and performance of your internet connection.

        Version: speedtest 1.2.0.84

        Usage: speedtest [<options>]
          -h, --help                        Print usage information
          -V, --version                     Print version number
          -L, --servers                     List nearest servers
          -s, --server-id=#                 Specify a server from the server list using its id
          -I, --interface=ARG               Attempt to bind to the specified interface when connecting to servers
          -i, --ip=ARG                      Attempt to bind to the specified IP address when connecting to servers
          -o, --host=ARG                    Specify a server, from the server list, using its host's fully qualified domain name
          -p, --progress=yes|no             Enable or disable progress bar (Note: only available for 'human-readable'
                                            or 'json' and defaults to yes when interactive)
          -P, --precision=#                 Number of decimals to use (0-8, default=2)
          -f, --format=ARG                  Output format (see below for valid formats)
              --progress-update-interval=#  Progress update interval (100-1000 milliseconds)
          -u, --unit[=ARG]                  Output unit for displaying speeds (Note: this is only applicable
                                            for ‘human-readable’ output format and the default unit is Mbps)
          -a                                Shortcut for [-u auto-decimal-bits]
          -A                                Shortcut for [-u auto-decimal-bytes]
          -b                                Shortcut for [-u auto-binary-bits]
          -B                                Shortcut for [-u auto-binary-bytes]
              --selection-details           Show server selection details
              --ca-certificate=ARG          CA Certificate bundle path
          -v                                Logging verbosity. Specify multiple times for higher verbosity
              --output-header               Show output header for CSV and TSV formats

         Valid output formats: human-readable (default), csv, tsv, json, jsonl, json-pretty

         Machine readable formats (csv, tsv, json, jsonl, json-pretty) use bytes as the unit of measure with max precision

         Valid units for [-u] flag: 
           Decimal prefix, bits per second:  bps, kbps, Mbps, Gbps
           Decimal prefix, bytes per second: B/s, kB/s, MB/s, GB/s
           Binary prefix, bits per second:   kibps, Mibps, Gibps
           Binary prefix, bytes per second:  kiB/s, MiB/s, GiB/s
           Auto-scaled prefix: auto-binary-bits, auto-binary-bytes, auto-decimal-bits, auto-decimal-bytes

Inconsistency
-------------

It is not a goal of this application to be a reliable latency reporting tool.

Latency reported by this tool should not be relied on as a value indicative of ICMP
style latency. It is a relative value used for determining the lowest latency server
for performing the actual speed test against.

There is the potential for this tool to report results inconsistent with Speedtest.net.
There are several concepts to be aware of that factor into the potential inconsistency:

1. Speedtest.net has migrated to using pure socket tests instead of HTTP based tests
2. This application is written in Python
3. Different versions of Python will execute certain parts of the code faster than others
4. CPU and Memory capacity and speed will play a large part in inconsistency between
   Speedtest.net and even other machines on the same network

Issues relating to inconsistencies will be closed as wontfix and without
additional reason or context.
