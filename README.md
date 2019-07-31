# Azure ARM
 ARM Templates Repo

In the parameters, please note:
1. In example of ViBiCloud Admins and ViBiCloud Helpdesk, it is refering to which group (not user, although a user object from Azure AD is possible) in AzureAD to manage a subscription with delegated permissions (Contributor or Reader).
2. Service Automation Account and Policy Automation Account IS NOT an Azure Automation Acount. They're both a service principal which can be crated through app registration.
3. All of the "principalId" values are objectID values from user/group/service principal in Azure AD.
4. Get group ObjectID in PS: (Get-AzADGroup -DisplayName '<yourGroupName>').id
5. Get user objectID in PS: (Get-AzADUser -UserPrincipalName '<yourUPN>').id
6. Get Service Principal objectID in PS: (Get-AzADServicePrincipal -SearchString ‘mySPN’).Id
7. Use latest version of Azure PS in order to get the commands above work.
8. "roleDefinitionId" is an ID for specific IAM roles such as Contributor or Reader. To get this value from PS: (Get-AzRoleDefinition -Name '<roleName>').id
9. A full set of Azure-related permissions (IAM permissions) can be read here: https://docs.microsoft.com/en-us/azure/role-based-access-control/built-in-roles 
10. "principalIdDisplayName" is just a friendly name for customers to see, not the exact name of user/group/servicePrincipal in our AzureAD.
11. To deploy your own template (which is saved locally on your machine), use:
New-AzDeployment -Name 'LightHouseOnboard' -Location 'Southeast Asia' -TemplateFile '<localPath>/MSP_delegation.json' -TemplateParameterFile '<localPath>/MSP_delegation.parameters.json' -Verbose
12. A full documentation for Azure Lighthouse can be found here: https://docs.microsoft.com/en-us/azure/lighthouse/ 
13. As this is a feature that's just recently get into General Availability release, documentation can be modified by Microsoft occassionally.