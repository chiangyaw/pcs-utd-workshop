# Prisma Cloud Ultimate Test Drive (UTD) Workshop
## Assignment 3.1
### Prisma Cloud CI/CD Security
Prisma Cloud CI/CD Security covers a set of predefined rules that aim to identify vulnerabilities in the CI/CD pipeline by analyzing the security settings and configurations of various systems, as well as their inter-connectivity. The risks are classified based on different security categories, including attack vectors, misconfigurations, and bad practices found throughout the CI/CD pipeline.

Through 'CI/CD Risks', you can view an inventory and description of the CI/CD risks detected in a scan, including their severity and the potential impact of the risk. You can remediate risks events by applying suggested solutions or suppress them if you do not want not to actively address them. In addition you can view a Kill Chain graph, which visualizes the stages of a cyber attack on the repository CI/CD pipeline.

Notes: The lab uses a read-only user, which doesn’t have access to all parts of the Prisma Cloud. Because of this, you will not be able to see a lot of the items described in this particular task. Only non-read-only users have access to these parts. 

#### CI/CD Risks
Note: This section of the lab is not visible to read-only users, hence this is more on information basis only. 
1. When you select Prisma Cloud > Application Security > Visibility > Repositories, you will see all the repos that are on boarded onto Prisma Cloud.

    ![alt text](/resources/pcs-screen-93.png)

2. You can also see the issues and the code Technologies for those repositories. Clicking on the icon under the Actions section will open up a further details of that repo

    ![alt text](/resources/pcs-screen-94.png)
    * Details: 
    
    ![alt text](/resources/pcs-screen-95.png)
    
    * Graph:
    
    ![alt text](/resources/pcs-screen-96.png)
    
    * Expanding the individual items within the graph will provide more information.
    
    ![alt text](/resources/pcs-screen-97.png)

3. Within Prisma Cloud > Application Security > CICD > CICD Risks , we can get visibility into your CICD environments that are connected to Prisma Cloud.

    ![alt text](/resources/pcs-screen-98.png)

4. Scrolling further down the page, we can see the Alerts and clicking on one of the Alerts will bring up more information about that alert.

    ![alt text](/resources/pcs-screen-99.png)

5. Here you can see the Risk Location in the Delivery Chain, which shows where this alert/attack fits in into the software delivery chain. You can also see further Details and Description of this Vulnerability/Alert and also Steps to Solve.

    ![alt text](/resources/pcs-screen-100.png)

6. Clicking on Open Events will show other alerts as well

    ![alt text](/resources/pcs-screen-101.png)

7. Exploring other alerts will show more information.

    ![alt text](/resources/pcs-screen-102.png)

You have completed the Prisma cloud Ultimate Test Drive (UTD) Workshop. You can head over to the summary section [here](/10-Summary.md).