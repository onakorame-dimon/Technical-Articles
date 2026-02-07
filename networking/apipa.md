# __APIPA (Automatic Private IP Addressing)__

The first time I heard about APIPA addresses was when I started working with Azure VPN gateways. Before then, I was already familiar with the reserved private IP address ranges defined in RFC 1918 (RFC: a publicly published technical document that defines internet standards, protocols, or best practices, maintained by the IETF).
Although not defined in this document, APIPA addresses could be configured on Azure VPN gateways for private cloud connections. This made me want to understand what these addresses were and how they differed from the private address ranges I already knew.

## __What is APIPA?__
APIPA is an acronym for Automatic Private IP Addressing. It is a feature that enables devices on a LAN to automatically assign themselves an IP address for communication with other devices on the same LAN when they are unable to reach a DHCP server.
Devices using APIPA receive an IP address from the range 169.254.0.0/16.

## __History of APIPA__
In the early days of IPv4, the Internet Engineering Task Force (IETF) reserved the IPv4 address block 169.254.0.0/16 (169.254.0.0–169.254.255.255) for link-local addressing.

A link-local address is used for communication within a single logical division of a network, or within the broadcast domain to which the host is connected.
Later, Microsoft used this address range to implement Automatic Private IP Addressing in the Windows operating system, first appearing in Windows 98.

## __How APIPA works__
When the DHCP process fails, Windows automatically assigns an IP address from the APIPA address range: 
169.254.0.1 to 169.254.254.255.

Using the Address Resolution Protocol (ARP), the client verifies that the selected APIPA address is unique on the local network before using it.

## __Why use APIPA?__
APIPA is commonly used in home networks and small office environments, particularly where DHCP servers are unavailable or where administrators want to avoid the overhead of setting up and maintaining a DHCP server.
It provides a quick and efficient way for devices to retain basic network connectivity.

## __Difference between APIPA and Private IP address ranges__
RFC 1918 defines private IPv4 address ranges, while APIPA behavior is specified separately for link-local addressing.

One major difference between APIPA and private IP address ranges is scope:
APIPA addresses can only be used within a single broadcast domain and cannot span across multiple broadcast domains. Since APIPA relies on ARP for address conflict detection, there is no mechanism for these messages to traverse routers.
Private IP addresses, however, can be routed across broadcast domains when properly configured.


