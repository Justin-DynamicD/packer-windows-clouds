# Packer Windows Clouds

Working sample code to generate Server templates used in various cloud providers.

Each server is configured with winrm and a self-signed certificate called "packer" so that configuration and management can be handled after deployment. The configuraiton itself was lifted from Ansible, so should be pretty reliable in it's operation.

There are multiple definitions for the various server versions (server 2012,server 2016, etc.) due to differeing requirements between them.  All powershell scripts standardize on WMF 5.1 (PowerShell 5.1) for maximum reuse between versions.

## About Packer

Those new to packer are encouraged to read up here: [https://www.packer.io/](https://www.packer.io/).  While most providers have native ways to build cloud images, packer provides a standardized method that makes it easy to repeat and move between cloud providers, making it an ideal system to use.

Windows servers, however, can sometimes be trickier to use with packer due to winrm configuration being required out of the box.  Thus this is a barebones example of how this can still be acvhieved.

## Running the build

The build will check environment variables for details, as well as login information.  I find it easiest to either add this information into your profile or simply cut-n-paste it in as needed when doing dev work ... keeps pesky passwords out of code and all.  Exact vars required will vary by cloud.

Cloud Specific Notes:

- [AWS](documentation/aws.md)
