---
# Configurations
# black, white, league, beige, sky, simple, serif, night, moon, solarized
theme: night
# cube, page, concave, zoom, linear, fade, none, default
transition: slide
#  Syntax highlighting style https://highlightjs.org/static/demo/
highlight: monokai
backgroundTransition: zoom
progress: true
controls: true
hideAddressBar: true
# Editor settings
editor:
  fontSize: 14
  theme: monokai
---

## Packet Traveling

<img src="https://www.practicalnetworking.net/wp-content/uploads/2016/01/packtrav-series-title.gif" />

Inspired by <a href="https://www.practicalnetworking.net/series/packet-traveling/packet-traveling/">Packet Traveling</a> <br/>
JANUARY 28, 2016 Ed Harmoush

---

## OSI

<!-- .slide: data-auto-animate -->
<style>
  .box {
    display: flex;
    flex-direction: row;
    align-items: stretch;
    justify-content: space-between;
  }
  .osi,.osi-images {
    flex: 0 0 auto;
    display: flex;
    flex-direction: column;
  }
  .osi-images {
    flex: 1 1 auto;
  }
  .osi>div,.osi-images>div{
    display: flex;
    align-items: center;
    justify-content: center;
    flex: 0 0 60px;
    padding: 5px;
    border: 1px solid coral;
  }
  .osi>div {}
  .osi-images>div:first-child{
    flex: 0 0 184px;
    padding: 15px 5px;
  }
  .osi-images img {
    margin: 0;
    height: 60px;
    width: fit-content;
  }
</style>
<div data-id="box" class="box">
  <div data-id="osi" class="osi">
    <div>Layer 7 - Application</div>
    <div>Layer 6 - Presentation</div>
    <div>Layer 5 - Session</div>
    <div>Layer 4 – Transport</div>
    <div>Layer 3 – Network</div>
    <div>Layer 2 – Data Link</div>
    <div>Layer 1 – Physical</div>
  </div>
  <div data-id="osi-images" class="osi-images">
    <div>L5+</div>
    <div><img src="https://www.practicalnetworking.net/wp-content/uploads/2016/01/packtrav-layer-4-1024x555.png" alt=""></div>
    <div><img src="https://www.practicalnetworking.net/wp-content/uploads/2016/01/packtrav-router-300x179.png" alt=""></div>
    <div><img src="https://www.practicalnetworking.net/wp-content/uploads/2016/01/packtrav-nics-and-switches.png" alt=""></div>
    <div><img src="https://www.practicalnetworking.net/wp-content/uploads/2016/01/packtrav-physical-wires.png" alt=""></div>
  </div>
