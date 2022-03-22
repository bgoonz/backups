# JavaScript client library reference | Web3.Storage Documentation

[https://docs.web3.storage/reference/js-client-library/](https://docs.web3.storage/reference/js-client-library/)

To use the JavaScript client library for Web3.Storage, you must first [obtain a free API token](https://docs.web3.storage/how-tos/generate-api-token).

The client library automatically packs your uploads into a content addressible archive (CAR) for uploading to the Web3.Storage service, which [stores](https://docs.web3.storage/reference/js-client-library/#store-files) data as blocks prefixed with the *[content identifier* (CID)](https://docs.web3.storage/concepts/content-addressing#cids-location-independent-globally-unique-keys) derived from a cryptographic hash of the data. You can then use a file's CID to [retrieve](https://docs.web3.storage/reference/js-client-library/#retrieve-files) it.

This page covers the core functionality of the JavaScript client. See the [JavaScript utility libraries page](https://docs.web3.storage/reference/js-utilities) for some additional packages that may be useful when working with Web3.Storage.

## Constructor[#](https://docs.web3.storage/reference/js-client-library/#constructor)

The constructor for Web3.Storage is simple; all you need is your API token.

```
import { Web3Storage } from 'web3.storage'const client = new Web3Storage({ token: apiToken })
```

## Store files[#](https://docs.web3.storage/reference/js-client-library/#store-files)

Store files using the `put()` method.

### Usage[#](https://docs.web3.storage/reference/js-client-library/#usage)

```
<clientObject>.put(file[], { options })
```

### Examples[#](https://docs.web3.storage/reference/js-client-library/#examples)

- Browser
- Node.js

In the browser, using a file chooser to prompt the user for files to store:

```
const fileInput = document.querySelector('input[type="file"]')const rootCid = await client.put(fileInput.files, {  name: 'cat pics',
```

### Return value[#](https://docs.web3.storage/reference/js-client-library/#return-value)

The method returns a string containing the CID of the uploaded CAR.

### Parameters[#](https://docs.web3.storage/reference/js-client-library/#parameters)

Method parameters are supplied in positional order.

[Untitled](JavaScript%207b4b2/Untitled%20D%20a37b5.csv)

An `{options}` object has the following properties that can be used as parameters when calling `put()`:

## Retrieve files[#](https://docs.web3.storage/reference/js-client-library/#retrieve-files)

Retrieve files using the `get()` method. You will need the CID you obtained at upload time that references the CAR for your uploaded files.

### Usage[#](https://docs.web3.storage/reference/js-client-library/#usage-1)

### Return value[#](https://docs.web3.storage/reference/js-client-library/#return-value-1)

Returns `undefined` if there are no matches for the given CID.

If found, the method returns a `Web3Response` object, which extends the [Fetch API response object](https://developer.mozilla.org/en-US/docs/Web/API/Response) to add two iterator methods unique to the Web3.Storage client library: `files()` and `unixFsIterator()`.

Parameters are supplied in positional order.

```
string
```

## Check status[#](https://docs.web3.storage/reference/js-client-library/#check-status)

Retrieve metadata about your file by using the `status()` method and supplying the CID of the file you are interested in. This metadata includes the creation date and file size, as well as details about how the network is storing your data. Using this information, you can identify peers on the [IPFS (InterPlanetary File System)](https://ipfs.io/) network that are pinning the data, and [Filecoin](https://filecoin.io/) storage providers that have accepted deals to store the data.

### Usage[#](https://docs.web3.storage/reference/js-client-library/#usage-2)

Parameters are supplied in positional order.

```
string
```

### Return value[#](https://docs.web3.storage/reference/js-client-library/#return-value-2)

Returns `undefined` if there are no matches for the given CID.

If found, the `status()` method returns a `{Status}` object that contains the metadata for your object's storage deal on the Web3.Storage network, with the following properties:

## List uploads[#](https://docs.web3.storage/reference/js-client-library/#list-uploads)

List previous uploads with the `list()` method.

### Usage[#](https://docs.web3.storage/reference/js-client-library/#usage-3)

The following example stores return values from a call to `list()` into a JavaScript array:

The `list()` method accepts an `{options}` object with the following properties:

### Return value[#](https://docs.web3.storage/reference/js-client-library/#return-value-3)

The return value for `list()` is an `AsyncIterable` object, containing objects whose data structure is the same as the return value for `status()` but with one extra propery: a string field called `name` that corresponds to the value given passed to the `name` parameter in the original call to `put()`. This means that iterating through results from your call to `list()` yields objects with the below example structure.

## Store CAR files[#](https://docs.web3.storage/reference/js-client-library/#store-car-files)

### Usage[#](https://docs.web3.storage/reference/js-client-library/#usage-4)

### Examples[#](https://docs.web3.storage/reference/js-client-library/#examples-2)

### Return value[#](https://docs.web3.storage/reference/js-client-library/#return-value-4)

The method returns a string containing the CID of the uploaded CAR.

### Parameters[#](https://docs.web3.storage/reference/js-client-library/#parameters-4)

Method parameters are supplied in positional order.

[Untitled](JavaScript%207b4b2/Untitled%20D%20caae7.csv)

An `{options}` object has the following properties that can be used as parameters when calling `putCar()`: