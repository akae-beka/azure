# az cli

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


List role assignments from Azure User:
```
az role assignment list --all --assignee "$(az account show | awk '/name/ {print $2}' | tail -n +2 | cut -b 2-37)" -o table
```
