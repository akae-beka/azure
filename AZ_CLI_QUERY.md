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


```
az network nic show -g $OPERATOR_RESOURCE_GROUP -n opocp01.scf-ocp-p-02.scf.pro.weu2.azure.paas.cloudcenter.corp-nic01 --query ipConfigurations[0].subnet.id -o tsv




az vm show -g $OPERATOR_RESOURCE_GROUP -n opocp01.scf-ocp-p-02.scf.pro.weu2.azure.paas.cloudcenter.corp --query networkProfiles[0].networkInterfaces.id -o tsv


az vm show -g $OPERATOR_RESOURCE_GROUP -n opocp01.scf-ocp-p-02.scf.pro.weu2.azure.paas.cloudcenter.corp --query networkProfile


az vm show -g $OPERATOR_RESOURCE_GROUP -n opocp01.scf-ocp-p-02.scf.pro.weu2.azure.paas.cloudcenter.corp --query networkProfile.networkInterfaces[0].id
```
