# Prisma Cloud Ultimate Test Drive (UTD) Workshop
## Prisma Cloud Application Security
The Application Security on Prisma Cloud console provides comprehensive security for your software engineering environment, covering the entire software development lifecycle from code to cloud including Infrastructure as Code (IaC) security, Software Composition Analysis (SCA), Secrets Security, CI/CD pipeline security and container image scanning. Application Security is manifested through visibility, detection, prevention, and remediation capabilities. By leveraging these, you gain comprehensive insights into your engineering ecosystem and establish a robust security posture to protect your organization’s software development environment.

In this activity, you will:
* Examine code that have secrets hardcoded/exposed
* Investigate issues related to misconfigured Kubernetes resource definitions
* Examine vulnerabilities that occur due to vulnerable packages within Dockerfiles
* Investigate misconfigurations in storage related resource definitions

Note: This is a standalone activity and is not dependent on other activities.


### Examine code that has secrets hardcoded/exposed
1. Navigate to Prisma Cloud > Application Security > Code > Projects. Below are a few examples of filters that you can use. Make sure that there’s nothing selected for the Severities filter.
2. Select the Secrets tab and set the repository filter to utd-labs-qa/utd-vuln-code
![alt text](/resouces/pcs-screen-82.png)
3. The above filter lists all the resource definitions (Terraform and AWS CloudFormation) where secrets are hard coded or exposed. Explore the different code blocks that are matched by this filter.
4. Click on cnf.yaml and on the right pane, select issues and scroll down to see the details.

### Investigate IaC Misconfigurations
1. Select the IaC Misconfiguration tab and set the below filters:
    * Repository: utd-labs-qa/utd-vuln-code
    * Issue Status: Errors
    * Severities: Critical, High
    Note: Once you apply the filter, you may need to scroll down the page to find the highlighted result.
![alt text](/resouces/pcs-screen-83.png)
2. The above filter lists all the issues/misconfiguration within the selected repository. Explore the different code blocks that are matched by this filter.

### Examine vulnerabilities in code
1. Select the Vulnerabilities tab and set the below filters:
    * Repository: utd-labs-qa/utd-vuln-code
    * Issue Status: Errors
    * Code Categories: Vulnerabilities
    * Severities: Critical, High
2. The above filter lists all the resource definitions (Dockerfiles) vulnerable base-image, package or code is detected. Explore the different code blocks that are matched by this filter.
![alt text](/resouces/pcs-screen-84.png)
3. If you had clicked on the CVE link, to return to Prisma Cloud Screen, select CloudShare > Keyboard > Home

### Prisma Cloud Application Security
1. Head over to [utd-vuln-code Github repository](https://github.com/utd-labs-qa/utd-vuln-code/tree/development). This repo contains intentionally vulnerable code and this repo has already been onboarded within Prisma Cloud, which we will review in a bit.
![alt text](/resouces/pcs-screen-85.png)
2. Head over to the [open pull requests in the Github repo](https://github.com/utd-labs-qa/utd-vuln-code/pull/2).
3. Here, you can see various comments by Prisma Cloud that occur automatically when a pull request is created for an onboarded source code repository.
![alt text](/resouces/pcs-screen-86.png)
4. Looking closely at one of the findings and comments, you can see the violation title and description and also information on how to fix it. You can also see the code snippet which triggered this violation.
![alt text](/resouces/pcs-screen-87.png)
5. Scrolling to the top of the PR, clicking on View reviewed changes brings up another interesting view which you can explore.
![alt text](/resouces/pcs-screen-88.png)
![alt text](/resouces/pcs-screen-89.png)
6. You can also view these findings in Prisma Cloud as well. Head over to Prisma Cloud > Application Security > Code > Projects > VCS Pull Requests and select the following filters:
    * Repositories: utd-labs-qa/utd-vuln-code
    * Pull Request: #2 - Updates
![alt text](/resouces/pcs-screen-90.png)

### Auto Remediation
1. Navigate to Prisma Cloud > Application Security > Code > Projects and click on the overview tab. Select the below filters. Make sure to unselect the filters selected in the previous task(s) first.
    * Repository: utd-labs-qa/utd-vuln-code
2. Note: Please note that you will not be able to see “Fix” and “Submit” options as we are using a user with Read-Only permissions for the purpose of the lab. “Fix” and “Submit” options will apply the Prisma Cloud suggested fix and commit the changes to the source control repository. The “Fix” and “Submit” options are included in the screenshots to demonstrate the capabilities of the Application Security module.
![alt text](/resouces/pcs-screen-91.png)
3. Clicking on any of the results will display the Details section that contains information on what the fix is and is highlighted in green.
![alt text](/resouces/pcs-screen-92.png)
4. Clicking on + icon against a file or sub results of the file will create a fix and will be added to the staged PR. When you click Submit, the PR will be created with all the fixes that you selected.

Once you're done, you can move on to the next section [here](/09-CICDSecurity.md)