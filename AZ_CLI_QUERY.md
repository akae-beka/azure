# az cli

Use JMESPath query string with AZ CLI.

### Network query

List all A record sets in a zone with query:
```
az network private-dns record-set a list -g $RESOURCE_GROUP -z <private-dns-zone> --query "[*].{Name:name,ResourceGroup:resourceGroup,Records:aRecords[0].ipv4Address}" -o table
```


### Storage Account query

Get primaryEndpoint for storage account:
```
az storage account list -g $RESOURCE_GROUP --query "[?contains(name, '$STORAGE_ACCOUNT')].primaryEndpoints" -o json
```

Get storage account name on specificy region Azure:
```
az storage account list -g $RESOURCE_GROUP --query "[?location == 'westeurope'].{Name:name}" -o table
```
