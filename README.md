# Packer Windows Clouds

Working sample code to generate Server templates used in various cloud providers.

Each server is configured with winrm and a self-signed certificate called "packer" so that configuration and management can be handled after deployment.  The configuraiton itself was lifted from Ansible, so guaranteed ot be compatible with that system.

There are multiple definitions for the various server versions (server 2012,server 2016, etc.) due to differeing requirements between them.  All images currently standardize on WMF 5.1 (PowerShell 5.1).

## Running the build

The build will check environment variables for details, as well as login information.  I find it easiest to either add this information into your profile or simply cut-n-paste it in as needed when doing dev work ... keeps pesky passwords out of code and all.  Exact vars required will vary by cloud.

Cloud Specific Notes:

- [AWS](documentation/aws.md)
