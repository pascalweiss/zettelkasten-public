#public

### Overview
1. **No Client Configuration**: Every device in the network can access homelab services (homelab.lan and subdomains) without manual edits (like /etc/hosts or manually entering DNS servers).

2. **Dynamic Subdomains**: Subdomains such as `<sub>.homelab.lan` or `<MR-23>.<sub>.homelab.lan` can dynamically be applied, without requiring additional DNS entries for each new service or test deployment.

  
### Implementation Details

#### DNSMasq on the Router

• A GL-MT6000 router (running a GL.iNet-customized OpenWrt) provides DNS. Under **DHCP and DNS → General Settings**, a rule is defined:

```
/homelab.lan/192.168.8.200
```

• This wildcard mapping means all requests for *.homelab.lan resolve to the homelab server at 192.168.8.200.


#### Automatic DNS Assignment

• The router’s DHCP automatically sets itself (192.168.8.1) as the DNS server for LAN clients. No need for manual configuration on each device.

• Initially, DNSMasq rejected external queries by default if localservice=1. Changing it to 0 allowed DNS to function network-wide:

```
uci set dhcp.@dnsmasq[0].localservice='0'
uci commit dhcp
/etc/init.d/dnsmasq restart
```

#### No Per-Device Changes

• Because devices on the LAN receive the router as their DNS by default, they can immediately resolve homelab.lan subdomains without extra edits.


#### Wildcard Subdomains for CI/CD

• With `/homelab.lan/192.168.8.200` in place, any subdomain of homelab.lan (e.g., `test.myapp.homelab.lan` or `mr-23.myapp.homelab.lan`) automatically points to the homelab server.

• A reverse proxy [[homelab - Ingress ]] on 192.168.8.200 inspects the incoming Host header and routes it to the appropriate container or application.

• This setup allows CI/CD pipelines to create new deployments and subdomains without modifying DNS rules on the router.


### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

