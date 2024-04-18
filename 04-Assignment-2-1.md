# Prisma Cloud Ultimate Test Drive (UTD) Workshop
## Assignment 2.1
### Application Portal Overview
The Application Portal is one stop shop for all the applications that are used in this workshop. Under the hood, it utilizes Kasm Workspaces, which is a streaming platform for delivering browser-based access to applications, and web services and this setup is running as a docker container within the Docker workstation. Within this workspace, Chrome browser is preinstalled and it provides a secure and isolated browsing environment.

Below are the steps to access the Application Portal:
1. Select the Application Portal tab to open the portal.
2. Credentials: kasm_user/p@lo@lto

    ![alt text](/resources/applicationportal-login-1.png)

3. Once logged in, when you click inside the page, allow the clipboard permission when prompted.

    ![alt text](/resources/applicationportal-login-2.png)

4. Below are some screenshots of the interface.
    
    ![alt text](/resources/applicationportal-login-3.png)

5. Important: This is a browser in browser setup running as a Docker container. DO NOT open more than 3-4 browser tabs at the same time as it may cause resource exhaustion on the Docker workstation VM.
6. If due to inactivity, you see a blue screen when you access the Application Portal, click on “Connect” option
    
    ![alt text](/resources/applicationportal-login-4.png)

### Kubernetes VM Overview
The Kubernetes VM provided in this workshop is running a single node Kubenetes cluster launched via k3s. Within the lab, you will be working with this VM to perform various things such as deploying Prisma Cloud defender, Argo CD, running log4j attacks etc.

To access and login to Kubernetes VM, follow these steps:
1. Select the Kubernetes tab to open the ssh terminal that is already logged in to this VM. If not already logged in, use the CloudShare interface to login.


### Log in to Prisma Cloud Compute Edition Console
To access the Prisma Cloud Compute Edition Console (PCCE Console) in this lab, follow these steps:

1. Head over to the Application Portal as mentioned above.
2. Click on Prisma Cloud Compute Console. Henceforth referred to as PCCE Console
![alt text](/resources/ap-screen-1.png)

3. When presented a Security exception, click on Advanced > Proceed to 10.160.154.170 (unsafe)
![alt text](/resources/ap-screen-2.png)
![alt text](/resources/ap-screen-3.png)
![alt text](/resources/ap-screen-4.png)

4. Login to the PCCE console using the following credentials, with Local/LDAP in the drop down:
    * Credentials: admin/p@lo@lto


### Prisma Cloud Compute Edition overview
This task guides you through key elements of the Prisma Cloud Compute console to ensure that you are aware of them. Use this time to explore these elements at your own pace to discover points of interest.

1. Once logged in, you will be placed in Radars, the primary interface for monitoring and understanding your environment. It is designed to let you visualize and navigate through all of Prisma Cloud Compute’s data. Click on any container to view the details on that container.The defender and the console containers are the key components for Prisma Cloud Compute Edition.
![alt text](/resources/pcce-screen-1.png)
![alt text](/resources/pcce-screen-2.png)

2. Change the View based on different Radar view categories by clicking the dropdown on the top left corner

![alt text](/resources/pcce-screen-3.png)

3. Click Radars > Hosts, then click the docker-workstation host icon to review the host dashboard. There is only one host in this lab.

![alt text](/resources/pcce-screen-4.png)

4. Change the View based on different Radar view categories by clicking the dropdown on the top left corner.

### Runtime Security
Runtime defense is the set of features that provide both predictive and threat based active protection for running containers. For example, predictive protection includes capabilities like determining when a container runs a process not included in the origin image or creates an unexpected network socket. Threat based protection includes capabilities like detecting when malware is added to a container or when a container connects to a botnet.

Prisma Cloud has distinct sensors for file system, network, and process activity. Each sensor is implemented individually, with its own set of rules and alerting. The runtime defense architecture is unified to both simplify the admin experience and to show more detail about what Prisma Cloud automatically learns from each image. Runtime defense has two principle object types: models and rules.

PCC features to be used:
* Container Models
* Runtime defense for processes
* Runtime defense for networking
* Runtime defense for file systems

In this activity you will:
* Setup Kubernetes Cluster
* Create runtime policies for Process, Network and File System.
* Test and review event logs to confirm activity

#### Setup Kubernetes Cluster
1. Go back to the main portal, select the Kubernetes tab, this logs in via SSH to the Kubernetes VM.

2. Run the following script to setup your Kubernetes cluster (it will take approximately less than 2 mins for the creation to be complete):
```
bash /home/sysadmin/apps/00-k3s-setup.sh
```
![alt text](/resources/k8s-screen-21.png)

