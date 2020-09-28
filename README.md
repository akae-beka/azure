# azure

<!-- TOC -->

- [Network](#Network)
    - [private-endpoint](#private-endpoint)
    - [private-dns](#private-dns)
    - [vnet](#vnet)
    - [subnet](#subnet)
    - [nic](#nic)
- [Storage](#Storage)
    - [storage-account](#storage-account)
    
    
# Network

## private-endpoint
List private-endpoint:
```
az network private-endpoint list -g $RESOURCE_GROUP -o table
```
Show private-endpoint:
```
az network private-endpoint show -g $RESOURCE_GROUP -n MyPrivateEndpoint -o `table|yaml|json`
```

## private-dns
List private-dns zone:
```
az network private-dns zone list -g $RESOURCE_GROUP -o table
```
List private-dns record-set:
```
az network private-dns record-set a list -g $RESOURCE_GROUP -z <private-dns-zone>
```
Create private-dns zone:
```
az network private-dns zone create -g $RESOURCE_GROUP -n <private-zone-name>
```
## vnet

## subnet

## nic
List network interfaces:
```
az network nic list -g $RESOURCE_GROUP -o table
```
Get the details of a network interface:
```
az network nic show -g $RESOURCE_GROUP -n <nic-name> -o `table|yaml|json`
```

# Storage

## storage-account
List storage account:
```
 az storage account list -g $RESOURCE_GROUP -o table
```
