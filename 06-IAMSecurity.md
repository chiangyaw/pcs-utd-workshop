# Prisma Cloud Ultimate Test Drive (UTD) Workshop
## Prisma Cloud IAM Security
Prisma Cloud IAM security capabilities help you evaluate the effective permissions assigned to users, workloads, and data (also called entitlements) on your cloud provider so that you can properly administer identity and access management (IAM) policies and enforce access using the principle of least privilege. With these information, Prisma Cloud allows user to investigate further on risky IAM permissions and configuration, remediate/mitigrate them to reduce security risks.

In this activity, you will:
* View Alert on risky AWS IAM Permissions.
* Analyze the current resource configuration settings.
* Analyze the change history for the IAM configuration settings(show how the resource got to its current state).
* View how Prisma Cloud remediation commands can be leveraged to remediate security findings.

Note: This is a standalone activity and is not dependent on other activities.

Hint: As you navigate the alerts view in the Prisma Cloud console you can click the Add filters button to enable/disable the needed filters.

### Investigate Risky AWS EC2 IAM Permissions
1. Navigate to Prisma Cloud Enterprise Edition console > Cloud Security > Alerts > Overview.
2. Select the Reset Filters icon on the top right corner of the screen to reset all filters. Use Add Filter option to add the specified filters below
3. In the filter options, select the following:
    * Time Range = All Time
    * Alert Status = Open
    * Policy Severity = High
    * Policy Type = IAM
    * Policy Name = AWS EC2 instance with data destruction permissions
4. Navigate to Prisma Cloud Enterprise Edition console > Cloud Security > Alerts > Overview.
    
    ![alt text](/resources/pcs-screen-66.png)

5. Click on AWS EC2 instance with data destruction permissions and Click on the value under the Asset Name column to view more information about the resource.

    ![alt text](/resources/pcs-screen-67.png)
    ![alt text](/resources/pcs-screen-68.png)

6. In the Resource sidecar, click on the below options to explore further.
    * Clicking on View Config will bring up the configuration of the selected resource
    
    ![alt text](/resources/pcs-screen-69.png)
    
    * Clicking on Overview will provide an overview of the resource. After reviewing, close the pop up or click Done.
    * Clicking on Attack Paths will bring up the attack path graph and highlights where the selected resource fits in the path. Further clicking on the various items within the graph will show relevant information and configuration of the selected item
    
    ![alt text](/resources/pcs-screen-70.png)
    
    * Clicking on the Audit Trail will open up the Audit trail for this resource where you will be able to see the timeline of the configuration changes made on the resource from the time it was discovered by Prisma Cloud. This is continuously monitored by Prisma Cloud and any changes to the configuration are recorded. Click on the </> to view the resource configuration
    
    ![alt text](/resources/pcs-screen-71.png)
    
    * Clicking on Alerts will show the various alerts that are open for this specific resource
    
    ![alt text](/resources/pcs-screen-72.png)
    
    * Clicking on Findings will show the various findings about the selected resource and the severity of those findings.
    
    ![alt text](/resources/pcs-screen-73.png)
    
    * Clicking on the Vulnerabilities will show the various vulnerabilities that were detected for this resource. Further clicking on options such as Critical & High , Exploitable and Patchable will filter the results.
    
    ![alt text](/resources/pcs-screen-74.png)
    
    * Feel free to explore the rest of the options and once done, close the window.
    
    ![alt text](/resources/pcs-screen-75.png)

7. Click on AWS EC2 instance with data destruction permissions and click the corresponding value for the Alert ID to see the Overview. and remediation Recommendation.

    ![alt text](/resources/pcs-screen-76.png)
    ![alt text](/resources/pcs-screen-77.png)

8. Once done reviewing, close the window.
    
    ![alt text](/resources/pcs-screen-78.png)

### Investigate Over Permissive IAM Permissions
1. In this task, we will find out, with a simple RQL query, the net effective permissions of an IAM user to demonstrate the effectiveness of IAM RQL queries in Prisma Cloud
2. Navigate to Prisma Cloud > Cloud Security > Investigate and select Net AWS IAM Permissions from Saved Searches
    
    ![alt text](/resources/pcs-screen-79.png)

3. The RQL query of the selected search query should look like the following:
```
config from iam where source.cloud.resource.name = 'demo-user' AND
dest.cloud.account = 'AWS Account'
```
4. Click on the Graph icon.

    ![alt text](/resources/pcs-screen-80.png)

5. This graph shows the permissions that the IAM user demo-user holds within the specified AWS Account. Feel free to explore the graph further.
6. Within the Destinations column of the graph, to further narrow down the search to a specific AWS Service such as S3, update the query with the following
```
config from iam where source.cloud.resource.name = 'demo-user' AND dest.cloud.account = 'AWS Account' AND dest.cloud.service.name = 's3'
```
    
![alt text](/resources/pcs-screen-81.png)

7. From the screenshot, you can see that there’s a “*” (wildcard) permission assigned, which is not a best practice implementation in a production environment.
8. To investigate the permissions of the IAM role used by EKS Node in the previous task, use the below query and explore the Graph/Table
```
config from iam where dest.cloud.account = 'AWS Account' AND grantedby.cloud.entity.name = 'EKSNodeGroupRole-cnsp-eu' AND source.cloud.service.name = 'ec2'
```

Once you're done, you can move on to the next section [here](/07-ComputeOverview.md)