# az cli

Use JMESPath query string with AZ CLI.

List all A record sets in a zone with query:
```
az network private-dns record-set a list -g $RESOURCE_GROUP -z <private-dns-zone> --query "[*].{Name:name,ResourceGroup:resourceGroup,Records:aRecords[0].ipv4Address}" -o table
```
