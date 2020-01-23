# Lab 03: Schedule a Repeatable Test Pipeline

## Goal

The goal of this lab will show the following:

1. Use Triggers in Azure DevOps Pipelines to schedule UI tests

## Schedule a Test Pipeline

#### Objectives

In this lab, you will:

  Configure Azure DevOps Pipelines

  Automate testing with EasyRepro

#### Prerequisites

  Azure DevOps

  EasyRepro

#### Estimated Time to Complete This Lab

  10 minutes

#### Scenario

In this exercise, you will go understanding how to modify an existing Pipeline to run on a schedule.

#### Navigate to Azure Project Repository.

1. First, navigate to dev.azure.com and find your project.      

     <img src="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Project.JPG" alt="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/blob/master/lab01/images/ADO-BAST306T-Build-NewPipelineButton.JPG" style="zoom:50%;" />

2. Click Repositories or **Repos**.

 

     <img src="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Repo.JPG" alt="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/blob/master/lab01/images/ADO-BAST306T-Repo.JPG" style="zoom:50%;" />

3. This is where you code resides. For this Exercise we are working with this code but will focus on another area of DevOps: Pipelines.

#### Configure Existing Build Pipeline Trigger

4. Click on Pipelines:

     <img src="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build.JPG" style="zoom:50%;" />

5. Locate the pipeline from the first lab. It should be titled "Lab 01 - Run Tests and Examine Results"

     ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab03/images/ADO-Build-LocatePipeline.JPG)

6. Edit the Pipeline. The button should be located in the upper right hand corner.

     ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab03/images/ADO-BAST306T-Build-Queue-Lab01.JPG)

7. Click on the "Triggers" tab. This tab should be around the central area of the screen.

     ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab03/images/ADO-Build-Triggers-Tab.JPG)

8. Click the "+ Add" button in the Scheduled area.

     ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab03/images/ADO-Build-Triggers-Schedule-Add.JPG)

9. Review the default for scheduling pipelines. Here you should see days of the weeks and times that can be localized to your time zone. You will also see a checkbox for scheduling only if the source code has changed. Finally, a filter below allows for specifying which source to use.

     ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab03/images/ADO-Build-Triggers-Schedule-Default.JPG)

10. Using the same "+ Add" button you can add as many scheduled triggers as needed. Here is an example of scheduling the pipeline to run at midnight, 08:00am, noon, and 05:00pm:

     ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab03/images/ADO-Build-Triggers-Schedule-Customized.JPG)

## Conclusion and Next Steps

After this lab you should be able to take UI or any unit tests and schedule pipelines. This is useful to monitor how Dynamics is performing throughout the day. This technique can also be used to schedule gathering of telemetry.
