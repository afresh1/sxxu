sxxu - Example network
======================

This is an example network for sxxu, I suppose it might work but I haven't
actually tested it fully.  I pulled from a mostly working setup and cleaned
it up, eventually I will setup a test network using these configs and verify
functionality but for now, know that they probably don't actually work.

The network is like this:
Internet networks are faked in the 10/8 network private nets are 192.168/16

- remote networks
  - public  (vr0)   10.0.66.12/24
  - private (vr1) 192.168.66.0/24
remote-router - private 192.168.66.1/24
 - remote net - 192.168.66.0/24 - dhcp

- internet - ( provided by you )

- local network
  - public  (carp0)   10.0.33.11/24 on em0
  - private (carp1) 192.168.33.1/24 on em1
  - dmz     (carp2) 192.168.34.1/24 on em2
carp-router1 - (em1) 192.168.33.11/24 - (em2) 192.168.34.11/24
carp-router2 - (em1) 192.168.33.12/24 - (em2) 192.168.34.12/24
| \
|  dmz - 192.168.34.0/24
|   \
\    web + mail + ns01 + ns02
 - internal net - 192.168.33.0/24 - dhcp for clients
