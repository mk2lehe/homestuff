# homestuff

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
