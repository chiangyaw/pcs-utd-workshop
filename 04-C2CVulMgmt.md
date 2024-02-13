# Prisma Cloud Ultimate Test Drive (UTD) Workshop
## Prisma Cloud Code to Cloud Vulnerability Management
Identifying and remediating vulnerabilities across applications, workloads and systems is important to protect against cyberattacks and keep data safe. This comes as no surprise, considering that 80% of open-source software packages contain vulnerabilities. Prisma Cloud offers code-to-cloud traceback capability, which offers users a visual map of all application artifacts from code to cloud. With code-to-cloud traceback, users can precisely identify and address artifacts throughout the application lifecycle.

In this activity, you will:
* View and understand vulnerabilities presented in the cloud environment.
* Analyze the impact of the vulnerability presented
* View how Prisma Cloud can be leveraged to reduce security risks caused by vulnerabilities.

Note: This is a standalone activity and is not dependent on other activities.

### Prisma Cloud Code to Cloud Vulnerability Management
1. Navigate to **Prisma Cloud Enterprise Edition > Cloud Security > Dashboard > UTD - Vulnerabilities.**
2. Set the following filters (you can add additional filter by clicking on the Add Filter button):
    * Time Range = All Time
    
    ![alt text](/resources/pcs-screen-49.png)

This provides an overview of the current vulnerabilities that exist across your system. A modified version of this dashboard should be visible to you in the lab. Wtih this dashboard, users can prioritize the vulnerabilities in the cloud environment, focusing on vulnerabilities that are Critical & High in severity, Exploitable, Patchable and ultimately what is in use. It also provides the top impacting vulnerabilities so that the users can investigate further on the impact.

3. Scroll down to the bottom on the dashboard, you will see the **Vulnerability Impact By Stage**. This gives the users a view on how the vulnerability and impacting the environment, and the lifecycle of the vulnerability all the way from Code & Build, Deploy, and Runtime. 
    
    ![alt text](/resources/pcs-screen-50.png)

### Prisma Cloud Code to Cloud Infinity Graph
Note: This section of the lab is not visible to read-only users, hence this is more on information basis only. 
1. By clicking into any of the CVEs on **Top Impacting Vulnerabilities**, it will open up a graph showing a visual map of how a specific vulnerabilities mapped from code to cloud. 
    
    ![alt text](/resources/pcs-screen-51.png)

The Code to Cloud Infinity Graph shows how a single vulnerability end up in runtime environment, where it all start from code. By having this visual map, users is able to trace back all the way to the source, and fix it there. With the Infinity Graph, users are also able to identify exactly where the vulnerabilty is discovered, across different applictions throughout the lifecycle. The ultimate goal is to fix all these impacted applications, and minimize the attack surface in the cloud environment.

2. By clicking into the specific CVE (triangle icon), it will open up a side car window, where it will show the details of the CVE, which include the stages impacted, CVSS score, severity of the CVE and also Risk factors. It also provide a description of the CVE.

    ![alt text](/resources/pcs-screen-52.png)

3. By clicking into Assets, it will show all the assets that are impacted, and here the users are able to view the fix recommended by Prisma Cloud, and click into actionable items to remediate the vulnerability, such as Submit Pull Request, Create Jira Ticket, etc, depending on which stage the vulnerability is required to be fix.

    ![alt text](/resources/pcs-screen-53.png)

Over here, the side window also shows the Package Version & Fix Version for the package related to the CVE. In order for the vulnerability to be remediated. Prisma Cloud not just detect the CVE, it also provides recommendation on the fix to remediate the vulnerability. With these information and actionable buttons, users do not need to jump to a different solution or manually create tickets to fix all these vulnerabilities, which ultimate reduce the time required to fix and remediate vulnerability in their cloud environment.

Once you're done, you can move on to the next section [here](/04-C2CVulMgmt.md)