You are tasked with modifying an ARM template for deploying a virtual network. The current template is located in the /root/arm-templates directory under the filename vnet-deployment-template.json. You need to make the following changes to the template:

Change the name and displayName tag of the virtual network to arm-vnet-datacenter.

Update the addressPrefixes to 192.168.0.0/16.

Add one more tag named Environment with value KKE-datacenter.

After making these changes, you need to deploy the ARM template using the Azure CLI.

Use the following command to find out the resource group to use:
```
az group list --query '[].name' --output table | grep 'kml'
```
update the json file as per instructions
```
vi /root/arm-templates/vnet-deployment-template.json
```
<img width="1065" height="609" alt="image" src="https://github.com/user-attachments/assets/1c8ee019-919a-443f-8272-2bb976d2b289" />


deploy the group using updated template

az deployment group create --resource-group kml_rg_main-868086acffbb444c --template-file /root/arm-templates/vnet-deployment-template.json
