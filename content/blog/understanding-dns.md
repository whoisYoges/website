+++
title = "Understanding DNS"
date = "2023-02-28"
page_template = "page.html"
description = "Understanding about dns clustering and how it works?"
[extra]
gotoTop = true
shareable = true
comparison = true
+++
Let try to understand about DNS as ddep as we can?
<!-- more -->

## The concept of DNS
Before diving deep into DNS, we need to understand some of the following basic concepts and terminologies.

### IP Address
Every device on the internet has a unique Internet Protocol (IP) address. An IP address is a numerical label assigned to each device connected to a computer network that uses the Internet Protocol for communication.  
For e.g IP address of github.com is 20.205.243.166.

### DNS
The Domain Name System (DNS) is the phonebook of the Internet which is used to translate human-readable domain names into it's ip addresses, such as github.com into 20.205.243.166. DNS is a critical part of the internet infrastructure, and it allows users to access websites and other online services using easy-to-remember names instead of IP addresses.

### DNS Server
A DNS server is a computer server that contains a database of public IP addresses and their associated hostnames (domain names) which is used to translate domain names into IP addresses, making it possible for DNS clients to reach the origin server.  

*Note: You may see a DNS server referred to by other names, such as a name server or nameserver, and a domain name system server.*

DNS servers use specialized software called DNS server software or DNS resolver software to manage and resolve domain name requests. Some popular DNS server software includes:

1. BIND (Berkeley Internet Name Domain): This is the most widely used DNS server software, developed by the Internet Systems Consortium (ISC).
2. Microsoft DNS: This DNS server software is built into Windows Server operating systems.
3. PowerDNS: A high-performance, reliable, and scalable DNS server software that supports various backends and features.
4. Unbound: A secure and modern recursive DNS resolver that provides high performance and customization.
5. Knot DNS: A lightweight, high-performance DNS server software designed for modern architectures.
6. NSD (Name Server Daemon): A fast, simple, and secure authoritative-only DNS server software.
7. Dnsmasq: A lightweight and easy-to-configure DNS server software that also provides DHCP and TFTP services.

