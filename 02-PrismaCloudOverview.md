# Prisma Cloud Ultimate Test Drive (UTD) Workshop
## Prisma Cloud Overview
Prisma Cloud is a comprehensive cloud-native application protection platform (CNAPP) with the industry’s broadest security and compliance coverage. It protects cloud native applications, data, network, compute, storage, users, and higher-level PaaS services across cloud platforms. Prisma Cloud enables capabilities such as Cloud Security Posture Management (CSPM) and Cloud Workload Protection Platform (CWPP) for comprehensive visibility and threat detection across your organization’s hybrid, multi-cloud infrastructure. It dynamically discovers resources as they are deployed and correlates cloud-service-provided data to enable security and compliance insights into your cloud applications and workloads.

In this activity, you will:
* Log in to Prisma Cloud Lab account
* Learn about the Prisma Cloud console and help center
* Review how to on-board a AWS account on Prisma Cloud tenant

Note: This is a standalone activity and is not dependent on other activities.

### Log in to Prisma Cloud Enterprise Edition Console
1. Click on the Prisma Cloud Enterprise tab to open the demo tenant login.
![alt text](/resouces/pcs-screen-1.png)
2. Follow the screen to login and then click on the Prisma Cloud icon.
Note: If you see a page expired message then refresh the web page by clicking on the Home button as highlighted in below screen capture.
3. While using the Prisma Cloud console, you can use CloudShare > Keyboard > Home | Back | Forward to navigate back and forth.
![alt text](/resouces/pcs-screen-2.png)
4. To check the on-boarded public cloud accounts click on the Settings on the and select Account Groups. Click on the 4 Cloud Account(s) under Default Account Group. You can see the public cloud accounts connected to this Prisma Cloud demo account.
Note: The screenshots captured in this workshop guide might vary slightly from the actual lab account.
![alt text](/resouces/pcs-screen-3.png)
![alt text](/resouces/pcs-screen-4.png)
We have already connected AWS, Azure and GCP accounts to this Prisma Cloud tenant, and this lab account can be used for testing across all three public cloud providers. Prisma Cloud also supports Alibaba Cloud & Oracle Cloud Infrastructure.
NOTE: The Prisma Cloud Enterprise Edition account used in this lab is a read-only account, it does not have full access to the Prisma Cloud Service and access to some functions is denied. This account cannot make changes to the configuration of the associated Prisma Cloud Services.

Once you are able to access Prisma Cloud Enterprise Edition Console, you can move on to the next section [here](03-C2CRemediation.md)!