# Day 3: Create VM using Azure CLI

The Nautilus DevOps team is in the process of migrating some of their workloads to Azure. One of the tasks involves creating a new Virtual Machine (VM) using the Azure CLI. The team does not have access to the Azure portal but can manage Azure resources via the azure-client host (the landing host for this lab).

1) Create a new Azure Virtual Machine named `xfusion-vm` using the Azure CLI.

2) Use the `Ubuntu2204` image and set the VM size to `Standard_B2s`.

3) Make sure the admin username is set to `azureuser` and SSH keys are generated for secure access.

4) Use `Standard_LRS` storage account, disk size must be `30GB` and ensure the VM `xfusion-vm` is in the running state after creation.


Step 1 — Check existing Resource Groups

```
az group list -o table
```

Step 2 — Create the Virtual Machine

```
az vm create \
  --name xfusion-vm \
  --resource-group kml_rg_main-7cc8243da2e34602 \  # Resource group must be changed based on step 1 result
  --location eastus \
  --image Ubuntu2204 \
  --size Standard_B2s \
  --admin-username azureuser \
  --generate-ssh-keys \
  --os-disk-size-gb 30 \
  --storage-sku Standard_LRS  
```

Step 3 - Verify the VM status

```
az vm get-instance-view \
  --name xfusion-vm \
  --resource-group kml_rg_main-7cc8243da2e34602 \
  --query "instanceView.statuses" \
  --output table

```
