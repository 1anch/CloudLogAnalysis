---

copyright:
  years: 2017

lastupdated: "2017-11-09"

---


{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}


# Provisioning the Log Analysis service
{: #provision}

You can provision the {{site.data.keyword.loganalysisshort}} service from {{site.data.keyword.Bluemix}} UI, or from the command line.
{:shortdesc}


## Provisioning from the UI
{: #ui}

Complete the following steps to provision an instance of the {{site.data.keyword.loganalysisshort}} service in the {{site.data.keyword.Bluemix_notm}}:

1. Log in to your {{site.data.keyword.Bluemix_notm}} account.

    The {{site.data.keyword.Bluemix_notm}} dashboard can be found at: [http://bluemix.net ![External link icon](../../../icons/launch-glyph.svg "External link icon")](http://bluemix.net){:new_window}.
    
	After you log in with your user ID and password, the {{site.data.keyword.Bluemix_notm}} UI opens.

2. Click **Catalog**. The list of the services that are available on {{site.data.keyword.Bluemix_notm}} opens.

3. Select the **DevOps** category to filter the list of services that is displayed.

4. Click the **Log Analysis** tile.

5. Select a service plan. By default, the **Lite** plan is set.

    For more information about the service plans, see [Service plans](/docs/services/CloudLogAnalysis/log_analysis_ov.html#plans).
	
6. Click **Create** to provision the {{site.data.keyword.loganalysisshort}} service in the {{site.data.keyword.Bluemix_notm}} space where you are logged in.
  
 

## Provisioning from the CLI
{: #cli}

Complete the following steps to provision an instance of the {{site.data.keyword.loganalysisshort}} service in the {{site.data.keyword.Bluemix_notm}} through the command line:

1. [Pre-requisite] Install the {{site.data.keyword.Bluemix_notm}} CLI.

   For more information, see [Installing the {{site.data.keyword.Bluemix_notm}} CLI](/docs/cli/reference/bluemix_cli/download_cli.html#download_install).
   
   If the CLI is installed, continue with the next step.
    
2. Log in to the region, organization, and space in the {{site.data.keyword.Bluemix_notm}} where you want to provision the service. 

    For more information, see [How do I log in to the {{site.data.keyword.Bluemix_notm}}](/docs/services/CloudLogAnalysis/qa/cli_qa.html#login).
	
3. Run the `bx cf create-service` command to provision an instance.

    ```
	bx cf create-service service_name service_plan service_instance_name
	```
	{: codeblock}
	
	Where
	
	* service_name is the name of the service, that is, **ibmLogAnalysis**.
	* service_plan is the service plan name. For a list of plans, see [Service plans](/docs/services/CloudLogAnalysis/log_analysis_ov.html#plans).
	* service_instance_name is the name that you want to use for the new service instance that you create.
	
	For more information about the cf command, see [cf create-service](/docs/cli/reference/cfcommands/index.html#cf_create-service).

	For example, to create an instance of the {{site.data.keyword.loganalysisshort}} service with the Lite plan, run the following command:
	
	```
	bx cf create-service ibmLogAnalysis standard my_logging_svc
	```
	{: codeblock}
	
4. Verify that the service is created successfully. Run the following command:

    ```	
	bx cf services
	```
	{: codeblock}
	
	The output of running the command looks as follows:
	
	```
    Getting services in org MyOrg / space MySpace as xxx@yyy.com...
    OK
    
    name                           service                  plan                   bound apps              last operation
    my_logging_svc                ibmLogAnalysis           standard                                        create succeeded
	```
	{: screen}

	



