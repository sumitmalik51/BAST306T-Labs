# Lab 01: Explore insights and Create Alerts

Goal:

The goal of this lab will show the following:

3. Review data in Application Insights
4. Create a Azure Monitor Log Alert Rule based on App Insights data



## Labs

Lab 02: Explore insights and Create Alerts

### Review Data in Application Insights

### Create Azure Monitor Log Alert



## Review and Take Action on Insights

#### Objectives

In this lab, you will:

Work with Application Insights Kusto Queries.

Examine how to create an Azure Monitor Log Alert.



#### Prerequisites

Azure DevOps

Azure

#### Estimated Time to Complete This Lab

30 minutes

#### Scenario

In this exercise, you will go understanding how to create an Azure DevOps Build Pipeline to run EasyRepro unit tests.

#### Navigate to Azure Application Insights Analytics

1. Open a web browser and navigate to portal.azure.com.

2. Locate the Resource Group "**Ready2020-BAST306T**".

   ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/Azure-ResourceGroup-Items.JPG)

3. Locate the Application Insights resource called "**BAST306T**".

   ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/AppInsights-LogoAndName.JPG)

4. Open the resource.

5. Click on the Log Analytics button.

   ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab02/images/AppInsights-AnalyticsButton.JPG)

   #### Run Exceptions Query and Create Log Alert

6. Begin by inputting the following query in the Query Editor pane in the middle of the Analytics screen.

   ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab02/images/AppInsights-Analytics-ExceptionsQuery.JPG)

7. Confirm you see results in the results pane.

8. Click the Log Alert button.

   ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab02/images/AppInsights-Analytics-NewAlertRule.JPG)

9. The Azure Monitor pane will become available allowing to create an Azure Monitor Log Alert.

   ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab02/images/AppInsights-Analytics-ExceptionsQuery.JPG)