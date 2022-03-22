# How To Update Node.js To Latest Version On Linux, macOS, & Windows

[https://www.whitesourcesoftware.com/free-developer-tools/blog/how-to-update-node-js-to-latest-version/](https://www.whitesourcesoftware.com/free-developer-tools/blog/how-to-update-node-js-to-latest-version/)

Node.js is a popular open-source, cross-platform server-side environment for building robust applications. Since a vibrant community of contributors backs it, the platform is continuously updated to introduce new features, security patches, and other performance improvements.

So, updating to the latest Node.js version can help you to make the most of the technology. You can decide to work with the Long-term Supported (LTS) version or the Current version that comes with the latest features.

Typically, LTS is recommended for most users because it is a stable version that provides predictable update releases as well as a slower introduction of substantial changes.

In this article, you will learn how to quickly and easily update Node.js on different operating systems—macOS, Linux, and Windows.

As we'll demonstrate, there are many ways of updating to the next version of Node.js. So, you can choose the option that best meets your system requirements and preferences.

## Checking your version of Node.js

Before getting started, you can check the version of Node.js currently deployed on your system by running the following command on the terminal:

**node –version**

or (shortened method):

**node -v**

Let's now talk about the different ways on how to update Node.js.

## 1. Updating using a Node version manager on macOS or Linux

A Node version manager is a utility that lets you install different Node.js versions and switch flawlessly between them on your machine. You can also use it to update your version of Node.js.

On macOS or Linux, you can use either of the following Node version managers:

- **nvm**
- **n**

Let's talk about each of them.

**a) nvm**

**[nvm](https://github.com/nvm-sh/nvm)** is a script-based version manager for Node.js. To install it on macOS or Linux, you can use either Wget or cURL.

For Wget, run the following command on the terminal:

**wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.3/install.sh | bash**

For cURL, run the following:

**curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.3/install.sh | bash**

The above commands assume that you're installing **nvm** version 0.35.3. So, you'll need to check [the latest version](https://github.com/nvm-sh/nvm/releases) before installing it on your machine.

With these commands, you can clone the repository to **~/.nvm**. This way, you can make changes to your bash profile, allowing you to access **nvm** system-wide.

To confirm if the installation was successful, you can run the following command:

If everything went well, it'd output **nvm**.

Next, you can simply download and update to the latest Node.js version by running the following:

**nvm install node**

Note that **node** refers to an alias of the latest Node.js version.

You can also reference LTS versions in aliases as well as .**nvmrc** files using the notation **lts/*** for the most recent LTS releases.

Here is an example:

**nvm install –lts**

If you want to install and upgrade to a specific version, you can run the following:

**nvm install <version-number>**

For example, if you want to update Node.js to version 12.18.3, you can run:

**nvm install 12.18.3**

After the upgrade, you can set that version to be the default version to use throughout your system:

**nvm use 12.18.3**

You can see the list of installed Node.js versions by running this command:

Also, you can see the list of versions available for installation by running this command:

**b) n**

**[n](https://www.npmjs.com/package/n)** is another useful Node version manager you can use for updating Node.js on macOS and Linux.

Since it's an [npm-based package](https://renovate.whitesourcesoftware.com/blog/updating-npm-packages/), if you already have Node.js available on your environment, you can simply install it by running this command:

Then, to download and update to your desired Node.js version, execute the following:

For example, if you want to update Node.js to version 12.18.3, you can run:

To see a list of your downloaded Node.js versions, run **n** on its own:

You can specify to update to the newest LTS version by running:

You can also specify to update to the latest current version by running:

You can specify to update to the newest LTS version by running:

## 2. Updating using a Node version manager on Windows

On Windows, you can use the following Node version manager:

- **nvm-windows**

Let's talk about it.

**a) nvm-windows**

**[nvm-windows](https://github.com/coreybutler/nvm-windows/)** is a Node version management tool for the Windows operating system. While it's not the same as **nvm**, both tools share several usage similarities for Node.js version management.

Before installing **nvm-windows**, it's recommended to uninstall any available Node.js versions from your machine. This will avoid potential conflict issues during installation.

Next, you can download and run the latest [nvm-setup.zip](https://github.com/coreybutler/nvm-windows/releases) installer.

Also, since the utility runs in an Admin shell, you'll need to begin the Command Prompt or Powershell as an Administrator before using it.

If you want to install and upgrade to a specific version, you can run the following:

You can specify to update to the newest LTS version by running:

For example, if you want to update Node.js to version 12.18.3, you can run:

After the upgrade, you can switch to that version:

**nvm use**

**12.18.3**

You can also specify to update to the latest stable Node.js version:

You can see the list of installed Node.js versions by running this command:

Also, you can see the list of versions available for download by running this command:

## 3. Updating using a Node installer on Linux

Using a Node installer is the least recommended way of upgrading Node.js on Linux. Nonetheless, if it's the only route you can use, then follow the following steps:

- Go to the official [Node.js downloads site](https://nodejs.org/en/download/), which has different Linux binary packages, and select your preferred built-in installer or source code. You can choose either the LTS releases or the latest current releases.
- Download the binary package using your browser. Or, you can download it using the following Wget command on the terminal:

![How%20To%20Upd%20fe3b7/node-js-linux.png](How%20To%20Upd%20fe3b7/node-js-linux.png)

- Download the binary package using your browser. Or, you can download it using the following Wget command on the terminal:

Remember to change the version number on the Wget command depending on the one you want.

- Install the **xz-utils** utility using the following command:

This utility will be used for unpacking the binary package.

- Finally, run the following command to unpack and install the binary package on usr/local:

## 4. Updating using a Node installer on macOS and Windows

Another way of updating your Node.js on macOS and Windows is to go to the official [download site](https://nodejs.org/en/download/) and install the most recent version. This way, it'll overwrite your existing old version with the latest one.

You can follow the following steps to update it using this method:

- On the Node.js download page, select either the LTS version or the latest current version.

![How%20To%20Upd%20fe3b7/node-js-mac-windows.png](How%20To%20Upd%20fe3b7/node-js-mac-windows.png)

- Depending on your system, click either the **Windows Installer** option or the **macOS installer** option.
- Run the installation wizard. It will magically complete the installation process and upgrade your Node.js version by replacing it with the new, updated one.

## 5. Updating using Homebrew on macOS

[Homebrew](https://brew.sh/) is a popular package management utility for macOS.

To use it for installing Node.js, run the following command on your macOS terminal:

Later, if you'd like to update it, run the following commands:

Furthermore, you can switch between installed Node.js versions:

## Conclusion

That's how to upgrade your Node.js version on Linux, macOS, or Windows. With every update of Node.js, you can get enhanced features, increased security, better compatibility with other technologies, and more.

You need to be updating Node.js constantly to improve your development experience and create versatile applications.

Happy coding!

**Are you letting open-source vulnerabilities go undetected?**

**[WhiteSource Bolt](https://www.whitesourcesoftware.com/free-developer-tools/bolt)** is a powerful free extension that operates in real-time to provide visibility over your open source components within [Azure Pipelines](https://marketplace.visualstudio.com/items?itemName=whitesource.whiteSource-bolt-v2) or [GitHub](https://github.com/marketplace/whitesource-bolt).

- Get real-time alerts on security vulnerabilities
- Ensure the license compliance of open source components.
- Receive automated open-source inventory reports for every build or project.

**[Get it now](https://www.whitesourcesoftware.com/free-developer-tools/bolt)** and join thousands of developers who've already gained full visibility over their open-source components.
