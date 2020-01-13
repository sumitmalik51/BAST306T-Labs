# Lab 01: Configure Pipeline to run EasyRepro Tests and Review Insights

Goal:

The goal of this lab will show the following:

1. Configure Variables to push data to App Insights
2. Configure VS Test Task to use Test Cateogires
3. Review data in Application Insights
4. Create a Azure Monitor Log Alert Rule based on App Insights data



## Steps

### Import existing YAML pipeline schema

1. Begin by navigating to the 

### Locate Application Insights Instrumentation Key

### Configure Variables to use Instrumentation Key

### Configure VS Test Task to use Test Categories

TestCategory=BuildTest

### Run Pipeline

### Review Data in Application Insights

### Create Azure Monitor Log Alert



## Exercise 1: Create an Azure DevOps Build Pipeline with Continuous Integration

#### Objectives

In this exercise, you will:

·    Work with Azure DevOps Build Pipelines.

·    Examine how to enable Continuous Integration.

·    Work with Pipeline templates.

#### Prerequisites

Azure DevOps

EasyRepro

#### Estimated Time to Complete This Lab

30 minutes

#### Scenario

In this exercise, you will go understanding how to create an Azure DevOps Build Pipeline with Continuous Integration.

Task 1: Navigate to Azure Project Repository.

\1.   First, navigate to dev.azure.com and find your project.

​                                

 

 BAST306T-Labs/blob/master/lab01/images/ADO-BAST306T-Build-NewPipelineButton.JPG

 

 

 

 ![https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/blob/master/lab01/images/ADO-BAST306T-Build-NewPipelineButton.JPG]()



\2.     Click Repositories or **Repos**.

 

 

 

 

 

 

 

 

\3.   This is where you code resides. For this Exercise we are working with this code but will focus on another area of DevOps: Pipelines.

Task 2: Create Build Pipeline using Visual Designer

\4.     Click on Pipelines:

 

 

 

 

 

 

 

\5.   Since we have a new project we should not be seeing any pipelines yet. Confirm you see this and click **New Pipeline**:

  

 

 

 

 

 

 

 



\6.   Here we will be using the Classic Editor or Visual Designer. It is worthwhile to note the use of YAML here. YAML allows us the ability to automate and scale our pipelines using a specialized format.

 

 

 

 

 

 

 

  

 

 

 

 

 

 

 

 

 



\7.     Select which source you want to base your build pipeline off of. For this workshop we are using Git:

 

 

 

 

 

 

 

\8.   Choose your workspace, project and branch:

  

 

 

 

 

 

 

 

 



\9.   The branch here is key as this is where we will be committing our code which will fire off the Build Pipeline. Click **Continue**.

\10. Now we are presented with a list of templates we can leverage. Alternativelly we can build our own step by step. In this case we will leverage the .NET Desktop Application template. Select it and click Apply.

  

 

 

 

 

 

 

 

 



\11.   First thing we will do here is configure which Agent Pool we want to use. Think of an Agent Pool as a container or virtual environment running your application. Select **VS 2019:**

 

 

 

 

 

 

 

 

 

 

 

\12. Now we will rename the Build Pipeline. Let’s use “**EasyRepro Workshop - Build**”.

\13. Navigate to the left of the main pane and confirm you see the tab ‘**Triggers**’:

  

 

 

 



\14. Check the Enable Continuous Integration checkbox. This will kick off this pipeline once we commit changes to our branch in Visual Studio.

  

 

 

 

 

 

 

 



\15. Now we will modify the Test Assemblies step to filter to only our **WorkshopUnitTests** class. Click on Test Assemblies:

  

 

 

 

 

 

 



\16. On the right locate the Test Case Filter textbox and input the following:

  

 

 

 

 

 



TestCaseFilter:"FullyQualifiedName=Microsoft.Dynamics365.UIAutomation.Sample.Web.WorkshopUnitTests"

 

 

 

 

\17. Choose the Save and Queue picklist and choose **Save**.

  

 

 

 

 

 



\18. Leave the pipeline in the default folder and select Save.

  

 

 

 

 

 

 



\19. Navigate to Builds and confirm you see your pipeline:

​    

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 



\1.   Notice how the constructor includes three key properties: the instrumentation key, an execution id and a requested.



| Parameter Name | Value                                                        |
| -------------- | ------------------------------------------------------------ |
| key            | The Application  Insights Instrumentation Key                |
| executionId    | An optional Guid or  string you can use to track or relate events in Application Insights |
| requestId      | An optional GUID  that would come from a Dynamics web request. |

 

\2.   Open the **TrackException** method and review how it works. Specifically review this line:

 

  



This line sends exceptions to Application Insights as opposed to the other methods which send to the custom events table. This is a key point of the workshop, where you store messages ultimately decides how you can monitor your application.

 

 

 

## Exercise 2: Commit EasyRepro changes to Git

#### Objectives

In this exercise, you will:

\1.    Navigate to local EasyRepro solution.

\2.    Open the solution.

\3.    Commit and Sync changes to Git

#### Prerequisites

Visual Studio 2019 or equivalent 

EasyRepro source code including sample unit tests downloaded

**Module 1: EasyRepro and Application Insights**

Azure DevOps Git based project

#### Estimated Time to Complete This Lab

15 minutes

#### Scenario

In this exercise, you will go through the process of locating the Telemetry class which is used to send events to Application Insights from EasyRepro

Task 1: Navigate to local EasyRepro solution

\3.   Start Visual Studio.

\4.   Once the splash screen loads, look to the left for the Open Recent list. Hopefully your solution or folder where you downloaded EasyRepro from the previous lab is shown here. If so and you see the solution choose the solution (.sln) file.

 

If you do not see the solution in the Open Recent list, optionally you can navigate to the solution in your file system.

 

\5.   Look for the **UIAutomation.sln** and open.

  

 

 

 

 

 

 

 

 

 

 



Once complete you should see a view similar to this:

  

 

 

 

 



Task 2: Commit and Sync changes to Git

\6.   Navigate to the **Microsoft.Dynamics365.UIAutomation.Sample** project.

\7.   Expand the project and confirm you see changes. Look for items like plus signs and checkmarks.

 

 

 

 

\8.   Right click on the project Microsoft.Dynamics365.UIAutomation.Sample and choose **Source Control** and **Commit**.

Right Click:

  

 

 

 

 

 

 

 

 

 

 

 



  Source Control:

 

 

 

 

 

 



 

## Lab Exercise Recap

You have now completed all the exercises in the lab for Module 1, “EasyRepro and Application Insights” You practiced:

·    Modifying a publisher.

·    Creating a new solution.

·    Adding solution components.

You have completed adding telemetry to a unit tests which cab used for analysis and monitoring by developers and administrators.