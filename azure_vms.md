# Azure

List available usage resources for VMs:
```
export TOTAL_REGIONAL="Total Regional vCPUs"
export TOTAL_FAMILY="Standard DSv3 Family vCPUs"

az vm list-usage -l eastus \
 --query "[?localName=='$TOTAL_REGIONAL' || localName == '$TOTAL_FAMILY'].{Name:name.localizedValue, CurrentValue:currentValue, Limit:limit}" \
 -o table
```
