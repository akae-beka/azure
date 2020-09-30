# az cli

Deallocate a VM:
```
az vm list -g $RG -d --query "[?contains(name, 'vmname') && powerState == 'VM running'].name" -o tsv | xargs -L1 bash -c 'az vm deallocate -g $RG -n $0'
```
