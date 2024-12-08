# AS214514.net

AS214514 is the personal, IPv6-only ASN of <a href="mailto:henry@henryclarke.uk">Henry Clarke</a>, a network engineer in the UK. The ASN is used for both learning about BGP/routing on the internet, and personal projects.

## Setup
AS214514 is currently setup on a Vultr instance running in London, running Bird to establish BGP to Vultr (AS20473), and advertising the IPv6 range assigned to AS214514 (2a0a:79c0:600::/44). 

AS214514 performs RPKI filtering (using [Routinator](https://github.com/NLnetLabs/routinator), and drops all RPKI invalid prefixes, along with other standard filtering best practices from [NLNOG](https://bgpfilterguide.nlnog.net/) including dropping BOGON prefixes & ASNs, along with only accepting routes with a prefix shorter than /48.

## Peering
If you are also running your own personal ASN, and would like to peer over a GRE tunnel, then please email <peering@as214514.net> and we can establish this. AS214514 has no physical presence in any data center, so peering is only available over a GRE tunnel to the instance running on Vultr.

AS214514 will advertise to you [AS214514:AS-HENRYCLARKE](https://apps.db.ripe.net/db-web-ui/lookup?source=ripe&key=AS214514%3AAS-HENRYCLARKE&type=as-set).

Please ensure that you publish your own AS-SET and preferably setup RPKI for your prefixes.

## Anycast
AS214514 has an anycast deployment, using nodes in both London, UK and New York, USA to advertise the AS214514 anycast prefix of 2a0a:79c0:60f::/48. 

This is used to serve the reverse DNS zone of AS214514's IPv6 allocation (2a0a:79c0:600::/44, `0.6.0.0.c.9.7.a.0.a.2.ip6.arpa.`). 

Additionally, each anycast node hosts a webserver which informs you which of the anycast nodes you were directed to. Check it out here: [https://anycast.as214514.net](https://anycast.as214514.net), it is IPv6-only so will only work if you have an IPv6 address. However, as part of the DNS deployment, each server also identifies itself in a TXT record published under `anycast.as214514.net`, if you don't have an IPv6 address, your recursive DNS server should so if you can't visit the website to check which anycast node you are 'closest' to, the DNS option should still give you an answer.

```
$ dig +short TXT anycast.as214514.net
"Served by AS214514 anycast infrastructure in London, UK (gblon-r1)"
```

## BGP Communities
BGP communities used by AS214514 that are applied to prefixes on export from AS214514 can be found on [bgp.tools](https://bgp.tools/communities/214514).

### Contact
To contact myself (Henry), please use: <a href="mailto:henry@henryclarke.uk">henry@henryclarke.uk</a>

To get in contact regarding AS214514, please use: <a href="mailto:noc@as214514.net">noc@as214514.net</a>
