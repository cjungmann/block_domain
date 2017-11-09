# BLOCK_DOMAIN

I wrote this script to make it easier to use _cron_ to block
or unblock certain websites on my home firewall.

I've concluded that it is easier to restrict my children's
internet usage by blocking sites with _iptables_ than by using
DHCP to deny internet access by MAC address.

As I write this README, I'm not sure if this will work on my
firewall, but I do know that it works on my local computer.

# How it Works

1. The program uses _host_ to get one or more ip addresses that
   are associated with the domain name.

2. For each ip address found by _host_, this program will call
   _whois_ to get a range of ip addresses or a CIDR.

3. Before writing a rule, it checks if the rule already exists.
   If so, it ignores the add request.

# Issues

## Netflix

Netflix seems to have so many ip addresses that _host_ returns
a different list at different invocations.  Thus, this script
may not be suitable for blocking Netflix.

It's possible that a tweak might be possible to repeatly call
_host_ to exhaust the list, but that seems unworkable.  There may
also be another utility I'm not yet aware of that will do a better
job finding ip addresses.