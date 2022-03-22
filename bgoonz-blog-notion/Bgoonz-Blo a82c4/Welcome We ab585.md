# Welcome | Web3.Storage Documentation

[https://docs.web3.storage/#get-an-api-token](https://docs.web3.storage/#get-an-api-token)

# Better storage. Better transfers. Better internet.

Now that you're signed up and logged in, it's time to [get your API token. ↓](https://docs.web3.storage/#get-an-api-token)

## Get an API token[#](https://docs.web3.storage/#get-an-api-token)

It only takes a few moments to get a free API token from Web3.Storage. This token enables you to interact with the Web3.Storage service without using the main website, enabling you to incorporate files stored using Web3.Storage directly into your applications and services.

1. Click **Create an API token**.
2. Enter a descriptive name for your API token and click **Create**.
3. Make a note of the **Token** field somewhere secure where you know you won't lose it. You can click **Copy** to copy your new API token to your clipboard.

Now that you have your new API token, it's time to use a simple script to [upload a file to Web3.Storage. ↓](https://docs.web3.storage/#create-the-upload-script)

## Create the upload script[#](https://docs.web3.storage/#create-the-upload-script)

You can use the Web3.Storage site to upload files, but it's also quick and easy to create and run a simple upload script — making it especially convenient to add large numbers of files. This script contains logic to upload a file to Web3.Storage and get a *[content identifier* (CID)](https://docs.web3.storage/concepts/content-addressing) back in return.

1. Create a file called `put-files.js` and paste in the following code:
    
    ```
    import process from 'process'import minimist from 'minimist'import { Web3Storage, getFilesFromPath } from 'web3.storage'async function main () {const args = minimist(process.argv.slice(2))const token = args.tokenif (!token) {return console.error('A token is needed. You can create one on https://web3.storage')if (args._.length < 1) {return console.error('Please supply the path to a file or directory')const storage = new Web3Storage({ token })const files = []for (const path of args._) {const pathFiles = await getFilesFromPath(path)    files.push(...pathFiles)console.log(`Uploading ${files.length} files`)const cid = await storage.put(files)console.log('Content added with CID:', cid)
    ```
    
2. Create another file called `package.json` and paste in the following code:
    
    ```
    "name": "web3-storage-quickstart","version": "0.0.0","private": true,"description": "Get started using web3.storage in Node.js","type": "module","scripts": {"test": "echo \"Error: no test specified\" && exit 1""dependencies": {"minimist": "^1.2.5","web3.storage": "^3.1.0""author": "YOUR NAME",
    ```
    
3. Save both files, and then run `npm install` from your project folder:
    
    This step may take a few moments. Once it's done, the command should output something like this:
    
    ```
    added 224 packages, and audited 225 packages in 14s40 packages are looking for funding run `npm fund` for details
    ```
    

Your script is good to go! Next, we'll [run the script to upload a file. ↓](https://docs.web3.storage/#run-the-script)

## Run the script[#](https://docs.web3.storage/#run-the-script)

Now that you've got your script ready to go, you just need to run it in your terminal window using `node`.

1. Run the script by calling `node put-files.js`, using `-token` to supply your API token and specifying the path and name of the file you want to upload. If you'd like to upload more than one file at a time, simply specify their paths/names one after the other in a single command. Here's how that looks in template form:
    
    Once you've filled in your details, your command should look something like this:
    
2. **Make a note of the CID, which looks like `bafyb...`.** You'll need it in order to get your file.

Next up, we'll go over two methods for you to [retrieve your data from Web3.Storage ↓](https://docs.web3.storage/#get-your-file)

## Get your file[#](https://docs.web3.storage/#get-your-file)

You've already done the most difficult work in this guide — getting your files from Web3.Storage is simple.

1. Go to `https://dweb.link/ipfs/YOUR_CID`, replacing `YOUR_CID` with the CID you noted in the last step.
2. You should see a link to your file. If you uploaded multiple files at once, you'll see a list of all the files you uploaded.
3. Click on a file's link to view it in your browser!

If you ever need to find your files again, and you've forgotten the CID, head over to the [Files section](https://web3.storage/files/) in Web3.Storage:

![Welcome%20We%20ab585/files-listing-7ee7f3a64ce3551c4f63e1562dd52fea.png](Welcome%20We%20ab585/files-listing-7ee7f3a64ce3551c4f63e1562dd52fea.png)

## Next steps[#](https://docs.web3.storage/#next-steps)

Congratulations! You've just covered the basics of Web3.Storage. To learn more, take a look at these useful resources:

### Was this information helpful?

### Help us improve this site!