# @datafire/lumminary

Client library for Lumminary API

## Installation and Usage
```bash
npm install --save @datafire/lumminary
```
```js
let lumminary = require('@datafire/lumminary').create({
  Bearer: ""
});

.then(data => {
  console.log(data);
});
```

## Description

# Introduction
The Lumminary API was built to allow third parties to interact with Lumminary customers and gain access to their genetic data. The Lumminary API is fast, scalable and highly secure. All requests to the Lumminary API take place over SSL, which means all communication of Customer data is encrypted.

Before we dive in, some definitions. This is what we mean by:

|Term|Definition|
|-----------|-----------|
|**Third party**|A third party (also referred to as "partner" or as "you") is a company which offers services and products using genetic data.|
|**Lumminary clients**|The Lumminary client (also referred to as "customer") is an individual who has created an account on the Lumminary platform.|
|**Lumminary**|This is  us - our services including the Lumminary platform, the API, the DNA App Store, the DNA Vault, the "Connect with Lumminary" button, and the website in its totality. |
|**CWL**|This is the acronym for the "Connect with Lumminary" button.|
|**dataset**|This is the term we use when we refer to a customer's genetic data.|
|**Lumminary API**|This is a library/module that you can use to integrate your apps with the Lumminary platform.|
|**Lumminary toolkit**|This is a stand alone application which helps you integrate with Lumminary without writing any code or interacting with the Lumminary API.|

Let's dive in, now. 
* [**Overview**](#section/Introduction/Overview)

* [**Install Lumminary API Client and Toolkit**](#Install-Lumminary-API-Client-andor-Toolkit)
* [**Obtaining credentials**](#Obtaining-credentials)
* [**Query customers authorizations**](#Query-customers-authorizations)
* [**Query customer genetic data**](#Query-customer-genetic-data)
* [**Submit reports**](#Submit-reports)

* [**"Connect with Lumminary" button**](#the-connect-with-lumminary-button)

* [**API specs**](#tag/Lumminary)

## Overview

In order to use Lumminary services, you'll need to install the Lumminary API Client or Toolkit. The Lumminary API Client and Toolkit are available in multiple programming languages, and we also provide a sandbox environment which you can use for integration and tests.

There are a couple of differences between the API Client and the Toolkit. Mainly, it's about the ease of use for integration. The Toolkit is basically a stand-alone application that facilitates the integration with the Lumminary API without the need to modify your already existing code.

You use the Lumminary API Client when you want to integrate it inside your own application. This means it gives you full flexibility regarding the integration into your own workflow.

You use the Lumminary Toolkit for an integration where the Toolkit is placed alongside your own application. You can use the Toolkit from the CLI - for example, to run a cronjob that processes incoming orders. The Toolkit uses the Lumminary API Client.

# Install Lumminary API Client and/or Toolkit

We provide the Lumminary API Client and Toolkit in multiple programming languages - default are PHP (minimum version 7.0), Python2.7 and Python3. However, if you need them in another language (Java, Obj-C, JavaScript, C#, Perl, CURL), please contact us.


## How to install the Lumminary API Client

#### PHP example:
The PHP Lumminary API Client is available at: https://github.com/Lumminary/lumminary-api-client-php

If you are already using [Composer](https://getcomposer.org), you can import the project by adding the following to your `composer.json`
```json
"repositories": [
    {
        "type": "git",
        "url": "https://github.com/Lumminary/lumminary-api-client-php.git",
        "reference": "master"
    }
],
"require": {
    "lumminary/api-client-php": "v1.0.6"
}
```

Then run `composer update lumminary/api-client-php`

#### Python example:

The Python Lumminary API Client is available at: https://github.com/Lumminary/lumminary-api-client-python

To install directly, run

```bash
pip install git+https://git@github.com/Lumminary/lumminary-api-client-python.git@v1.0.7#egg=lumminary-api-client
```

Or add the following line in your requirements.txt

```bash
git+https://git@github.com/Lumminary/lumminary-api-client-python.git@v1.0.7#egg=lumminary-api-client
```

## How to install the Lumminary Toolkit

#### PHP example:
The PHP Lumminary Toolkit is available at: https://github.com/Lumminary/lumminary-toolkit-php

To install the Lumminary Toolkit, run the following command where 'lumminary-toolkit-directory' is the directory where you want to install the Lumminary Toolkit:

`git clone git@github.com:Lumminary/lumminary-toolkit-php.git lumminary-toolkit-directory`

#### PYTHON example:

The Python Lumminary Toolkit is available at: https://github.com/Lumminary/lumminary-toolkit-python

To install the Lumminary Toolkit, run the following command where 'lumminary-toolkit-directory' is the directory where you want to install the Lumminary Toolkit:

```bash
git clone git@github.com:Lumminary/lumminary-toolkit-python.git lumminary-toolkit-directory
cd lumminary-toolkit-directory
virtualenv env
source env/bin/activate
pip install -r requirements.txt
```

Note that before running the toolkit, you should have the virtualenv enabled, like so : `source lumminary-toolkit-directory/env/bin/activate`

## Toolkit Setup

We recommend to run the Toolkit in a cronjob; at every run it will check for new Authorizations (Orders) and will download them; afterwards it will check for a new reports folder inside the old authorizations, process the reports, and delete the processed Authorizations and Reports from your server. 

The first step after you clone the Lumminary Toolkit project for your language is to configure it with your credentials. 

Go to the Lumminary Toolkit base diretory `cd lumminary-toolkit-directory`. Under the Toolkit directory, you will find a file `config/config_template.json` which has the following structure:

```json
{
    "api_key": <your-api-key>,
    "product_uuid": <your-product-uuid>,
    "api_host": "https:\/\/api.lumminary.com\/v1",
    "output_root": <your-authorization-data-basepath>,
    "export_handler": <your-export-handler-class>,
    "product_name": <your-product-name>,
    "operations": [
        "pull_datasets",
        "push_reports"
    ],
    "optional": {
        "dna_data_filename": "dna-data.tsv",
        "authorization_metadata_filename": "authorization-metadata.json"
    }
}
```

You should copy this config `cp config/config_template.json config/my-product1-config.json` then edit it `vim config/my-product1-config.json` to contain the following values:

| Config attribute | Example Value                      | Description |
|------------------|------------------------------------|-------------|
| api_key        | `"TiiU...bqg=="`                   |Your Lumminary API key.<br> You can obtain it from the Lumminary Admin  |
| product_uuid   | `"1234-1234-1234-1234"`            |Your product UUID. This value can be obtained from the Lumminary Admin |
| api_host       | `"https:\/\/api.lumminary.com\/v1"`   |   The API endpoint to use.<br>For the sandbox environment you can use "https:\/\/sandbox-api.lumminary.com\/v1"    |
| output_root    | `"/var/lumminary-orders/product1/"`         | The base directory where the Toolkit places the Authorizations for your Product <br> The Lumminary Toolkit will *never* overwrite Authorization data or create this directory, to protect from overwrites or typos    |
| export_handler |`"export_handler_tsv"`  | If you have a custom export handler, then your Lumminary contact will provide you with the name of your export handler.   |
| operations       |`["pull_datasets", "push_reports"]`        | These are two optional parameters that define the tasks that the Toolkit should perform. Possible values are: <br> 1. `pull_datasets` - this tells the Toolkit to download the Customer Authorization (Customer details and genetic data) <br> 2. `push_reports` - this tells the Toolkit to push the results to the API; see below for more details|
| optional       | `{}`                               | Export handler specific value |

After updating the config file for your Toolkit, it should look similar to (Note that these are all dummy values) :

```json
{
    "api_key": "TiiU...bqg==",
    "product_uuid": "1234-1234-1234-1234",
    "api_host": "https:\/\/api.lumminary.com\/v1",
    "output_root": "\/var\/lumminary-orders\/product1\/",
    "export_handler": "export_handler_tsv",
    "product_name": "product 1",
    "operations": [
        "pull_datasets",
        "push_reports"
    ],
    "optional": {
        "dna_data_filename": "dna-data.tsv",
        "authorization_metadata_filename": "authorization-metadata.json"
    }
}
```

You can now save and exit the text editor `:wq` and start polling the API for new Authorizations :

Python

```bash
# While still in the <lumminary-toolkit> directory
source env/bin/activate;
python lumminary_partner_toolkit.py --config-path config/my-lumminary-product1-config.json
```

PHP

```bash
# While still in the <lumminary-toolkit> directory
php lumminary-partner-toolkit.php --config-path config/my-lumminary-product1-config.json
```

When your Product receives new Authorizations, the Toolkit will pull all the relevant data and save it in the following files:

```bash
# The DNA data file. Format compatible with 23AndMe by default
<output_root>/<authorization_uuid>/dna-data.tsv

# The Authorization metadata
<output_root>/<authorization_uuid>/authorization.json
```

The contents of the files pulled when processing an Authorization are as follows:

```bash
$ head -n 5 <output_root>/<authorization_uuid>/dna-data.tsv
# rsid      chromosome  position        genotype
rs12070387  1           6267531         CC
rs149124387 1           12025561        CC
rs116458387 1           14920119        AA
rs4436387   1           15498452        CC

$ cat <output_root>/<authorization_uuid>/authorization.json 
{
    "authorization": <authorization_uuid>,
    "created_timestamp_utc": 1542920184,
    "customer": <customer_uuid>,
    "customer_address": {
        "address1": <address1>,
        "address2": <address2>,
        "city": <city>,
        "country": <country>,
        "state": <state>,
        "zipcode": <zipcode> 
    },
    "customer_email": <customer_email>,
    "customer_name": {
        "first_name": <customer_first_name>,
        "last_name": <customer_last_name>
    },
    "dataset": <dataset_uuid>,
    "product": <your_product_uuid>
}
```

After the Toolkit downloaded the Authorizations, you need to process the Customer genetic data file and the Customer details, individually. The Lumminary API supports multiple types of products:

| Scenario | How to Report |                    
|------------------|------------------------------------|
|The product is a file (.pdf, .jpeg etc.) | Put the result file(s) into the `tmp_reports` directory. Please refer to the Note underneath this table. |
|The product requires authentication | Create a file with the name `result.json` into the `tmp_reports` directory, with the following content: <br> `{ "credentials": { "username": "username@example.com", "password": "your generated password", "url": "https://your-website.com/report"}}`<br> The `url` should point to a login page that upon authentication redirects the user to the report page. You can find the customer's email address in the `authorization-metadata.json` and the `password` attribute must be a secure password. Please refer to the Note underneath this table. |
|The product is a physical product| Create a file with the name `result.json` into the `tmp_reports` directory, with the following content: <br> `{"physical_product": { "physical_product_completed": true }}` <br> This should be done upon dispatch. Please refer to the Note underneath this table. |
|An error occurred| Create a file with the name `result.json` into the `tmp_reports` directory, with the following content: <br> `{ "unfulfillable": {"error": "Reasons for why it is unfulfillable", }}` <br> The error message is for Lumminary internal usage, and it won't be visible to the customer. This will delete your Authorization, making it unuseable thereafter. So please use this only for unfixable errors, and never for temporary errors you attempt to resolve. Please refer to the Note underneath this table. |

###### Note
For each scenario above, we recommend you use a temporary directory to avoid uploading incomplete files or reports. So your workflow should be:
* create a temporary directory inside the `<output_root>/<authorization_uuid>`, such as `<output_root>/<authorization_uuid>/tmp_reports/`  
* place your result file(s) in the `tmp_reports` directory (as in the above table)
* rename the directory from `tmp_reports` to `reports`

We recommend running the Toolkit in a cronjob, wrapped by some locking mechanism. Also, Toolkit logs are very minimal but can be very helpful when debugging an issue, so please consider saving them to a file. For example, the following cronjob runs the Toolkit every minute:

```bash
# Open the crontab
crontab -e
```

PHP Toolkit

```bash
# Add the following line (replace <lumminary-toolkit-directory> with the absolute path of the Lumminary Toolkit)
* * * * * flock /var/lock/lumminary-toolkit.lock php <lumminary-toolkit-directory>/lumminary-partner-toolkit.php --config-path <lumminary-toolkit-directory>/config/my-product1-config.json >> /var/log/lumminary-toolkit.log
```

Python Toolkit

```bash
# Add the following line (replace <lumminary-toolkit-directory> with the absolute path of the Lumminary Toolkit)
* * * * * flock /var/lock/lumminary-toolkit.lock source env/bin/activate; python <lumminary-toolkit-directory>/lumminary_partner_toolkit.py --config-path <lumminary-toolkit-directory>/config/my-product1-config.json
```

## API endpoints
Lumminary provides two endpoint APIs, sandbox and production. You can use the sandbox for your integration and testing, simulate orders, upload genetic data, and generate reports. The sandbox works exactly like the production environment, and you can test your end-to-end integration.

In order to simulate a complete order, you need to use this test credit card: 

|Credit card number  | Expiration date| CVV2|
|--------------------|----------------|-----|
|4242 4242 4242 4242 |  12/30         | 123 |

### Sandbox
website: [sandbox-www.lumminary.com](https://sandbox-www.lumminary.com)

api-hostname: [sandbox-api.lumminary.com/v1](https://sandbox-api.lumminary.com/v1)

### Production
website: [lumminary.com](https://lummianary.com)

api-hostname: [api.lumminary.com/v1](https://api.lumminary.com/v1)

# Obtaining credentials
To obtain credentials, you need to register as a Lumminary partner. You can do this by [filling in this form](https://lumminary.com/register-for-connect-with-lumminary).

You will then receive the following:

|Credentials|Description|
|-------|-------|
|Product UUID|Each product you register on the Lumminary platform gets an UUID which will be used to identify that product to the Lumminary API|
|API key|The secret API key associated with the Product UUID|
|Partner UUID|Upon your first registration on the Lumminary platform, you will receive a single Partner UUID, which identifies you as one entity, regardless of product. This identifier is used for the Connect with Lumminary (CWL) functionality.|
|CWL Encryption Key|The CWL encryption key is associated with the Partner UUID and is used to encrypt all communication for the Connect with Lumminary functionality.|

Each product or service needs to have its own product UUID and API key, which means you have to fill in the form for all products and services that require access to Lumminary customer data.  

## Configure the credentials to the Lumminary API Client
The easiest way to set up your credentials is to use an environment file.

For this, you must create a file named `env.json` (but any name will do) in your project directory, which should contain:
```json
{
    "product_uuid": <your_product_uuid>,
    "api_key": <your_product_api_key>,
    "role": "role_product",
    "api_host": <lumminary_api_hostname_endpoint>
}
```

In order to load the Credentials from the `env.json`, you can use the following code:

#### PHP example:
```php
require_once(__DIR__."/vendor/autoload.php");
$credentials = new Lumminary\Client\Credentials();
$credentials->loadJSONCredentials(__DIR__."/env.json");
```

#### Python example:
```python
import lumminary_sdk as lumminary
import os

credentials = lumminary.Credentials()
credentials.load_json_credentials(
    os.path.join(
        os.getcwd(),
        "env.json"
    )
)
```

## Alternative credentials configuration
You also have the option of passing the credentials as constructor parameters when instantiating the `Credentials` class.

#### PHP example:

```php
require_once(__DIR__."/vendor/autoload.php");
$credentials = new Lumminary\Client\Credentials(
    <lumminary_api_hostname_endpoint>,
    <your_product_uuid>,
    <your_product_api_key>
);
```

#### Python example:

```python
import lumminary_sdk as lumminary

credentials = lumminary.Credentials(
    product_uuid = <your_product_uuid>,
    api_key = <your_product_api_key>,
    api_host = <lumminary_api_hostname_endpoint>,
    role = "role_product"
)
```

## Create an API instance

With the credentials configured and loaded, you can create an API client like so : 

#### PHP example

```php
$apiClient = new Lumminary\Client\ApiClient($credentials);
```

#### Python example

```python
apiClient = lumminary.LumminaryApi(credentials)
```

# Query customers authorizations
An Authorization represents permission from a client to access their personal and genetic data. 

There are 2 situations where customers grant you access to their data: 
* when a customer buys your product from the Lumminary DNA App Store
* when a customer clicks on the "Connect with Lumminary" button on your website

Each time either of the above situations happens, our platform creates an Authorization UUID. You can reliably assume that if you have an Authorization UUID, you automatically have access to all the personal information and genetic data needed by your products and services. After you process an Authorization you need to mark it as processed; processed Authorizations will no longer be on the list of new authorizations.

There are two ways to obtain the Authorization UUID:
* _polling_ - this method allows you to periodically interrogate our API and pulls the list of Authorization UUIDs. 
* _webhooks_ (coming soon) - this method allows our API to push the Authorization UUIDs into your platform.

## Poll method

To use the polling method, your servers periodically interrogate for new Authorization UUIDs. Please keep in mind that Authorizations not marked as processed will always be returned when polling for new Authorizations. This means there's a risk of parallel processing the same Authorization. To avoid this, you can, for example, consider using locking when processing.

#### A PHP example of using the polling API looks like:

```php
$productAuthorizations = $apiClient->getAuthorizationsQueue(
    $apiClient->getCredentials()->getProductUuid(),
);

foreach($productAuthorizations as $productAuthorization)
{
    /**
     *  Add your code for processing customer data here
     **/ 
    
    // Mark Authorization as processed 
    $apiClient->postProductAuthorization(
        $productAuthorization["productUuid"],
        $productAuthorization["authorizationUuid"]
    );
}
```

#### A Python example of using the polling API looks like:

```python
productAuthorizations = apiClient.get_authorizations_queue(
    apiClient.get_credentials().product_uuid
)

for productAuthorization in productAuthorizations:
    #######
    #   Add your code for processing customer data here
    #######

    # Mark Authorization as processed
    apiClient.post_product_authorization(
        productAuthorization.product_uuid,
        productAuthorization.authorization_uuid
    )
```

Based on the Authorization object obtained previously, we can now query the customer's information (personal details and genetic data).

#### PHP example:
```php
$authorizationMetadata = $apiClient->authorizationMetadata($productAuthorization["authorizationUuid"]);
```

#### Python example:
```python
authorizationMetadata = apiClient.authorization_metadata(productAuthorization.authorization_uuid)
```

#### authorizationMetadata object object structure

| Attribute name            | Description                                                                                |
|:-------------------------:|:-------------------------------------------------------------------------------------------|
| `customer`                | The UUID of the customer granting the Authorization                                        |
| `product`                 | The UUID of the product that was authorized (your product UUID)                            |
| `authorization`           | The UUID of the granted Authorization.                                                     |
| `created_timestamp_utc`   | The unix timestamp in UTC time zone when the customer granted the Authorization            |
| `dataset`                 | (present only if requested) The UUID of the dataset authorized by the customer             |
| `customer_email`          | (present only if requested) Customer contact email                                         |
| `customer_name`           | (present only if requested) Customer name                                                  |
| `customer_address`        | (present only if requested) Customer address                                               |

By *present only if requested* we mean this attribute will be returned if at the time of configuring either the "Connect with Lumminary" button or your product, you have explicitly requested for that particular set of data.

# Query customer genetic data
Based on the Authorization object obtained previously, now we have authorizationMetadata which contains the customer's information (personal details and genetic data). Let's use this information to extract some customer genetic data.

## Get individual SNPs
Out of all the available SNPs in the dataset, you can only access those for which the customer has previously granted permission.

For example, fetching details for a particular SNP:

#### PHP example:
```php
$rsId = "rs114326054";
$snpDetails = null;

// check to see if you have access to the customer genetic data
if (isset($productAuthorization["scopes"]["dataset"]))
{
    // get SNP information
    $snpDetails = $apiClient->getClientSnp(
        $productAuthorization["clientUuid"],
        $productAuthorization["scopes"]["dataset"],
        $rsId
    );
}
```

#### Python example:
```python
rsId = "rs114326054"
snpDetails = None

# check to see if you have access to the customer genetic data
if hasattr(productAuthorization.scopes, "dataset"):
    # get SNP information
    snpDetails = apiClient.get_client_snp(
        productAuthorization.client_uuid,
        productAuthorization.scopes.dataset,
        rsId
    )
```

##### The snpDetails object will contain these important attributes:

| Attribute name PHP     | Attribute name Python        | Description                                               |
|:-------------------------:|:-------------------------:|:----------------------------------------------------------|
| `snpId`                 | `snp_id`                    | The rsid of the SNP                                       |
| `referenceGenome`        |`reference_genome`          | The reference genome known to be used by the Dataset's source. <br> This impacts the reference allele, location, and based on the dbSNP build, also the SNP's accession |
| `genotypedAlleles`       | `genotyped_alleles`        | The genotype value of the customer's queried SNP. <br><br> If the attribute of this SNP has the `phased` flag set to True, <br>the first items in the lists for all SNPs will be on the same inherited chromosome, <br>and analogous for the second item. <br><br> If the SNP is unphased, the order of the items is irrelevant |
|`phased`                   | `phased`                  | A boolean. True if the SNP is known to be phased, False otherwise |
|`chromosomeAccession`     | `chromosome_accession`     | This is the chromosome accession number where the SNP is located; in the format of NC_00x |
|`location`                 | `location`                | This is the customer's SNP's location on the chromosome |

When trying to access any customer's SNP for which you don't have permission, an `Unauthorized` exception will be raised.

## Get all authorized SNPs

The function below returns all SNPs your product has access to. These are all the SNPs configured as mandatory for your product, as well as all SNPs that are configured as optional and available in the customer's data set. We encourage you to use this option if you need to get all available SNPs, because it is faster than fetching SNP details one by one.

For example, fetching all authorized SNPs:

#### PHP example:
```php
$datasetSnps = null;

// check to see if you have access to the customer genetic data
if (isset($productAuthorization["scopes"]["dataset"]))
{
    // get all authorized SNPs
    $datasetSnps = $apiClient->getClientSnpGroup(
        $productAuthorization["clientUuid"], 
        $productAuthorization["scopes"]["dataset"]
    );
}
```

#### Python example:
```python
datasetSnps = None

# check to see if you have access to the customer genetic data
if hasattr(productAuthorization.scopes, "dataset"):
    # get all authorized SNPs
    datasetSnps = apiClient.get_client_snp_group(
        productAuthorization.client_uuid,
        productAuthorization.scopes.dataset
    )
```

##### The datasetSnps variable will be a list of objects each having the following attributes:

| Attribute name PHP     | Attribute name Python        | Description                                               |
|:-------------------------:|:-------------------------:|:----------------------------------------------------------|
| `snpId`                  | `snp_id`                   | The rsid of the SNP                                       |
| `referenceGenome`        |`reference_genome`          | The reference genome known to be used by the Dataset's source. <br> This impacts the reference allele, location, and based on the dbSNP build, also the SNP's accession |
| `genotypedAlleles`       | `genotyped_alleles`        | The genotype value of the customer's queried SNP. <br><br> If the attribute of this SNP has the `phased` flag set to True, <br>the first items in the lists for all SNPs will be on the same inherited chromosome, <br>and analogous for the second item. <br><br> If the SNP is unphased, the order of the items is irrelevant |
|`phased`                   | `phased`                  | A boolean. True if the SNP is known to be phased, False otherwise |
|`chromosomeAccession`     | `chromosome_accession`     | This is the chromosome accession number where the SNP is located; in the format of NC_00x |
|`location`                 | `location`                | This is the customer's SNP's location on the chromosome |

When trying to access any customer's SNP for which you don't have permission, an `Unauthorized` exception will be raised.

## Get Genes

Along with individual SNPs, you can also get all the authorized SNPs from a particular gene, that are available in the customer's dataset.

Here, by genes, we refer strictly to the genomic region that produces some protein, without considering regulatory or noncoding regions that influence gene expression.

The gene name (known as symbol) can be from either of these two databases - NCBI and Ensembl.

For example, fetching details for a gene symbol:

#### PHP example
```php
$geneSymbol = "C1ORF159";
$geneDetails = null;
// check to see if you have access to the customer genetic data
if (isset($productAuthorization["scopes"]["dataset"]))
{
    // get all authorized SNPs within a gene
    $geneDetails = $apiClient->getClientGene(
        $productAuthorization["clientUuid"],
        $productAuthorization["scopes"]["dataset"],
        $geneSymbol
    );
}
```

#### Python example
```python
geneSymbol = "C1ORF159"
geneDetails = None
# check to see if you have access to the customer genetic data
if hasattr(productAuthorization.scopes, "dataset"):
    # get all authorized SNPs within a gene
    geneDetails = apiClient.get_client_gene(
        productAuthorization.client_uuid,
        productAuthorization.scopes.dataset,
        geneSymbol
    )
```

##### All the geneDetails object attributes are

| Attribute name PHP | Attribute name Python    | Description                                                                              |
|:---------------------:|:---------------------:|:-----------------------------------------------------------------------------------------|
| `molecularLocation`  | `molecular_location`   | An object containing the location of the gene within the chromosome - see below the molecular location object structure  |
| `snps`                | `snps`                | A list of SNP objects present in the gene - see below the SNP object structure           |
| `symbol`              | `symbol`              | The gene's accession string (name)                                                       |

##### Molecular location attributes 

| Attribute name PHP     | Attribute name Python    | Description                                                                              |
|:-------------------------:|:---------------------:|:-----------------------------------------------------------------------------------------|
| `chromosomeAccession`    | `chromosome_accession` | The scaffold/chromosome on which the gene is placed                                      |
| `start`                   | `start`               | The gene's start position on the scaffold                                                |
| `stop`                    | `stop`                | The gene's stop position on the scaffold                                                 |

##### SNP object structure

| Attribute name PHP     | Attribute name Python    | Description                                                                              |
|:-------------------------:|:---------------------:|:-----------------------------------------------------------------------------------------|
| `referenceGenome`        | `reference_genome`     | The reference genome known to be used by the Dataset's source. <br> This impacts the reference allele, location, and based on the dbSNP build, also the SNP's accession|
| `genotypedAlleles`       | `genotyped_alleles`    | The genotype value of the customer's queried SNP. <br><br> If the attribute of this SNP has the `phased` flag set to True, <br>the first items in the lists for all SNPs will be on the same inherited chromosome, <br>and analogous for the second item. <br><br> If the SNP is unphased, the order of the items is irrelevant                                          |
| `phased`                  | `phased`              | A boolean. True if the SNP is known to be phased, False otherwise                         |
| `chromosomeAccession`    | `chromosome_accession` | This is the chromosome accession number where the SNP is located; in the format of NC_00x |
| `location`                | `location`            | This is the customer's SNP's location on the chromosome                                   |

## Get customer genetic data in 23andMe tsv format

If your platform is already compatible with 23andMe genotype data files, you can use this specific function to generate data in the 23andMe format - list of rows in tab separated values.

#### PHP example:
```PHP
$authorizationDnaData = $apiClient->authorizationDnaData($productAuthorization["authorizationUuid"]);
```

#### Python example
```python
authorizationDnaData = apiClient.authorization_dna_data(productAuthorization.authorization_uuid)
```

`authorizationDnaData` contains a list of rows in a tsv (tab delimited values)/csv format (23andme-compatible)

# Submit reports

After you finish analysing the customer's genetic data, we need to inform the customer their analysis is complete. To do this, you will notify us using the function below. Finally, the customer will then:

* access their report file through a written electronic document (eg. .pdf or .doc)
* access their report on your website under an account with a username and a password or
* receive a physical product

## How to submit a report file

When you submit such a report file, Lumminary will save this document into the customer's account, from which the customer will then be able to access it directly.

#### PHP example
```php
$pathToReportFile = <path_to_report_file>;
$fileReport = new \SplFileObject($pathToReportFile); 
$friendlyFileName = "report_file_name"; //optional, give a friendly name to your report file
$apiClient->postAuthorizationResultFile(
   $productAuthorization["productUuid"],
   $productAuthorization["authorizationUuid"],
   $fileReport,
   $friendlyFileName
);
```

#### Python example
```python
pathToReport = <path_to_report_file>
originalFilename = "report_file_name" #optional, give a friendly name to your report file
apiClient.post_authorization_result_file(
   productAuthorization.product_uuid,
   productAuthorization.authorization_uuid,
   pathToReport,
   originalFilename
)
```

If you need to upload multiple files, you have to call the function for each file, one at a time. 

## How to submit a report so the customer can access it on your website

If the customer's results can be accessed on your website, you will need to create a customer account on your platform, generating a user and password which will be sent through the Lumminary API into the customer's Lumminary account. 

In case you don't generate a user and a password for the customer to access their report, use the function below with "null" value to username and password. We recommend you use the URL for customer reports on a dedicated page for reports only, rather than your homepage or some other generic page.

#### PHP example:
```php
$apiClient->postAuthorizationResultCredentials(
   $productAuthorization["productUuid"],
   $productAuthorization["authorizationUuid"],
   <username_generated_by_you>, //optional, default null
   <password_generated_by_you>, //optional, default null
   <report_on_your_website_url> // https://partnerwebsite.com/reports.php?reportid=a7508
);
```

#### Python example:
```python
apiClient.post_authorization_result_credentials(
   productAuthorization.product_uuid,
   productAuthorization.authorization_uuid,
   <username_generated_by_you>, # optional, default null
   <password_generated_by_you>, # optional, default null
   <report_on_your_website_url> # https://partnerwebsite.com/reports.php?reportid=a7508
)
```

## How to submit a physical product
In case you only send the customer a physical product and you don't generate any reports, you need to run the function below so we can mark the order as fulfilled and can inform the client.

#### PHP example:
```php
$apiClient->postProductAuthorization(
  $productAuthorization["productUuid"],
  $productAuthorization["authorizationUuid"]
);
```

#### Python example:
```python
apiClient.post_product_authorization(
   productAuthorization.product_uuid,
   productAuthorization.authorization_uuid
)
```

# The Connect with Lumminary button

The "Connect with Lumminary" functionality allows you to get customer details and genetic data from the Lumminary platform for free, anytime you want, for as long the customer grants you access. This functionality offers your customers the option to share their genetic data and other personal information (e.g. name, address, email etc.) stored on the Lumminary platform. 

Having this button on your website makes it very easy for the customer to share their genetic data with you, as they don't have to download and re-upload their data on your site. The customer always has the option to revoke your access to both their personal details and their genetic data.

**`To protect the customer's privacy, you are not allowed to save their data anywhere. You can, however, always access their data on the Lumminary platform, for as long as they grant you access. If you generate a report based on customer data, you are allowed to save that report on your platform.`**

In order to implement this functionality on your website, this is what you need to know:
* Register your product on the Lumminary platform
* Add the "Connect with Lumminary" button to your website
* Configure your website to retrieve customer data
* Possible errors

## Register your product on the Lumminary platform

If you're new to the Lumminary platform and don't already have any products in the DNA App Store, then you need to register by [filling in this form](https://lumminary.com/register-for-connect-with-lumminary).

You have to fill in the form for all products and services that require access to Lumminary customers' genetic data.  

## Add the Connect with Lumminary button to your website

Since the CWL flow involves encrypting and decrypting data, we recommend installing the Lumminary API Client, where you'll find some specific helper functions. 

In order to enable the button, you have to include the following script in the `<head>` tag of all the pages where you want to enable the “Connect with Lumminary” button:

```html
<head>
    <script defer src="https://lumminary.com/cwl/cwl.js"></script>
</head>
```

The Javascript creates a CSRF token and attaches it to the button to be transmitted and verified on our servers each time a user clicks on the button. The CSRF token expires after 5 minutes. In case the CSRF token is expired or tampered, the user will be redirected to your website where it's up to you to decide what to do next - reload the page with the button or show the customer an error message.

The `cwl.js` file is loaded as a deferred resource, which means that it will load after all the webpage code execution has been finished, so it will not have any impact on your website load speed.

### Chose a button colour

There are two type of buttons, so you can pick one that matches your branding. The buttons are SVG images, which means that you can scale them up or down to fit your design, without compromising on image quality. You can do this by changing the image height.

##### a. White button version


<img src="https://lumminary.com/cwl/connect-with-lumminary-white.svg" alt="Lumminary DNA tests" height="50" title="Connect with Lumminary"/>

<br>

```html
<a class="lumminary-connect-btn" data-partner-uuid="<partner-UUID>" data-request="<request>" style="cursor:pointer; text-decoration:none;" href="https://lumminary.com">
   <img src="https://lumminary.com/cwl/connect-with-lumminary-white.svg" alt="Lumminary DNA tests" height="50" title="Connect with Lumminary"/>
</a>
```

##### b.  Black button version

<img src="https://lumminary.com/cwl/connect-with-lumminary-black.svg" alt="Lumminary DNA tests" height="50" title="Connect with Lumminary"/>

<br>

```html
<a class="lumminary-connect-btn" data-partner-uuid="<partner-UUID>" data-request="<request>" style="cursor:pointer; text-decoration:none;" href="https://lumminary.com">
   <img src="https://lumminary.com/cwl/connect-with-lumminary-black.svg" alt="Lumminary DNA tests" height="50" title="Connect with Lumminary"/>
</a>
```

## Button configuration

Each button has 2 attributes which need to be configured:

1. **data-partner-uuid** where you have to add your partner UUID (you have received the partner UUID after filling in the form for product registration). 
2. **data-request** which is a string obtained by encrypting a serialized JSON (you have received the CWL encryption key after filling in the form for product registration). See details below. 

#### Data-request object

The data-request object has a standard format which needs to be preserved. It is formed of two types of data, some mandatory and some optional. You can use the optional fields to add any metadata or other information for your own use. The data-request object is going to be returned with the response from the authentication without being altered.

##### Mandatory information

The mandatory information is a list of scopes which you ask the client to grant permission for. These scopes are comma delimited, and the possible options are: `address`, `email`, `dataset`.

The scopes _address_, _email_, and _dataset_ can be used in any combination; you must request at least one scope.

| Attribute name    | Description                                         |
|:-----------------:|:----------------------------------------------------|
| `address`         | Requests access to a customer's name and address.   |
| `email`           | Requests access to a customer's email address.      |
| `dataset`         | Requests access to a customer's genetic data        |

#### PHP example:
```php
$objAuthorizationRequest ["scopes"] = "address,dataset,email";
```

#### Python example:
```python
objAuthorizationRequest ["scopes"] = "address,dataset,email"
```

Product UUID is your `productUuid` for which you ask customer permissions.

#### PHP example:
```php
$objAuthorizationRequest["productUuid"] = $credentials->getProductUuid();
```

#### Python example:
```python
objAuthorizationRequest["productUuid"] = credentials.product_uuid
```

##### Optional information

In the optional part of the object, you can add any useful data, such as customer ID,  session ID, or any parameter which can help you identify the response from Lumminary.

#### PHP example:
```php
$objAuthorizationRequest["customData"] = array();
$objAuthorizationRequest["customData"]["customerId"] = <partner-customer-id>;
$objAuthorizationRequest["customData"]["websiteSession"] = <customer-session>;
$objAuthorizationRequest["customData"]["customData3"] = <Some addional data>;
```

#### Python example:
```python
objAuthorizationRequest["customData"] = {}
objAuthorizationRequest["customData"]["customerId"] = <partner-customer-id>
objAuthorizationRequest["customData"]["websiteSession"] = <customer-session>
objAuthorizationRequest["customData"]["customData3"] = <Some addional data>
```

See below a complete example for a data-request object:

#### PHP example:
```php
$objAuthorizationRequest["scopes"] = "address,dataset,email";
$objAuthorizationRequest["productUuid"] = <product-UUID>;

$objAuthorizationRequest["customData"] = array();
$objAuthorizationRequest["customData"]["customerId"] = <partner-customer-id>;
$objAuthorizationRequest["customData"]["websiteSession"] = <customer-session>;
$objAuthorizationRequest["customData"]["customData3"] = <Some addional data>;
```

#### Python example:
```python
objAuthorizationRequest = {}
objAuthorizationRequest["scopes"] = "address,dataset,email"
objAuthorizationRequest["productUuid"] = <product-UUID>

objAuthorizationRequest["customData"] = {}
objAuthorizationRequest["customData"]["customerId"] = <partner-customer-id>
objAuthorizationRequest["customData"]["websiteSession"] = <customer-session>
objAuthorizationRequest["customData"]["customData3"] = <Some addional data>
```

## Creating the Authorization Request

The previously generated object (`objAuthorizationRequest`) will now need to be encrypted. In order to be able to encrypt the object and also query the Lumminary API to obtain the customer details and genetic data, you need to have the Lumminary API Client installed. If you haven't done this already, please follow these [steps](#Install-Lumminary-API-Client-andor-Toolkit).

### Add data-request attribute

After you have the Lumminary API Client installed correctly you can use the command below:

#### PHP example:
```php
// You have recieved the CWL encryption key after filling in the form for product registration
$partnerCwlKey = <partner-encryption-key>;
$requestValueEncryptedUrlEncoded = Lumminary\Client\LumminaryApi::cwl_data_request_build(
    $objAuthorizationRequest,
    $partnerCwlKey
);
```

#### Python example:
```python
import lumminary_sdk as lumminary

# You have recieved the CWL encryption key after filling in the form for product
partnerCwlKey = <partner-encryption-key> 
requestValueEncryptedUrlEncoded = lumminary.LumminaryApi.cwl_data_request_build(objAuthorizationRequest, partnerCwlKey)
```

The resulting string should be added in the `data-request` attribute of the `<a>` tag of the "Connect with Lumminary" button.

### Add data-partner-uuid attribute

Add the `data-partner-uuid` in the `data-partner-uuid` attribute of the `<a>` tag of the "Connect with Lumminary" button. You have received the partner UUID after filling in the form for product registration.

An example of a button correctly configured should look like this:

```html
<a class="lumminary-connect-btn" data-partner-uuid="4231-7446-2543-6542" data-request="7LfMX811Als0l%2FAvf84pB7n3mcycnTjgWl1FaVNffdqiOApMn4HAnk0Ux6eatObfYmxf1xPRjo7nBojsL4ImgOL932NK2Ei4VoUXjs9Y%2BcvphI0kxBSblLaeVXNPbJO9LsuNP%2BHJzDBAnZZdAObgYxHH2QDY3VD%2Ff%2FBXKw9WYDdBssAoegMFEJ9GgYutFQ4nTPXAt%2FdWCqoxYbZrYpCj2Pphk9lstc4Ib%2BLNxKiEtNCmVGr6sgmR2lPBwgylTsEX%2FMRCJb6sdQyZBhvSQCMFb0p3%2B9tEwV0%3D" style="cursor:pointer; text-decoration:none;" href="https://lumminary.com">
   <img src="https://lumminary.com/cwl/connect-with-lumminary-white.svg" alt="Lumminary DNA tests" height="50" title="Connect with Lumminary">
</a>
```

## Connect with Lumminary summary of user interaction

When a customer clicks on the “Connect with Lumminary” button, a pop-up window opens. After they choose which genetic file to share, the pop-up will automatically close and the user will be redirected to your callback URL in the parent window. Your callback URL needs to be predefined in the Lumminary partner portal. 

The GET request from the client to your callback URL will contain two querystring parameters - `request` and `response`:

1. `request` – this is exactly the same request that you previously sent in the `data-request` field. You can decrypt it with the CWL encryption key which you used to encrypt it.
2. `response` – the response is an urlencoded encrypted serialized JSON object which contains the Authorization UUID and the Authorization UTC unix timestamp. You will use the Authorization UUID to get the customer's data with the Lumminary API Client. The response string is encrypted with your CWL encryption key, the same as the `data-request` parameter. 

In order to decrypt the `response` parameter, you can use the following function:

#### PHP example:
```php
// the entire callback URL, including the querystring parameters
$callbackUrlWithPayload = "https://partnerwebsite.con/callback?request=...&response=...";

$cwlReturnObject = Lumminary\Client\LumminaryApi::cwl_url_query_extract(
    $callbackUrlWithPayload, 
    $partnerCwlKey  
);
```

#### Python example:
```python
// the entire callback URL, including the querystring parameters
callback_url_with_payload = "https://partnerwebsite.con/callback?request=...&response=..."

cwlReturnObject = apiClient.cwl_url_query_extract(
    callback_url_with_payload,
    partner_cwl_key
)
```

The `cwlReturnObject` will now contain an object like the example below:

```json
{
    "request": <your-request-parameter-echoed>,
    "response": {
        "authorizationUuid": <cwl-authorization-uuid>,
        "authorizationTimestamp": <cwl-authorization-created-timestamp>
    }
}
```

With the Authorization UUID (`authorizationUuid`) you can [query all the customer details](#Query-customer-genetic-data) from the Lumminary platform.

## Possible errors

When an error occurs, the customer is redirected to your callback URL. The redirect contains two querystring parameters - `request` and `response` - exactly like a regular response, but the `response` parameter contains an error object (see below) instead of an Authorization object.

#### PHP example:
```php
// the entire callback url, including the querystring parameters
$callbackUrlWithPayload = "https://partnerwebsite.con/callback?request=...&response=...";

$cwlReturnObject = Lumminary\Client\LumminaryApi::cwl_url_query_extract(
    $callbackUrlWithPayload, 
    $partnerCwlKey  
);
```

#### Python example:
```python
# the entire callback url, including the querystring parameters
callback_url_with_payload = "https://partnerwebsite.con/callback?request=...&response=..."

cwlReturnObject = apiClient.cwl_url_query_extract(
    callback_url_with_payload,
    partner_cwl_key
)
```

Example of a return object (`cwlReturnObject`) containing an error message:

```json
{
    "request": <your-request-parameter-echoed>,
    "response": {
        "error": {
            "id": <error id>,
            "message": <error message>
        }
    }
}
```

| Error Id          | Error Message                                                                                |
|:-----------------:|:---------------------------------------------------------------------------------------------|
| 1                 | Invalid Security Token                                                                       |
| 2                 | Invalid Access Scopes                                                                        |
| 3                 | Customer refuses your request (this happens when the customer cancels instead of granting access) |

## Actions

### post_jwt_auth
## Note:
* The JWT tokens returned should be passed to any resource that requires authentication, in the Authentication header, in the format `Bearer: your-token-here`
* Only JWT authentication tokens are provided (no refresh tokens). These tokens are valid for 30 seconds from the moment they were issued


```js
lumminary.post_jwt_auth({
  "username": "",
  "password": "",
  "role": ""
}, context)
```

#### Input
* input `object`
  * username **required** `string`: The email for a Client, or the API for a partner product
  * password **required** `string`: The passowrd for a Client, or the API key for a service
  * role **required** `string`: The role for which authentication will be made. Value : role_product
  * X-Fields `string`: An optional fields mask

#### Output
* output [JavascriptWebToken](#javascriptwebtoken)

### get_client_gene
Gets A gene by its symbol, which can be found by querying the reference/ resource.

Will return a 404 if a gene exists as a reference, but its genomic coordinates intersect no SNPs in the dataset


```js
lumminary.get_client_gene({
  "clientId": "",
  "datasetId": "",
  "geneSymbol": ""
}, context)
```

#### Input
* input `object`
  * X-Fields `string`: An optional fields mask
  * clientId **required** `string`: The UUID of the client
  * datasetId **required** `string`: The UUID of one of the client's dataset
  * geneSymbol **required** `string`: The symbol of a gene to be fetched

#### Output
* output [ClientGene](#clientgene)

### get_client_snp_group



```js
lumminary.get_client_snp_group({
  "clientId": "",
  "datasetId": ""
}, context)
```

#### Input
* input `object`
  * X-Fields `string`: An optional fields mask
  * clientId **required** `string`: The UUID of the client
  * datasetId **required** `string`: The UUID of one of the client's dataset

#### Output
* output `array`
  * items [ClientSNP](#clientsnp)

### post_client_snp_group
SNPs that are not present in the dataset are ignored, 404 is returned only if the dataset/client does not exist


```js
lumminary.post_client_snp_group({
  "snps": "",
  "clientId": "",
  "datasetId": ""
}, context)
```

#### Input
* input `object`
  * snps **required** `string`: JSON-encoded list of snps to be fetched
  * X-Fields `string`: An optional fields mask
  * clientId **required** `string`: The UUID of the client
  * datasetId **required** `string`: The UUID of one of the client's dataset

#### Output
* output `array`
  * items [ClientSNP](#clientsnp)

### get_client_snp
Gets SNP information, as provided by the dataset.

If fetching this as an product, the client must have already granted access to the snip (see the 'products' group)


```js
lumminary.get_client_snp({
  "clientId": "",
  "datasetId": "",
  "snpId": ""
}, context)
```

#### Input
* input `object`
  * X-Fields `string`: An optional fields mask
  * clientId **required** `string`: The UUID of the client
  * datasetId **required** `string`: The UUID of one of the client's dataset
  * snpId **required** `string`: The rsId of a SNP to be fetched

#### Output
* output [ClientSNP](#clientsnp)

### get_product
Get product details


```js
lumminary.get_product({
  "productId": ""
}, context)
```

#### Input
* input `object`
  * X-Fields `string`: An optional fields mask
  * productId **required** `string`: The UUID of the product

#### Output
* output [Product](#product)

### get_authorizations_queue



```js
lumminary.get_authorizations_queue({
  "productId": ""
}, context)
```

#### Input
* input `object`
  * seq_num_start `string`: The first sequence number from which to fetch (the sequence number of the last processed authorization)
  * X-Fields `string`: An optional fields mask
  * productId **required** `string`: The UUID of the product

#### Output
* output `array`
  * items [Authorization](#authorization)

### get_product_authorization



```js
lumminary.get_product_authorization({
  "productId": "",
  "authorizationId": ""
}, context)
```

#### Input
* input `object`
  * X-Fields `string`: An optional fields mask
  * productId **required** `string`: The UUID of the product
  * authorizationId **required** `string`: The UUID of the authorization

#### Output
* output [Authorization](#authorization)

### post_product_authorization
Signal that processing is complete, without uploading any result


```js
lumminary.post_product_authorization({
  "productId": "",
  "authorizationId": ""
}, context)
```

#### Input
* input `object`
  * productId **required** `string`: The UUID of the product
  * authorizationId **required** `string`: The UUID of the authorization

#### Output
*Output schema unknown*

### post_authorization_result_credentials
These can be log-in credentials for a website where the result is available


```js
lumminary.post_authorization_result_credentials({
  "productId": "",
  "authorizationId": ""
}, context)
```

#### Input
* input `object`
  * credentials_username `string`: Credentials for accessing the result. Includes password, username and url
  * credentials_password `string`: Credentials for accessing the result. Includes password, username and url
  * report_url `string`: Credentials for accessing the result. Includes password, username and url
  * X-Fields `string`: An optional fields mask
  * productId **required** `string`: The UUID of the product
  * authorizationId **required** `string`: The UUID of the authorization

#### Output
* output [ReportCredentials](#reportcredentials)

### post_authorization_result_file
g. a pdf report


```js
lumminary.post_authorization_result_file({
  "productId": "",
  "authorizationId": ""
}, context)
```

#### Input
* input `object`
  * file_report `string`, `object`: A binary file (e.g. pdf) that contains the result of the authorization
    * content `string`
    * encoding `string` (values: ascii, utf8, utf16le, base64, binary, hex)
    * contentType `string`
    * filename `string`
  * original_filename `string`: Optional original filename for the report. If not provided, the filename of uploaded file will be used
  * X-Fields `string`: An optional fields mask
  * productId **required** `string`: The UUID of the product
  * authorizationId **required** `string`: The UUID of the authorization

#### Output
* output [ReportFile](#reportfile)

### post_product_authorization_unfulfillable
Catch-all Authorization state, for authorizations that passed all verifications and should reach the partner Product, but cannot be fulfilled for various reasons


```js
lumminary.post_product_authorization_unfulfillable({
  "productId": "",
  "authorizationId": ""
}, context)
```

#### Input
* input `object`
  * productId **required** `string`: The UUID of the product
  * authorizationId **required** `string`: The UUID of the authorization

#### Output
*Output schema unknown*

### get_gene
Generic gene information


```js
lumminary.get_gene({
  "databaseName": "",
  "accession": ""
}, context)
```

#### Input
* input `object`
  * dbsnp_build `integer`: The dbSNP build for which to consider snps belonging to the gene. Defaults to 149
  * reference_genome `string`: The reference genome for which gene annotations will be returned. Defaults to GRCh37p13
  * X-Fields `string`: An optional fields mask
  * databaseName **required** `string`: The name of the database to search. E.g: Genbank
  * accession **required** `string`: The accession within the selected database

#### Output
* output [PublicGene](#publicgene)

### get_reference_genomes_group
Lists reference genome builds that are available


```js
lumminary.get_reference_genomes_group({}, context)
```

#### Input
* input `object`
  * X-Fields `string`: An optional fields mask

#### Output
* output `array`
  * items [ReferenceGenomeOverview](#referencegenomeoverview)

### get_reference_genome
Reference genome metadata


```js
lumminary.get_reference_genome({
  "genomeBuildAccession": ""
}, context)
```

#### Input
* input `object`
  * X-Fields `string`: An optional fields mask
  * genomeBuildAccession **required** `string`

#### Output
* output `array`
  * items [ReferenceChromosomeOverview](#referencechromosomeoverview)

### get_reference_chromosome
Fetch a closed interval of nucleotides on a given chromosome. Includes start and stop positions


```js
lumminary.get_reference_chromosome({
  "range_start": 0,
  "range_stop": 0,
  "genomeBuildAccession": "",
  "chromosomeAccession": ""
}, context)
```

#### Input
* input `object`
  * range_start **required** `integer`: Location on the chromosome
  * range_stop **required** `integer`: Location on the chromosome
  * X-Fields `string`: An optional fields mask
  * genomeBuildAccession **required** `string`: The accession of the reference genome
  * chromosomeAccession **required** `string`: The accession to the chromosome

#### Output
* output [ReferenceSequence](#referencesequence)

### get_reference_snp
Get reference SNP information, from dbSNP


```js
lumminary.get_reference_snp({
  "snpAccession": ""
}, context)
```

#### Input
* input `object`
  * dbsnp_version `integer`: The dbSNP build. Defaults to 149
  * grch_version `string`: The GRCh build on which to place snips. Defaults to GRCh37p13
  * X-Fields `string`: An optional fields mask
  * snpAccession **required** `string`: The rsId of the SNP

#### Output
* output [PublicSNP](#publicsnp)



## Definitions

### AccessScope
* AccessScope `object`
  * address [CustomerAddress](#customeraddress)
  * dataset `string`: Access to one of the customer's datasets
  * email `string`: Access to customer email
  * login `string`: Access to no customer information, just the customer UUID
  * name [CustomerName](#customername)
  * sex `string`: The sex of the customer. One of : F, M, null

### Authorization
* Authorization `object`
  * authorization_uuid **required** `string`: Identifier of the Authorization
  * client_uuid **required** `string`: The UUID of the client owning the Dataset to which the product is authorized
  * create_timestamp **required** `integer`: Creation timestamp for the Authorization
  * is_active **required** `boolean`: If false, the the authorization is revoked and data access authorizations fail
  * order `string`: Optional UUID of the Order that created the Authorization
  * product_uuid **required** `string`: Identifier of the Product to be authorized
  * report_credentials `array`
    * items [ReportCredentials](#reportcredentials)
  * report_files `array`
    * items [ReportFile](#reportfile)
  * scopes **required** [AccessScope](#accessscope)
  * sequence_number `integer`: The sequence number of the Authorization. Used as a filter when fetching new Authorizations
  * state **required** `string`: The authorization state. One of : ['authorization_state_pending_dataset', 'authorization_state_fulfillable', 'authorization_state_result_available', 'authorization_state_not_fulfillable']

### ClientGene
* ClientGene `object`
  * molecular_location **required** [MolecularLocation](#molecularlocation)
  * snps `array`
    * items [ClientSNP](#clientsnp)
  * symbol **required** `string`: The gene accession string

### ClientSNP
* ClientSNP `object`
  * chromosome_accession **required** `string`: The accession of the chromosome on which the SNP is placed
  * genotyped_alleles **required** `array`: A diploid genoyped allele, if available
    * items `string`: A haploid allele
  * location **required** `integer`: The SNP's position on the chromosome
  * phased **required** `boolean`: True if there is phasing information about the snp, false otherwise
  * reference_genome **required** `string`: The ID and build number of the genome against which the SNP was built and placed
  * snp_id **required** `string`: The ID of the SNP

### CustomerAddress
* CustomerAddress `object`
  * address1 `string`
  * address2 `string`
  * city `string`
  * country `string`
  * phone `string`
  * state `string`
  * zipcode `string`

### CustomerName
* CustomerName `object`
  * first_name `string`: Customer first name
  * last_name `string`: Customer last name

### FileLocation
* FileLocation `object`
  * filename_original **required** `string`
  * host **required** `string`
  * path **required** `string`

### JavascriptWebToken
* JavascriptWebToken `object`
  * access_token **required** `string`: The JWT containing the authorization token for further API calls

### MolecularLocation
* MolecularLocation `object`
  * chromosome_accession **required** `string`: The cromosome on which the gene is placed
  * start **required** `integer`: The gene's start position on the scaffold
  * stop **required** `integer`: The gene's stop position on the scaffold

### Product
* Product `object`
  * authorized_scopes **required** `array`: A list of scopes that the product can require from clients
    * items `string`
  * email `string`: The contact email for the product
  * product_uuid **required** `string`: The product identifier
  * redirect_uri `string`: A redirect url registered as a callback for the Connect with Lumminary authorization flow
  * snps_authorized **required** `array`: A superset of snps_min_required, containing all SNPs to which an Product has access (includes optional SNPs)
    * items `string`
  * snps_authorized_any **required** `boolean`: A boolean value specifying if SNP set is not strict
  * snps_min_required **required** [SnpsMinRequired](#snpsminrequired)
  * snps_min_required_any **required** `boolean`: A boolean value specifying if SNP set is not strict

### PublicGene
* PublicGene `object`
  * chromosome **required** `string`: The cromosome on which the gene is placed
  * molecular_end_position **required** `integer`: The gene's end position on the scaffold
  * molecular_start_position **required** `integer`: The gene's start position on the scaffold
  * parent_accession **required** `string`: The scaffold on which the gene is placed
  * snp_ids **required** `array`: The SNPs contained in the gene
    * items `string`: The SNP identifier
  * symbol **required** `string`: The gene accession string

### PublicSNP
* PublicSNP `object`
  * alternative_alleles `array`
    * items `string`: A haploid allele
  * chromosome **required** `string`: The cromosome on which the SNP is placed
  * chromosome_accession **required** `string`: The accession of the chromosome on which the SNP is placed
  * dbsnp_version **required** `integer`: The dbSNP build to which snip attributes like location and chromosome accession refer.
  * location **required** `integer`: The SNP's position on the chromosome
  * reference_allele **required** `string`: One of the possible alleles
  * reference_genome **required** `string`: The ID and build number of the genome against which the SNP was built and placed
  * snp_id **required** `string`: The ID of the SNP

### ReferenceChromosomeOverview
* ReferenceChromosomeOverview `object`
  * reference_accession **required** `string`: The versioned reference chromosome accession

### ReferenceGenomeOverview
* ReferenceGenomeOverview `object`
  * reference_accession **required** `string`: The versioned reference build release accession

### ReferenceSequence
* ReferenceSequence `object`
  * sequence **required** `string`: The nucleotide sequence

### ReportCredentials
* ReportCredentials `object`
  * authorization_uuid **required** `string`: The uuid of the authorization that generated this report
  * client_password `string`: The password generated password, on the partner product website
  * client_username `string`: The generated username, on the partner product website
  * create_timestamp **required** `integer`: Creation timestamp for Report
  * report_credentials_uuid **required** `string`: The uuid of the report
  * report_url `string`: URL to the report location

### ReportFile
* ReportFile `object`
  * authorization_uuid **required** `string`: The uuid of the authorization that generated this report
  * create_timestamp **required** `integer`: Creation timestamp for Report
  * file_location **required** [FileLocation](#filelocation)
  * report_file_uuid **required** `string`: The uuid of the report

### SnpsMinRequired
* SnpsMinRequired `object`
  * min_pct **required** `integer`: Minimum required percentage of snps that should be present in the Dataset for compatibility
  * snps **required** `array`: List of snps that are (possibly partially) required for the Product to be compatible with a Dataset
    * items `string`

