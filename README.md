# AS214514.net

AS214514 is the personal ASN of Henry Clarke, a network engineer in the UK. The ASN is used for both learning about BGP/routing on the internet, and personal projects.

## Setup
AS214514 is currently setup on a Vultr instance running in London, running Bird to establish BGP to Vultr (AS20473), and advertising the IPv6 range assigned to AS214514 (2a0a:79c0:600::/44). 

AS214514 performs RPKI filtering (using [Routinator](https://github.com/NLnetLabs/routinator), and drops all RPKI invalid prefixes, along with other standard filtering best practices from [NLNOG](https://bgpfilterguide.nlnog.net/) including dropping BOGON prefixes & ASNs, along with only accepting routes with a prefix shorter than /48.

## Peering
If you are also running your own personal ASN, and would like to peer over a GRE tunnel, then please email <peering@as214514.net> and we can establish this. AS214514 has no physical presence in any data center, so peering is only available over a GRE tunnel to the instance running on Vultr.

AS214514 will advertise to you [AS214514:AS-HENRYCLARKE](https://apps.db.ripe.net/db-web-ui/lookup?source=ripe&key=AS214514%3AAS-HENRYCLARKE&type=as-set).

Please ensure that you publish your own AS-SET and preferably setup RPKI for your prefixes.
