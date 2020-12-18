# Azure

List available usage resources for VMs:
```
export TOTAL_REGIONAL="Total Regional vCPUs"
export TOTAL_FAMILY="Standard DSv3 Family vCPUs"

az vm list-usage -l eastus \
 --query "[?localName=='$TOTAL_REGIONAL' || localName == '$TOTAL_FAMILY'].{Name:name.localizedValue, CurrentValue:currentValue, Limit:limit}" \
 -o table
```


### Create VMs

Create an Azure Virtual Machine:
```
export RG=`az group list --query "[?name=='$RG_NAME'].name" -o tsv` && \
export VM_NAME=MyVm && \
export VM_SIZE=Standard_D16s_v3 && \
export VM_IMAGE=`az image list -g $RG --query "[?name=='$IMAGE_NAME'].name" -o tsv`

az vm create -g $RG -n $VM_NAME --size $VM_SIZE --image $VM_IMAGE --generate-ssh-keys
```
