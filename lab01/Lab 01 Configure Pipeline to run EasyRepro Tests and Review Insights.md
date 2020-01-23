# Lab 01: Configure Pipeline to run EasyRepro Tests and Review Insights

Goal:

The goal of this lab will show the following:

1. Configure Variables to push data to App Insights
2. Configure VS Test Task to use Test Categories
3. Review data in Application Insights
4. Create a Azure Monitor Log Alert Rule based on App Insights data



## Labs

Lab 01 - Create an Azure DevOps Build Pipeline 

### Locate Variables for use

### Configure Variables to use Instrumentation Key

### Configure VS Test Task to use Test Categories

### Run Pipeline

Lab 02: Explore insights and Create Alerts

### Review Data in Application Insights

### Create Azure Monitor Log Alert



## Create an Azure DevOps Build Pipeline

#### Objectives

In this lab, you will:

Work with Azure DevOps Build Pipelines.

Examine how to enable automatic work item creation.

Work with Pipeline templates

Configure Visual Studio Test Task

#### Prerequisites

Azure DevOps

#### Estimated Time to Complete This Lab

30 minutes

#### Scenario

In this exercise, you will go understanding how to create an Azure DevOps Build Pipeline to run EasyRepro unit tests.

#### Navigate to Azure Application Insights

1. Open a web browser and navigate to portal.azure.com.

2. Locate the Resource Group "**Ready2020-BAST306T**".

     ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/Azure-ResourceGroup-Items.JPG)

3. Locate the Application Insights resource called "**BAST306T**".

     ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/AppInsights-LogoAndName.JPG)

4. Open the resource.

5. Locate the Instrumentation Key in the upper right hand corner of the main pane.

     ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/AppInsights-InstrumentationKey.JPG)

6. Store this value for later use.

#### Navigate to Azure Project Repository.

1. First, navigate to dev.azure.com and find your project.      

   <img src="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Project.JPG"       alt="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/blob/master/lab01/images/ADO-BAST306T-Build-NewPipelineButton.JPG"     style="zoom:50%;" />

2. Click Repositories or **Repos**.

 

   <img src="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Repo.JPG" alt="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/blob/master/lab01/images/ADO-BAST306T-Repo.JPG" style="zoom:50%;" />

3. This is where you code resides. For this Exercise we are working with this code but will focus on another area of DevOps: Pipelines.

#### Task 2: Create Build Pipeline using Visual Designer

4. Click on Pipelines:

   <img src="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build.JPG" style="zoom:50%;" />

5. Since we have a new project we should not be seeing any pipelines yet. Confirm you see this and click **New Pipeline**:

   <img src="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build-NewPipelineButton.JPG" style="zoom:50%;" />

6. Here we will be using the Classic Editor or Visual Designer. It is worthwhile to note the use of YAML here. YAML allows us the ability to automate and scale our pipelines using a specialized format. Click on Use Classic Editor.

7. Select which source you want to base your build pipeline off of. For this workshop we are using Git:

   <img src="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build-Classic-ChooseSource.JPG" style="zoom:50%;" />

8. Choose your workspace, project and branch:

   <img src="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build-Classic-ChooseSourceBranch.JPG" style="zoom:50%;" />

9. The branch here is key as this is where we will be committing our code which will fire off the Build Pipeline. Click **Continue**.

10. Now we are presented with a list of templates we can leverage. Alternatively we can build our own step by step. In this case we will leverage the .NET Desktop Application template. Select it and click Apply.

   <img src="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build-Classic-ChooseDotNetAppTemplate.JPG" style="zoom:50%;" />

11. First thing we will do here is configure which Agent Pool we want to use. Think of an Agent Pool as a container or virtual environment running your application. Select **VS 2019:**

12. Now we will rename the Build Pipeline. Let’s use “**Lab 01 - Run Test and Examine Results**”.

#### Configure Pipeline to create and link work items

13. Navigate to the left of the main pane and confirm you see the tab ‘**Options**’:

    ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build-Classic-Options-Tab.JPG)

14. Toggle the "Automatically link work items in this build" to enabled.

    ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build-Classic-Options-AutoLinkNewWorkItems.JPG)

15. Scroll down until you see the "**Create work items on failure**" toggle and enable.

16. Set the type of work item to "**Issue**"

    <img src="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build-Classic-Options-CreateWorkItemOnFailure.JPG" style="zoom:80%;" />

#### Configure Pipeline Variables

17. Navigate to the Variables tab.

    ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build-Classic-Variables-Tab.JPG)

18. Here we will define four variables that will allow us to connect to a Dynamics 365 instance and send data to Application Insights. Confirm your variables look something like this:

    <img src="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build-Classic-Variables-DefaultVariables.JPG" style="zoom:50%;" />

19. Now add the following variables:

    | Variable Name      | Variable Value                       |
    | ------------------ | ------------------------------------ |
    | OnlineUsername     | user@readydemo.onmicrosoft.com       |
    | OnlinePassword     | password for user                    |
    | OnlineOrg          | https://<readydemo>.crm.dynamics.com |
    | InstrumentationKey | your application insights key        |

    You should see something like this with values:

    <img src="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build-Classic-Variables-ModifiedVariables.JPG" style="zoom:50%;" />

#### Configure Pipeline Tasks to Build and Run Unit Tests

20. Begin by navigating to the Tasks tab:

      ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build-Classic-Tasks-Tab.JPG)

21. Navigate to the VS Test Task:

22. Locate the TestSettings input textbox. Here we will override default connection parameters with our pipeline variables we just created. Click the ellipsis.

      <img src="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build-Classic-Tasks-VSTest-TestSettingsDefault.JPG" style="zoom:50%;" />

23. Map to the settings file located in our EasyRepro Source repository.

24. Verify the settings input textbox looks like this:

25. Navigate to the Test Case Filter input textbox and input the following:

    ```
    TestCaseFilter:"FullyQualifiedName=Microsoft.Dynamics365.UIAutomation.Sample.Web.WorkshopUnitTests"
    ```

26.  Choose the Save and Queue picklist and choose **Save**.

27.  Leave the pipeline in the default folder and select Save.

28. Navigate to Builds and confirm you see your pipeline:

​      ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build-Queue-Lab01.JPG)

 
