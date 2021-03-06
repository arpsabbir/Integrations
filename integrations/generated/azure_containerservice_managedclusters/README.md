# @datafire/azure_containerservice_managedclusters

Client library for ContainerServiceClient

## Installation and Usage
```bash
npm install --save @datafire/azure_containerservice_managedclusters
```
```js
let azure_containerservice_managedclusters = require('@datafire/azure_containerservice_managedclusters').create({
  access_token: "",
  refresh_token: "",
  client_id: "",
  client_secret: "",
  redirect_uri: ""
});

.then(data => {
  console.log(data);
});
```

## Description

The Container Service Client.

## Actions

### Operations_List
Gets a list of compute operations.


```js
azure_containerservice_managedclusters.Operations_List({
  "api-version": ""
}, context)
```

#### Input
* input `object`
  * api-version **required** `string`: Client Api Version.

#### Output
* output [OperationListResult](#operationlistresult)

### ManagedClusters_List
Gets a list of managed clusters in the specified subscription. The operation returns properties of each managed cluster.


```js
azure_containerservice_managedclusters.ManagedClusters_List({
  "api-version": "",
  "subscriptionId": ""
}, context)
```

#### Input
* input `object`
  * api-version **required** `string`: Client Api Version.
  * subscriptionId **required** `string`: Subscription credentials which uniquely identify Microsoft Azure subscription. The subscription ID forms part of the URI for every service call.

#### Output
* output [ManagedClusterListResult](#managedclusterlistresult)

### ManagedClusters_ListByResourceGroup
Lists managed clusters in the specified subscription and resource group. The operation returns properties of each managed cluster.


```js
azure_containerservice_managedclusters.ManagedClusters_ListByResourceGroup({
  "api-version": "",
  "subscriptionId": "",
  "resourceGroupName": ""
}, context)
```

#### Input
* input `object`
  * api-version **required** `string`: Client Api Version.
  * subscriptionId **required** `string`: Subscription credentials which uniquely identify Microsoft Azure subscription. The subscription ID forms part of the URI for every service call.
  * resourceGroupName **required** `string`: The name of the resource group.

#### Output
* output [ManagedClusterListResult](#managedclusterlistresult)

### ManagedClusters_Delete
Deletes the managed cluster with a specified resource group and name.


```js
azure_containerservice_managedclusters.ManagedClusters_Delete({
  "api-version": "",
  "subscriptionId": "",
  "resourceGroupName": "",
  "resourceName": ""
}, context)
```

#### Input
* input `object`
  * api-version **required** `string`: Client Api Version.
  * subscriptionId **required** `string`: Subscription credentials which uniquely identify Microsoft Azure subscription. The subscription ID forms part of the URI for every service call.
  * resourceGroupName **required** `string`: The name of the resource group.
  * resourceName **required** `string`: The name of the managed cluster resource.

#### Output
*Output schema unknown*

### ManagedClusters_Get
Gets the details of the managed cluster with a specified resource group and name.


```js
azure_containerservice_managedclusters.ManagedClusters_Get({
  "api-version": "",
  "subscriptionId": "",
  "resourceGroupName": "",
  "resourceName": ""
}, context)
```

#### Input
* input `object`
  * api-version **required** `string`: Client Api Version.
  * subscriptionId **required** `string`: Subscription credentials which uniquely identify Microsoft Azure subscription. The subscription ID forms part of the URI for every service call.
  * resourceGroupName **required** `string`: The name of the resource group.
  * resourceName **required** `string`: The name of the managed cluster resource.

#### Output
* output [ManagedCluster](#managedcluster)

### ManagedClusters_UpdateTags
Updates a managed cluster with the specified tags.


```js
azure_containerservice_managedclusters.ManagedClusters_UpdateTags({
  "api-version": "",
  "subscriptionId": "",
  "resourceGroupName": "",
  "resourceName": "",
  "parameters": null
}, context)
```

#### Input
* input `object`
  * api-version **required** `string`: Client Api Version.
  * subscriptionId **required** `string`: Subscription credentials which uniquely identify Microsoft Azure subscription. The subscription ID forms part of the URI for every service call.
  * resourceGroupName **required** `string`: The name of the resource group.
  * resourceName **required** `string`: The name of the managed cluster resource.
  * parameters **required** [TagsObject](#tagsobject)

#### Output
* output [ManagedCluster](#managedcluster)

### ManagedClusters_CreateOrUpdate
Creates or updates a managed cluster with the specified configuration for agents and Kubernetes version.


```js
azure_containerservice_managedclusters.ManagedClusters_CreateOrUpdate({
  "api-version": "",
  "subscriptionId": "",
  "resourceGroupName": "",
  "resourceName": "",
  "parameters": null
}, context)
```

#### Input
* input `object`
  * api-version **required** `string`: Client Api Version.
  * subscriptionId **required** `string`: Subscription credentials which uniquely identify Microsoft Azure subscription. The subscription ID forms part of the URI for every service call.
  * resourceGroupName **required** `string`: The name of the resource group.
  * resourceName **required** `string`: The name of the managed cluster resource.
  * parameters **required** [ManagedCluster](#managedcluster)

#### Output
* output [ManagedCluster](#managedcluster)

### ManagedClusters_GetAccessProfile
Gets the accessProfile for the specified role name of the managed cluster with a specified resource group and name.


```js
azure_containerservice_managedclusters.ManagedClusters_GetAccessProfile({
  "api-version": "",
  "subscriptionId": "",
  "resourceGroupName": "",
  "resourceName": "",
  "roleName": ""
}, context)
```

#### Input
* input `object`
  * api-version **required** `string`: Client Api Version.
  * subscriptionId **required** `string`: Subscription credentials which uniquely identify Microsoft Azure subscription. The subscription ID forms part of the URI for every service call.
  * resourceGroupName **required** `string`: The name of the resource group.
  * resourceName **required** `string`: The name of the managed cluster resource.
  * roleName **required** `string`: The name of the role for managed cluster accessProfile resource.

#### Output
* output [ManagedClusterAccessProfile](#managedclusteraccessprofile)

### AgentPools_List
Gets a list of agent pools in the specified managed cluster. The operation returns properties of each agent pool.


```js
azure_containerservice_managedclusters.AgentPools_List({
  "api-version": "",
  "subscriptionId": "",
  "resourceGroupName": "",
  "resourceName": ""
}, context)
```

#### Input
* input `object`
  * api-version **required** `string`: Client Api Version.
  * subscriptionId **required** `string`: Subscription credentials which uniquely identify Microsoft Azure subscription. The subscription ID forms part of the URI for every service call.
  * resourceGroupName **required** `string`: The name of the resource group.
  * resourceName **required** `string`: The name of the managed cluster resource.

#### Output
* output [AgentPoolListResult](#agentpoollistresult)

### AgentPools_Delete
Deletes the agent pool in the specified managed cluster.


```js
azure_containerservice_managedclusters.AgentPools_Delete({
  "api-version": "",
  "subscriptionId": "",
  "resourceGroupName": "",
  "resourceName": "",
  "agentPoolName": ""
}, context)
```

#### Input
* input `object`
  * api-version **required** `string`: Client Api Version.
  * subscriptionId **required** `string`: Subscription credentials which uniquely identify Microsoft Azure subscription. The subscription ID forms part of the URI for every service call.
  * resourceGroupName **required** `string`: The name of the resource group.
  * resourceName **required** `string`: The name of the managed cluster resource.
  * agentPoolName **required** `string`: The name of the agent pool.

#### Output
*Output schema unknown*

### AgentPools_Get
Gets the details of the agent pool by managed cluster and resource group.


```js
azure_containerservice_managedclusters.AgentPools_Get({
  "api-version": "",
  "subscriptionId": "",
  "resourceGroupName": "",
  "resourceName": "",
  "agentPoolName": ""
}, context)
```

#### Input
* input `object`
  * api-version **required** `string`: Client Api Version.
  * subscriptionId **required** `string`: Subscription credentials which uniquely identify Microsoft Azure subscription. The subscription ID forms part of the URI for every service call.
  * resourceGroupName **required** `string`: The name of the resource group.
  * resourceName **required** `string`: The name of the managed cluster resource.
  * agentPoolName **required** `string`: The name of the agent pool.

#### Output
* output [AgentPool](#agentpool)

### AgentPools_CreateOrUpdate
Creates or updates an agent pool in the specified managed cluster.


```js
azure_containerservice_managedclusters.AgentPools_CreateOrUpdate({
  "api-version": "",
  "subscriptionId": "",
  "resourceGroupName": "",
  "resourceName": "",
  "agentPoolName": "",
  "parameters": null
}, context)
```

#### Input
* input `object`
  * api-version **required** `string`: Client Api Version.
  * subscriptionId **required** `string`: Subscription credentials which uniquely identify Microsoft Azure subscription. The subscription ID forms part of the URI for every service call.
  * resourceGroupName **required** `string`: The name of the resource group.
  * resourceName **required** `string`: The name of the managed cluster resource.
  * agentPoolName **required** `string`: The name of the agent pool.
  * parameters **required** [AgentPool](#agentpool)

#### Output
* output [AgentPool](#agentpool)

### AgentPools_GetUpgradeProfile
Gets the details of the upgrade profile for an agent pool with a specified resource group and managed cluster name.


```js
azure_containerservice_managedclusters.AgentPools_GetUpgradeProfile({
  "api-version": "",
  "subscriptionId": "",
  "resourceGroupName": "",
  "resourceName": "",
  "agentPoolName": ""
}, context)
```

#### Input
* input `object`
  * api-version **required** `string`: Client Api Version.
  * subscriptionId **required** `string`: Subscription credentials which uniquely identify Microsoft Azure subscription. The subscription ID forms part of the URI for every service call.
  * resourceGroupName **required** `string`: The name of the resource group.
  * resourceName **required** `string`: The name of the managed cluster resource.
  * agentPoolName **required** `string`: The name of the agent pool.

#### Output
* output [AgentPoolUpgradeProfile](#agentpoolupgradeprofile)

### AgentPools_GetAvailableAgentPoolVersions
Gets a list of supported versions for the specified agent pool.


```js
azure_containerservice_managedclusters.AgentPools_GetAvailableAgentPoolVersions({
  "api-version": "",
  "subscriptionId": "",
  "resourceGroupName": "",
  "resourceName": ""
}, context)
```

#### Input
* input `object`
  * api-version **required** `string`: Client Api Version.
  * subscriptionId **required** `string`: Subscription credentials which uniquely identify Microsoft Azure subscription. The subscription ID forms part of the URI for every service call.
  * resourceGroupName **required** `string`: The name of the resource group.
  * resourceName **required** `string`: The name of the managed cluster resource.

#### Output
* output [AgentPoolAvailableVersions](#agentpoolavailableversions)

### ManagedClusters_ListClusterAdminCredentials
Gets cluster admin credential of the managed cluster with a specified resource group and name.


```js
azure_containerservice_managedclusters.ManagedClusters_ListClusterAdminCredentials({
  "api-version": "",
  "subscriptionId": "",
  "resourceGroupName": "",
  "resourceName": ""
}, context)
```

#### Input
* input `object`
  * api-version **required** `string`: Client Api Version.
  * subscriptionId **required** `string`: Subscription credentials which uniquely identify Microsoft Azure subscription. The subscription ID forms part of the URI for every service call.
  * resourceGroupName **required** `string`: The name of the resource group.
  * resourceName **required** `string`: The name of the managed cluster resource.

#### Output
* output [CredentialResults](#credentialresults)

### ManagedClusters_ListClusterUserCredentials
Gets cluster user credential of the managed cluster with a specified resource group and name.


```js
azure_containerservice_managedclusters.ManagedClusters_ListClusterUserCredentials({
  "api-version": "",
  "subscriptionId": "",
  "resourceGroupName": "",
  "resourceName": ""
}, context)
```

#### Input
* input `object`
  * api-version **required** `string`: Client Api Version.
  * subscriptionId **required** `string`: Subscription credentials which uniquely identify Microsoft Azure subscription. The subscription ID forms part of the URI for every service call.
  * resourceGroupName **required** `string`: The name of the resource group.
  * resourceName **required** `string`: The name of the managed cluster resource.

#### Output
* output [CredentialResults](#credentialresults)

### ManagedClusters_ResetAADProfile
Update the AAD Profile for a managed cluster.


```js
azure_containerservice_managedclusters.ManagedClusters_ResetAADProfile({
  "api-version": "",
  "subscriptionId": "",
  "resourceGroupName": "",
  "resourceName": "",
  "parameters": null
}, context)
```

#### Input
* input `object`
  * api-version **required** `string`: Client Api Version.
  * subscriptionId **required** `string`: Subscription credentials which uniquely identify Microsoft Azure subscription. The subscription ID forms part of the URI for every service call.
  * resourceGroupName **required** `string`: The name of the resource group.
  * resourceName **required** `string`: The name of the managed cluster resource.
  * parameters **required** [ManagedClusterAADProfile](#managedclusteraadprofile)

#### Output
*Output schema unknown*

### ManagedClusters_ResetServicePrincipalProfile
Update the service principal Profile for a managed cluster.


```js
azure_containerservice_managedclusters.ManagedClusters_ResetServicePrincipalProfile({
  "api-version": "",
  "subscriptionId": "",
  "resourceGroupName": "",
  "resourceName": "",
  "parameters": null
}, context)
```

#### Input
* input `object`
  * api-version **required** `string`: Client Api Version.
  * subscriptionId **required** `string`: Subscription credentials which uniquely identify Microsoft Azure subscription. The subscription ID forms part of the URI for every service call.
  * resourceGroupName **required** `string`: The name of the resource group.
  * resourceName **required** `string`: The name of the managed cluster resource.
  * parameters **required** [ManagedClusterServicePrincipalProfile](#managedclusterserviceprincipalprofile)

#### Output
*Output schema unknown*

### ManagedClusters_RotateClusterCertificates
Rotate certificates of a managed cluster.


```js
azure_containerservice_managedclusters.ManagedClusters_RotateClusterCertificates({
  "api-version": "",
  "subscriptionId": "",
  "resourceGroupName": "",
  "resourceName": ""
}, context)
```

#### Input
* input `object`
  * api-version **required** `string`: Client Api Version.
  * subscriptionId **required** `string`: Subscription credentials which uniquely identify Microsoft Azure subscription. The subscription ID forms part of the URI for every service call.
  * resourceGroupName **required** `string`: The name of the resource group.
  * resourceName **required** `string`: The name of the managed cluster resource.

#### Output
*Output schema unknown*

### ManagedClusters_GetUpgradeProfile
Gets the details of the upgrade profile for a managed cluster with a specified resource group and name.


```js
azure_containerservice_managedclusters.ManagedClusters_GetUpgradeProfile({
  "api-version": "",
  "subscriptionId": "",
  "resourceGroupName": "",
  "resourceName": ""
}, context)
```

#### Input
* input `object`
  * api-version **required** `string`: Client Api Version.
  * subscriptionId **required** `string`: Subscription credentials which uniquely identify Microsoft Azure subscription. The subscription ID forms part of the URI for every service call.
  * resourceGroupName **required** `string`: The name of the resource group.
  * resourceName **required** `string`: The name of the managed cluster resource.

#### Output
* output [ManagedClusterUpgradeProfile](#managedclusterupgradeprofile)



## Definitions

### AccessProfile
* AccessProfile `object`: Profile for enabling a user to access a managed cluster.
  * kubeConfig `string`: Base64-encoded Kubernetes configuration file.

### AgentPool
* AgentPool: Agent Pool.
  * id `string`: Resource ID.
  * name `string`: The name of the resource that is unique within a resource group. This name can be used to access the resource.
  * type `string`: Resource type
  * properties [ManagedClusterAgentPoolProfileProperties](#managedclusteragentpoolprofileproperties)

### AgentPoolAvailableVersions
* AgentPoolAvailableVersions `object`: The list of available versions for an agent pool.
  * id `string`: Id of the agent pool available versions.
  * name `string`: Name of the agent pool available versions.
  * properties **required** [AgentPoolAvailableVersionsProperties](#agentpoolavailableversionsproperties)
  * type `string`: Type of the agent pool  available versions.

### AgentPoolAvailableVersionsProperties
* AgentPoolAvailableVersionsProperties `object`: The list of available agent pool versions.
  * agentPoolVersions `array`: List of versions available for agent pool.
    * items `object`
      * default `boolean`: Whether this version is the default agent pool version.
      * isPreview `boolean`: Whether Kubernetes version is currently in preview.
      * kubernetesVersion `string`: Kubernetes version (major, minor, patch).

### AgentPoolListResult
* AgentPoolListResult `object`: The response from the List Agent Pools operation.
  * nextLink `string`: The URL to get the next set of agent pool results.
  * value `array`: The list of agent pools.
    * items [AgentPool](#agentpool)

### AgentPoolType
* AgentPoolType `string` (values: VirtualMachineScaleSets, AvailabilitySet): AgentPoolType represents types of an agent pool. VirtualMachineScaleSets type is still in PREVIEW.

### AgentPoolUpgradeProfile
* AgentPoolUpgradeProfile `object`: The list of available upgrades for an agent pool.
  * id `string`: Id of the agent pool upgrade profile.
  * name `string`: Name of the agent pool upgrade profile.
  * properties **required** [AgentPoolUpgradeProfileProperties](#agentpoolupgradeprofileproperties)
  * type `string`: Type of the agent pool upgrade profile.

### AgentPoolUpgradeProfileProperties
* AgentPoolUpgradeProfileProperties `object`: The list of available upgrade versions.
  * kubernetesVersion **required** `string`: Kubernetes version (major, minor, patch).
  * osType **required** [OSType](#ostype)
  * upgrades `array`: List of orchestrator types and versions available for upgrade.
    * items `object`
      * isPreview `boolean`: Whether Kubernetes version is currently in preview.
      * kubernetesVersion `string`: Kubernetes version (major, minor, patch).

### CloudError
* CloudError `object`: An error response from the Container service.
  * error [CloudErrorBody](#clouderrorbody)

### CloudErrorBody
* CloudErrorBody `object`: An error response from the Container service.
  * code `string`: An identifier for the error. Codes are invariant and are intended to be consumed programmatically.
  * details `array`: A list of additional details about the error.
    * items [CloudErrorBody](#clouderrorbody)
  * message `string`: A message describing the error, intended to be suitable for display in a user interface.
  * target `string`: The target of the particular error. For example, the name of the property in error.

### ContainerServiceDiagnosticsProfile
* ContainerServiceDiagnosticsProfile `object`: Profile for diagnostics on the container service cluster.
  * vmDiagnostics **required** [ContainerServiceVMDiagnostics](#containerservicevmdiagnostics)

### ContainerServiceLinuxProfile
* ContainerServiceLinuxProfile `object`: Profile for Linux VMs in the container service cluster.
  * adminUsername **required** `string`: The administrator username to use for Linux VMs.
  * ssh **required** [ContainerServiceSshConfiguration](#containerservicesshconfiguration)

### ContainerServiceMasterProfile
* ContainerServiceMasterProfile `object`: Profile for the container service master.
  * count `integer` (values: 1, 3, 5): Number of masters (VMs) in the container service cluster. Allowed values are 1, 3, and 5. The default value is 1.
  * dnsPrefix **required** `string`: DNS prefix to be used to create the FQDN for the master pool.
  * firstConsecutiveStaticIP `string`: FirstConsecutiveStaticIP used to specify the first static ip of masters.
  * fqdn `string`: FQDN for the master pool.
  * osDiskSizeGB [ContainerServiceOSDisk](#containerserviceosdisk)
  * storageProfile [ContainerServiceStorageProfile](#containerservicestorageprofile)
  * vmSize **required** [ContainerServiceVMSize](#containerservicevmsize)
  * vnetSubnetID [ContainerServiceVnetSubnetID](#containerservicevnetsubnetid)

### ContainerServiceNetworkProfile
* ContainerServiceNetworkProfile `object`: Profile of network configuration.
  * dnsServiceIP `string`: An IP address assigned to the Kubernetes DNS service. It must be within the Kubernetes service address range specified in serviceCidr.
  * dockerBridgeCidr `string`: A CIDR notation IP range assigned to the Docker bridge network. It must not overlap with any Subnet IP ranges or the Kubernetes service address range.
  * loadBalancerProfile [ManagedClusterLoadBalancerProfile](#managedclusterloadbalancerprofile)
  * loadBalancerSku `string` (values: standard, basic): The load balancer sku for the managed cluster.
  * networkPlugin `string` (values: azure, kubenet): Network plugin used for building Kubernetes network.
  * networkPolicy `string` (values: calico, azure): Network policy used for building Kubernetes network.
  * podCidr `string`: A CIDR notation IP range from which to assign pod IPs when kubenet is used.
  * serviceCidr `string`: A CIDR notation IP range from which to assign service cluster IPs. It must not overlap with any Subnet IP ranges.

### ContainerServiceOSDisk
* ContainerServiceOSDisk `integer`: OS Disk Size in GB to be used to specify the disk size for every machine in this master/agent pool. If you specify 0, it will apply the default osDisk size according to the vmSize specified.

### ContainerServiceSshConfiguration
* ContainerServiceSshConfiguration `object`: SSH configuration for Linux-based VMs running on Azure.
  * publicKeys **required** `array`: The list of SSH public keys used to authenticate with Linux-based VMs. Only expect one key specified.
    * items [ContainerServiceSshPublicKey](#containerservicesshpublickey)

### ContainerServiceSshPublicKey
* ContainerServiceSshPublicKey `object`: Contains information about SSH certificate public key data.
  * keyData **required** `string`: Certificate public key used to authenticate with VMs through SSH. The certificate must be in PEM format with or without headers.

### ContainerServiceStorageProfile
* ContainerServiceStorageProfile `string` (values: StorageAccount, ManagedDisks): Storage profile specifies what kind of storage used. Choose from StorageAccount and ManagedDisks. Leave it empty, we will choose for you based on the orchestrator choice.

### ContainerServiceVMDiagnostics
* ContainerServiceVMDiagnostics `object`: Profile for diagnostics on the container service VMs.
  * enabled **required** `boolean`: Whether the VM diagnostic agent is provisioned on the VM.
  * storageUri `string`: The URI of the storage account where diagnostics are stored.

### ContainerServiceVMSize
* ContainerServiceVMSize `string` (values: Standard_A1, Standard_A10, Standard_A11, Standard_A1_v2, Standard_A2, Standard_A2_v2, Standard_A2m_v2, Standard_A3, Standard_A4, Standard_A4_v2, Standard_A4m_v2, Standard_A5, Standard_A6, Standard_A7, Standard_A8, Standard_A8_v2, Standard_A8m_v2, Standard_A9, Standard_B2ms, Standard_B2s, Standard_B4ms, Standard_B8ms, Standard_D1, Standard_D11, Standard_D11_v2, Standard_D11_v2_Promo, Standard_D12, Standard_D12_v2, Standard_D12_v2_Promo, Standard_D13, Standard_D13_v2, Standard_D13_v2_Promo, Standard_D14, Standard_D14_v2, Standard_D14_v2_Promo, Standard_D15_v2, Standard_D16_v3, Standard_D16s_v3, Standard_D1_v2, Standard_D2, Standard_D2_v2, Standard_D2_v2_Promo, Standard_D2_v3, Standard_D2s_v3, Standard_D3, Standard_D32_v3, Standard_D32s_v3, Standard_D3_v2, Standard_D3_v2_Promo, Standard_D4, Standard_D4_v2, Standard_D4_v2_Promo, Standard_D4_v3, Standard_D4s_v3, Standard_D5_v2, Standard_D5_v2_Promo, Standard_D64_v3, Standard_D64s_v3, Standard_D8_v3, Standard_D8s_v3, Standard_DS1, Standard_DS11, Standard_DS11_v2, Standard_DS11_v2_Promo, Standard_DS12, Standard_DS12_v2, Standard_DS12_v2_Promo, Standard_DS13, Standard_DS13-2_v2, Standard_DS13-4_v2, Standard_DS13_v2, Standard_DS13_v2_Promo, Standard_DS14, Standard_DS14-4_v2, Standard_DS14-8_v2, Standard_DS14_v2, Standard_DS14_v2_Promo, Standard_DS15_v2, Standard_DS1_v2, Standard_DS2, Standard_DS2_v2, Standard_DS2_v2_Promo, Standard_DS3, Standard_DS3_v2, Standard_DS3_v2_Promo, Standard_DS4, Standard_DS4_v2, Standard_DS4_v2_Promo, Standard_DS5_v2, Standard_DS5_v2_Promo, Standard_E16_v3, Standard_E16s_v3, Standard_E2_v3, Standard_E2s_v3, Standard_E32-16s_v3, Standard_E32-8s_v3, Standard_E32_v3, Standard_E32s_v3, Standard_E4_v3, Standard_E4s_v3, Standard_E64-16s_v3, Standard_E64-32s_v3, Standard_E64_v3, Standard_E64s_v3, Standard_E8_v3, Standard_E8s_v3, Standard_F1, Standard_F16, Standard_F16s, Standard_F16s_v2, Standard_F1s, Standard_F2, Standard_F2s, Standard_F2s_v2, Standard_F32s_v2, Standard_F4, Standard_F4s, Standard_F4s_v2, Standard_F64s_v2, Standard_F72s_v2, Standard_F8, Standard_F8s, Standard_F8s_v2, Standard_G1, Standard_G2, Standard_G3, Standard_G4, Standard_G5, Standard_GS1, Standard_GS2, Standard_GS3, Standard_GS4, Standard_GS4-4, Standard_GS4-8, Standard_GS5, Standard_GS5-16, Standard_GS5-8, Standard_H16, Standard_H16m, Standard_H16mr, Standard_H16r, Standard_H8, Standard_H8m, Standard_L16s, Standard_L32s, Standard_L4s, Standard_L8s, Standard_M128-32ms, Standard_M128-64ms, Standard_M128ms, Standard_M128s, Standard_M64-16ms, Standard_M64-32ms, Standard_M64ms, Standard_M64s, Standard_NC12, Standard_NC12s_v2, Standard_NC12s_v3, Standard_NC24, Standard_NC24r, Standard_NC24rs_v2, Standard_NC24rs_v3, Standard_NC24s_v2, Standard_NC24s_v3, Standard_NC6, Standard_NC6s_v2, Standard_NC6s_v3, Standard_ND12s, Standard_ND24rs, Standard_ND24s, Standard_ND6s, Standard_NV12, Standard_NV24, Standard_NV6): Size of agent VMs.

### ContainerServiceVnetSubnetID
* ContainerServiceVnetSubnetID `string`: VNet SubnetID specifies the VNet's subnet identifier.

### CredentialResult
* CredentialResult `object`: The credential result response.
  * name `string`: The name of the credential.
  * value `string`: Base64-encoded Kubernetes configuration file.

### CredentialResults
* CredentialResults `object`: The list of credential result response.
  * kubeconfigs `array`: Base64-encoded Kubernetes configuration file.
    * items [CredentialResult](#credentialresult)

### ManagedCluster
* ManagedCluster: Managed cluster.
  * id `string`: Resource Id
  * location **required** `string`: Resource location
  * name `string`: Resource name
  * tags `object`: Resource tags
  * type `string`: Resource type
  * identity [ManagedClusterIdentity](#managedclusteridentity)
  * properties [ManagedClusterProperties](#managedclusterproperties)

### ManagedClusterAADProfile
* ManagedClusterAADProfile `object`: AADProfile specifies attributes for Azure Active Directory integration.
  * clientAppID **required** `string`: The client AAD application ID.
  * serverAppID **required** `string`: The server AAD application ID.
  * serverAppSecret `string`: The server AAD application secret.
  * tenantID `string`: The AAD tenant ID to use for authentication. If not specified, will use the tenant of the deployment subscription.

### ManagedClusterAPIServerAccessProfile
* ManagedClusterAPIServerAccessProfile `object`: Access profile for managed cluster API server.
  * authorizedIPRanges `array`: Authorized IP Ranges to kubernetes API server.
    * items `string`
  * enablePrivateCluster `boolean`: Whether to create the cluster as a private cluster or not.

### ManagedClusterAccessProfile
* ManagedClusterAccessProfile: Managed cluster Access Profile.
  * id `string`: Resource Id
  * location **required** `string`: Resource location
  * name `string`: Resource name
  * tags `object`: Resource tags
  * type `string`: Resource type
  * properties [AccessProfile](#accessprofile)

### ManagedClusterAddonProfile
* ManagedClusterAddonProfile `object`: A Kubernetes add-on profile for a managed cluster.
  * enabled **required** `boolean`: Whether the add-on is enabled or not.

### ManagedClusterAgentPoolProfile
* ManagedClusterAgentPoolProfile: Profile for the container service agent pool.
  * availabilityZones `array`: (PREVIEW) Availability zones for nodes. Must use VirtualMachineScaleSets AgentPoolType.
    * items `string`
  * count `integer`: Number of agents (VMs) to host docker containers. Allowed values must be in the range of 1 to 100 (inclusive). The default value is 1.
  * enableAutoScaling `boolean`: Whether to enable auto-scaler
  * enableNodePublicIP `boolean`: Enable public IP for nodes
  * maxCount `integer`: Maximum number of nodes for auto-scaling
  * maxPods `integer`: Maximum number of pods that can run on a node.
  * minCount `integer`: Minimum number of nodes for auto-scaling
  * nodeTaints `array`: Taints added to new nodes during node pool create and scale. For example, key=value:NoSchedule.
    * items `string`
  * orchestratorVersion `string`: Version of orchestrator specified when creating the managed cluster.
  * osDiskSizeGB [ContainerServiceOSDisk](#containerserviceosdisk)
  * osType [OSType](#ostype)
  * provisioningState `string`: The current deployment or provisioning state, which only appears in the response.
  * scaleSetEvictionPolicy [ScaleSetEvictionPolicy](#scalesetevictionpolicy)
  * scaleSetPriority [ScaleSetPriority](#scalesetpriority)
  * type [AgentPoolType](#agentpooltype)
  * vmSize [ContainerServiceVMSize](#containerservicevmsize)
  * vnetSubnetID [ContainerServiceVnetSubnetID](#containerservicevnetsubnetid)
  * name `string`: Unique name of the agent pool profile in the context of the subscription and resource group.

### ManagedClusterAgentPoolProfileProperties
* ManagedClusterAgentPoolProfileProperties `object`: Properties for the container service agent pool profile.
  * availabilityZones `array`: (PREVIEW) Availability zones for nodes. Must use VirtualMachineScaleSets AgentPoolType.
    * items `string`
  * count `integer`: Number of agents (VMs) to host docker containers. Allowed values must be in the range of 1 to 100 (inclusive). The default value is 1.
  * enableAutoScaling `boolean`: Whether to enable auto-scaler
  * enableNodePublicIP `boolean`: Enable public IP for nodes
  * maxCount `integer`: Maximum number of nodes for auto-scaling
  * maxPods `integer`: Maximum number of pods that can run on a node.
  * minCount `integer`: Minimum number of nodes for auto-scaling
  * nodeTaints `array`: Taints added to new nodes during node pool create and scale. For example, key=value:NoSchedule.
    * items `string`
  * orchestratorVersion `string`: Version of orchestrator specified when creating the managed cluster.
  * osDiskSizeGB [ContainerServiceOSDisk](#containerserviceosdisk)
  * osType [OSType](#ostype)
  * provisioningState `string`: The current deployment or provisioning state, which only appears in the response.
  * scaleSetEvictionPolicy [ScaleSetEvictionPolicy](#scalesetevictionpolicy)
  * scaleSetPriority [ScaleSetPriority](#scalesetpriority)
  * type [AgentPoolType](#agentpooltype)
  * vmSize [ContainerServiceVMSize](#containerservicevmsize)
  * vnetSubnetID [ContainerServiceVnetSubnetID](#containerservicevnetsubnetid)

### ManagedClusterIdentity
* ManagedClusterIdentity `object`: Identity for the managed cluster.
  * principalId `string`: The principal id of the system assigned identity which is used by master components.
  * tenantId `string`: The tenant id of the system assigned identity which is used by master components.
  * type `string` (values: SystemAssigned, None): The type of identity used for the managed cluster. Type 'SystemAssigned' will use an implicitly created identity in master components and an auto-created user assigned identity in MC_ resource group in agent nodes. Type 'None' will not use MSI for the managed cluster, service principal will be used instead.

### ManagedClusterListResult
* ManagedClusterListResult `object`: The response from the List Managed Clusters operation.
  * nextLink `string`: The URL to get the next set of managed cluster results.
  * value `array`: The list of managed clusters.
    * items [ManagedCluster](#managedcluster)

### ManagedClusterLoadBalancerProfile
* ManagedClusterLoadBalancerProfile `object`: Profile of the managed cluster load balancer
  * effectiveOutboundIPs `array`: The effective outbound IP resources of the cluster load balancer.
    * items [ResourceReference](#resourcereference)
  * managedOutboundIPs `object`: Desired managed outbound IPs for the cluster load balancer.
    * count `integer`: Desired number of outbound IP created/managed by Azure for the cluster load balancer. Allowed values must be in the range of 1 to 100 (inclusive). The default value is 1. 
  * outboundIPPrefixes `object`: Desired outbound IP Prefix resources for the cluster load balancer.
    * publicIPPrefixes `array`: A list of public IP prefix resources.
      * items [ResourceReference](#resourcereference)
  * outboundIPs `object`: Desired outbound IP resources for the cluster load balancer.
    * publicIPs `array`: A list of public IP resources.
      * items [ResourceReference](#resourcereference)

### ManagedClusterPoolUpgradeProfile
* ManagedClusterPoolUpgradeProfile `object`: The list of available upgrade versions.
  * kubernetesVersion **required** `string`: Kubernetes version (major, minor, patch).
  * name `string`: Pool name.
  * osType **required** [OSType](#ostype)
  * upgrades `array`: List of orchestrator types and versions available for upgrade.
    * items `object`
      * isPreview `boolean`: Whether Kubernetes version is currently in preview.
      * kubernetesVersion `string`: Kubernetes version (major, minor, patch).

### ManagedClusterProperties
* ManagedClusterProperties `object`: Properties of the managed cluster.
  * aadProfile [ManagedClusterAADProfile](#managedclusteraadprofile)
  * agentPoolProfiles `array`: Properties of the agent pool.
    * items [ManagedClusterAgentPoolProfile](#managedclusteragentpoolprofile)
  * apiServerAccessProfile [ManagedClusterAPIServerAccessProfile](#managedclusterapiserveraccessprofile)
  * dnsPrefix `string`: DNS prefix specified when creating the managed cluster.
  * enablePodSecurityPolicy `boolean`: (PREVIEW) Whether to enable Kubernetes Pod security policy.
  * enableRBAC `boolean`: Whether to enable Kubernetes Role-Based Access Control.
  * fqdn `string`: FQDN for the master pool.
  * kubernetesVersion `string`: Version of Kubernetes specified when creating the managed cluster.
  * linuxProfile [ContainerServiceLinuxProfile](#containerservicelinuxprofile)
  * maxAgentPools `integer`: The max number of agent pools for the managed cluster.
  * networkProfile [ContainerServiceNetworkProfile](#containerservicenetworkprofile)
  * nodeResourceGroup `string`: Name of the resource group containing agent pool nodes.
  * provisioningState `string`: The current deployment or provisioning state, which only appears in the response.
  * servicePrincipalProfile [ManagedClusterServicePrincipalProfile](#managedclusterserviceprincipalprofile)
  * windowsProfile [ManagedClusterWindowsProfile](#managedclusterwindowsprofile)

### ManagedClusterServicePrincipalProfile
* ManagedClusterServicePrincipalProfile `object`: Information about a service principal identity for the cluster to use for manipulating Azure APIs.
  * clientId **required** `string`: The ID for the service principal.
  * secret `string`: The secret password associated with the service principal in plain text.

### ManagedClusterUpgradeProfile
* ManagedClusterUpgradeProfile `object`: The list of available upgrades for compute pools.
  * id `string`: Id of upgrade profile.
  * name `string`: Name of upgrade profile.
  * properties **required** [ManagedClusterUpgradeProfileProperties](#managedclusterupgradeprofileproperties)
  * type `string`: Type of upgrade profile.

### ManagedClusterUpgradeProfileProperties
* ManagedClusterUpgradeProfileProperties `object`: Control plane and agent pool upgrade profiles.
  * agentPoolProfiles **required** `array`: The list of available upgrade versions for agent pools.
    * items [ManagedClusterPoolUpgradeProfile](#managedclusterpoolupgradeprofile)
  * controlPlaneProfile **required** [ManagedClusterPoolUpgradeProfile](#managedclusterpoolupgradeprofile)

### ManagedClusterWindowsProfile
* ManagedClusterWindowsProfile `object`: Profile for Windows VMs in the container service cluster.
  * adminPassword `string`: The administrator password to use for Windows VMs.
  * adminUsername **required** `string`: The administrator username to use for Windows VMs.

### OSType
* OSType `string` (values: Linux, Windows): OsType to be used to specify os type. Choose from Linux and Windows. Default to Linux.

### OperationListResult
* OperationListResult `object`: The List Compute Operation operation response.
  * value `array`: The list of compute operations
    * items [OperationValue](#operationvalue)

### OperationValue
* OperationValue `object`: Describes the properties of a Compute Operation value.
  * display [OperationValueDisplay](#operationvaluedisplay)
  * name `string`: The name of the compute operation.
  * origin `string`: The origin of the compute operation.

### OperationValueDisplay
* OperationValueDisplay `object`: Describes the properties of a Compute Operation Value Display.
  * description `string`: The description of the operation.
  * operation `string`: The display name of the compute operation.
  * provider `string`: The resource provider for the operation.
  * resource `string`: The display name of the resource the operation applies to.

### Resource
* Resource `object`: The Resource model definition.
  * id `string`: Resource Id
  * location **required** `string`: Resource location
  * name `string`: Resource name
  * tags `object`: Resource tags
  * type `string`: Resource type

### ResourceReference
* ResourceReference `object`: A reference to an Azure resource.
  * id `string`: The fully qualified Azure resource id.

### ScaleSetEvictionPolicy
* ScaleSetEvictionPolicy `string` (values: Delete, Deallocate): ScaleSetEvictionPolicy to be used to specify eviction policy for low priority virtual machine scale set. Default to Delete.

### ScaleSetPriority
* ScaleSetPriority `string` (values: Low, Regular): ScaleSetPriority to be used to specify virtual machine scale set priority. Default to regular.

### SubResource
* SubResource `object`: Reference to another subresource.
  * id `string`: Resource ID.
  * name `string`: The name of the resource that is unique within a resource group. This name can be used to access the resource.
  * type `string`: Resource type

### TagsObject
* TagsObject `object`: Tags object for patch operations.
  * tags `object`: Resource tags.


