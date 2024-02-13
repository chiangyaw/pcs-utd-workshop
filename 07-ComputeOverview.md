# Prisma Cloud Ultimate Test Drive (UTD) Workshop
## Prisma Cloud Compute Edition Overview
Prisma Cloud offers a rich set of cloud workload protection capabilities. Collectively, these features are called Compute. Compute has a dedicated management interface, called Compute Console, that can be accessed in one of two ways, depending on the product you have. Prisma Cloud Enterprise Edition — Hosted by Palo Alto Networks. Prisma Cloud Enterprise Edition is a SaaS offering. Prisma Enterprise Edition comprises 3 parts: Cloud Security, Application Security and Runtime Security. Prisma Cloud Compute is a standalone version of Prisma Cloud Runtime Security and can be self hosted.
    
![alt text](/resouces/pcc-screen-01.png)

Prisma Cloud Compute Edition (PCCE) - Hosted by you in your environment. Prisma Cloud Compute Edition (PCCE) is a self-hosted offering that’s deployed and managed by you. It includes the Prisma Cloud Compute module only. You can download the Prisma Cloud Compute Edition software from the Palo Alto Networks Customer Support Portal. Compute Console is delivered as a container image, so you can run it on any host with a container runtime (e.g. Docker Engine).
    
![alt text](/resouces/pcc-screen-02.png)

With Prisma Cloud Compute Edition (PCCE), Radar is the primary interface for monitoring and understanding your environment. It is the default view when you first log into PCCE Console. It is designed to let you visualize and navigate through all of Prisma Cloud’s data. For example, you can visualize connectivity between microservices, then instantly drill into the per-layer vulnerability analysis tool, assess compliance, and investigate incidents, all without leaving the Radar canvas.

In this activity, you will:
* Review and operate the Radar
* Review image for easy analysis of your containerized apps
* Review network traffic flows
* Review runtime, vulnerability or compliance issue they contain

Note: This is a standalone activity and is not dependent on other activities.

### Log in to Prisma Cloud Compute Edition Console
1. There are a couple of ways to access the Prisma Cloud Compute Edition Console (PCCE Console) in this lab.
2. Approach 1 - Application Portal:
    * Head over to the Application Portal
        *  Credentials: kasm_user/p@lo@lto
    * Click on Prisma Cloud Compute Console . Henceforth referred to as PCCE Console
    
    ![alt text](/resouces/pcc-screen-03.png)
    
    * When presented a Security exception, click on Advanced > Proceed to 10.160.154.170 (unsafe)
    
    ![alt text](/resouces/pcc-screen-04.png)
    ![alt text](/resouces/pcc-screen-05.png)
    
    * Login to the PCCE console using the following credentials, with Local/LDAP in the drop down:
        * Credentials: admin/p@lo@lto
3. Approach 2 - Via External Address:
    * Click on Docker Workstation CloudShare Tab. From the left pane, select Connectivity > Connection Details > External Address (when you click on it, the address will be copied to clipboard)
    
    ![alt text](/resouces/pcc-screen-06.png)
    
    * On your laptop browser, navigate to: https://<external address>:8083
        Note: You will get a security exception, please ignore it for this lab and proceed to the login page. We are using a self-signed certificate, which causes the exception.
4. If the message Your connection is not private opens, click Advanced, and then Proceed to <IP address> (unsafe). Non Chrome browsers might have a different behavior
5. Login to the PCCE console using the following credentials, with Local/LDAP in the drop down:
    * Credentials: admin/p@lo@lto

### Prisma Cloud Compute Edition Overview
1. Once logged in, you will be placed in Radars, the primary interface for monitoring and understanding your environment. It is designed to let you visualize and navigate through all of Prisma Cloud Compute’s data. Click on any container to view the details on that container.The defender and the console containers are the key components for Prisma Cloud Compute Edition.

    ![alt text](/resouces/pcc-screen-07.png)
    ![Alt text](/resouces/pcc-screen-08.png)

2. Change the View based on different Radar view categories by clicking the dropdown on the top left corner

    ![Alt text](/resouces/pcc-screen-09.png)

3. Click Radars > Hosts, then click the docker-workstation host icon to review the host dashboard. There is only one host in this lab.

    ![Alt text](/resouces/pcc-screen-10.png)

4. Change the View based on different Radar view categories by clicking the dropdown on the top left corner.

Once you're done, you can move on to the next section [here](/08-ApplicationSecurity.md)