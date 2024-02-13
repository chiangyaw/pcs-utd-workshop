# Prisma Cloud Ultimate Test Drive (UTD) Workshop
## Overview of Your Ultimate Test Drive Class Environment
Before beginning of this workshop, make sure you have a laptop/desktop with a reliable browser installed, and a proper internet connectivity. In any situation if you are facing connectivity issue or not able to access Cloudshare environment, please try to disable your SASE client or firewall, and try again. If the issue still persist, please contact your lab instructor.

### Log in to your Ultimate Test Drive Class Environment
1. Open a browser window and navigate to the class URL provided by your instructor. If you have an invitation email, you will find the class URL and passphrase there.
2. Complete the registration form and click Register and Login at the bottom.
3. Depending on your browser, you may be asked to install a plugin. Please click yes to allow the plugin to be installed, then continue the login process.
4. Once you log in, the environment will be created automatically for you. The upper left-hand corner will show you the progress of the preparation. You will see the lab availability time when it is ready for use.
![alt text](/resouces/cloudshare-screen-1.png)
Note: You can leverage the **keyboard > send text** feature inside of CloudShare when the guide instructs you to copy/paste linux commands. Also note that when copying/pasting commands, make sure to remove the line breaks if any before commands are executed.

### Docker Workstation Overview
The Docker workstation provided in this workshop has multiple applications running on it in the form of Docker containers such as:
* Prisma Cloud Compute Edition (Console & Defender)
* Prometheus
* Grafana
* Splunk
* Visual Studio Code
* Jenkins
* Registry v2
* DVWA - Damn Vulnerable Web Application docker container, which is a PHP/MySQL web application that is very vulnerable
* Webhook tester
* Mail Server

All the above applications are accessible via the Application Portal tab from the CloudShare environment. To access and login to the Docker workstation, follow the following steps:
1. Select the Docker Workstation tab to open the ssh terminal that is already logged in to this VM. If not already logged in, use the CloudShare interface to login.
![alt text](/resouces/cloudshare-screen-2.png)
If you prefer to use your own terminal from your laptop, you can ssh to this VM using the External Address and the user name and password under Connection Details in the Connectivity section.
Note: You can also SSH to Docker Workstation from your laptop terminal (MAC) or Putty (Windows) using the external address and login credentials as highlighted in the screenshot.

```
ssh sysadmin@<external address>
```
![alt text](/resouces/cloudshare-screen-3.png)

### Application Portal Overview
The Application Portal is one stop shop for all the applications that are used in this workshop. Under the hood, it utilizes Kasm Workspaces, which is a streaming platform for delivering browser-based access to applications, and web services and this setup is running as a docker container within the Docker workstation. Within this workspace, Chrome browser is preinstalled and it provides a secure and isolated browsing environment.

A few key points to take note:
1. Credentials: kasm_user/p@lo@lto
2. Homepage: http://homepage:3000 (henceforth referred to as Homepage).
3. The Application Portal, upon startup, opens the webpage: If Homepage is not loaded, please refresh the browser tab or open a new browser tab and navigate to aforementioned URL
4. Homepage provides you access to the various applications used within this workshop.
5. These applications are all running as Docker containers and they are accessible via their internal IPs only via the Application portal.
6. This ensures that the traffic doesn’t go out the internet, making the setup a bit more secure and reduces latency.

Here are also a list of applications that are accessible via Application Portal and the respective tracks where these are used in the lab:
1. Prisma Cloud Compute Edition: Click this tab to login on Prisma Cloud Compute Edition (PCCE) console
    * Credentials: admin/p@lo@lto
2. Prometheus: Monitoring and Alerting Tookit
    * Credentials: admin/admin
3. Grafana: Analytics and interactive visualization web application
4. Splunk: Log aggregation
    * Credentials: admin/password
5. Webhook Receiver: Webhook container to receive incoming webhooks
6. Mail Server: Locally hosted mail server
7. Visual Studio Code: IDE 
    * Credentials: admin/password
8. Jenkins: CICD
    * Credentials: admin/p@lo@lto
9. DVWA: Damn Vulnerable Web Application docker container is a PHP/MySQL web application

Below are the steps to access the Application Portal:
1. Select the Application Portal tab to open the portal.
2. Credentials: kasm_user/p@lo@lto

    ![alt text](/resouces/applicationportal-login-1.png)

3. Once logged in, when you click inside the page, allow the clipboard permission when prompted.

    ![alt text](/resouces/applicationportal-login-2.png)

4. Below are some screenshots of the interface.
    
    ![alt text](/resouces/applicationportal-login-3.png)

5. Important: This is a browser in browser setup running as a Docker container. DO NOT open more than 3-4 browser tabs at the same time as it may cause resource exhaustion on the Docker workstation VM.
6. If due to inactivity, you see a blue screen when you access the Application Portal, click on “Connect” option
    
    ![alt text](/resouces/applicationportal-login-4.png)

### Kubernetes VM Overview
The Kubernetes VM provided in this workshop is running a single node Kubenetes cluster launched via k3s. Within the lab, you will be working with this VM to perform various things such as deploying Prisma Cloud defender, Argo CD, running log4j attacks etc.

To access and login to Kubernetes VM, follow these steps:
1. Select the Kubernetes tab to open the ssh terminal that is already logged in to this VM. If not already logged in, use the CloudShare interface to login.

If you prefer to use your own terminal from your laptop, you can ssh to this VM using the External Address and the user name and password under Connection Details in the Connectivity section.

Note: You can also SSH to Docker Workstation from your laptop terminal (MAC) or Putty (Windows) using the external address and login credentials as highlighted in the screenshot.
```
ssh sysadmin@<external address>
```
![alt text](/resouces/cloudshare-screen-4.png)

Once you are able to access the items above, you can move on to the next section [here](02-PrismaCloudOverview.md)!