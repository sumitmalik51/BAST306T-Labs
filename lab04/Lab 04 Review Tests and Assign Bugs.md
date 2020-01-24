# Lab 04: Review Tests and Assign Bugs

## Goal

The goal of this lab will show the following:

* Review Previous Failed Pipeline runs
* Located failed tests
* Create a new bug from a failed test
* Associate to a User Story work item

## Schedule a Test Pipeline

#### Objectives

In this lab, you will:

 * Examine test outcomes
 * Create work items from outcomes

#### Prerequisites

 * Azure DevOps


#### Estimated Time to Complete This Lab

 * 10 minutes

#### Scenario

In this exercise, you will go understanding how to examine test outcomes. The results of the unit tests are stored with the build pipeline build along with the logs and artifacts. The retention of these results are configurable within the Azure DevOps project settings. Each build can be reviewed at a high level for various test result statuses.

#### **Navigate to Azure Project Repository.**

1. First, navigate to dev.azure.com and find your project.      

    <img src="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Project.JPG" alt="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/blob/master/lab01/images/ADO-BAST306T-Build-NewPipelineButton.JPG" style="zoom:50%;" />

1. Click Repositories or **Repos**.

   <img src="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Repo.JPG" alt="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/blob/master/lab01/images/ADO-BAST306T-Repo.JPG" style="zoom:50%;" />

1. This is where you code resides. For this Exercise we are working with this code but will focus on another area of DevOps: Pipelines.

#### Review Failed Build Pipeline

1. Click on Pipelines:

     <img src="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build.JPG" style="zoom:50%;" />

1. Locate the pipeline from the first lab. It should be titled "Lab 01 - Run Tests and Examine Results"

     ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab03/images/ADO-Build-LocatePipeline.JPG)

1. Hopefully, this pipeline shows a red X icon. This means the last run failed. We are going to explore why the pipeline run failed and take action.

1. Begin by clicking in the pipeline.

1. Next, locate the top record if there are multiple runs for the pipeline. 

     ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab04/images/ADO-Build-Failed-Overview.JPG)

     To drill down into this particular run we need to click on the record.

     Before moving on, I want to point out the different tabs you see at the top, specifically the Analytics tab. This tab is useful to understand trends in our pipeline which can help us continuously check for quality. In a live project you should expect this to come in handy to help identify where items tied to new features or possible regressions have impacted the application. In this lab we won't much to look at but when you work with pipelines in the future keep this tab in mind!

     

1. Click on the Individual run and confirm you see the build summary, tests and code coverage tabs.

     ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab04/images/ADO-Build-Failed-Run-OverviewTab.JPG)

1. The summary is useful for us to understand where the build pipeline failed. In some cases it may have failed in other places then where we expect, for instance it didn't build correctly or couldn't fetch the code to build. If everything works as expected we should see an error message similar to "*Test Run Failed.*"

     ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab04/images/ADO-Build-Failed-Run-SummaryTab-TestRunFailed.JPG)

1. Click on the Tests tab at the top of the page.

     ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab04/images/ADO-Build-Failed-Run-TestsTab.JPG)

1. Confirm you see at least one failed test. Normally you would hope for all green but for this lab we are expecting a failed test so we can document and provide work item feedback.

1. Near the middle of the page you should see tests that have failed. These will have red x next to them and may look like the following:

     ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab04/images/ADO-Build-Failed-Run-TestsTab-FailedTests.JPG)

1. Highlight  a single failed test.

      ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab04/images/ADO-Build-Failed-Run-TestsTab-FailedTests.JPG)

1. Click on the "**Bug v**" button.

      ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab04/images/ADO-Build-Failed-Run-TestsTab-FailedTests-BugDropdown.JPG)

1. Click **Create Bug**.

1. You'll be shown a modal which contains the new bug work item. Take a moment to check out the exception message, stack trace, linked build, etc.

      

      ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab04/images/ADO-Build-Failed-Run-TestsTab-FailedTests-Bug-Overview.JPG)

1. Here we will want to add a link to an existing work item "Test Case".

1. Click on "**+ Add link**" in the related work section located in the far right of the bug form.

      ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab04/images/ADO-Build-Failed-Run-TestsTab-FailedTests-Bug-LinkWorkItemButton.JPG)

      

1. Select **Existing Item**

      ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab04/images/ADO-Build-Failed-Run-TestsTab-FailedTests-Bug-LinkWorkItemButton-Existing.JPG)

1. Choose ID **316**. You should see the work item pull up.

      ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab04/images/ADO-Build-Failed-Run-TestsTab-FailedTests-Bug-LinkTestCase.JPG)

1. Click **Ok** to link the work item.

1. Click **Save and Close** to create the new bug.

## **Conclusion and Next Steps**

Once everything has been completed, feel free to run the pipeline again. You should see that the failed test is now linked to the existing bug and existing test case. You can now choose to add the existing build by choosing to add to linked bug instead of the create new bug from Step 12.

After this lab you should be able to take any failed tests and create work items as shown in Lab 01. If tests are involved and some have failed we have worked through how to locate the failed tests and create bugs manually. The logical next step here is to automate the creation of the bug and have it assigned to a work item. I'd suggest reviewing the service hooks and Power Automate for a no/low code approach. Unfortunately this is out of scope of this lab but I will provide supplemental material to show how this can be done.