# Use-RBAC-and-Design-a-Custom-Role
As an Administrator for your organisation that is migrating its primary web app from its on-premises datacenter to Azure, and you need to allow developers to create and deploy Azure virtual machines by assigning an appropriate role.

At the end of this project, we accomplished the following:
1. Assigned built-in roles and verified permissions.
2. Created a virtual machine as a developer.
3. Designed a custom role.

## Steps
I will use RBAC and design a custom role as a proof of concept. 
1. First, you will assign built-in roles and verify permissions.
2. Next, you will create a virtual machine as a developer.
3. Finally, you will design a custom role.

## 1. Assign built-in roles and verify permissions
1. Sign in to http://portal.azure.com as admin
2. Use role-based access control (RBAC) to allow the Dev1-55552985@cloudslice.onmicrosoft.com developer account to manage certain resources in the corp-datalod55552985 resource group by
3. By adding the following role assignments: Storage Account Contributor, Virtual Machine Contributor, Network Contributor.
4. Open an * InPrivate* or Incognito browser window on your local machine, sign in to the Azure portal at https://portal.azure.com as Dev1-55552985@cloudslice.onmicrosoft.com
5. Create a storage account named sa55552985 with default settings in the corp-datalod55552985 resource group to verify the new role assignment.
6. It may take a few minutes for the new role assignments to be fully active.
7. If you get an unexpected result when you check your work, please wait a few minutes and try again.



## 2. Create a virtual machine as a developer
>>> Make sure you are signed in to Microsoft Azure as the Developer: Dev1-55552985@cloudslice.onmicrosoft.com.

>>> Create an Azure virtual machine by using the values in the following table. For any property that is not specified, use the default value.

Property --------------	Value
Resource group:	rp-datalod**********
Virtual machine name:	VM1
Region:	(US) East US
Image	Windows Server 2016 Datacenter: - x64 Gen2
Size:	Standard B2s
Admin Username:	AzureAdmin
Admin Password:	Pa55w.rd55552985
Select inbound ports:	RDP (3389)
OS disk type:	Standard HDD
Auto-shutdown:	Disabled
Boot diagnostics:	Disable
Close the InPrivate or Incognito browser window.

Want to learn more? Review the documentation on creating an Azure VM.

>>> It may take a few minutes for the audit log to be updated after the virtual machine has been created. 
>>> If you get an unexpected result when you check your work, please wait a few minutes and try again.



## 3. Design a custom role

In the original Microsoft Edge browser window, ensure that you are signed in to the Microsoft Azure portal as admin1-55552985@cloudslice.onmicrosoft.com .

>>> Launch an Azure Cloud Shell PowerShell session by using the values in the following table. For any property that is not specified, use the default value.

Property --------------	Value
Resource group:	corp-datalod55552985
Region:	(US) East US
Storage account:	New csshell55552985
File share:	fs55552985

>>Identify the operations associated with virtual machines by using the Get-AzProviderOperation cmdlet.

>>Note the operations for read, start, and deallocate.

>>You can use the operations associated with an Azure resource as actions when you create an Azure role-based access control (RBAC) custom role.

>>Retrieve the role definition for the Virtual Machine Contributor role and then output it to $home\clouddrive\VMOperatorRole.json by using the Get-AzRoleDefinition and the ConvertTo-Json cmdlets.
>>You can use Azure role-based access control (RBAC) role assignments to grant access to resources at a specific scope-subscription, resource group, resource-by assigning a role to a user, group, service principal, or managed identity.
>>There are two types of roles that you can use: built-in and custom. You can create a custom role by using the Azure portal, Azure PowerShell®, Azure command-line interface (CLI) 2.0, and the REST API.


1. Get-AzRoleDefinition
2. ConvertTo-Json
3. Custom roles
4. Open the VMOperatorRole.json file in the Azure Cloud Shell code editor by using the code command in the $home\clouddrive folder.
5. If prompted, switch to Cloud Shell classic mode and then run the commands again.

>> You can edit the definition of a built-in role by using the Azure Cloud Shell code editor, and then you can save the definition as a new custom role.


>>> Edit the VMOperatorRole.json file by changing the properties in the following table:

Property	Value
1. Name:	"Virtual Machine Operator55552985"
2. Id: Delete the entire line
3. IsCustom:	true
4. Description: "Lets you view, start and stop virtual machines."
5. AssignableScopes	"/subscriptions/d28df0a3-5e54-471f-b9ce-df15fa1a8ff3/resourceGroups/corp-datalod55552985"
6. Edit the VMOperatorRole.json file to contain only the "Microsoft.Compute/*/read", "Microsoft.Compute/virtualMachines/start/action", and "Microsoft.Compute/virtualMachines/deallocate/action" actions.
7. Make sure that there is a comma at the end of each action, except for the final action in the list.
8. Save the VMOperatorRole.json file.
>>If you do not see the ellipsis, you can save the file by using CTRL+S and then close the code editor by selecting the X in the top right corner of the editor.

>>Attempt to create a new custom role by using the New-AzRoleDefinition cmdlet and the VMOperatorRole.json file.

>>Due to security restrictions within the lab environment, you will receive an expected error stating that you are not authorised to create a custom role.


## 4. Summary
Congratulations
