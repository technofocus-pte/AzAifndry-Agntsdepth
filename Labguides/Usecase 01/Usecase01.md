
# Use Case 01- Developing Multimodal AI Applications for Image Classification

**Introduction**

This use case demonstrates how to utilize  GPT-4o model for image
classification by combining its multimodal capabilities with a
user-friendly web interface. It highlights the power of GPT-4o in
interpreting visual content and generating meaningful natural language
descriptions, making it ideal for applications in AI-driven image
understanding.

**Objective:**

- Showcase the integration of GPT-4o with Azure services for image
  classification.

- Enable users to upload images and receive intelligent, descriptive
  outputs from GPT-4o.

- Provide a working example of how to build multimodal AI applications
  using Python and Streamlit.

- Inspire developers to explore GPT-4o’s potential in real-world
  scenarios involving vision and language.

## Task 0: Understand the VM and the credentials

In this task, we will identify and understand the credentials that we
will be using throughout the lab.

1.  **Instructions** tab hold the lab guide with the instructions to be
    followed throughout the lab.

2.  **Resources** tab has got the credentials that will be needed for
    executing the lab.

    - **URL** – +++portal.azure.com+++
    - **Subscription** – **@lab.CloudSubscription.Id**
    - **Username** – +++@lab.CloudPortalCredential(User1).Username+++
    - **Temporary Access Token (TAP)** – +++@lab.CloudPortalCredential(User1).AccessToken+++
    - **Resource Group** – **ResourceGroup1**

	>[!Alert] Make sure you create all your resources under this Resource group

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image1.png)

3.  **Help** tab holds the Support information. The **ID** value here is
    the **Lab instance ID** which will be used during the lab execution.

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image2.png)

##  Task 1 : Register Service provider

1.  Open a browser go to +++https://portal.azure.com+++ and sign in with
    your cloud slice account below.

	Username: +++@lab.CloudPortalCredential(User1).Username+++
	
	Temporary Access Token (TAP):  +++@lab.CloudPortalCredential(User1).AccessToken+++
	
	![A screenshot of a computer Description automatically
	generated](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image3.png)
	
	![A screenshot of a login box Description automatically
	generated](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image4.png)

2.  Click on **Subscriptions** tile.

	![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image5.png)

3.  Click on the subscription name.

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image6.png)

4.  Expand Settings from the left navigation menu. Click on **Resource
    providers**, enter +++Microsoft.AlertsManagement+++ and select
    i,t, and then click **Register**.

	![A screenshot of a computer AI-generated content may be
	incorrect.](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image7.png)

	![A screenshot of a computer AI-generated content may be
	incorrect.](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image8.png)

5.  Click on **Resource providers**,
    enter +++Microsoft.DBforPostgreSQL+++ and select the resource and then
    click **Register**.

	![A screenshot of a computer AI-generated content may be
	incorrect.](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image9.png)

	![A screenshot of a computer AI-generated content may be
	incorrect.](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image10.png)

	![A screenshot of a computer AI-generated content may be
	incorrect.](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image11.png)

	![A screenshot of a computer AI-generated content may be
	incorrect.](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image12.png)

6.  Repeat the steps 10 and 11 to register the following Resource
    providers.

	- +++Microsoft.Search+++
	- +++Microsoft.Web+++
	- +++Microsoft.ManagedIdentity+++

## **Task 2: Create Azure OpenAI resource**

1.  In Azure portal, search box, type +++Microsoft Foundry+++ and
    then click on the Microsoft Foundry.

	![A screenshot of a computer AI-generated content may be
	incorrect.](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image13.png)

2.  In Microsoft Foundry page , select under **Use with Foundry**, **Azure OpenAI**.

	![A screenshot of a computer AI-generated content may be
	incorrect.](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image14.png)

3.  Click on **+ Create**, **Azure OpenAI**.

	![A screenshot of a computer AI-generated content may be
	incorrect.](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image15.png)

