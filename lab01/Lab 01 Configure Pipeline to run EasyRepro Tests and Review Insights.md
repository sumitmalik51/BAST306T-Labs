# Lab 01: Configure Pipeline to run EasyRepro Tests and Review Insights

## Goal

The goal of this lab will show the following:

1. Configure Variables to push data to App Insights
2. Configure VS Test Task to use Test Categories

## Create an Azure DevOps Build Pipeline

#### Objectives

In this lab, you will:

* Work with Azure DevOps Build Pipelines.

* Examine how to enable automatic work item creation.

* Work with Pipeline templates

* Configure Visual Studio Test Task

#### Prerequisites

* Azure DevOps

### Estimated Time to Complete This Lab

* 30 minutes

### Scenario

In this exercise, you will go understanding how to create an Azure DevOps Build Pipeline to run EasyRepro unit tests.

### **Navigate to Azure Application Insights**

1. Open a web browser and navigate to portal.azure.com.

2. If prompted to login, use the provided credentials from the lab site.

     ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Azure-Login.JPG)

3. Click on **Resource Groups**:

     ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Azure-Locate-ResourceGroup.JPG)

4. Locate the Resource Group "**Ready2020-BAST306T**" and click to open.

     *It may not look exactly like the image below*.

     ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/Azure-ResourceGroup-Items.JPG)

5. Locate the Application Insights resource called "**BAST306T**".

     ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/AppInsights-LogoAndName.JPG)

6. Open the resource.

7. Locate the Instrumentation Key in the upper right hand corner of the main pane.

     ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/AppInsights-InstrumentationKey.JPG)

8. Store this value for later use.

### **Navigate to Azure Project Repository.**

1. First, navigate to dev.azure.com and find your project.      

   <img src="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Project.JPG"       alt="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/blob/master/lab01/images/ADO-BAST306T-Build-NewPipelineButton.JPG"     style="zoom:50%;" />

2. Click Repositories or **Repos**.

   <img src="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Repo.JPG" alt="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/blob/master/lab01/images/ADO-BAST306T-Repo.JPG" style="zoom:50%;" />

3. This is where you code resides. For this Exercise we are working with this code but will focus on another area of DevOps: Pipelines.

### **Task 2: Create Build Pipeline using Visual Designer.**

1. Click on Pipelines:

   <img src="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build.JPG" style="zoom:50%;" />

1. Since we have a new project we should not be seeing any pipelines yet. Confirm you see this and click **New Pipeline** or **Create Pipeline**:

   <img src="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build-NewPipelineButton.JPG" style="zoom:50%;" />

1. Here we will be using the Classic Editor or Visual Designer. It is worthwhile to note the use of YAML here. YAML allows us the ability to automate and scale our pipelines using a specialized format. **Click on Use Classic Editor.** Its near the bottom and can be overlooked so take time to ensure you choose this option.

   ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build-Classic-UseClassicEditor.JPG)

1. Select which source you want to base your build pipeline off of. For this workshop we are using Git:

   <img src="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build-Classic-ChooseSource.JPG" style="zoom:50%;" />

1. Choose your workspace, project and branch:

   <img src="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build-Classic-ChooseSourceBranch.JPG" style="zoom:50%;" />

1. The branch here is key as this is where we will be committing our code which will fire off the Build Pipeline. Click **Continue**.

1. Now we are presented with a list of templates we can leverage. Alternatively we can build our own step by step. In this case we will leverage the .NET Desktop Application template. Select it and click **Apply**.

   <img src="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build-Classic-ChooseDotNetAppTemplate.JPG" style="zoom:50%;" />

1. First thing we will do here is configure which Agent Pool we want to use. Think of an Agent Pool as a container or virtual environment running your application. Locate the "Agent Specification" drop down. Select **Windows-2019:**

   Default:

   <img src="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build-Classic-Pipeline-AgentDefault.JPG" style="zoom:50%;" />

   Modified with "**windows-2019**":

   <img src="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build-Classic-Pipeline-AgentVS2019.JPG" style="zoom:50%;" />

1. Now we will rename the Build Pipeline. The default name may look something like below with the name of the project and the template we used. Let's rename this to something more relevant. Let’s use “**Lab 01 - Run Test and Examine Results**”.

   Default:

   <img src="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build-Classic-Pipeline-Rename.JPG" style="zoom:50%;" />

### **Configure Pipeline to create and link work items.**

1. Navigate to the left of the main pane and confirm you see the tab ‘**Options**’:

    ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build-Classic-Options-Tab.JPG)

1. Toggle the "Automatically link work items in this build" to enabled.

    ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build-Classic-Options-AutoLinkNewWorkItems.JPG)

1. Scroll down until you see the "**Create work items on failure**" toggle and enable.

