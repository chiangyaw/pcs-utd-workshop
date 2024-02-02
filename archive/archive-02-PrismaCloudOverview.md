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

### Prisma Cloud Dasboards and Inventory
1. In this task, we will explore various parts of the UI within Prisma Cloud that provide rich contextualized information correlated from various data sources within Prisma Cloud. For example, the Dashboards are meant to be a starting point for users in the real world situations to get an overview of their environment. In our lab, some parts of the UI discussed in this specific section are not visible to the read-only user. Hence, we will try our best to show you an overview of what they are and what they look like via screenshots and descriptions.
2. When you first login to Prisma Cloud, from the top left corner, you can select one of the 3 options for your current view: **Cloud Security**, **Runtime Security** and **Application Security**. To get started, select **Cloud Security**.
![alt text](/resouces/pcs-screen-5.png)
3. On the Welcome page, you can see the Urgent Risks and Incidents, which provide you information such as Incidents, Attack Paths, Vulnerabilities, Exposures and Identity Risks. **In the lab, this part is not visible as it’s not available for the read-only user**.
![alt text](/resouces/pcs-screen-6.png)
4. When you select **Prisma Cloud > Cloud Security > Dashboards**, by default you will be able to see four dashboards and also the **Latest Events** section.
![alt text](/resouces/pcs-screen-7.png)
5. **Latest Events (Not Visible):**
    * This presents immediate things that need your attention. This is a continuous real-time feed of events
    ![alt text](/resouces/pcs-screen-8.png)
    * Clicking on **See All Events** will open up all the events
    ![alt text](/resouces/pcs-screen-9.png)
6. **Code To Cloud Dashboard (Not Visible):**
    * This Dashboard provides visibility about various items in your environment categorized into the following 3 categories: Code and Build , Deploy and Runtime. 
    ![alt text](/resouces/pcs-screen-10.png)
    * Clicking on items such as **Repository Systems, Repositories, Container images, Cloud Assets** etc will take you to their respective pages within Prisma Cloud. The Dashboard conveniently provides all things in one place.
7. **Command Center Dashboard (Not Visible):**
    * This dashboard is a command center, which provides information such as Urgent Issues, Urgent Incidents, Top Incidents by Policy, Urgent Attack Paths etc This is a highly customizable dashboard and the screenshots below do not represent all the options visible in the dashboard but merely provides you a glimpse of what’s available.
    ![alt text](/resouces/pcs-screen-11.png)
8. **Vulnerabilities Dashboard (Visible):** This provides an overview of the current vulnerabilities that exist across your system. A modified version of this dashboard should be visible to you in the lab.
    ![alt text](/resouces/pcs-screen-12.png) 
