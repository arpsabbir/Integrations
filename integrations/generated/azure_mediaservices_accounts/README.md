# @datafire/azure_mediaservices_accounts

Client library for Azure Media Services

## Installation and Usage
```bash
npm install --save @datafire/azure_mediaservices_accounts
```
```js
let azure_mediaservices_accounts = require('@datafire/azure_mediaservices_accounts').create({
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

This Swagger was generated by the API Framework.

## Actions

### Operations_List
Lists all the Media Services operations.


```js
azure_mediaservices_accounts.Operations_List({
  "api-version": ""
}, context)
```

#### Input
* input `object`
  * api-version **required** `string`: The Version of the API to be used with the client request.

#### Output
* output [OperationCollection](#operationcollection)

### Locations_CheckNameAvailability
Checks whether the Media Service resource name is available.


```js
azure_mediaservices_accounts.Locations_CheckNameAvailability({
  "subscriptionId": "",
  "locationName": "",
  "parameters": {},
  "api-version": ""
}, context)
```

#### Input
* input `object`
  * subscriptionId **required** `string`: The unique identifier for a Microsoft Azure subscription.
  * locationName **required** `string`: The name of the location
  * parameters **required** [CheckNameAvailabilityInput](#checknameavailabilityinput)
  * api-version **required** `string`: The Version of the API to be used with the client request.

#### Output
* output [EntityNameAvailabilityCheckOutput](#entitynameavailabilitycheckoutput)

### Mediaservices_ListBySubscription
List Media Services accounts in the subscription.


```js
azure_mediaservices_accounts.Mediaservices_ListBySubscription({
  "subscriptionId": "",
  "api-version": ""
}, context)
```

#### Input
* input `object`
  * subscriptionId **required** `string`: The unique identifier for a Microsoft Azure subscription.
  * api-version **required** `string`: The Version of the API to be used with the client request.

#### Output
* output [SubscriptionMediaServiceCollection](#subscriptionmediaservicecollection)

### Mediaservices_GetBySubscription
Get the details of a Media Services account


```js
azure_mediaservices_accounts.Mediaservices_GetBySubscription({
  "subscriptionId": "",
  "accountName": "",
  "api-version": ""
}, context)
```

#### Input
* input `object`
  * subscriptionId **required** `string`: The unique identifier for a Microsoft Azure subscription.
  * accountName **required** `string`: The Media Services account name.
  * api-version **required** `string`: The Version of the API to be used with the client request.

#### Output
* output [SubscriptionMediaService](#subscriptionmediaservice)

### Mediaservices_List
List Media Services accounts in the resource group


```js
azure_mediaservices_accounts.Mediaservices_List({
  "subscriptionId": "",
  "resourceGroupName": "",
  "api-version": ""
}, context)
```

#### Input
* input `object`
  * subscriptionId **required** `string`: The unique identifier for a Microsoft Azure subscription.
  * resourceGroupName **required** `string`: The name of the resource group within the Azure subscription.
  * api-version **required** `string`: The Version of the API to be used with the client request.

#### Output
* output [MediaServiceCollection](#mediaservicecollection)

### Mediaservices_Delete
Deletes a Media Services account


```js
azure_mediaservices_accounts.Mediaservices_Delete({
  "subscriptionId": "",
  "resourceGroupName": "",
  "accountName": "",
  "api-version": ""
}, context)
```

#### Input
* input `object`
  * subscriptionId **required** `string`: The unique identifier for a Microsoft Azure subscription.
  * resourceGroupName **required** `string`: The name of the resource group within the Azure subscription.
  * accountName **required** `string`: The Media Services account name.
  * api-version **required** `string`: The Version of the API to be used with the client request.

#### Output
*Output schema unknown*

### Mediaservices_Get
Get the details of a Media Services account


```js
azure_mediaservices_accounts.Mediaservices_Get({
  "subscriptionId": "",
  "resourceGroupName": "",
  "accountName": "",
  "api-version": ""
}, context)
```

#### Input
* input `object`
  * subscriptionId **required** `string`: The unique identifier for a Microsoft Azure subscription.
  * resourceGroupName **required** `string`: The name of the resource group within the Azure subscription.
  * accountName **required** `string`: The Media Services account name.
  * api-version **required** `string`: The Version of the API to be used with the client request.

#### Output
* output [MediaService](#mediaservice)

### Mediaservices_Update
Updates an existing Media Services account


```js
azure_mediaservices_accounts.Mediaservices_Update({
  "subscriptionId": "",
  "resourceGroupName": "",
  "accountName": "",
  "parameters": {},
  "api-version": ""
}, context)
```

#### Input
* input `object`
  * subscriptionId **required** `string`: The unique identifier for a Microsoft Azure subscription.
  * resourceGroupName **required** `string`: The name of the resource group within the Azure subscription.
  * accountName **required** `string`: The Media Services account name.
  * parameters **required** [MediaService](#mediaservice)
  * api-version **required** `string`: The Version of the API to be used with the client request.

#### Output
* output [MediaService](#mediaservice)

### Mediaservices_CreateOrUpdate
Creates or updates a Media Services account


```js
azure_mediaservices_accounts.Mediaservices_CreateOrUpdate({
  "subscriptionId": "",
  "resourceGroupName": "",
  "accountName": "",
  "parameters": {},
  "api-version": ""
}, context)
```

#### Input
* input `object`
  * subscriptionId **required** `string`: The unique identifier for a Microsoft Azure subscription.
  * resourceGroupName **required** `string`: The name of the resource group within the Azure subscription.
  * accountName **required** `string`: The Media Services account name.
  * parameters **required** [MediaService](#mediaservice)
  * api-version **required** `string`: The Version of the API to be used with the client request.

#### Output
* output [MediaService](#mediaservice)

### Mediaservices_SyncStorageKeys
Synchronizes storage account keys for a storage account associated with the Media Service account.


```js
azure_mediaservices_accounts.Mediaservices_SyncStorageKeys({
  "subscriptionId": "",
  "resourceGroupName": "",
  "accountName": "",
  "parameters": {},
  "api-version": ""
}, context)
```

#### Input
* input `object`
  * subscriptionId **required** `string`: The unique identifier for a Microsoft Azure subscription.
  * resourceGroupName **required** `string`: The name of the resource group within the Azure subscription.
  * accountName **required** `string`: The Media Services account name.
  * parameters **required** [SyncStorageKeysInput](#syncstoragekeysinput)
  * api-version **required** `string`: The Version of the API to be used with the client request.

#### Output
*Output schema unknown*



## Definitions

### ApiError
* ApiError `object`: The API error.
  * error [ODataError](#odataerror)

### CheckNameAvailabilityInput
* CheckNameAvailabilityInput `object`: The input to the check name availability request.
  * name `string`: The account name.
  * type `string`: The account type. For a Media Services account, this should be 'MediaServices'.

### EntityNameAvailabilityCheckOutput
* EntityNameAvailabilityCheckOutput `object`: The response from the check name availability request.
  * message `string`: Specifies the detailed reason if the name is not available.
  * nameAvailable **required** `boolean`: Specifies if the name is available.
  * reason `string`: Specifies the reason if the name is not available.

### Location
* Location `object`
  * name **required** `string`

### MediaService
* MediaService `object`: A Media Services account.
  * properties [MediaServiceProperties](#mediaserviceproperties)
  * location `string`: The Azure Region of the resource.
  * tags `object`: Resource tags.
  * id `string`: Fully qualified resource ID for the resource.
  * name `string`: The name of the resource.
  * type `string`: The type of the resource.

### MediaServiceCollection
* MediaServiceCollection `object`: A collection of MediaService items.
  * @odata.nextLink `string`: A link to the next page of the collection (when the collection contains too many results to return in one response).
  * value `array`: A collection of MediaService items.
    * items [MediaService](#mediaservice)

### MediaServiceProperties
* MediaServiceProperties `object`: Properties of the Media Services account.
  * mediaServiceId `string`: The Media Services account ID.
  * storageAccounts `array`: The storage accounts for this resource.
    * items [StorageAccount](#storageaccount)

### Metric
* Metric `object`: A metric emitted by service.
  * aggregationType `string` (values: Average, Count, Total): The metric aggregation type
  * dimensions `array`: The metric dimensions.
    * items [MetricDimension](#metricdimension)
  * displayDescription `string`: The metric display description.
  * displayName `string`: The metric display name.
  * name `string`: The metric name.
  * unit `string` (values: Bytes, Count, Milliseconds): The metric unit

### MetricDimension
* MetricDimension `object`: A metric dimension.
  * displayName `string`: The display name for the dimension.
  * name `string`: The metric dimension name.
  * toBeExportedForShoebox `boolean`: Whether to export metric to shoebox.

### MetricProperties
* MetricProperties `object`: Metric properties.
  * serviceSpecification [ServiceSpecification](#servicespecification)

### ODataError
* ODataError `object`: Information about an error.
  * code `string`: A language-independent error name.
  * details `array`: The error details.
    * items [ODataError](#odataerror)
  * message `string`: The error message.
  * target `string`: The target of the error (for example, the name of the property in error).

### Operation
* Operation `object`: An operation.
  * display [OperationDisplay](#operationdisplay)
  * name **required** `string`: The operation name.
  * origin `string`: Origin of the operation.
  * properties [MetricProperties](#metricproperties)

### OperationCollection
* OperationCollection `object`: A collection of Operation items.
  * @odata.nextLink `string`: A link to the next page of the collection (when the collection contains too many results to return in one response).
  * value `array`: A collection of Operation items.
    * items [Operation](#operation)

### OperationDisplay
* OperationDisplay `object`: Operation details.
  * description `string`: The operation description.
  * operation `string`: The operation type.
  * provider `string`: The service provider.
  * resource `string`: Resource on which the operation is performed.

### Provider
* Provider `object`: A resource provider.
  * providerName **required** `string`: The provider name.

### ServiceSpecification
* ServiceSpecification `object`: The service metric specifications.
  * metricSpecifications `array`: List of metric specifications.
    * items [Metric](#metric)

### StorageAccount
* StorageAccount `object`: The storage account details.
  * id `string`: The ID of the storage account resource. Media Services relies on tables and queues as well as blobs, so the primary storage account must be a Standard Storage account (either Microsoft.ClassicStorage or Microsoft.Storage). Blob only storage accounts can be added as secondary storage accounts.
  * type **required** `string` (values: Primary, Secondary): The type of the storage account.

### SubscriptionMediaService
* SubscriptionMediaService `object`: A Media Services account.
  * properties [MediaServiceProperties](#mediaserviceproperties)
  * location `string`: The Azure Region of the resource.
  * tags `object`: Resource tags.
  * id `string`: Fully qualified resource ID for the resource.
  * name `string`: The name of the resource.
  * type `string`: The type of the resource.

### SubscriptionMediaServiceCollection
* SubscriptionMediaServiceCollection `object`: A collection of SubscriptionMediaService items.
  * @odata.nextLink `string`: A link to the next page of the collection (when the collection contains too many results to return in one response).
  * value `array`: A collection of SubscriptionMediaService items.
    * items [SubscriptionMediaService](#subscriptionmediaservice)

### SyncStorageKeysInput
* SyncStorageKeysInput `object`: The input to the sync storage keys request.
  * id `string`: The ID of the storage account resource.