</div>
Note:
<em>Layer 1 – Physical</em>: 传送比特流：0 & 1。“Physical” — this layer was named in the 1970s，WiFi 也是第一层协议 <hr/>
<em>Layer 2 – Data Link</em>: 负责定位数据包的传输路径（发送者、接收者等）。如何定位？<br/>
Network Interface Card (NIC) <br/>
Media Access Control address, aka MAC address。由于经常被制造商烧进芯片，也叫 Burned In Address (BIA)<br/>
Switch: 交换机，用于扩展网络为子网提供更多接口，连接更多设备 <br>
数据链路层的首要功能是将数据包从一个 NIC 传送到另一个 NIC。或者换句话说：将数据包从一跳、一跳地传送下去。
<hr/>
<em>Layer 3 – Network</em>: 网络层 负责端到端的数据包传输，通过 Internet Protocol address, or the IP Address. 区分子网<br/>
Router: 路由器，跨网络通信必须使用路由器。<br/>
Layer 2 VS Layer 3：通过Mac地址 Layer 2 已经可以唯一定位一台终端，为什么还需要 Layer 3呢？<br>
Layer 2 uses <strong>MAC addresses</strong> and is responsible for packet delivery from <strong>hop to hop</strong>.<br>
Layer 3 uses <strong>IP addresses</strong> and is responsible for packet delivery from <strong>end to end</strong>.<br>
也就是说，Mac地址只负责一跳传输，一个数据包从发送终端到达接收终端往往需要多跳。
<a href="https://www.practicalnetworking.net/wp-content/uploads/2016/01/packtrav-l2-vs-l3.gif">查看图片</a>
<hr/>
<em>Layer 4 – Transport</em>: 传输层，用来区分不同的网络流。（快递举例，浏览器，音乐播放器，IM软件）一台终端同时接收和发送多份网络数据包，需要准确区分哪些包是由谁发出，或发送给谁的。<br/>
Port Numbers: Both TCP and UDP have 65,536 ports. Source IP + Port <==> Destination IP + Port 标识一个 unique application stream <br>
第二层 数据链路层 是 hop to hop <br>
第三层 网络层 是 end to end <br>
第四层 传输层 是 service to service <br>
<hr/>
<em>Layer 5 – 7</em>: L5-7 or L5+ ，网络数据被展示给用户之前的最后一步，我们今天暂不需要理解其中的差异，不影响我们理解今天的内容。主要用来规范应用程序数据格式。<hr/>
<em>封装和解封装</em>
<a href="https://www.practicalnetworking.net/wp-content/uploads/2016/01/packtrav-encap-decap.gif">查看图片</a>
Layer 4 添加：<strong>TCP header</strong><strong>Source and Destination port</strong>
Layer 3 添加：<strong>IP header</strong><strong>Source and Destination IP address</strong>
Layer 2 添加：<strong>Ethernet header</strong><strong>Source and Destination MAC address</strong>
<hr/>
---
<!-- .slide: data-auto-animate -->
<style>
  .tcp-ip {
    flex: 0 0 auto;
    display: flex;
    flex-direction: column;
  }
  .tcp-ip {
    flex: 1 1 auto;
  }
  .tcp-ip>div{
    display: flex;
    align-items: center;
    justify-content: center;
    flex: 0 0 60px;
    padding: 5px;
    border: 1px solid coral;
  }
  .osi>div {}
  .tcp-ip>div:first-child{
    flex: 0 0 184px;
    padding: 15px 5px;
  }
  .tcp-ip>div:last-child{
    flex: 0 0 122px;
    padding: 10px 5px;
  }
</style>
## OSI VS TCP/IP
<div data-id="box" class="box">
  <div data-id="osi" class="osi">
    <div>Layer 7 - Application</div>
    <div>Layer 6 - Presentation</div>
    <div>Layer 5 - Session</div>
    <div>Layer 4 – Transport</div>
    <div>Layer 3 – Network</div>
    <div>Layer 2 – Data Link</div>
    <div>Layer 1 – Physical</div>
  </div>
  <div data-id="tcp-ip" class="tcp-ip">
    <div>Application</div>
    <div>Transport</div>
    <div>Internet</div>
    <div>Network Access (link)</div>
  </div>
</div>
---
<!-- .slide: data-auto-animate -->
<style>
  .protocol {
    flex: 0 0 auto;
    display: flex;
    flex-direction: column;
    font-size: 14px;
    line-height: 1.5;
  }
  .protocol {
    flex: 1 1 auto;
  }
  .protocol>div{
    display: flex;
    align-items: center;
    justify-content: center;
    flex: 0 0 60px;
    padding: 5px;
    border: 1px solid coral;
  }
  .protocol>div:first-child{
    flex: 0 0 184px;
    padding: 15px 5px;
  }
