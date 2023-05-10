## How to install Node.js and npm
Node.js is a JavaScript runtime for server-side programming. It allows developers to create scalable backend functionality using JavaScript, a language many are already familiar with from browser-based web development.
## Prerequisites

This guide assumes that you are using Ubuntu 20.04. Before you begin, you should have a non-root user account with sudo privileges set up on your system.

## Option 1 —Installing Node.js with Apt from the Default Repositories**
Refresh your local package index first by typing:

`sudo apt update`

Then install Node.js:

`sudo apt install nodejs`

Check that the install was successful by querying `node` for its version number:

`node -v`

    Output
    v10.19.0

If the package in the repositories suits your needs, this is all you need to do to get set up with Node.js. In most cases, you’ll also want to also install `npm`, the Node.js package manager. You can do this by installing the `npm` package with `apt`:

`sudo apt install npm`

This will allow you to install modules and packages to use with Node.js.

At this point you have successfully installed Node.js and `npm` using `apt`and the default Ubuntu software repositories.

## Option 2 — Installing Node.js with Apt Using a NodeSource PPA**

To install a different version of Node.js, you can use a *PPA* (personal package archive) maintained by NodeSource. These PPAs have more versions of Node.js available than the official Ubuntu repositories. Node.js v12, v14, and v16 are available as of the time of writing.

First, we will install the PPA in order to get access to its packages. From your home directory, use `curl` to retrieve the installation script for your preferred version, making sure to replace `16.x` with your preferred version string (if different).

    cd ~
    curl -sL https://deb.nodesource.com/setup_16.x -o /tmp/nodesource_setup.sh

Inspect the contents of the downloaded script with `nano` (or your preferred text editor):

`nano /tmp/nodesource_setup.sh`

When you are satisfied that the script is safe to run, exit your editor, then run the script with `sudo`:

`sudo bash /tmp/nodesource_setup.sh`

The PPA will be added to your configuration and your local package cache will be updated automatically. You can now install the Node.js package in the same way you did in the previous section:

`sudo apt install nodejs`

Verify that you’ve installed the new version by running `node` with the `-v` version flag:

`node -v`

    Output
    v16.6.1

The NodeSource `nodejs` package contains both the `node` binary and `npm`, so you don’t need to install `npm` separately.

At this point you have successfully installed `Node.js` and `npm` using `apt` and the NodeSource PPA.



