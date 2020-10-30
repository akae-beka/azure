# az cli


### Azure VM
Deallocate a VM:
```
az vm list -g $RG -d --query "[?contains(name, 'vmname') && powerState == 'VM running'].name" -o tsv | xargs -L1 bash -c 'az vm deallocate -g $RG -n $0'
```
Stop a VM:
```
az vm list -g $RG --query "[?contains(name, 'vmname')].name" -o tsv | xargs -L1 bash -c 'az vm stop -g $RG -n $0 --debug'
```
Delete a VM:
```
az vm list -g $RG --query "[?contains(name, 'vmname')].name" -o tsv | xargs -L1 bash -c 'az vm delete -g $RG -n $0 -y --debug'
```
### Azure Network
Delete a NIC:
```
az network nic list -g $RG --query "[?contains(name, 'nicname')].name" -o tsv | xargs -L1 bash -c 'az network nic delete -g $RG -n $0 --debug'
```

### Azure Disk
Delete a disk:
```
az disk list -g $RG --query "[?contains(name, 'diskname')].name" -o tsv | xargs -L1 bash -c 'az disk delete -g $RG -n $0 -y --debug'
```


List role assignments from Azure User:
```
az role assignment list --all --assignee "$(az account show | awk '/name/ {print $2}' | tail -n +2 | cut -b 2-37)" -o table
```