</style>
## OSI VS TCP/IP
<div data-id="box" class="box">
  <div data-id="osi" class="osi">
    <div>Layer 7 - Application</div>
    <div>Layer 6 - Presentation</div>
    <div>Layer 5 - Session</div>
    <div>Layer 4 – Transport</div>
    <div>Layer 3 – Network</div>
    <div>Layer 2 – Data Link</div>
    <div>Layer 1 – Physical</div>
  </div>
  <div data-id="protocol" class="protocol">
    <div>HTTP | DNS | FTP | DHCP | SMTP | SSH | TELNET | RPC | SOAP </div>
    <div>TCP | UDP | TLS/SSL </div>
    <div>IP | ICMP（v6）| IPsec</div>
    <div>
      Wi-Fi(IEEE 802.11) | PPPoE | ARP | 以太网 | L2TP
    </div>
    <div>
      以太网 | 光纤 | 双绞线 | "猫" | 电线通信 | 同步光网络 | 同轴电缆
    </div>
  </div>
  <div data-id="tcp-ip" class="tcp-ip">
    <div>Application</div>
    <div>Transport</div>
    <div>Internet</div>
    <div>Network Access (link)</div>
  </div>
</div>

Note:
<em>Application</em>: DHCP（v6） | DNS | FTP | Gopher | HTTP（SPDY、HTTP/2） | IMAP4 | IRC | NNTP | XMPP | POP3 | SIP | SMTP | SNMP | SSH | TELNET | RPC | RTCP | RTP | RTSP | SDP | SOAP | GTP | STUN | NTP | SSDP <hr/>
<em>Transport</em>: TCP（T/TCP · Fast Open） | UDP | DCCP | SCTP | RSVP | PPTP | TLS/SSL <hr/>
<em>Internet</em>: IP（v4·v6） | ICMP（v6） | IGMP | IS-IS | IPsec | BGP | RIP | OSPF | RARP <hr/>
<em>Data Link</em>: Wi-Fi（IEEE 802.11） | ARP | WiMAX（IEEE 802.16） | ATM | DTM | 令牌环 | 以太网 | FDDI | 帧中继 | GPRS | EV-DO | HSPA | HDLC | PPP | PPPoE | L2TP | ISDN | SPB | STP <hr/>
<em>Physical</em>: 以太网 | 调制解调器 | 电力线通信 | 同步光网络 | G.709 | 光导纤维 | 同轴电缆 | 双绞线
---
## Key Players

* Host
* Network
* Switch
* Router
* ARP(Address Resolution Protocol)

Note: 
<em>Host</em>: PC, laptop, mobile phones, smart TVs, smart watches, certain cars, and even some refrigerators <br/>
Client or the Server
<hr/>
<em>Network</em>: A Network is simply two or more connected devices<br>
typically grouped together by <strong>similar purposes</strong> or <strong>physical location</strong>. 
A network can take many different forms, for example: <br>
* A group of PCs in a classroom
* Home network
* Public Wifi
* Company -> multiple networks
* Entire Internet
<hr/>
<em>Switch</em>: Inside Network, Layer 2, MAC Address table, ports, floods the frame out each switch port <br>
<a href="https://www.practicalnetworking.net/wp-content/uploads/2016/01/packtrav-switch-l2-1024x174.png" target="_blank">查看图片</a>
<hr/>
<em>Router</em>: Between networks, Layer 3, Routing Table(AKA Routes), multiple ways to fill Routing Table<br />
<a href="https://www.practicalnetworking.net/wp-content/uploads/2016/01/packtrav-router-l3-1024x213.png" target="_blank">查看图片</a>
<hr/>
<em>ARP</em>: Layer 2 - MAC Address, Layer 3 - IP Address, bridges these two addressing schemes.<br/>
当两台终端需要通信时，他们必须知道彼此的IP地址（人工/DNS 无所谓），但是他们并不知道彼此的Mac地址。<br>
ARP Table: a mapping of IP addresses to correlating MAC addresses。Owned by L3<br>
<a href="https://www.practicalnetworking.net/wp-content/uploads/2016/01/packtrav-arp-l2-l3-1024x256.png" target="_blank">查看图片</a>

<hr/>
---
## Host to Host Communication

---
## Host to Host through a Switch

---
## Host to Host through a Router

---
## Summary

---
