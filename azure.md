# Azure

Check if virtual network has a `dnsServers` configured:
```
export VNET=`az network vnet list --subscription $(az account list --query "[].id" -o tsv) --query "[].name" -o tsv` && \
export VNET_RG=`az network vnet list --subscription $(az account list --query "[].id" -o tsv) --query "[].resourceGroup" -o tsv`

az network vnet show -g $VNET_RG -n $VNET --query "dhcpOptions.dnsServers" -o json

az network vnet show -g $VNET_RG -n $VNET --query "{Name:name,RG:resourceGroup,DNS:dhcpOptions.dnsServers}" -o json
```

Update a virtual network with the IP address of a DNS server:
```
export DNS=10.2.0.8
export VNET=`az network vnet list --subscription $(az account list --query "[].id" -o tsv) --query "[].name" -o tsv` && \
export VNET_RG=`az network vnet list --subscription $(az account list --query "[].id" -o tsv) --query "[].resourceGroup" -o tsv`

az network vnet update -g $VNET_RG -n $VNET --dns-servers $DNS
```

Check subnet in virtual network:
```
export VNET=`az network vnet list --subscription $(az account list --query "[].id" -o tsv) --query "[].name" -o tsv` && \
export VNET_RG=`az network vnet list --subscription $(az account list --query "[].id" -o tsv) --query "[].resourceGroup" -o tsv` && \
export SUBNET=`az network vnet subnet list -g $VNET_RG --vnet-name $VNET --query "[?contains(addressPrefix, '$(hostname -i | cut -b 1-10)')].name" -o tsv`

az network vnet subnet show -g $VNET_RG --vnet-name $VNET -n $SUBNET -o table
```
