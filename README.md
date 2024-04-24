# Capturing Packets with Wireshark
![image](https://github.com/chrisreddy1/Packet-Capture/assets/156823759/10750e72-9918-4393-ac95-25c7753bb51d)

## Introduction

Scenario:
I am working for a company that wants to detect certain TCP/IP network traffic on their server, specifically web traffic. My task is to set up and demonstrate Wireshark’s packet capture capabilities.

Project Goal:
The IT manager wants to be able to capture ethernet network web traffic on the server and be able to detect certain IP addresses as well.

## Task 1: Install and Set Up Wireshark on Ubuntu
- To get the latest stable version of Wireshark on Ubuntu Linux, use the add-apt-repository command: sudo add-apt-repository ppa:wireshark-dev/stable

<img width="473" alt="1" src="https://github.com/chrisreddy1/Packet-Capture/assets/156823759/e464c245-b7e8-4a84-9484-892751f497f1">

<img width="473" alt="2" src="https://github.com/chrisreddy1/Packet-Capture/assets/156823759/e8fe63f4-e510-49d1-bffb-513225ce79d6">

- Wireshark should not be run as superuser for security reasons.

- The user can be added to the Wireshark group to add packet capture capabilities: sudo usermod -aG wireshark $USER

<img width="254" alt="3" src="https://github.com/chrisreddy1/Packet-Capture/assets/156823759/60eeb6fd-0e4d-42a8-a272-6437252535af">

## Task 2: Start a Packet Capture on an Ethernet Port and Save it to a File
- The wired interface includes the ethernet packet capture, which begins with ‘en’ in Wireshark.

<img width="440" alt="4" src="https://github.com/chrisreddy1/Packet-Capture/assets/156823759/eb9bf713-ba03-4b55-b939-c7115dc4d848">

- The Wireshark app includes controls to start packet capture, stop capture, save the packets to a file, and load the capture file.

<img width="442" alt="5" src="https://github.com/chrisreddy1/Packet-Capture/assets/156823759/d0310aab-9259-4034-8781-fd4f904860ad">

- A capture can only be saved once the capture has stopped.

<img width="440" alt="6" src="https://github.com/chrisreddy1/Packet-Capture/assets/156823759/53971e26-9d01-4e73-9053-8674e0c2ef1f">

## Task 3: Use a Display Filter to Detect HTTPS Packets
- To display certain packets in an existing packet capture, use a display filter.

- To display only HTTPS traffic, use a filter on TCP port 443: tcp.port == 443

<img width="412" alt="9" src="https://github.com/chrisreddy1/Packet-Capture/assets/156823759/a595d66e-f4c2-420f-801f-1c26d968583c">

## Task 4: Visit a Web Page and Detect its IP Address Using a Display Filter
- A TLS handshake display filter may be used to detect a website visit in a packet list: tls.handshake.type ==1

<img width="410" alt="10" src="https://github.com/chrisreddy1/Packet-Capture/assets/156823759/5662da53-b158-4cc7-88ad-c4cf37c78ba7">

- The IP address is used in a filter to obtain packet information for a particular website: ip.addr == 142.251.111.103

<img width="413" alt="11" src="https://github.com/chrisreddy1/Packet-Capture/assets/156823759/e5c4a10a-c9dc-40e1-bbc5-ab1b9b76c9ae">

## Task 5: Locate All HTTPS Packets from a Capture Not Containing a Certain IP Address
- A Conditional statement may be used to include and eliminate packets from a Wireshark capture: !(ip.addr == 162.159.61.4) and tcp.port == 443

<img width="433" alt="12" src="https://github.com/chrisreddy1/Packet-Capture/assets/156823759/891487dc-262e-4804-bade-728b7760a3cc">

- A compound conditional should include parentheses to avoid order of execution errors: !(ip.addr == 162.159.61.4) and (tcp.port == 80 or tcp.port == 443)

<img width="430" alt="13" src="https://github.com/chrisreddy1/Packet-Capture/assets/156823759/d0c79647-d1ae-4fb4-b800-eb7d2d8d7ec6">

## Conclusion

What I learned:
- Installed and set up Wireshark on Ubuntu.
- Used a display filter to detect IP addresses in packets.
- Used a display filter to detect HTTP and HTTPS packets.

Skills practiced:
Ethernet, Wireshark Filters, Wireshark Packet Capture, Wireshark, Network Packets