3. Once done, run the below commands to verify that everything is working:
```
alias kubectl='k3s kubectl'
kubectl get pods -A
```

#### Setup Prisma Cloud Defender in Kubernetes
1. Login via SSH to the Kubernetes VM.

2. Run the command to examine the setup script:
```
cat /home/sysadmin/apps/02-install-defender.sh
```

3. When ready, run the script:
```
bash /home/sysadmin/apps/02-install-defender.sh
```
![alt text](/resources/k8s-screen-22.png)

4. Run the following command to see the status of the defender deployment:
```
kubectl -n twistlock get pod -o wide
```
![alt text](/resources/k8s-screen-23.png)

5. Head over to Prisma Cloud Compute Edition Console > Manage > Defenders to verify the successful deployment. It might take 1-2 mins for the defender to show up as active.

![alt text](/resources/pcce-screen-53.png)

6. Navigate to Prisma Cloud Compute Edition Console > Radars > Hosts to see the newly added Kubernetes host. If you don’t see it yet, click on the Refresh icon.

![alt text](/resources/pcce-screen-54.png)

7. We have now successfully deployed Prisma Cloud Defender on the Kubernetes cluster.

#### Setup Kubernetes Auditing and Admission Control
Kubernetes Auditing and Admission Control allows you to setup create security guardrails in your Kubernetes environment by enforcing policies such as protecting against misconfigured or overprivileged pods etc.

1. Navigate to Prisma Cloud Compute Edition Console > Defend > Access and select Kubernetes tab and enable Kubernetes auditing.

![alt text](/resources/pcce-screen-55.png)

2. Click on Add Rule > Select from existing rules

![alt text](/resources/pcce-screen-56.png)

3. Select all the rules in the and click on Add

![alt text](/resources/pcce-screen-57.png)

4. Navigate to Prisma Cloud Compute Edition Console > Defend > Access and select Admission tab and enable Admission Control.

![alt text](/resources/pcce-screen-59.png)

#### Setup ArgoCD
Argo CD is a continuous delivery tool that lets you deploy your application on a Kubernetes cluster. We will be using Argo CD to deploy Bank-Of-Anthos application from the previous activities on our Kubernetes cluster.

1. Run the command to examine the ArgoCD setup script, which sets up required kubernetes namespaces and other things: 
```
cat /home/sysadmin/apps/01-argo-setup.sh
```

2. When ready, run the script:
```
bash /home/sysadmin/apps/01-argo-setup.sh
```
![alt text](/resources/k8s-screen-25.png)

3. Once the script executes successfully, scroll down to the end of the script output to retrieve the login credentials. 
![alt text](/resources/k8s-screen-27.png)

*Note: You are not required to login to ArgoCD GUI for the activities below. However, you can still login with the GUI with the login credentials. You can head over to Application Portal > ArgoCD tile and login using the credentials.*

#### Deploy QA App on Kubernetes Cluster
1. Login via SSH to the Kubernetes VM.

2. Run the following command to see the application that we are
deploying:
```
cat /home/sysadmin/apps/02-qa-argo-app.yaml
```

3. When ready, apply manifest:
```
kubectl apply -f /home/sysadmin/apps/02-qa-argo-app.yaml
```

4. It takes about 1-2 mins for the application to be ready. You can run the following to check on the status:
```
kubectl -n qa get pods
```
![alt text](/resources/k8s-screen-24.png)

*Note: The activities below would not require you to access the Bank of Anthos application. However, you can still navigate to the Application Portal and access the bank-of-anthos application.*

#### Check Container Model States
1. Head over to Kubernetes VM and run the below commands to understand the setup and workloads that we’ll be investigating.

```
kubectl -n qa get po -l app=manual-run
kubectl -n qa get deploy manual-run
```
The output of the first command lists out Pod that is part of a Kubernetes deployment named manual-run. Normally, as soon as this pod starts up, it starts doing malicious things, which sets off alerts. But for the purpose of this lab, we have  modified the startup command so that the Pod does nothing but sleep. This gives us a chance to perform interactive things with that Pod.

![alt text](/resources/k8s-screen-1.png)

2. Navigate to Monitor > Runtime > Container Models. Search for ubuntu:malware (shorthand for the Container image that our malicious deployments are using)

![alt text](/resources/pcce-screen-5.png)

3. If the state(s) are in “Learning”, then click on three dots in the Actions column, choose Manual Relearning. Click on Action again, and choose Manual Relearning again to stop the learning.

