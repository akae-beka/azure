# az cli JMESPath query string

List all A record sets in a zone with query:
```
az network private-dns record-set a list -g $RESOURCE_GROUP -z privatelink.file.core.windows.net --query "[*].{Name:name,ResourceGroup:resourceGroup,TTL:ttl,FQDN:fqdn,Kind:type,Records:aRecords[0].ipv4Address}" -o table
```
