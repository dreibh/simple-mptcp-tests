# Introduction

This repository contains some simple test scripts for Linux MPTCP in the mainline kernel.

## Scripts

* [testbed-setup](testbed-setup): Create local testbed with namespaces. The number of networks can be specified as command-line parameter.
* [testbed-removal](testbed-removal): Remove the testbed namespaces.
* [test-ncat-server](test-ncat-server): Run a simple test server with ncat.
* [test-ncat-client](test-ncat-client): Run a simple connected test with ncat.
* [test-monitor-server](test-monitor-server): Run "ip mptcp monitor" in the server namespace.
* [test-monitor-client](test-monitor-client): Run "ip mptcp monitor" in the client namespace.
* [test-tshark](test-tshark): Run T-Shark in the server or client namespace.

## Run a Test

1. Run testbed-setup with number of networks (1 to 9), e.g.:
   ```
   ./testbed-setup 3
   ```

2. Start server monitor in a separate shell:
   ```
   ./test-server-monitor
   ```

3. Start client monitor in a separate shell:
   ```
   ./test-client-monitor
   ```

4. Start a server in a separate shell, e.g.:
   ```
   ./test-ncat-server
   ```

5. Start T-Shark in the client or server namespace in a separate shell, e.g.:
   ```
   ./test-client-tshark client
   ```
   or to write a PCAP file:
   ```
   ./test-client-tshark server -w /tmp/server.pcap
   ```

6. Run a client, e.g.:
   ```
   ./test-ncat-client
   ```
   The monitors now should provide information about the MPTCP status. Also, the MPTCP protocol flow should be displayed by T-Shark.

# Links
* [NetPerfMeter – A TCP/MPTCP/UDP/SCTP/DCCP Network Performance Meter Tool](https://www.nntb.no/~dreibh/netperfmeter/)
* [HiPerConTracer – High-Performance Connectivity Tracer](https://www.nntb.no/~dreibh/hipercontracer/index.html)
* [Dynamic Multi-Homing Setup (DynMHS)](https://www.nntb.no/~dreibh/dynmhs/index.html)
* [Multipath TCP for Linux](https://www.mptcp.dev/pm.html)
* [Using Upstream MPTCP in Linux Systems](https://netdevconf.info/0x14/pub/papers/59/0x14-paper59-talk-paper.pdf)
* [Multipath TCP on RHEL 8](https://developers.redhat.com/articles/2021/10/20/multipath-tcp-rhel-8-one-many-subflows#multipath_tcp_in_red_hat_enterprise_linux_8)
