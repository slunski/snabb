## `loadgen`: Load-generator design

![loadgen](.images/loadgen.png)

The loadgen design reads a PCAP trace file, creates a loop from its
contents (in case of short traces), and simultaneously loads this
traffic into a set of LoadGen apps. The result is that each LoadGen
app transmits the contents of the pcap input file in a loop.

### Performance

    Hardware  | commit   | # ports | pktlen | NUMA  | Mpps   | Mpps / port
    ----------+----------+---------+--------+-------+--------+------------
    chur      | 46605d54 | 1       |     64 | Good  |  14.1  | 14.2
    chur      | 46605d54 | 1       |     64 | Bad   |  13.9  | 13.9
    chur      | 46605d54 | 20      |     64 | Good  | 266    | 13.3
    chur      | 46605d54 | 20      |     64 | Bad   | 204    | 10.2