![alt text](/resources/pcce-screen-6.png)
![alt text](/resources/pcce-screen-7.png)

#### Container Process Monitoring

1. Login to Kubernetes VM and run the below commands:

```
kubectl -n qa exec -it deploy/manual-run -- bash /opt/manual-run.sh
```
![alt text](/resources/k8s-screen-2.png)

2. Navigate to Prisma Cloud > Monitor > Events > Container Audits and clear the existing filter.

![alt text](/resources/k8s-screen-3.png)

3. Set the below filters. After each filter, hit the Return (or Enter) key.
    * Filter "ubuntu:malware" > Hit Return/Enter
    * Filter "Event type: Crypto Miner Process" > Hit Return/Enter

![alt text](/resources/pcce-screen-8.png)

4. Clicking on the result will bring up more details about the identified process. Once done reviewing, close it.

![alt text](/resources/pcce-screen-9.png)

5. Navigate to Prisma Cloud > Monitor > Events > Admission Audits and clear the existing filter. Set the following filter: Operation: Connect

![alt text](/resources/pcce-screen-10.png)

6. This will list out the events where you/someone connected to a Pod (step 1 of this task). You can click on the result and view the event. When done, click close.

#### Runtime Network Control for DNS
1. Navigate to Prisma Cloud > Monitor > Events > Container Audits and clear the existing filter.

![alt text](/resources/pcce-screen-11.png)

2. Set the below filters. After each filter, hit the Return (or Enter) key:
    * Filter "ubuntu:malware" > Hit "Return/Enter"
    * Filter "Category: network" > Hit "Return/Enter"

![alt text](/resources/pcce-screen-12.png)
![alt text](/resources/pcce-screen-13.png)

3. This filter returns all the results for Network audits and a vertical port scanning process was detected by Prisma Cloud.

#### Runtime Monitoring for File System
1. Navigate to Prisma Cloud > Monitor > Events > Container Audits and clear the existing filter.
![alt text](/resources/pcce-screen-14.png)

2. Set the below filters. After each filter, hit the Return (or Enter) key:
    * Filter "ubuntu:malware" > Hit Enter/Return
    * Filter "Category: filesystem" > Hit Enter/Return

![alt text](/resources/pcce-screen-15.png)
![alt text](/resources/pcce-screen-16.png)

3. Explore the event related to /usr/bin/useradd. Clicking on that, we can see that there was a user created by the script
![alt text](/resources/pcce-screen-18.png)

#### Secure Runtime
1. Navigate to Monitor > Runtime > Container Models. Search for ubuntu:malware (shorthand for the Container image that our malicious deployments are using)
![alt text](/resources/pcce-screen-19.png)

2. In the results row click on three dots (...) and then click Copy Into Rule.
![alt text](/resources/pcce-screen-20.png)

3. Anti-malware - Click on the Anti-malware. Under Anti-malware monitoring and set the Prisma Cloud advanced threat protection to Prevent.
![alt text](/resources/pcce-screen-21.png)

4. Process-Monitoring - Click on the Processes tab
![alt text](/resources/pcce-screen-22.png)
    * Under Denied & all other processes, set the first 2 items to Prevent under Anti-malware and exploit prevention and the last 2 to block
    * Under explicitly denied processes, specify the following processes and set the rule to Prevent:
        - /bin/netcat
        - /opt/xmrig-6.19.2/xmrig
        - /bin/nc.traditional

![alt text](/resources/pcce-screen-23.png)

5. Network-Monitoring - Click on the Networking tab
![alt text](/resources/pcce-screen-24.png)
    * Under Denied & all other network activity, set the outbound IP to ```1.1.1.1``` and set the Outbound IPs effect to Block
    * Scroll down to the DNS Section and enable it.
    * Under Denied and all other domains, set the following domain: ```btc.ss.poolin.me``` and set the Domains effect to Prevent
    ![alt text](/resources/pcce-screen-25.png)

6. File-system Monitoring - Click on File-System tab
![alt text](/resources/pcce-screen-26.png)
    * Set all the items to Prevent under Denied & all other paths > Anti-malware and exploit prevention
    * For Paths list, set /usr/bin/ and set the Paths effect to Prevent
    * Click Save. You will be asked whether to relearn the container model. Click Don’t Relearn.
    ![alt text](/resources/pcce-screen-27.png)
    ![alt text](/resources/pcce-screen-28.png)

7. On the Kubernetes VM , exec into the Pod again and run the following commands to test the rules that we configured.

