# Day 44: Integrating Azure Event Hub with Virtual Machines

The Nautilus DevOps team wants to integrate an Azure Virtual Machine with Azure Event Hubs for centralized log collection. Follow these steps to complete the task:

- **Create Azure Event Hubs Namespace**:
   - Create an Event Hubs namespace named `nautilus-namespace` in the `East US` region.
   - Select the `Standard` pricing tier. Make sure to enable `Enable Auto-inflate`.

- **Create an Event Hub**:
   - Within the namespace, create an Event Hub named `nautilus-hub`.

- **Verify the Virtual Machine Configuration**:
  - A VM named `nautilus-vm` already exists.
  - A Python script named `send_logs.py` already exists on the VM under `/home/azureuser`. This script is used to send logs to the Event Hub. Make sure to execute this script mutiple times.

- **Verify Logs**:
  -  Ensure the logs are successfully sent to the Event Hub by checking the Event Hubs metrics in the Azure portal.


## Task 1: Create Azure Event Hubs Namespace:

1. Go to `Event Hubs` and click `Create`.

   <img width="1365" height="502" alt="image" src="https://github.com/user-attachments/assets/96458caa-4bbe-4f6a-9a8a-3e24cb1f39af" />

2. Create an Event Hubs namespace named `nautilus-namespace` in the `East US` region and select the `Standard` pricing tier. Make sure to enable `Enable Auto-inflate`.

   <img width="1365" height="409" alt="image" src="https://github.com/user-attachments/assets/8e22932b-f584-4c02-ae13-48327b2f22d4" />

3. On the `Review + create` tab, click `Create`.

   <img width="1365" height="452" alt="image" src="https://github.com/user-attachments/assets/b8b37440-8b47-4a71-99e7-a48fa7411552" />


## Task 2: Create an Event Hub:

1. Go to `nautilus-namespace` dashboard and click on `+ Event Hub`.

   <img width="1365" height="429" alt="image" src="https://github.com/user-attachments/assets/5359cee1-13f4-420a-a4df-bcea2e131c07" />

2. Enter name and leave others as default.

   <img width="1365" height="438" alt="image" src="https://github.com/user-attachments/assets/0ed3c82b-004f-40ab-9621-952b88163964" />

3. On the `Review + create` tab, click `Create`.

   <img width="1365" height="452" alt="image" src="https://github.com/user-attachments/assets/b07b84d7-3a01-4e9e-85bb-6725e77e4f44" />


## Task 3: Get connections string

1. On the `Event Hubs namespace` page, select `Shared Access Policies` on the left menu under `Settings`.

   <img width="1082" height="439" alt="image" src="https://github.com/user-attachments/assets/5db09cfa-2593-4587-ab3e-f6203d9fd924" />

2. Select a **shared access policy** in the list of policies. The default one is named: `RootManageSharedAccessPolicy`. You can add a policy with appropriate permissions (send, listen), and use that policy.

   <img width="1072" height="516" alt="image" src="https://github.com/user-attachments/assets/d0221e2b-1dba-432d-b0f6-76b74a5e6fb2" />

3. Select the copy button next to the `Connection string-primary` key field.

   <img width="523" height="574" alt="image" src="https://github.com/user-attachments/assets/8acbb133-517e-424d-8cc3-692c4d27b6c4" />


## Task 4: Verify the Virtual Machine Configuration:

1. SSH into VM from azure-client host:

   ```sh
   ssh azureuser@<nautilus-vm-pub-ip>
   ```
   
2. Update the python script with connection string.

   `connection_str = "<your_event_hub_connection_string>"`

3. Run the python script multiple time:

   ```sh
   python3 send_logs.py
   ```

## Task 5: Verify logs are successfully sent to the Event Hub

1. Go to Event Hub and check it's metrics at the end of the page.

   <img width="1103" height="428" alt="image" src="https://github.com/user-attachments/assets/fb8b3f39-8178-4c76-8408-1901ea22cd7f" />

   <img width="1096" height="420" alt="image" src="https://github.com/user-attachments/assets/f3eedf69-fa0d-4fbf-9baf-8040fd4db214" />
