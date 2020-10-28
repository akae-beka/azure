# azure

<!-- TOC -->

- [Subscriptions](#Subscriptions)
- [Login](#login)
- [Roles](#roles)
- [Network](#Network)
    - [private-endpoint](#private-endpoint)
    - [private-dns zone](#private-dns-zone)
    - [private-dns record](#private-dns-record)
    - [vnet](#vnet)
    - [subnet](#subnet)
    - [nic](#nic)
- [VM](#VM)
- [Image](#Image)
- [Storage](#Storage)
    - [storage-account](#storage-account)

# Subscriptions
Get the details of a subscription:
```
az account show
```
Get a list of subscriptions for the logged in account:
```
az account list -o table
```

# Login
Azure service principal login:
```
az login --service-principal -u $AZ_USER -p $AZ_PASSWORD -t $AZ_TENANT
```

# Roles
List role assignments with query:
```
az role assignment list --all --assignee "$AZ_USER" --query "[*].{Name:principalName, Role:roleDefinitionName, Scope:scope}" -o json
```

List role assignments:
```
az role assignment list --all --assignee "$(az account list --query "[].user.name" -o tsv)" -o table
```


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

## private-dns zone

Manage Private DNS zones

List Private DNS zones:
```
az network private-dns zone list -g $RESOURCE_GROUP -o table
```
Create a Private DNS zone:
```
az network private-dns zone create -g $RESOURCE_GROUP -n <private-zone-name>
```
Get a Private DNS zone:
```
az network private-dns zone show -g $RESOURCE_GROUP -n <private-zone-name>
```

## private-dns-record

Manage Private DNS records and record sets

List all `A` record sets in a zone:
```
az network private-dns record-set a list -g $RESOURCE_GROUP -z <private-dns-zone>
```
Create an empty `A` record set:
```
az network private-dns record-set a create -g $RESOURCE_GROUP -z <private-dns-zone> -n <record-set-name> --ttl 300
```
Add an `A` record:
```
az network private-dns record-set a add-record -g $RESOURCE_GROUP -z <private-dns-zone> -n <record-set-name> -a <ipv4-address>
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

# VM
List details of Virtual Machines:
```
az vm list -g $RESOURCE_GROUP -o table -d
```
List IP addresses associated with a VM:
```
az vm list-ip-addresses -g $RESOURCE_GROUP -o table
```


# Image
List custom VM images:
```
az image list -g $RESOURCE_GROUP -o table
```

# Storage

## storage-account
List storage account:
```
 az storage account list -g $RESOURCE_GROUP -o table
```