1. Set the type of work item to "**Issue**"

    <img src="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build-Classic-Options-CreateWorkItemOnFailure.JPG" style="zoom:80%;" />

### **Configure Pipeline Variables.**

1. Navigate to the Variables tab.

    ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build-Classic-Variables-Tab.JPG)

1. Here we will define four variables that will allow us to connect to a Dynamics 365 instance and send data to Application Insights. Confirm your variables look something like this:

    <img src="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build-Classic-Variables-DefaultVariables.JPG" style="zoom:50%;" />

1. Now add the following variables using the "**+ Add**" button underneath the predefined variables:

    | Variable Name      | Variable Value                       |
    | ------------------ | ------------------------------------ |
    | OnlineUsername     | user@readydemo.onmicrosoft.com       |
    | OnlinePassword     | password for user                    |
    | OnlineOrg          | https://<readydemo>.crm.dynamics.com |
    | InstrumentationKey | your application insights key        |
    | BrowserType        | Chrome                               |
    

Variable Name - Variable Value

OnlineUsername - user@ondemandlabuser.onmicrosoft.com

OnlinePassword - [**password for ondemandlabuser**]

The **OnlineUsername** and **OnlinePassword** come from the lab instructions when you launched the lab. This should correlate to the login you used for the virtual environment.

![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build-Classic-Variables-Dynamics-SkeptraLab.jpg)

OnlineOrg - 

The OnlineOrg variable comes from the trial of Dynamics 365 that is available in the VM.

To get to the correct Dynamics 365 org follow these steps:

 1. Open a browser in the VM

 2. Navigate to "https://admin.powerplatform.microsoft.com"

    ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/D365-BAST306T-HomeDynamicsPage.JPG)

 3. You may or may not get prompted to fill in your credentials. If so, these will be the same username and password used for the **OnlineUsername** and **OnlinePassword** variables.

    OnlineUsername - user@ondemandlabuser.onmicrosoft.com

    OnlinePassword - [**password for ondemandlabuser**]

 4. Click **Sign In**.

 5. In the left navigation window, you will notice options to work within the Power Platform Admin Center. For this exercise we are going to open an environment. Begin by clicking on the **Environments** option.

    

 6. Locate the environments in the Power Platform Admin Center. You may notice one or two with the same name. To determine which one we will need for our tests we need to open the one labeled "**Production**"

    ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/D365-BAST306T-PPAC-DynamicsInstances.jpg)

 7. You will see an ellipsis "..." near the word "Production". Click the ellipsis.

    ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/D365-BAST306T-PPAC-OpenEnv.jpg)

 8. A picklist will appear with an option to "**Open environment**". **Click** this option. 

 9. **Wait** for Dynamics 365 to render.

    ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/D365-BAST306T-Accounts.JPG)

 10. Click on **Accounts**.

    ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/D365-BAST306T-Accounts.JPG)

 11. Verify you see records in the middle window or view.

     ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/D365-BAST306T-Accounts-ActiveAccountsView.JPG)

 12. If not, go back to step 6 and try the other org labeled "**Sandbox**" and steps 6-8.

 13. Locate the URL at the top of the browser window and grab the portion that looks like this. https://<CrmOrg>.crm.dynamics.com/main.aspx

     ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/D365-BAST306T-OrgUrl.JPG)

InstrumentationKey - [**your application insights key** **from step 6** **at the beginning of the lab**]

<img src="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/AppInsights-InstrumentationKey.JPG" style="zoom:150%;" />

BrowserType - Chrome

You should see something like this with the values you entered:
    ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build-Classic-Variables-ModifiedVariables.JPG)

Next to **OnlinePassword** where you input the value, you should see a <u>lock symbol</u>. **Click** this symbol so it shows that the variable is locked.

![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build-Classic-Variables-ModifiedVariables-LockedPassword.JPG)

#### Configure Pipeline Tasks to Build and Run Unit Tests.**

1. Begin by navigating to the **Tasks** tab:

      ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build-Classic-Tasks-Tab.JPG)

1. Navigate to the **VS Test Task**. This should look like the image below and maybe called VsTest - testAssemblies by default:

    <img src="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build-Classic-Tasks-VSTest-AgentImage.JPG" style="zoom:50%;" />

1. Locate the Test files input box. You should see something that references the BuildConfiguration pipeline variable and the word test. This is a wildcard string looking for any test assemblies that include the name test. Our assembly is called "Microsoft.Dynamics365.UIAutomation.BAST306T" so we want to change the test string to say **BAST306T**:

      Modified:

      <img src="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build-Classic-Tasks-VSTest-TestFiles-BAST306T.JPG" style="zoom:50%;" />

