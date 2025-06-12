#public  
### Goal

Ensure that homelab domains (*.homelab.lan) remain resolvable when connecting from outside the local network via an OpenVPN tunnel.

  

### Implementation Details

#### OpenVPN Server on the Router

• The router [[GL.iNet GL-MT6000]] runs an OpenVPN server. In the configuration, DNS can be pushed to clients:
```
push "dhcp-option DNS 10.8.0.1"
```

• In my case, this didn't work. Maybe because I didn't find the right config file, or because of modifications by GL.Inet. See 

  

#### Allowing DNS Queries from the VPN Subnet

• DNSMasq may initially refuse queries from 10.8.0.x (the VPN subnet). By setting:

```
uci set dhcp.@dnsmasq[0].localservice='0'
uci commit dhcp
/etc/init.d/dnsmasq restart
```

the router permits DNS lookups from VPN clients.

  

#### Client-Side Configuration

• If the server does not successfully push DNS, it is possible to add DNS directives on the client side:

```
dhcp-option DNS 10.8.0.1
```

  

• This instructs the client to use the homelab router as DNS while on VPN, preserving internal domain resolution.



### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