These software packages provide a range of features, including caching, forwarding, security, and DNSSEC (DNS Security Extensions) support. A complete comparison between DNS server softwares can be found [here](https://en.wikipedia.org/wiki/Comparison_of_DNS_server_software).

<table>
    <caption>Some Free & Public DNS Servers</caption>
    <thead>
    <tr>
        <th scope="col">Provider</th>
        <th scope="col">Primary DNS</th>
        <th scope="col">Secondary DNS</th>
    </tr>
    </thead>
    <tbody>
    <tr>
        <td data-label="Provider">Google</a></td>
        <td data-label="Primary DNS"><span>8.8.8.8</span></td>
        <td data-label="Default search engine"><span>8.8.4.4</span></td>
    </tr>
    <tr>
        <td data-label="Provider">Control D</a></td>
        <td data-label="Primary DNS"><span>76.76.2.0</span></td>
        <td data-label="Default search engine"><span>76.76.10.0</span></td>
    </tr>
    <tr>
        <td data-label="Provider">Quad9</a></td>
        <td data-label="Primary DNS"><span>9.9.9.9</span></td>
        <td data-label="Default search engine"><span>149.112.112.112</span></td>
    </tr>	
    <tr>
        <td data-label="Provider">OpenDNS Home</a></td>
        <td data-label="Primary DNS"><span>208.67.222.222</span></td>
        <td data-label="Default search engine"><span>208.67.220.220</span></td>
    </tr>
    <tr>
        <td data-label="Provider">Cloudflare</a></td>
        <td data-label="Primary DNS"><span>1.1.1.1</span></td>
        <td data-label="Default search engine"><span>1.0.0.1</span></td>
    </tr>
    <tr>
        <td data-label="Provider">CleanBrowsing</a></td>
        <td data-label="Primary DNS"><span>185.228.168.9</span></td>
        <td data-label="Default search engine"><span>185.228.169.9</span></td>
    </tr>
    <tr>
        <td data-label="Provider">Alternate DNS</a></td>
        <td data-label="Primary DNS"><span>76.76.19.19</span></td>
        <td data-label="Default search engine"><span>76.223.122.150</span></td>
    </tr>	 	
    <tr>
        <td data-label="Provider">AdGuard DNS</a></td>
        <td data-label="Primary DNS"><span>94.140.14.14</span></td>
        <td data-label="Default search engine"><span>94.140.15.15</span></td>
    </tr>
    </tbody>
</table>

These different DNS servers communicate with each other using special protocols known as DNS protocol which is a standardized protocol for resolving domain names to IP addresses and vice versa.  
DNS servers typically communicate with each other using a combination of two protocols: the Transmission Control Protocol (TCP) and the User Datagram Protocol (UDP).  
DNS queries and responses are usually sent using UDP, which is faster and more efficient for simple requests. However, if the response is too large for a single UDP packet, or if the query requires a more reliable connection, DNS servers will use TCP instead.

DNS servers also use a variety of mechanisms to discover and communicate with each other, including recursive queries, zone transfers, and forwarding. These mechanisms allow DNS servers to share information and collaborate to provide reliable and accurate name resolution for clients.

#### How DNS Servers Resolve a DNS Query

When you enter a website address into your browsers address bar, a DNS server goes to work to find the address that you want to visit. It does this by sending a DNS query to several servers, each of which translates a different part of the domain name you entered. The different servers queried are:

- A DNS Recursor/Resolver: The recursor can be thought of as a librarian who is asked to go find a particular book somewhere in a library. The DNS recursor is a server designed to receive queries from client machines through applications such as web browsers. Typically the recursor is then responsible for making additional requests in order to satisfy the client’s DNS query.

- A Root Nameserver: The root server is the first step in translating (resolving) human readable host names into IP addresses. It can be thought of like an index in a library that points to different racks of books - typically it serves as a reference to other more specific locations.

- A TLD Nameserver: The top level domain server (TLD) can be thought of as a specific rack of books in a library. This nameserver is the next step in the search for a specific IP address, and it hosts the last portion of a hostname (In example.com, the TLD server is “com”).

- An Authoritative Nameserver: This final nameserver can be thought of as a dictionary on a rack of books, in which a specific name can be translated into its definition. The authoritative nameserver is the last stop in the nameserver query. If the authoritative name server has access to the requested record, it will return the IP address for the requested hostname back to the DNS Recursor (the librarian) that made the initial request.

Once the IP address is returned, the website you wanted to visit is then displayed in your web browser.

![How-DNS-Servers-Resolve-a-DNS-Query](/assets/images/blogs/concept-of-dns/DNS_servers.jpg)


### Anycast
Anycast is a network addressing and routing methodology that allows multiple devices to share the same IP address. When a client sends a request to an anycast IP address, the request is routed to a variety of different locations or *nodes* and responed from the nearest active node.

![Anycast](/assets/images/blogs/concept-of-dns/anycast.jpg)

### Unicast
It uses a one-to-one association, where each destination address is uniquely identified as a single receiver endpoint. Traditional DNS deployments are configured with unicast addresses.

![Unicast](/assets/images/blogs/concept-of-dns/unicast.png)

### Multicast
It uses a one-to-unique many association, where datagrams are routed from a single sender to multiple selected endpoints in a single transmission, using a multicast group address. A common use of multicast is streaming audio, where the audio is published via multicast addressing and clients pick up the routed stream as a channel.

![Multicast](/assets/images/blogs/concept-of-dns/multicast.png)

### Broadcast
It uses a one-to-many association, where datagrams are routed from a single sender to all other connected endpoints in a single transmission, using a broadcast address. The network automatically replicates datagrams as needed for all network segments (links) that contain an eligible receiver.

![Broadcast](/assets/images/blogs/concept-of-dns/broadcast.png)

### Why Anycast?
- Performance improvement
- Service reliability
- Load balancing
- Reduces impact of DoS attacks

## Anycast DNS
Anycast DNS is a method of distributing DNS (Domain Name System) queries across multiple servers located in different geographic locations. This is done by configuring multiple servers with the same IP address, allowing clients to connect to the nearest available server, thus reducing latency and improving response times.

Suppose you have a website hosted on multiple servers located in different regions of the world, and you want to ensure that clients are always connected to the nearest available server for the best performance. You can achieve this by configuring each server with the same anycast IP address.

When a client sends a DNS query to resolve your website's domain name, the query is sent to the nearest anycast DNS server, based on the client's network topology. The anycast routing protocol then delivers the query to the nearest server that is advertising that IP address.

For example, suppose you have three servers located in North America, Europe, and Asia, respectively. Each server is configured with the same anycast IP address, say 192.0.2.1. When a client in North America sends a DNS query to resolve your website's domain name, the query is sent to the anycast DNS server located in North America. The anycast routing protocol then delivers the query to the server in North America that is advertising the 192.0.2.1 IP address. Similarly, when a client in Asia sends a DNS query, the query is sent to the anycast DNS server in Asia, which then delivers the query to the server in Asia that is advertising the 192.0.2.1 IP address.

![Why-Anycast](/assets/images/blogs/concept-of-dns/why-anycast.jpg)

Anycast DNS is widely used by large websites, content delivery networks (CDNs), and cloud providers to distribute their services across multiple regions and ensure high availability and performance. It is also commonly used in DDoS (Distributed Denial of Service) mitigation, as it allows traffic to be spread across multiple servers, making it harder for attackers to overwhelm a single server.

## DNS Cluster
A DNS cluster is a group of DNS servers that work together to provide high availability and redundancy for a domain's DNS records. The cluster consists of multiple servers that are located in different geographic locations and communicate with each other to ensure that they have the same DNS records.

When a user requests to access a domain, the DNS cluster will respond by directing the request to the closest server, which will then provide the user with the IP address associated with the domain. This ensures that users receive a fast and reliable response time, even if one of the servers in the cluster goes down.

Here's an example of how a DNS cluster might work:

Let's say there is a website called example.com that is hosted on a web server in the United States. The website is popular and receives visitors from all over the world. To ensure that the website can be accessed quickly and reliably by users in different geographic locations, the website's owner sets up a DNS cluster consisting of three servers: one in the United States, one in Europe, and one in Asia.

When a user in the United States types example.com into their web browser, their DNS request will be directed to the server in the United States. If the server is working properly, it will respond with the IP address of the web server hosting example.com, and the user will be able to access the website.

If the server in the United States goes down, however, the DNS request will be directed to the next closest server, which is the server in Europe. This server will provide the user with the IP address of the web server hosting example.com, and the user will still be able to access the website, although the response time may be slightly slower due to the increased distance.

If both the servers in the United States and Europe are down, the DNS request will be directed to the server in Asia, which will provide the user with the IP address of the web server hosting example.com.

In this way, the DNS cluster ensures that users can always access the website, regardless of which server is working or where the user is located.

## Differences in Anycast DNS and DNS Cluster
1. Routing Method: Anycast DNS uses anycast routing, which routes traffic to the nearest available DNS server based on network conditions, while DNS clustering uses a load balancing mechanism to distribute traffic across multiple servers.

2. IP Addressing: In anycast DNS, multiple servers share the same IP address, while in DNS clustering, each server has its own unique IP address.

3. Network Configuration: Anycast DNS requires specialized network configurations and routing protocols to work properly, while DNS clustering can be set up using standard load balancing mechanisms and network equipment.

4. Scalability: Anycast DNS is highly scalable and can easily handle large volumes of traffic by adding more servers to the anycast network, while DNS clustering can also be scaled up by adding more servers to the cluster.

5. Service Level Agreement (SLA): Anycast DNS typically offers a higher SLA than DNS clustering because it provides better resilience against network outages and hardware failures.

## cPanel
cPanel is a popular web hosting control panel that allows website owners to manage various aspects of their hosting account.

## cPanel Only DNS
cPanel's DNS management interface allows users to manage their DNS records without the need for advanced technical knowledge. One of the options available in cPanel's DNS management interface is the ability to use cPanel only DNS.

cPanel only DNS means that all DNS records for a domain are managed solely through cPanel's DNS management interface. This means that cPanel is responsible for hosting and serving the DNS records for the domain, rather than the DNS being hosted by an external DNS provider.

When a user chooses to use cPanel only DNS, cPanel creates a DNS zone for the domain and automatically generates the necessary DNS records. The user can then modify or add to these records as needed using cPanel's DNS management interface.

### Benefits of cPanel only DNS
One benefit of using cPanel only DNS is that it can simplify DNS management for users who are not familiar with advanced DNS concepts. It also allows users to manage all aspects of their hosting account from within cPanel, rather than having to use separate interfaces for DNS management and other hosting functions.

### Downsides of cPanel only DNS
However, there are also some potential downsides to using cPanel only DNS. One is that it may limit flexibility and customization options for users who need more advanced DNS management capabilities. Additionally, if there are issues with cPanel's DNS service, it can affect the availability and performance of the domain's website and email services.

## Anycast VPS
Anycast VPS is a type of virtual private server (VPS) that uses anycast networking to improve its performance and availability. Anycast VPS hosting is based on the anycast routing technology that allows multiple servers to share the same IP address, making it possible for users to access the same service from different locations.

An anycast VPS provider typically operates multiple data centers located in different regions or countries, and assigns the same IP address to each of the VPS instances hosted in these data centers. When a user sends a request to the anycast IP address, the network infrastructure routes the traffic to the nearest data center based on network topology, latency, and other factors.

This approach provides several benefits for VPS hosting, including:

1. Improved performance: Anycast VPS hosting can help reduce latency and increase the speed of access to VPS instances by directing traffic to the nearest data center.

2. Increased availability: By distributing VPS instances across multiple data centers, anycast VPS hosting can provide better resilience and availability in case of hardware failures, network outages, or other disruptions.

3. Scalability: Anycast VPS providers can easily add more capacity by deploying additional VPS instances in different data centers as demand grows.

Overall, anycast VPS hosting can be an effective way to enhance the performance and reliability of VPS hosting, especially for applications that require low latency and high availability.
