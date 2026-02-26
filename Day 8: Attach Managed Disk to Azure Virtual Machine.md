# Day 8: Attach Managed Disk to Azure Virtual Machine
https://engineer.kodekloud.com/task?id=691b0c7b4aa4b86f475f82bf&status=start
An existing VM named `nautilus-vm` and a managed disk named `devops-disk` already exist in the `East US` region.

Attach the disk `nautilus-disk` to the VM `devops-vm` as a data disk.

Ensure the disk is attached to the VM `devops-vm`.

Make sure that the virtual machine initialization has been completed before submitting this task.

## Add a data disk

Azure Docs to be followed: [Attach an existing disk](https://learn.microsoft.com/en-us/azure/virtual-machines/linux/attach-disk-portal#attach-an-existing-disk)

- Sign in to the `Azure portal`.
- Search for and select `Virtual machines`.
- Select a virtual machine from the list.

  <img width="1083" height="237" alt="image" src="https://github.com/user-attachments/assets/ba3ec441-d024-4221-9af9-793a01adc11a" />

- On the virtual machine pane, From `Settings`, choose `Disk`.
  
  <img width="1366" height="615" alt="image" src="https://github.com/user-attachments/assets/25a9bffe-b6d7-469a-8359-e3d67985e931" />

- Under `Data disk`, choose `Attach existing disk` and select the existing disk.

  <img width="1628" height="208" alt="image" src="https://github.com/user-attachments/assets/2ae9b924-ed06-4d4b-ac2c-0ca0ee3d6c6d" />