4.  In the **Create Azure OpenAI** window, under the **Basics** tab,
    enter the following details and click on the **Next** button.

    1.  **Subscription**: **@lab.CloudSubscription.Name**
    2.  **Resource group:** : **ResourceGroup1**
	
    3.  **Region**: For this lab, you will use a  **gpt-4-vision**
        model. This model is currently only available in [certain
        regions](https://learn.microsoft.com/azure/ai-services/openai/concepts/models#embeddings-models). 
		Please try **@lab.CloudResourceGroup(ResourceGroup1).Location** 
		prior to another region from list linked.
		
    4.  **Name**: +++aoai-gpt4-vision@lab.LabInstance.Id+++ 
    5.  **Pricing tier**: Select **Standard S0**

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image17.png)

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image18.png)

1.  In the **Network** tab, leave all the radio buttons in the default
    state, and click on the **Next** button.

	![A screenshot of a computer Description automatically generated](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image19.png)

2.  In the **Tags** tab, leave all the fields in the default state, and
    click on the **Next** button.

	![A screenshot of a computer Description automatically generated](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image20.png)

3.  In the **Review + submit** tab, once the Validation is Passed, click
    on the **Create** button.

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image21.png)

4.  Wait for the deployment to complete. The deployment will take around
    2-3 minutes.

5.  On **Microsoft.CognitiveServicesOpenAI** window, after the
    deployment is completed, click on **Go to resource** button.

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image22.png)

6.  In the Overview section of the Azure OpenAI home page, copy the
    Azure OpenAI resource name, resource group, and subscription ID, and
    save them in a notepad.

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image23.png)

7.  Click on **Keys and Endpoints** from the left navigation menu under **Resource Management** and
    then copy the endpoint value in a notepad to **AzureAI ENDPOINT**
    and key to a variable **AzureAIKey**.

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image24.png)

8.  On the **aoai-gpt4o-vision@lab.LabInstance.Id** window, click on **Overview** in the
    left-sided navigation menu, scroll down to **Get Started** tile and
    click on **Go to AzureOpenAI Studio** button as shown in the below
    image to open **Azure AI Foundry portal** in a new browser.

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image25.png)

## **Task 3: Deploying an Azure OpenAI model gpt-4o**

1.  On the **Azure AI Foundry | Azure Open AI Service** homepage,
    navigate to **Shared resources** section and click on **Deployments**.

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image26.png)

2.  In the **Deployments** window, drop down the **+Deploy model** and
    select **Deploy base model.**

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image27.png)

3.  In the **Select a model** dialog box, navigate and carefully select
    **gpt-4o**, then click on **Confirm** button.

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image28.png)

4.  In the **Deploy model gpt-4o** dialog box, under the **Deployment
    name** field, ensure that **gpt-4o**, select the Deployment type as
    **Global Standard**. Then click on the **Deploy** button.

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image29.png)

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image30.png)

## Task 4: GPT-4o with Vision demo

1.  In your Windows search box, type Visual Studio, then click on
    **Visual Studio Code**.

	![A screenshot of a computer Description automatically generated](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image31.png)

2.  In the **Visual Studio Code** editor, click on **File**, then
    navigate and click on **Open Folder**.

	![A screenshot of a computer Description automatically generated](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image32.png)

3.  Navigate and select **gpt-4o-image-classification** folder from
    **C:\LabFiles** and click on the **Select Folder** button.

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image33.png)

4.  If you see a dialog box - **Do you trust the authors of the files in
    this folder?**, then click on **Yes, I trust the author**.

	![A screenshot of a computer Description automatically generated with
	medium confidence](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image34.png)

5.  In Visual Studio Code dropdown the **GPT-4O-IMAGE-CLASSIFICATION**,
    click on **azure.env** file.

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image35.png)

6.  Update the parameters, replace **Azure OpenAI resource name,
    Subscription, Resource group name, Azure OpenAI Endpoint, Azure
    OpenAI Key** (The values that you have saved in your notepad in
    Task 2) and Save the file.

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image36.png)

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image37.png)

