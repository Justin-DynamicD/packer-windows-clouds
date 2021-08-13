# AWS Specific

## Environment variables

The build will check environment variables for details, as well as login information.  I find it easiest to either add this information into your profile or simply cut-n-paste it in as needed when doing dev work ... keeps pesky passwords out of code and all.

PowerShell:

```PowerShell
$Env:AWS_ACCESS_KEY_ID=""
$Env:AWS_SECRET_ACCESS_KEY=""
$Env:AWS_SESSION_TOKEN=""
$Env:AWS_REGION="us-west-2"
```

Bash:

```Bash
export AWS_ACCESS_KEY_ID=""
export AWS_SECRET_ACCESS_KEY=""
export AWS_SESSION_TOKEN=""
export AWS_REGION="us-west-2"
```

## Running the build

The only required variables are the subnet and vpc_id.  Make sure to specify a network that allows fort a public IP to be assigned so that packer can reliably attach during provisioning.

```Bash
packer build -var "subnet_id=subnet-00000000000000" -var "vpc_id=vpc-00000000000000000" ./aws-win2019.json
```

## Note on Sysprep

AWS provides [EC2Launch v2](https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/ec2launch-v2.html) in order to sysprep and ready Windows server to deploy from image, which is run as the final step of image prep.  2012 or earlier images cannot use this method, and will need to rely on [EC2Config](https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/Creating_EBSbacked_WinAMI.html#sysprep-using).
