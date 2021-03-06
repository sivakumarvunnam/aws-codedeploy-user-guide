# Working with the AWS CodeDeploy Agent<a name="codedeploy-agent"></a>

 The AWS CodeDeploy agent is a software package that, when installed and configured on an instance, enables that instance to be used in AWS CodeDeploy deployments\. 

**Note**  
 The AWS CodeDeploy agent is required only if you deploy to an EC2/On\-Premises compute platform\. The agent is not required for deployments that use the AWS Lambda compute platform\. 

A configuration file is placed on the instance when the agent is installed\. This file is used to specify how the agent works\. This configuration file specifies directory paths and other settings for AWS CodeDeploy to use as it interacts with the instance\. You can change some of the configuration options in the file\. For information about working with the AWS CodeDeploy agent configuration file, see [AWS CodeDeploy Agent Configuration Reference](reference-agent-configuration.md)\.

For more information about working with the AWS CodeDeploy agent, such as steps for installing, updating, and verifying versions, see [Managing AWS CodeDeploy Agent Operations](codedeploy-agent-operations.md)\.


+ [Operating Systems Supported by the AWS CodeDeploy Agent](#codedeploy-agent-supported-operating-systems)
+ [Communication Protocol and Port for the AWS CodeDeploy Agent](#codedeploy-agent-outbound-port)
+ [AWS SDK for Ruby \(aws\-sdk\-core\) Support for the AWS CodeDeploy Agent](#codedeploy-agent-aws-sdk-core-support)
+ [Supported Versions of the AWS CodeDeploy Agent](#codedeploy-agent-supported-versions)
+ [Application Revision and Log File Cleanup](#codedeploy-agent-revisions-logs-cleanup)
+ [Managing AWS CodeDeploy Agent Operations](codedeploy-agent-operations.md)

## Operating Systems Supported by the AWS CodeDeploy Agent<a name="codedeploy-agent-supported-operating-systems"></a>

### Supported Amazon EC2 AMI Operating Systems<a name="codedeploy-agent-supported-operating-systems-ec2"></a>

The AWS CodeDeploy agent has been tested on the following Amazon EC2 AMI operating systems:

+ Amazon Linux 2017\.03\.x, 2016\.09\.0, 2016\.03\.1, 2016\.03\.0, 2015\.03, 2014\.09\.1

+ Ubuntu Server 16\.04 LTS and 14\.04 LTS 

+ Microsoft Windows Server 2016, 2012 R2, and 2008 R2

+ Red Hat Enterprise Linux \(RHEL\) 7\.x

The AWS CodeDeploy agent is available as open source for you to adapt to your needs\. It can be used with other Amazon EC2 AMI operating systems\. For more information, go to the [AWS CodeDeploy Agent](https://github.com/aws/aws-codedeploy-agent) repository in GitHub\.

### Supported On\-Premises Operating Systems<a name="codedeploy-agent-supported-operating-systems-on-premises"></a>

The AWS CodeDeploy agent has been tested on the following on\-premises operating systems:

+ Ubuntu Server 14\.04 LTS

+ Microsoft Windows Server 2016, 2012 R2, and 2008 R2 

+ Red Hat Enterprise Linux \(RHEL\) 7\.x

The AWS CodeDeploy agent is available as open source for you to adapt to your needs\. It can be used with other on\-premises instance operating systems\. For more information, go to the [AWS CodeDeploy Agent](https://github.com/aws/aws-codedeploy-agent) repository in GitHub\.

## Communication Protocol and Port for the AWS CodeDeploy Agent<a name="codedeploy-agent-outbound-port"></a>

The AWS CodeDeploy agent communicates outbound using HTTPS over port 443\.

## AWS SDK for Ruby \(aws\-sdk\-core\) Support for the AWS CodeDeploy Agent<a name="codedeploy-agent-aws-sdk-core-support"></a>

Versions of the AWS CodeDeploy agent earlier than 1\.0\.1\.880 are compatible only with version 2\.1\.2 and earlier versions of the AWS SDK for Ruby \(aws\-sdk\-core 2\.1\.2\)\. If you are using a version of the AWS CodeDeploy agent earlier than 1\.0\.1\.880, we recommend that you update to the latest version\. For information, see the following:

+ [Determine the Version of the AWS CodeDeploy Agent](codedeploy-agent-operations-version.md)

+ [Install or Reinstall the AWS CodeDeploy Agent](codedeploy-agent-operations-install.md)

The latest version of the AWS SDK for Ruby compatible the AWS CodeDeploy Agent is aws\-sdk\-core 2\.3\.

## Supported Versions of the AWS CodeDeploy Agent<a name="codedeploy-agent-supported-versions"></a>

Your instances must be running a supported version of the AWS CodeDeploy agent\. The current minimum supported version is 1\.0\.1\.854\. If you are running an earlier version, deployments to your instances may fail\. 

The following table lists the currently supported versions of the AWS CodeDeploy agent and the features and enhancements included with each release\.


| Version | Release date | Details | 
| --- | --- | --- | 
|  1\.0\.1\.1352  |  November 16, 2017  |  **Feature**: Introduced a new feature for testing and debugging an EC2/On\-Premises deployment on a local machine or instance where the AWS CodeDeploy Agent is installed\.  | 
|  1\.0\.1\.1106  |  May 16, 2017  |  **Feature**: Introduced new support for handling content in a target location that wasn't part of the application revision from the most recent successful deployment\. Deployments options for existing content now include retaining the content, overwriting the content, or failing the deployment\.  **Enhancement**: Made the AWS CodeDeploy agent compatible with version 2\.9\.2 of the AWS SDK for Ruby \(aws\-sdk\-core 2\.9\.2\)\.  | 
|  1\.0\.1\.1095  |  March 29, 2017  |  **Enhancement**: Introduced support for the AWS CodeDeploy agent in the China \(Beijing\) Region\. **Enhancement**: Enabled Puppet to run on Windows Server instances when invoked by a lifecycle event hook\. **Enhancement**: Improved the handling of `untar` operations\.  | 
| 1\.0\.1\.1067 | January 6, 2017 |  **Enhancement**: Revised many error messages to include more specific causes for deployment failures\. **Enhancement**: Fixed an issue that prevented the AWS CodeDeploy agent from identifying the correct application revision to deploy during some deployments\. **Enhancement**: Reverted the usage of `pushd` and `popd` before and after the `untar` operation\.  | 
| 1\.0\.1\.1045 | November 21, 2016 | Enhancement: Made the AWS CodeDeploy agent compatible with version 2\.6\.11 of the AWS SDK for Ruby \(aws\-sdk\-core 2\.6\.11\)\.  | 
| 1\.0\.1\.1037 | October 19, 2016 |  The AWS CodeDeploy agent for Amazon Linux, RHEL, and Ubuntu Server instances has been updated with the following change\. For Windows Server instances, the latest version remains 1\.0\.1\.998\. **Enhancement**: The agent can now determine which version of Ruby is installed on an instance so it can invoke the `codedeploy-agent` script using that version\.  | 
| 1\.0\.1\.1011\.1 | August 17, 2016 | Enhancement: Removed the changes introduced by version 1\.0\.1\.1011 due to issues with shell support\. This version of the agent is functionally equivalent to version 1\.0\.1\.998 released on July 11, 2016\. | 
| 1\.0\.1\.1011 | August 15, 2016 | The AWS CodeDeploy agent for Amazon Linux, RHEL, and Ubuntu Server instances has been updated with the following changes\. For Windows Server instances, the latest version remains 1\.0\.1\.998\.**Feature**: Added support for invoking the AWS CodeDeploy agent using the bash shell on operating systems where the systemd init system is in use\.Enhancement: Enabled support for all versions of Ruby 2\.x in the AWS CodeDeploy agent and the AWS CodeDeploy agent updater\. Updated AWS CodeDeploy agents are no longer dependent on Ruby 2\.0 only\. \(Ruby 2\.0 is still required for deb and rpm versions of the AWS CodeDeploy agent installer\.\) | 
| 1\.0\.1\.998 | July 11, 2016 |  **Enhancement**: Fixed support for running the AWS CodeDeploy agent with user profiles other than *root*\. The variable named `USER` is replaced by `CODEDEPLOY_USER` to avoid conflicts with environmental variables\.  | 
| 1\.0\.1\.966 | June 16, 2016 |  **Feature**: Introduced support for running the AWS CodeDeploy agent with user profiles other than *root*\. **Enhancement**: Fixed support for specifying the number of application revisions you want the AWS CodeDeploy agent to archive for a deployment group\. **Enhancement**: Made the AWS CodeDeploy agent compatible with version 2\.3 of the AWS SDK for Ruby \(aws\-sdk\-core 2\.3\)\.  **Enhancement**: Fixed issues with UTF\-8 encoding during deployments\. **Enhancement**: Improved accuracy when identifying process names\.  | 
| 1\.0\.1\.950 | March 24, 2016 |  **Feature**: Added installation proxy support\. **Enhancement**: Updated the installation script to not download the AWS CodeDeploy agent if the latest version is already installed\.  | 
| 1\.0\.1\.934 | February 11, 2016 |  **Feature**: Introduced support for specifying the number of application revisions you want the AWS CodeDeploy agent to archive for a deployment group\.   | 
| 1\.0\.1\.880 | January 11, 2016 | Enhancement: Made the AWS CodeDeploy agent compatible with version 2\.2 of the AWS SDK for Ruby \(aws\-sdk\-core 2\.2\)\. Version 2\.1\.2 is still supported\.  | 
| 1\.0\.1\.854 | November 17, 2015 |  **Feature**: Introduced support for the SHA\-256 hash algorithm\.   After October 17, 2016, all installations of the AWS CodeDeploy agent must be updated, at minimum, to version 1\.0\.1\.854 or deployments will fail\. For more information see [Deployment fails with the message “Validation of PKCS7 signed message failed”](troubleshooting-deployments.md#troubleshooting-deployments-agent-SHA-256)\.  **Feature**: Introduced version tracking support in `.version` files\. **Feature**: Made the deployment group ID available through the use of an environment variable\. **Enhancement**: Added support for monitoring AWS CodeDeploy agent logs using [Amazon CloudWatch Logs](http://docs.aws.amazon.com/AmazonCloudWatch/latest/DeveloperGuide/WhatIsCloudWatchLogs.html)\.  | 

For related information, see the following:

+ [Determine the Version of the AWS CodeDeploy Agent](codedeploy-agent-operations-version.md)

+ [Install or Reinstall the AWS CodeDeploy Agent](codedeploy-agent-operations-install.md)

For a history of AWS CodeDeploy agent versions, see the [Release Repository on GitHub](https://github.com/aws/aws-codedeploy-agent/releases)\.

## Application Revision and Log File Cleanup<a name="codedeploy-agent-revisions-logs-cleanup"></a>

The AWS CodeDeploy agent archives revisions and log files on instances\. The AWS CodeDeploy agent cleans up these artifacts to conserve disk space\.

**Application revision deployment logs**: You can use the **:max\_revisions:** option in the agent configuration file to specify the number of application revisions to archive by entering any positive integer\. AWS CodeDeploy also archives the log files for those revisions\. All others are deleted, with the exception of the log file of the last successful deployment\. That log file will always be retained, even if the number of failed deployments exceeds the number of retained revisions\. If no value is specified, AWS CodeDeploy will retain the five most recent revisions in addition to the currently deployed revision\. 

**AWS CodeDeploy logs**: For Amazon Linux, Ubuntu Server, and RHEL instances, the AWS CodeDeploy agent rotates the log files under the `/var/log/aws/codedeploy-agent` folder\. The log file is rotated at 00:00:00 \(instance time\) daily\. Log files are deleted after seven days\. The naming pattern for rotated log files is `codedeploy-agent.YYYYMMDD.log`\.