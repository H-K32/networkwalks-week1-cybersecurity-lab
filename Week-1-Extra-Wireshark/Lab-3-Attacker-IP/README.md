# Lab 3 – Identify the Attacker's IP

## Overview

This lab involved analyzing captured network traffic in Wireshark to identify suspicious activity against a web server and determine the attacker's IP address.

## Objective

- Analyze captured network packets.
- Identify repeated TCP SYN requests.
- Determine the attacker's IP address.
- Identify open and closed ports.
- Determine the type of attack.

## Tools Used

- Wireshark
- Networkwalks browser-based lab environment

## Tasks and Findings

| Task | Description | Finding |
|---|---|---|
| 1 | Count captured packets | 309 packets |
| 2 | Filter TCP SYN packets | 72 packets |
| 3 | Identify the attacker | Identified by repeated SYN requests |
| 4 | Count destination ports tested | Analyzed destination ports |
| 5 | Identify open ports | Identified through SYN, ACK responses |
| 6 | Identify closed-port response | RST, ACK |
| 7 | Count closed ports | Analyzed RST responses |
| 8 | Identify the attack type | TCP SYN port scan |
| 9–10 | Additional lab tasks | Completed in the Networkwalks environment |

## Wireshark Filters

**Display TCP SYN packets:**

```text
tcp.flags.syn == 1
```

**Display SYN, ACK responses:**

```text
tcp.flags.syn == 1 && tcp.flags.ack == 1
```

**Display TCP reset responses:**

```text
tcp.flags.reset == 1
```

**Filter server responses to the attacker:**

```text
ip.src == 192.168.10.20 && ip.dst == 192.168.10.66 && tcp.flags.reset == 1
```

## Conclusion

The packet analysis revealed repeated TCP SYN requests directed at multiple server ports. The server responded differently depending on whether the ports were open or closed. This traffic pattern was consistent with a TCP SYN port scan.

## Screenshots

Screenshots captured during the lab:

![Task 1](screenshots/task%20one.jpg)

![Task 2](screenshots/task%20two.jpg)

![Task 3](screenshots/task%20three.jpg)

![Task 4](screenshots/task%20four.jpg)

![Task 5](screenshots/task%20five.jpg)

![Task 6](screenshots/task%20six.jpg)

![Task 7](screenshots/task%20seven.jpg)

![Task 9](screenshots/task%20nine.jpg)

![Final Result](screenshots/final%20result.jpg)
