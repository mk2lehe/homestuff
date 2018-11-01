# homestuff

Upnp discovery:

http://www.upnp-hacks.org/upnp.html 

1. upnp discovery browser sends SSDP to 239.255.255.250:1900 on UDP
* works across subnets, tested with wireshark: ssdp && (ip.src == 192.168.2.106 && ip.addr == 239.255.255.250 ) where 192.168.2.106 is android phone running upnp browser
2. all upnp devices responds using udp unicast.
* works across subnets
3. port 80 works:
http://192.168.2.120/ajax/upnp/get_device_info
Somehow, network devices in win still don't work on different subnets


Source: http://divideoverflow.com/2014/08/reversing-spotify-connect/

Spotify connect devices advertises itself via Zeroconf (avahi-publish) as a local _spotify-connect._tcp service, which runs a simple HTTP service.

From a windows command prompt on wifi-laptop:

H:\>dns-sd -B _spotify-connect._tcp
Browsing for _spotify-connect._tcp
Timestamp     A/R Flags if Domain                    Service Type              Instance Name
18:46:46.512  Add     2  9 local.                    _spotify-connect._tcp.    VardagsrumHEOS

At this point, at least two devices are missing. 
"Service Browser" on wifi-android gives the same result.
spotify on wifi-laptop can see all devices(!).

? Spotify on laptop does not use dns-sd as service discovery browser? 

? Either 

enabling mdns reflector makes it possible to 
H:>ping -4 ubnt.local
https://www.reddit.com/r/Ubiquiti/comments/6wxdhw/edgerouter_local_hostname/ 
It also seems to help for discovery (?)

4. Enable igmp-proxy (config tree) with switch0(LAN) as upstram and switch0.55(VLAN) downstream makes controller app (LAN) find VLAN devices