8. Run: ```kubectl -n qa exec -it deploy/manual-run sh``` ; Now that we have an interactive shell for the Pod, let’s re-run commands from the manual-run.sh that we ran before.

    * Process and Crypto moner Defense: ```/opt/xmrig-6.19.2/xmrig --help```
    ![alt text](/resources/k8s-screen-4.png)

    * Network Defense - I: ```nslookup btc.ss.poolin.me```

    ![alt text](/resources/k8s-screen-5.png)

    * Network Defense - II: ```/bin/netcat```

    ![alt text](/resources/k8s-screen-6.png)

    * Network Defense - III : ```curl 1.1.1.1```

    ![alt text](/resources/k8s-screen-7.png)

    * The previous command will terminate the shell. To reinitiate, run the below command:
    ```
    kubectl -n qa exec -it deploy/manual-run sh
    ```
    * Filesystem (defense against modified binary) : ```gcc /tmp/main2.c -o /usr/bin/main3.o```

    ![alt text](/resources/k8s-screen-8.png)

    * Filesystem : ```useradd test```

    ![alt text](/resources/k8s-screen-9.png)

#### Incident Monitoring 
1. At the Prisma Cloud Compute console, go to RADAR View by navigating to Radars > Containers, and clear all the filters.

2. Select the filter icon and select qa namespace checkbox to filter Pods only from QA namespace.

3. You can use your mouse to zoom in and out of the Radar graph view to view a container/pod closely.

    ![alt text](/resources/pcce-screen-29.png)

4. Find the ubuntu container and click the image to bring up details for the image.

    ![alt text](/resources/pcce-screen-30.png)
    ![alt text](/resources/pcce-screen-31.png)

5. Go to Monitor > Runtime > Incident Explorer

    ![alt text](/resources/pcce-screen-32.png)
    ![alt text](/resources/pcce-screen-33.png)

#### Forensics
1. From the Incident Explorer view on the Prisma Cloud Compute console, click View live forensic.

    ![alt text](/resources/pcce-screen-34.png)
    ![alt text](/resources/pcce-screen-35.png)

2. The Forensics view shows the events that were detected.

    ![alt text](/resources/pcce-screen-37.png)

3. Run the below command in Docker-Workstation VM to clean up containers from previous task to free up some resources:
```
docker stop registry
```

### Runtime Security II
Identify and prevent vulnerabilities across the entire application lifecycle while prioritizing risk for your cloud native environments. Integrate vulnerability management into any process, while continuously monitoring, identifying, and preventing risks to all the hosts, images, and functions in your environment. Prisma Cloud combines vulnerability detection with an always up-to-date threat feed and knowledge about your runtime deployments to prioritize risks specifically for your environment.

PCC features to be used:
* Vulnerability Management.
* Logging and reporting for verification
* WaaS

In this activity you will:
* Review Vulnerability Explorer
* Create image vulnerability rule
* Enforce security with vulnerability rule
* Run log4j attack
* Secure your environment from log4j attacks

#### Vulnerability Overview
![alt text](/resources/pcce-screen-38.png)
1. Navigate to PCCE Console > Monitor > Vulnerabilities. This gives an overview of Images, Hosts and Function vulnerabilities trend over the time

2. Scroll down to the Top critical vulnerabilities (CVEs) section to view the top 10 CVEs based on Risk Score. It may take a few moments for the vulnerabilities to become visible.

![alt text](/resources/pcce-screen-39.png)

3. The Risk Score takes into account the CVE’s severity, and other info such as is there a fix, is the container reachable from the Internet, etc.

4. This allows customer to prioritize which CVEs to fix first in their environment, among the hundreds of CVEs discovered

5. Go to PCCE Console > Monitor > Vulnerabilities > Images. 

    This gives an overview of the number of vulnerabilities found in each image, color coded Brown for Critical, Red for High severity, Orange for Medium severity, and Yellow for Low severity.

![alt text](/resources/pcce-screen-40.png)

6. Click on vulnerables/web-dvwa:latest image to open the details page. Note, there is a High vulnerability in the image.

7. Select the Layers tab. This shows the vulnerabilities found at each layer of the container image.

8. Click Close to close the Image details window.

#### Setup rule to detect log4j attacks
1. Head over the PCCE Console > Defend > WAAS > Container > In-line. Click on Add Rule . Use the name Log4j-WaaS-Inline

![alt text](/resources/pcce-screen-41.png)

2. Click in Scope field > Add Collection and set the following options:
    * Name: Log4j-Image-Collection
    * Images: us-central1-docker.pkg.dev/panw-utd-public-cloud/utd-public-images/utd-cnsp/log4j-victim:1.0
    * Click Save

    ![alt text](/resources/pcce-screen-42.png)
    * In this screen, select Log4j-Image-Collection checkbox and click Select Collections and then click save

    ![alt text](/resources/pcce-screen-43.png)