7.  In Visual Studio Code dropdown the **GPT-4O-IMAGE-CLASSIFICATION**
    and select **Image classification with Azure OpenAI gpt-4o - Flowers
    example.ipynb** notebook.

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image38.png)

8.  In the main page of Visual Studio Code editor, scroll down to
    **install requirements** heading and run the 1st cell. If
    prompted to select the environment, then select **Python
    Environments** as shown in the image.

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image39.png)

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image40.png)

9.  If prompted to select the path, then select the **Python** version that shows as the **Global env** path as shown in the image.

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image41.png)

10. If you see an windows security alert dialog box - then click on
    **Allow access**. Run the following code blocks.

	>[!Alert] If prompted to Install a required package, please select **Install**.
	
	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image42.png)

	![A screenshot of a computer AI-generated content may be
	incorrect.](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image43.png)

	![A screenshot of a computer AI-generated content may be
	incorrect.](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image44.png)

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image45.png)

	![A screenshot of a computer AI-generated content may be
	incorrect.](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image46.png)

11. To restart Jupyter kernel, click on **Restart** button.

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image47.png)

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image48.png)

12. To import the libraries, select cell. Then, execute the cell by
    clicking on the **start icon**.

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image49.png)

13. Select **4th** cell. Then, execute the cell by clicking on the
    **start icon**.

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image50.png)

14. To check the OpenAI, system versions, select 5th, 6th and
    7th cells. Then, execute the cell by clicking on the **start
    icon**.

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image51.png)

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image52.png)

15. Define a helper function to create embeddings, select and execute
    the 8th, 9th, 10th and 11th cells by clicking on the
    **Play** button.

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image53.png)

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image54.png)

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image55.png)

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image56.png)

16. To Image classification, select and execute the 12th, 13th, 14th and 15th cells by clicking on the **Play** button.

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image57.png)

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image58.png)

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image59.png)

17. To test, select and execute the **16th, 17th**, **18th**
    and **19th** cells by clicking on the **Play** button.

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image60.png)

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image61.png)

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image62.png)

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image63.png)

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image64.png)

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image65.png)

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image66.png)

	![A close up of a flower AI-generated content may be
	incorrect.](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image67.png)

18. Select and execute the **20th, 21st, 22nd, 23rd, 24th
    and 25th** cells by clicking on the **Play** button.

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image68.png)

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image69.png)

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image70.png)

	![A screen shot of a computer AI-generated content may be
	incorrect.](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image71.png)

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image72.png)

	![A screen shot of a graph AI-generated content may be
	incorrect.](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image73.png)

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image74.png)

	![A screenshot of a computer AI-generated content may be
	incorrect.](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image75.png)

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image76.png)

	![A screenshot of a computer AI-generated content may be
	incorrect.](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image77.png)

## Task 5: Delete the resources

1.  To delete the storage account, navigate to **Azure portal Home**
    page, click on **Resource groups**.

	![A screenshot of a computer Description automatically generated](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image78.png)

2.  Click on the **ResourceGroup1** resource group.

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image79.png)

3.  In the **Resource group** home page, select the **delete resource
    group**

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image80.png)

4.  In the **Delete Resources** pane that appears on the right side,
    navigate to **Enter “resource group name” to confirm deletion**
    field, then click on the **Delete** button.

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image81.png)

5.  On **Delete confirmation** dialog box, click on **Delete** button.

	![](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image82.png)

6.  Click on the bell icon, you’ll see the notification –**Deleted
    resource group AOAI-RG89.**

	![A screenshot of a computer Description automatically
	generated](https://raw.githubusercontent.com/technofocus-pte/AzAifndry-Agntsdepth/refs/heads/Cloudslice/Labguides/Usecase%2001/media/image83.png)

**Summary**

This usecase presents a Streamlit-based web application that allows
users to upload images and receive descriptive classifications powered
by Azure OpenAI's GPT-4o model. It highlights the model’s ability to
interpret visual content and generate natural language responses.


---------------------------------------------------------------------------------------------------------------------------------------------------------------------------





