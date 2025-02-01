# AS214514.net

AS214514 is the personal, IPv6-only ASN of <a href="mailto:henry@henryclarke.uk">Henry Clarke</a>, a network engineer in the UK. The ASN is used for both learning about BGP/routing on the internet, and personal projects.

## Setup
AS214514 is currently setup on multiple VPS', two in London (Vultr and iFog) and one in New York (Vultr), these Debian VPS' run Bird and advertise the IPv6 range assigned to AS214514 (2a0a:79c0:600::/44). 

AS214514 performs RPKI filtering (using [Routinator](https://github.com/NLnetLabs/routinator), and drops all RPKI invalid prefixes, along with other standard filtering best practices from [NLNOG](https://bgpfilterguide.nlnog.net/) including dropping BOGON prefixes & ASNs, along with only accepting routes with a prefix shorter than /48.

## Peering

AS214514 is a member of FogIXP and peers with both of the FogIXP route servers. AS214514 connects to FogIXP in London.

If you are not a member of FogIXP but would like to peer with AS214514 (personal ASN's welcome!), then peering is available over a GRE tunnel, please email <peering@as214514.net> and we can establish this. AS214514 has an open peering policy, with no restrictions on its peer ASNs.

AS214514 will advertise to you [AS214514:AS-HENRYCLARKE](https://apps.db.ripe.net/db-web-ui/lookup?source=ripe&key=AS214514%3AAS-HENRYCLARKE&type=as-set).

Please ensure that you publish your own AS-SET, setup RPKI for your prefixes, and keep your PeeringDB entry up to date.

## Anycast
AS214514 has an anycast deployment, using nodes in both London, UK and New York, USA to advertise the AS214514 anycast prefix of 2a0a:79c0:60f::/48. 

This is used to serve the reverse DNS zone of AS214514's IPv6 allocation (2a0a:79c0:600::/44, `0.6.0.0.c.9.7.a.0.a.2.ip6.arpa.`). 

Additionally, each anycast node hosts a webserver which informs you which of the anycast nodes you were directed to: [https://anycast.as214514.net](https://anycast.as214514.net), it is IPv6-only so will only work if you have an IPv6 address. However, as part of the DNS deployment, each server also identifies itself in a TXT record published under `anycast.as214514.net`, if you don't have an IPv6 address, your recursive DNS server should so if you can't visit the website to check which anycast node you are 'closest' to, the DNS option should still give you an answer.

```
$ dig +short TXT anycast.as214514.net
"Served by AS214514 anycast infrastructure in London, UK (gblon-r1)"
```

## BGP Communities
BGP communities used by AS214514 that are applied to prefixes on export from AS214514 can be found on [bgp.tools](https://bgp.tools/communities/214514).

These communities are used recripiocally, in that (for example) a prefix tagged with a location origin community (such as `(214514, 0, 400)`) means that the prefix was either advertised by AS214514 from London, or learnt by AS214514 in London. Likewise, prefixes with the community `(214514, 0, 105)` are either those advertise by AS214514 to an IXP route server, or learnt by AS214514 from an IXP route server.

## AS214514 Changelog

Changes to AS214514 infrastructure that are visible to the outside world:
- 16-07-2024: AS214514 is assigned to Henry Clarke.
- 16-07-2024: AS214514 starts advertising the IPv6 subnet assigned from a Vultr VPS in London
- 6-12-2024: AS214514 starts doing anycast, and deploys a router on Vultr in New York, with 2a0a:79c0:60f::/48 being the Anycast prefix used.
- 7-12-2024: AS214514 starts serving the reverse DNS zone for its IPv6 allocation and PTR records within 2a0a:79c0:600::/44 now have answers.
- 6-1-2025: AS214514 deploys another anycast VPS, this time on iFog in London.
- 12-1-2025: AS214514 joins FogIXP (using above anycast node), and starts peering with the route servers.
- 23-1-2025: `gblon-r1` (Vultr) and `gblon-r2` (iFog) start using `conntrackd` to share iptables state, and as a result `gblon-r2` starts also advertising the /44 summary route, meaning that either router is used for traffic towards the internet from Henry's home network, adding additional resiliency.
- 1-2-2025: Geofeed added to inet6num object per RFC8805/RFC9092, available at: https://as214514.net/geofeed.csv
  
### Contact
To contact myself (Henry), please use: <a href="mailto:henry@henryclarke.uk">henry@henryclarke.uk</a>

To get in contact regarding AS214514, please use: <a href="mailto:noc@as214514.net">noc@as214514.net</a>