3. Expand the WaaS rule that we created in previous step and click on +Add App

    ![alt text](/resources/pcce-screen-44.png)

4. In the Create new WAAS app screen:
    * Scroll down and click on + Add endpoint and leave all the default options that are preselected

    ![alt text](/resources/pcce-screen-45.png)

    * Scroll further down and select create

    ![alt text](/resources/pcce-screen-47.png)

    * Scroll up and head over the Custom rule column in the same Create new WAAS app screen. Click on Select Rules

    ![alt text](/resources/pcce-screen-48.png)

    * In the Custom rules search bar, type in log4j and hit return. Select all the resulting items and click Apply. At the next screen, click Save.

    ![alt text](/resources/pcce-screen-49.png)

#### Run Log4j attack
1. Deploy the vulnerable log4j and the attacker applications within your Kubernetes setup (you can examine the code first if you’d like).
```
kubectl apply -f /home/sysadmin/apps/03-log4j.yaml
```

![alt text](/resources/k8s-screen-10.png)

2. Monitor the Pods and wait until they are fully Running:
```
kubectl get pods -w
```

Once they are running, you can press CTRL+C to exit out of the previous command and proceed with next steps

![alt text](/resources/k8s-screen-11.png)

3. As part of the log4j attack, a malware sample is downloaded to /tmp directory. Before we run the attack, let’s make sure there’s no malware (file named as malware-sample):
```
kubectl exec -it deploy/victim -- ls /tmp
```
![alt text](/resources/k8s-screen-12.png)

4. Run the attack and verify. You should see a string Hello World after the first command executes and a malware-sample downloaded after the second command executes.
```
kubectl exec -it deploy/att-svr -- bash /app/attack.sh
kubectl exec -it deploy/victim -- ls /tmp
```
![alt text](/resources/k8s-screen-13.png)

5. To see if the actual attack was detected, head over to Prisma Cloud Compute Console > Events > WAAS for Containers. Scroll down further to and click on the number corresponding to Custom Rule under Attack type

![alt text](/resources/k8s-screen-14.png)
![alt text](/resources/k8s-screen-15.png)

6. Examine the detected event. Scrolling down further to the forensic event, you can see that the attack was detected.

![alt text](/resources/k8s-screen-16.png)

7. Navigate to Prisma Cloud Compute Console > Monitor > WAAS and examine the WAAS dashboard. Scrolling down to the Event Traffic Sources, you can find the log4j attack event here

![alt text](/resources/k8s-screen-17.png)
![alt text](/resources/k8s-screen-18.png)

#### Block log4j attacks and images
Block Log4j attacks
1. Head over the PCCE Console > Defend > WAAS > Container > In-line. Expand the previously created rule "Log4j-WaaS-Inline".

![alt text](/resources/k8s-screen-19.png)

2. Under the App list, we had created an app previously. For that app, click on 3 dots under the Actions column and click edit.

![alt text](/resources/k8s-screen-20.png)

3. Head over to Custom rules and under user-selected custom rules, change the Alert setting to Prevent and click save

![alt text](/resources/pcce-screen-17.png)

Re-run Log4j attack
1. Navigate to Kubernetes VM and run the following command:
```
kubectl exec -it deploy/att-svr -- bash /app/attack.sh
```

2. This time, you will not see a Hello World! message

3. Run the below command in preparation for the next step:
```
kubectl delete -f /home/sysadmin/apps/03-log4j.yaml
```

Block Log4j Images:
1. Go to PCCE Console > Defend > Vulnerabilities > Images > Deployed
2. Click on +Add Rule to add a new rule called “Block Log4j vulnerability”
3. Go to Advanced settings and click on +Add exception with the following configurations:
    * CVE: CVE-2021-44228
    * Effect: Block
4. Click Add
5. Repeat steps 6 and 7 for the following 2 additional Log4j CVEs: CVE-2021-45046 and CVE-2021-4104 and click save.
![alt text](/resources/pcce-screen-50.png)

6. Run the following command to redeploy the log4j vulnerable application and this time, you will see that the Victim Pod will not get to the running state:
```
kubectl apply -f /home/sysadmin/apps/03-log4j.yaml
kubectl get po
kubectl describe po -l app=victim
```
![alt text](/resources/pcce-screen-51.png)
![alt text](/resources/pcce-screen-52.png)

Once you're done, you can move on to the next section [here](/05-Assignment-3-1.md)
