# OSM descriptors which onboards srsLTE traffic simulators

## Clone the repository to get the descriptors

```bash
git clone https://github.com/gatici/lte_simulators.git
```

##  Onboard the descriptors

```bash
osm vnfpkg-create hackfest_magma-agw-enb_vnfd
osm nspkg-create hackfest_magma-agw-enb_nsd
```

## Onboard the network service

Vim-network-name is the subnet which is also used by your OSM machine.

```bash
osm ns-create --ns_name enb --nsd_name hackfest_magma-agw-enb_nsd --vim_account aws-site --config "{vld: [ {name: mgmt, vim-network-name: subnet-098c0d6260c1f0a95 }], additionalParamsForVnf: [{member-vnf-index: 'MagmaAGWsrsLTE', additionalParams: {bind_address_subnet: '192.168.32.0/19', mme_addr: '192.168.63.190', enb_mcc: '722', enb_mnc: '71'}}]}"
```

mme_addr: AGW eth1 ip address

bind_address_subnet: AGW and enodeb will communicate for S1 interface and GTP.

