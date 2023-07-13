# Untitled

## TASK1:   **NETWORK BANDWIDTH**

<aside>
🦄 **NETWORK BANDWIDTH**

### LINK

| TOPIC | LINK |
| --- | --- |
| How to Use iPerf to Measure Network Performance | https://www.baeldung.com/linux/iperf-measure-network-performance |
|  | https://linuxhint.com/iperf_command_usage/ |
|  |  |

### COMMAND

|  |  |
| --- | --- |
|  |  |
|  |  |
- **iperf command**
    
    <aside>
    🦄 ss
    
    To perform network bandwidth checks using iperf, you can use various command options depending on your requirements. Here are some commonly used iperf commands:
    
    1. Server Mode:
        - To start the iperf server, listening on a specific port (default is 5201):
            
            ```
            iperf -s
            ```
            
        - To specify the port explicitly:
            
            ```
            iperf -s -p <port_number>
            ```
            
    2. Client Mode:
        - To initiate a bandwidth test to a specific server IP address or hostname:
            
            ```
            iperf -c <server_ip/hostname>
            ```
            
        - To specify the server port explicitly:
            
            ```
            iperf -c <server_ip/hostname> -p <port_number>
            ```
            
    3. Test Duration:
        - To set the duration of the bandwidth test (in seconds):
            
            ```
            iperf -c <server_ip/hostname> -t <duration>
            ```
            
    4. UDP Testing:
        - To perform a UDP bandwidth test instead of TCP (useful for testing packet loss and jitter):
            
            ```
            iperf -c <server_ip/hostname> -u
            ```
            
        - To specify the UDP bandwidth (in bits per second) for the test:
            
            ```
            iperf -c <server_ip/hostname> -u -b <bandwidth>
            ```
            
    5. Parallel Connections:
        - To use multiple parallel client connections for the test:
            
            ```
            iperf -c <server_ip/hostname> -P <num_connections>
            ```
            
    
    These are just a few examples of the many options available in iperf. You can explore more options and customization by referring to the iperf documentation or running `iperf --help` for a complete list of available options.
    
    </aside>
    

### NOTES :

<aside>
🍁 Bandwidth specifically refers to the capacity at which a network can transmit data. For example, if the bandwidth of a network is 40 Mbps, it implies that the network cannot transmit data faster than 40 Mbps in any given case.

- the [iPerf](https://iperf.fr/) tool to measure network performance and bandwidth
- **it works in a client-server model and supports UDP and TCP**.
- ****Installing *iPerf* on Client and Server
`sudo apt install iperf`**

---

iperf -c 5.182.18.49 -i 5 -t 15 -w 416K -p 5003

- *i* specifies the interval time in seconds. 10 is the default
*t* specifies the time to run the test in seconds
*p* specifies the port. 5001 is the default
*w* specifies the TCP window size. 85 KB is the default

---

**How do you install iPerf?**
CentOS / Red Hat Linux operating systems
Run the following command on the command line:
`yum install iperf`

Debian / Ubuntu Linux operating systems
Run the following commands on the command line:
`apt-get update
apt-get -y install iperf`

===========
How do you use iPerf?

**On the server side, run the following command:**

`iperf -s`

The following information is an example of the command and its output on the client side:

`iperf -c 10.10.10.5`

============

**To Test The Link For 20 Seconds And Look At The Results Every 2 Seconds, You Can Change The Commands On The Client Side And The Server Side As Follows:**

server :
`iperf -s -p 8000 -i 2`

Client side:

`iperf -c 10.10.10.5 -p 8000 -t 20 -i 2`

================
How do you change the TCP Port (-p 8000)?

**Server Side:**  
`iperf -s -w 1024k -i 2 -p 8000`

**Client Side:**
`iperf -i 2 -t 20 -c 10.10.10.5 -p 8000 -w 1024k`

---

</aside>

### PRACTICAL :

<aside>
🦄

```nasm
ravi@server:~$ **iperf -s -p 8000 i2**
iperf: ignoring extra argument -- i2
------------------------------------------------------------
Server listening on TCP port 8000
TCP window size:  128 KByte (default)
------------------------------------------------------------
[  4] local 192.168.122.29 port 8000 connected with 192.168.122.109 port 51106
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-20.0 sec  22.2 GBytes  9.51 Gbits/sec

=====**************===============
ravi@client1:~$ **iperf -c 192.168.122.29 -p 8000 -t 20 -i 2**
------------------------------------------------------------
Client connecting to 192.168.122.29, TCP port 8000
TCP window size: 1.78 MByte (default)
------------------------------------------------------------
[  3] local 192.168.122.109 port 51106 connected with 192.168.122.29 port 8000
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0- 2.0 sec  2.33 GBytes  9.99 Gbits/sec

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**ravi@server:~$ iperf -s -w 1024k -i 2**
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size:  416 KByte (WARNING: requested 1000 KByte)
------------------------------------------------------------
[  4] local 192.168.122.29 port 5001 connected with 192.168.122.109 port 57666
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0- 2.0 sec   267 MBytes  1.12 Gbits/sec

**iperf -i 2 -t 20 -c 192.168.122.29 -w 1024k**
------------------------------------------------------------
Client connecting to 192.168.122.29, TCP port 5001
TCP window size:  416 KByte (WARNING: requested 1000 KByte)
------------------------------------------------------------
[  3] local 192.168.122.109 port 57666 connected with 192.168.122.29 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0- 2.0 sec   265 MBytes  1.11 Gbits/sec

----
```

</aside>

</aside>