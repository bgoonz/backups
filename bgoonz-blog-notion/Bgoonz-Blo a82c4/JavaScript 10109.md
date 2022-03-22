# JavaScript client library reference | Web3.Storage Documentation

[https://docs.web3.storage/reference/js-client-library/#store-files](https://docs.web3.storage/reference/js-client-library/#store-files)

```
import { Web3Storage } from 'web3.storage'const client = new Web3Storage({ token: apiToken })
```

## Store files[#](https://docs.web3.storage/reference/js-client-library/#store-files)

Store files using the `put()` method.

```
<clientObject>.put(file[], { options })
```

### Examples[#](https://docs.web3.storage/reference/js-client-library/#examples)

- Node.js

In the browser, using a file chooser to prompt the user for files to store:

```
const fileInput = document.querySelector('input[type="file"]')const rootCid = await client.put(fileInput.files, {  name: 'cat pics',
```

### Return value[#](https://docs.web3.storage/reference/js-client-library/#return-value)

The method returns a string containing the CID of the uploaded CAR.

### Parameters[#](https://docs.web3.storage/reference/js-client-library/#parameters)

Method parameters are supplied in positional order.

[Untitled](JavaScript%2010109/Untitled%20D%206d40d.csv)

An `{options}` object has the following properties that can be used as parameters when calling `put()`:

## Retrieve files[#](https://docs.web3.storage/reference/js-client-library/#retrieve-files)

Retrieve files using the `get()` method. You will need the CID you obtained at upload time that references the CAR for your uploaded files.

### Example[#](https://docs.web3.storage/reference/js-client-library/#example)

### Return value[#](https://docs.web3.storage/reference/js-client-library/#return-value-1)

Returns `undefined` if there are no matches for the given CID.

If found, the method returns a `Web3Response` object, which extends the [Fetch API response object](https://developer.mozilla.org/en-US/docs/Web/API/Response) to add two iterator methods unique to the Web3.Storage client library: `files()` and `unixFsIterator()`.

Parameters are supplied in positional order.

```
string
```

## Check status[#](https://docs.web3.storage/reference/js-client-library/#check-status)

Retrieve metadata about your file by using the `status()` method and supplying the CID of the file you are interested in. This metadata includes the creation date and file size, as well as details about how the network is storing your data. Using this information, you can identify peers on the [IPFS (InterPlanetary File System)](https://ipfs.io/) network that are pinning the data, and [Filecoin](https://filecoin.io/) storage providers that have accepted deals to store the data.

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

[Untitled](JavaScript%2010109/Untitled%20D%20cf4f5.csv)

An `{options}` object has the following properties that can be used as parameters when calling `putCar()`: