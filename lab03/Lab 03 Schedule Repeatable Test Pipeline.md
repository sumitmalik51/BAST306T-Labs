# Lab 01: Explore insights and Create Alerts

Goal:

The goal of this lab will show the following:

3. Review data in Application Insights
4. Create a Azure Monitor Log Alert Rule based on App Insights data

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

In this exercise, you will go understanding how to create an Azure Monitor Log Alert based off telemetry gathered from your EasyRepro tests in the first lab.

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

   ![https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/AppInsights-Analytics-ExceptionsQuery.JPG](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/AppInsights-Analytics-ExceptionsQuery.JPG)

7. Confirm you see results in the results pane.

8. Click the Log Alert button.

   ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/AppInsights-Analytics-NewAlertRule.JPG)

9. The Azure Monitor pane will become available allowing to create an Azure Monitor Log Alert.

   ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/AppInsights-Analytics-ExceptionsQuery.JPG)

10. Begin by confirming the resource is your Application Insights resource.

11. Then we need to configure the query we will use. In this case we will use the exception query to create an alert. First, confirm you see the following:

    <img src="https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/AzureMonitor-Condition-Default.JPG" style="zoom:80%;" />

12. Click the Red Alert icon or the "Whenever the Custom log search is <logic undefined>" link.

13. You will see a textbox to input a Kusto query.

    ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/AzureMonitor-Condition-SearchQuery.JPG)

14. Use the following query:

    ```
    exceptions
    ```

15. Set the threshold to be any number greater than zero.

    ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/AzureMonitor-Condition-AlertLogic.JPG)

13. Click the OK button.

![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/AzureMonitor-Actions-OkButton.JPG)

14. So far we have pointed our Azure Monitor alert rule to our Application Insights resource and provided a Kusto query to run every x minutes. If the query returns more than 0 records we will want to perform an action.

#### Configure Azure Monitor Alert Action to Email

15. We will now configure the alert to email us when the alert is triggered.

16. Navigate to the Actions area of the Alert.

    ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/AzureMonitor-Actions-Default.JPG)

17. Click the "**Create action group**" button.

18. Name the action group.

    ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/AzureMonitor-Actions-NewActionGroup-NameYourActionGroup.JPG)

19. Choose the Email/SMS/Phone option. Out of the available options check the email checkbox and provide your alias. By doing this you are telling the Azure Monitor Alert to email you when the condition configured above is met.

    ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/AzureMonitor-Actions-NewActionGroup-EmailYourAliasField.JPG)

20. Click Ok.

    ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/AzureMonitor-Actions-OkButton.JPG)

21. Now you should see the Action Group area again and this time you need to click the "Select action group" button.

    ![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/AzureMonitor-Actions-Default.JPG)

22. To finish up the Azure Monitor Alert, we will give it a name and description and severity level.

23. Begin by adding the following:

    

![](https://raw.githubusercontent.com/aliyoussefi/BAST306T-Labs/master/lab01/images/AzureMonitor-Details-NameAndSevLevel.JPG)

| Property                  | Value                                                        |
| ------------------------- | ------------------------------------------------------------ |
| Alert rule name           | Email Your Alias and Kick off Logic App                      |
| Description               | This alert is used for the BAST306T Lab 01. It will email a microsoft alias and fire a logic app. |
| Severity                  | Sev 3                                                        |
| Enable rule upon creation | Yes                                                          |
| Suppress Alerts           | True                                                         |

