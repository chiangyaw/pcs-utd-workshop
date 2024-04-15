# Prisma Cloud Ultimate Test Drive (UTD) Workshop - Bonus
## Prisma Cloud Compliance Overview
The Compliance Overview is a dashboard that provides a snapshot of your overall compliance posture across various compliance standards.

Use the Compliance Dashboard as a tool for risk oversight across all the supported cloud platforms and gauge the effectiveness of the security processes and controls you have implemented to keep your enterprise secure. You can also create compliance reports and run them immediately, or schedule them on a recurring basis to measure your compliance over time.

The Compliance Dashboard supports you whether you’ve spent a lot of time designing and establishing internal regulations and devising the right policies, or you use the built-in regulatory compliance standards available on Prisma Cloud.

You can also find the list of compliance standards that Prisma Cloud supports [here](https://docs.prismacloud.io/en/classic/cspm-admin-guide/prisma-cloud-compliance/compliance-dashboard)

In this activity, you will:
* Review Compliance Overview in Prisma Cloud Enterprise Edition
* Schedule and generate compliance report for internal consumption

Note: This is a standalone activity and is not dependent on other activities.

### Compliance Overview
1. Go to Prisma Cloud Enterprise > Cloud Security > Compliance
2. Here you can see a list of compliance standards supported by Prisma Cloud out of the box:
    
    ![alt text](/resources/pcs-screen-103.png)

3. Type "NIST" in the search bar on top right corner to filter the compliance standards. Click on "NIST SP 800-171 Revision 2".

    ![alt text](/resources/pcs-screen-104.png)

4. On the next page, you can see how the compliance standard is being structured. This is based on the actual compliance requirement, and Prisma Cloud maps the policies according to each section of the compliance requirement. Click on "CONFIGURATION MANAGEMENT".

    ![alt text](/resources/pcs-screen-105.png)

5. On the next page, you can also see how policies are mapped to each sub-section of the compliance standard. Click on the numbers under Policies Assigned, same row as section 3.4.2.

    ![alt text](/resources/pcs-screen-106.png)

6. On the next page, you will be able to see all the policies that are mapped to this particular sub-section. This allows user to understand how all the policies are built into the compliance requirement and how Prisma Cloud is able to assist organizations on their compliance towards a certain standards or regulatory requirement.

    ![alt text](/resources/pcs-screen-107.png)

### Download Compliance Report
    
Note: The lab uses a read-only user, which doesn’t have access to generate a compliance report. Therefore, we'll only run through the steps to download a compliance report.

1. Go to Prisma Cloud Enterprise > Cloud Security > Reports
2. On this page, you will see all the different reports created by existing users or yourself, either for one time usage or regular schedule.

    ![alt text](/resources/pcs-screen-108.png)

3. On the search bar, type "NIST". Click on the Download icon in the Action column to download the report.

    ![alt text](resources/pcs-screen-111.png)

    Note: As you're accessing Prisma Cloud via a full screen remote desktop, you're might not be able to view the downloaded document. For a sample NIST report, you can refer to a sample document [here](/resources/NIST_SAMPLE_REPORT.pdf).

    Note: You can schedule a compliance report to be sent to specific team or team members in a regular basis (weekly, daily, etc).

