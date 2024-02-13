# Prisma Cloud Ultimate Test Drive (UTD) Workshop
## Prisma Cloud Threat Detection
Prisma Cloud enables threat detection across the Cloud Security Posture Management (CSPM) and Cloud Workload Protection Platform (CWPP) modules so that you can prevent and detect security risks across their multi-and-hybrid cloud environments, hosts, containers, and serverless functions. CSPM supports two categories of policies which are Incident and Risk, with Incident being the group of policies that supplies the threat detection functionality and includes two types of anomaly policies: User Entity Behavior Analytics (UEBA) and Network anomaly which utilizes either machine learning or AutoFocus. The Risk category corresponds to the config policies which uses the resource query language (RQL).

With anomaly policies, data is collected from various sources such as audit and network flow logs and are processed using sophisticated data analysis techniques like machine learning, statistical modeling, and graph analysis to detect threats; both known-and-unknown. With RQL based policies, events related to user or network activity are analyzed to match a certain criteria, such as a JSON field having a specific value.

Threat detection in the CWPP module consists of a collection of threat data that is aggregated from a myriad of sources both commercial and open source, and that is then delivered via the Prisma Cloud Intelligence Stream. This threat data is then consumed across various feature sets of Compute such as Vulnerabilities and Runtime. 

In this activity, you will:

* View a Network Alert for suspicious activity
* Analyze the Network Visualization to trace resources that may have been impacted
* View the traffic that is reaching your cloud workloads
* Examine Vulnerabilities that have been detected on your cloud Workload to understand the risk posture

Note: This is a standalone activity and is not dependent on other activities.

Hint: As you navigate the alerts view in the Prisma Cloud console you can click the Add filters button to enable/disable the needed filters.

# Examine a Network Alert
1. In the Prisma Cloud Enterprise Edition console, click the Alerts tab and then Overview.
2. Select the Reset Filters icon on the top right corner of the screen to reset all filters and set the Time Range to All Time.
3. Click on Add Filter icon and select the following options and look for the alert Suspicious Traffic to Multiple AWS Resources:
    * Alert Status = Open
    * Policy Type = Network
    * Cloud Account = AWS Account
    
    ![alt text](/resouces/pcs-screen-54.png)

4. Here you can see a list of resources causing this alert to fire.

    ![alt text](/resouces/pcs-screen-55.png)

# Examining the Traffic from Suspicious IPs
1. Head over to the Investigate window. For your convenience, we have already created a query to list out the resources for the previous alert. To use that, within the Saved Searches, select Suspicious Traffic to multiple AWS Resources.

    ![alt text](/resouces/pcs-screen-56.png)

2. Make sure to set the time window to All Time. Your graph may look a little different as the cloud environment is very dynamic. This shows all the resources that are taking traffic from Suspicious IPs, which are flagged by Prisma Cloud.

    ![alt text](/resouces/pcs-screen-57.png)

3. Toggle between Swimlane and Organic for different visualizations of the traffic.

    ![alt text](/resouces/pcs-screen-58.png)

4. For the rest of the flow, we will stick with Swimlane visualization. Clicking on the GuardDuty Tester VPC will expand it and reveal LinuxBastion host

    ![alt text](/resouces/pcs-screen-59.png)

5. Hover your mouse and click on the line connecting Suspicious IP and Linux Bastion

    ![alt text](/resouces/pcs-screen-60.png)

6. This will open a sidecar. Click on Connection Details Table view to see the breakdown of the traffic flow between suspicious IPs and the LinuxBastion host.

    ![alt text](/resouces/pcs-screen-61.png)
    ![alt text](/resouces/pcs-screen-62.png)

7. Close the Connection Details window and the Suspicious IPs > LinuxBastion window.
8. Click on the LinuxBastion host and this will open another window that provides the network summary of that VM.

    ![alt text](/resouces/pcs-screen-63.png)

9. Click on the LinuxBastion VM, and under the Instance Summary, click the value corresponding to Asset ID to investigate further the VM. Go to the Findings tab at the top of the page to get details

    ![alt text](/resouces/pcs-screen-64.png)
    ![alt text](/resouces/pcs-screen-65.png)

Once you're done, you can move on to the next section [here](/06-IAMSecurity.md)