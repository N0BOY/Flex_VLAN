# FlexRadio Remote Access via Layer 2 VPN Bridging using OpenWRT+ZeroTier
## What-is?

This article provides a solution to remote access the FlexRadio when SmartLink is restricted while the internet provider is using CGNAT (StarLink, Mobile Hotspot) or the internet is under strict Firewall rules (school/company network).

Because of the network scalability, data security, and routing efficiency, most VPNs virtualize the Network Layer (Layer 3) that routes the IP packets over a server backbone. In L3 VPN, each network side is on a different subnet. Devices on the same VPN can connect to but not discover each other.

Therefore, when using L3 VPN bridging, the SmartSDR client can only connect to the FlexRadio via fixed IP or subnet scanning (when using macOS or iOS) but not under device discovery mode (when using Windows or Maestro panel).

Alternatively, Layer 2 VPN virtualizes the Datalink Layer. Network nodes at geographically separate locations can appear as operating within the same physical local connection or Local Area Network (LAN).

By using L2 VPN, Windows SmartSDR and Maestro can discover the FlexRadio from the remote site as "local radio."

In a previous post, [Michael Walker VA3MW wrote a CGNAT workaround](https://helpdesk.flexradio.com/hc/en-us/articles/4414672618267-Remote-Operation-Working-around-CGNAT-is-it-possible-) that utilize softEther enabled Windows PCs and Azure Cloud to set up an L2 VPN link between the FlexRadio and the SmartSDR client.

The following discussion shows another approach using an OpenWRT router installed with ZeroTier VPN. In such a setup, instead of using a PC, the OpenWRT router acts as a routed Access Point (AP) that bridges the LAN and VPN into one Virtual LAN (VLAN).

> Note: In this article, "router" and "AP" are interchangeable.

**Hardware - OpenWRT device**

![](media/16523981463869/download.png)
* Cost-efficient: $30-70 for [OpenWRT compatible device](https://openwrt.org/toh/start)
* Easy-to-scale: add more APs to expand the VLAN

**Software - ZeroTier VPN**

![](media/16523981463869/16526144193805.jpg)
* Multi-platform: Windows/macOS/Linux/iOS/Android
* Peer-to-peer VPN with Software-defined Wide Area Network (SD-WAN)
* Emulates L2 with multipath, multicast, and bridging
* 256-bit end-to-end encryption

## How-to? 

(## What-is?

This article provides a solution to remote access the FlexRadio when SmartLink is restricted while the internet provider is using CGNAT (StarLink, Mobile Hotspot) or the internet is under strict Firewall rules (school/company network).

Because of the network scalability, data security, and routing efficiency, most VPNs virtualize the Network Layer (Layer 3) that routes the IP packets over a server backbone. In L3 VPN, each network side is on a different subnet. Devices on the same VPN can connect to but not discover each other.

Therefore, when using L3 VPN bridging, the SmartSDR client can only connect to the FlexRadio via fixed IP or subnet scanning (when using macOS or iOS) but not under device discovery mode (when using Windows or Maestro panel).

Alternatively, Layer 2 VPN virtualizes the Datalink Layer. Network nodes at geographically separate locations can appear as operating within the same physical local connection or Local Area Network (LAN).

By using L2 VPN, Windows SmartSDR and Maestro can discover the FlexRadio from the remote site as "local radio."

In a previous post, [Michael Walker VA3MW wrote a CGNAT workaround](https://helpdesk.flexradio.com/hc/en-us/articles/4414672618267-Remote-Operation-Working-around-CGNAT-is-it-possible-) that utilize softEther enabled Windows PCs and Azure Cloud to set up an L2 VPN link between the FlexRadio and the SmartSDR client.

The following discussion shows another approach using an OpenWRT router installed with ZeroTier VPN. In such a setup, instead of using a PC, the OpenWRT router acts as a routed Access Point (AP) that bridges the LAN and VPN into one Virtual LAN (VLAN).

> Note: In this article, "router" and "AP" are interchangeable.

**Hardware - OpenWRT device**

![](media/16523981463869/download.png)
* Cost-efficient: $30-70 for [OpenWRT compatible device](https://openwrt.org/toh/start)
* Easy-to-scale: add more APs to expand the VLAN

**Software - ZeroTier VPN**

![](media/16523981463869/16526144193805.jpg)
* Multi-platform: Windows/macOS/Linux/iOS/Android
* Peer-to-peer VPN with Software-defined Wide Area Network (SD-WAN)
* Emulates L2 with multipath, multicast, and bridging
* 256-bit end-to-end encryption

## How-to? 

(Synthesising more details...)