1. Locate the **TestSettings** input textbox. Here we will override default connection parameters with our pipeline variables we just   created. Click the **ellipsis**.

      <img src="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build-Classic-Tasks-VSTest-TestSettingsDefault.JPG" style="zoom:50%;" />

1. Map to the **settings** file located in our EasyRepro Source repository.

    Default Window:

    <img src="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build-Classic-Tasks-VSTest-SettingsWindow-Default.JPG" style="zoom:50%;" />

    **EasyRepro.runsettings** located in Window:

    <img src="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build-Classic-Tasks-VSTest-SettingsWindow-EasyReproRunSettings.JPG" style="zoom:50%;" />

    

1. Verify the settings input textbox looks like this:

    <img src="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build-Classic-Tasks-VSTest-TestSettingsModified.JPG" style="zoom:50%;" />

1. Navigate to the **Override test run parameters** input. Input the following:

    ```
    -OnlineUsername $(OnlineUsername) -OnlinePassword $(OnlinePassword) -OnlineCrmUrl $(OnlineOrg) -AzureKey $(InstrumentationKey) -BrowserType $(BrowserType)
    ```

    This is used to overwrite the runsettings file parameters with our variables we defined. This allows us to do a couple of things:

    1. Not store out credentials in source

    2. Provide dynamic credentials when we run a build. This means we can share this pipeline with multiple test users!

       <img src="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build-Classic-Tasks-VSTest-OverrideTestRunParams-Modified.JPG" style="zoom:50%;" />

1. Navigate to the **Test Filter Criteria** input textbox and input the following:

    ```
    FullyQualifiedName~Microsoft.Dynamics365.UIAutomation.BAST306T.BAST306_Labs
    ```

    Before we move on, I want to point out what this means. What we are doing here is telling our testing tool that we only want to run tests that are contained in what's called a class. A class or test class, is a way for us to logically group tests that may be related e.g. *Creating accounts, opening leads*. 

    The **FullyQualifiedName** filter allows us to point to a specific class (or other items like individual tests, namespaces, etc). For this Pipeline we are telling the tooling to look in the **Microsoft.Dynamics365.UIAutomation.BAST306T** namespace for the **BAST306_Labs** class.

    <img src="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build-Classic-Tasks-VSTest-TestFilterCriteria-EasyReproClass.JPG" style="zoom:50%;" />

    Once you have added to the Test Filter Criteria, field it should look like this:

    <img src="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build-Classic-Tasks-VSTest-TestFilterCriteria-Modified-BAST306_Labs.JPG" style="zoom:50%;" />

1. Choose the Save and Queue picklist and choose **Save**.

    <img src="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build-Classic-Pipeline-SaveAndQueuePicklist.JPG" style="zoom:50%;" />

1. Leave the pipeline in the default folder and select **Save**.

    <img src="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build-Classic-Pipeline-SaveBuildPipeline.JPG" style="zoom:50%;" />

1. Navigate to **Pipelines** on the left navigation and confirm you see your pipeline:

​      <img src="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build-Pipeline-Run-ViewPipeline.JPG" style="zoom:50%;" />

10. Click the **Run Pipeline** button.

    <img src="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build-Pipeline-Run-RunPipeline.JPG" style="zoom:50%;" />

11. Confirm you see the Run Pipeline screen. This screen is useful for providing runtime variables. Example of this would be adding user story identifiers, login credentials, etc.

    <img src="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build-Pipeline-Run-RunPipelineWindow.JPG" style="zoom:50%;" />

12. Click the **Run** button.

    <img src="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build-Pipeline-Run-RunPipelineWindow-RunButton.JPG" style="zoom:50%;" />

13. Confirm the Agent is queued or running.

    <img src="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/ADO-BAST306T-Build-Pipeline-Queue-JobStatus.JPG" style="zoom:50%;" />

14. Now click into the Agent job 1 and you can see the pipeline in action.




## **Conclusion and Next Steps**

At this point you have now configured a Azure DevOps (ADO) Pipeline to build and run a Unit Test project. The Unit Tests performed multiple actions in a Power Apps environment and uploaded telemetry to Application Insights. 

Throughout this lesson you learned how to work with variables and test criteria. Variables allow for reuse and scalability of pipelines allowing them to be cloned as templates or run with dynamic values.

You also reviewed the Test Filter Criteria and how to run tests within a class. There are multiple ways to filter tests including Test Categories and Priorities, ways to run tests in multiple test assemblies and with dynamic run setting files.

Now that these tests have run using the native ADO task, we have the ability to explore tests and tie failed tests to bugs and provide feedback to the development and support teams.

In the following labs we will explore how to review telemetry delivered from tests and take action, increasing productivity and allowing us to focus on tackling the issue at hand in a more proactive manner.
