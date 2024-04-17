# Prisma Cloud Ultimate Test Drive (UTD) Workshop
## Assignment 3.1
### Prisma Cloud CI/CD Security
Prisma Cloud CI/CD Security covers a set of predefined rules that aim to identify vulnerabilities in the CI/CD pipeline by analyzing the security settings and configurations of various systems, as well as their inter-connectivity. The risks are classified based on different security categories, including attack vectors, misconfigurations, and bad practices found throughout the CI/CD pipeline.

Through 'CI/CD Risks', you can view an inventory and description of the CI/CD risks detected in a scan, including their severity and the potential impact of the risk. You can remediate risks events by applying suggested solutions or suppress them if you do not want not to actively address them. In addition you can view a Kill Chain graph, which visualizes the stages of a cyber attack on the repository CI/CD pipeline.

#### CI/CD Risks
1. When you select Prisma Cloud > Application Security > Visibility > Repositories, you will see all the repos that are on boarded onto Prisma Cloud.

    ![alt text](/resources/App_Repo.png)

2. You can also see the issues and the code Technologies for those repositories. Clicking on the icon under the Actions section will open up a further details of that repo

    ![alt text](/resources/App_Repo_Tech.png)
    * Details: 
    
    ![alt text](/resources/App_Repo_Tech_Details.png)
    
    * Graph:
    
    ![alt text](/resources/App_Repo_Tech_Graph.png)
    
    * Expanding the individual items within the graph will provide more information.
    
    ![alt text](/resources/App_Repo_tech_Graph_Expand.png)

3. Within Prisma Cloud > Application Security > CICD > CICD Risks , we can get visibility into your CICD environments that are connected to Prisma Cloud.

    ![alt text](/resources/App_CICD_1.png)

4. Scrolling further down the page, we can see the Alerts and clicking on one of the Alerts will bring up more information about that alert.

    ![alt text](/resources/App_CICD_2.png)

5. Here you can see the Risk Location in the Delivery Chain, which shows where this alert/attack fits in into the software delivery chain. You can also see further Details and Description of this Vulnerability/Alert and also Steps to Solve.

    ![alt text](/resources/App_CICD_Overview.png)

6. Clicking on Open Events will show other alerts as well

    ![alt text](/resources/App_CICD_OpenEvents.png)

7. Exploring other alerts will show more information.

    ![alt text](/resources/App_CICD_Other.png)

8.  Within Prisma Cloud > Application Security >SBOM, you have a catalog of all your software component in your repositories and making it easy to search for packages eg log4j and export the list. 

    ![alt text](/resources/App_SBOM_Generate.png)

You have completed the Prisma cloud Ultimate Test Drive (UTD) Workshop. You can head over to the summary section [here](/10-Summary.md).
