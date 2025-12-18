**Introduction**

This lab provides a practical overview of **Sora**, OpenAI’s advanced
text-to-video generation model, integrated with **Azure OpenAI**
services. It demonstrates how to leverage Sora within the **Azure AI
Studio** and **Azure AI Foundry** environments to generate high-quality
video content from natural language prompts. The lab covers API
configuration, prompt execution, and video retrieval, showcasing how
cutting-edge generative models can be applied in cloud-based workflows
for content creation and innovation.

**Objectives**

- Understand the fundamentals of Sora and its integration with Azure
  OpenAI.

- Set up and configure access to Azure AI Studio and the Sora API.

- Generate videos from natural language prompts using prebuilt Sora
  endpoints.

- Analyze and retrieve generated video content from API responses.

- Explore use cases for AI-generated video in business and creative
  domains.

## Task 0: Understand the VM and the credentials

In this task, we will identify and understand the credentials that we
will be using throughout the lab.

1.  Instructions tab hold the lab guide with the instructions to be
    followed throughout the lab.

2.  Resources tab has got the credentials that will be needed for
    executing the lab.

- URL – URL to the Azure portal

- **Subscription – This is the ID of the subscription assigned to you**

- **Username – The user id with which you need to login to the Azure
  services.**

- **Password – Password to the Azure login. Let us call this Username
  and password as Azure login credentials. We will use these creds
  wherever we mention Azure login credentials.**

- **Resource Group – The Resource group assigned to you.**

**\[!Alert\] Important: Make sure you create all your resources under
this Resource group**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image1.png)

3.  Help tab holds the Support information. The ID value here is the Lab
    instance ID which will be used during the lab execution.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image2.png)

##  Task 1 : Register Service provider

1.  **Open a browser go to +++ sign in with your cloud slice account
    below.**

- **Username: <+++@lab.CloudPortalCredential>(User1).Username+++**

- **Password: \<<+++@lab.CloudPortalCredential>(User1).Password\>+++**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image3.png)

> ![A screenshot of a login box AI-generated content may be
> incorrect.](./media/image4.png)

4.  Click on Subscriptions tile.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image5.png)

5.  Click on the subscription name.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image6.png)

6.  Expand Settings from the left navigation menu. Click on Resource
    providers, enter +++**Microsoft.AlertsManagement**+++ and select it,
    and then click Register.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image7.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image8.png)

7.  Click on Resource providers,
    enter +++**Microsoft.DBforPostgreSQL**+++ and select i,t, and then
    click Register.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image9.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image10.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image11.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image12.png)

8.  Repeat the steps \#10 and \#11 to register the following Resource
    providers.

- **Microsoft.Search**

- **Microsoft.Web**

- **Microsoft.ManagedIdentity**

## Task 2: Create Azure OpenAI resource

1.  In Azure portal, search box, type **+++Microsoft Foundry+++** and
    then click on the Microsoft Foundry.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image13.png)

2.  In Azure AI Foundry page , select **Azure OpenAI** under the **Use
    with AI Foundry**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image14.png)

3.  Click on **+Create Azure OpenAI**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image15.png)

4.  In the Create Azure OpenAI window, under the Basics tab, enter the
    following details and click on the **Next** button.

&nbsp;

1)  Subscription: Select the assigned subscription

2)  Resource group:  Select the assigned Resource group

3)  Region: For this lab, you will use a  **SORA** model. This model is
    currently only available in [certain
    regions](https://learn.microsoft.com/azure/ai-services/openai/concepts/models#embeddings-models).
    Please select a region from this list, In this lab East US 2 is
    using for this resource.

4)  Name: aoaisoraXXXXX (XXXXX can be Lab instant ID)

5)  Pricing tier: Select Standard S0

Note: To find your lab instant ID, select 'Help' and copy the instant
ID.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image16.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image17.png)

5.  In the Network tab, leave all the radio buttons in the default
    state, and click on the **Next** button.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image18.png)

6.  In the Tags tab, leave all the fields in the default state, and
    click on the **Next** button.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image19.png)

7.  In the **Review + submit** tab, once the Validation is Passed, click
    on the **Create** button.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image20.png)

8.  Wait for the deployment to complete. The deployment will take around
    2-3 minutes.

&nbsp;

9.  On Microsoft.CognitiveServicesOpenAI window, after the deployment is
    completed, click on Go to resource button.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image21.png)

10. In the Overview section of the **Azure OpenAI home** page, copy the
    **Azure OpenAI** **resource name** and save them in a notepad.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image22.png)

11. Click on **Keys and Endpoints** from the left navigation menu and
    then copy the endpoint value in a notepad to **AzureAI
    ENDPOINT** and **key** to a variable AzureAIKey.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image23.png)

12. On the aoaisoraXXXXX window, click on Overview in the left-sided
    navigation menu, scroll down to Explore and deploy tile and click
    on Explore Azure AI Foundry portal button as shown in the below
    image to open Azure AI Foundry portal in a new browser.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image24.png)

## Task 3: Deploying an Azure OpenAI model Sora

1.  On the **Azure AI Foundry** **| Azure Open AI Service** homepage,
    navigate to Components section and click on Deployments.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image25.png)

2.  In the Deployments window, drop down the +Deploy model and
    select Deploy base model.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image26.png)

3.  In the Select a model dialog box, navigate and carefully
    select **sora**, then click on **Confirm** button.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image27.png)

4.  In the Deploy model **sora** dialog box, under the Deployment
    name field, ensure that **sora**, select the Deployment type
    as **Standard**. Then click on the **Deploy** button.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image28.png)

5.  In the Deployments window, drop down the **+Deploy model** and
    select **Deploy base model.**

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image29.png)

6.  In the Select a model dialog box, navigate and carefully
    select **gpt-4.1**, then click on **Confirm** button.

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image30.png)

7.  In the Deploy model **gpt 4.1** dialog box, under the Deployment
    name field, ensure that **gpt 4.1**, select the Deployment type
    as Global **Standard**. Then click on the **Deploy** button.

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image31.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image32.png)

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image33.png)

## Task 4: Generate AI-Powered Videos Using Sora with Azure AI Foundry

1.  In your Windows search box, type Visual Studio, then click on Visual
    Studio Code.

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image34.png)

2.  In the Visual Studio Code editor, click on File, then navigate and
    click on Open Folder.

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image35.png)

8.  Navigate and select **sora** folder from C**:\LabFiles** and click
    on the **Select** **Folder** button.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image36.png)

9.  If you see a dialog box - **Do you trust the authors of the files in
    this folder?**, then click on **Yes, I trust the author**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image37.png)

10. In Visual Studio Code dropdown the **SORA** and select **SORA with
    Azure AI Foundry.ipynb** notebook.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image38.png)

11. In the main page of Visual Studio Code editor, scroll down
    to **install requirements** heading and run the 1^(st) cell. If
    prompted to select the environment, then select **Python
    Environments** as shown in the image.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image39.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image40.png)

12. If prompted to select the path, then select the **Python version
    3.13.1 or later version** path as shown in the image.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image41.png)

![A screenshot of a computer program AI-generated content may be
incorrect.](./media/image42.png)

![A screenshot of a computer program AI-generated content may be
incorrect.](./media/image43.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image44.png)

![A screen shot of a computer program AI-generated content may be
incorrect.](./media/image45.png)

![A screenshot of a computer program AI-generated content may be
incorrect.](./media/image46.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image47.png)

![](./media/image48.png)

![A person and dog in the water AI-generated content may be
incorrect.](./media/image49.png)

![A person walking in the water AI-generated content may be
incorrect.](./media/image50.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image51.png)

![A person and child in the water AI-generated content may be
incorrect.](./media/image52.png)

![A screenshot of a computer program AI-generated content may be
incorrect.](./media/image53.png)

![A screenshot of a video AI-generated content may be
incorrect.](./media/image54.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image55.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image56.png)

![A screenshot of a video AI-generated content may be
incorrect.](./media/image57.png)

![A screenshot of a video AI-generated content may be
incorrect.](./media/image58.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image59.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image60.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image61.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image62.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image63.png)

![A close up of a person's eye AI-generated content may be
incorrect.](./media/image64.png)

![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image65.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image66.png)

![A close up of an eye AI-generated content may be
incorrect.](./media/image67.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image68.png)

![](./media/image69.png)

![](./media/image70.png)

![A screenshot of a video AI-generated content may be
incorrect.](./media/image71.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image72.png)

![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image73.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image74.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image75.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image76.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image77.png)

![A screenshot of a computer program AI-generated content may be
incorrect.](./media/image78.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image79.png)

## Task 5: Create Videos with the Azure OpenAI Sora API

1.  In your Windows search box, type Visual Studio, then click on Visual
    Studio Code.

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image34.png)

2.  In the Visual Studio Code editor, click on File, then navigate and
    click on Open Folder.

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image35.png)

3.  Navigate and select **visionary-lab** folder
    from C**:\LabFiles** and click on the **Select** **Folder** button.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image80.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image81.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image82.png)

![A screenshot of a computer program AI-generated content may be
incorrect.](./media/image83.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image84.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image85.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image86.png)

![](./media/image87.png)

![A screenshot of a computer program AI-generated content may be
incorrect.](./media/image88.png)

![A screenshot of a computer program AI-generated content may be
incorrect.](./media/image89.png)

![A screenshot of a computer program AI-generated content may be
incorrect.](./media/image90.png)

![](./media/image91.png)

![A screenshot of a computer program AI-generated content may be
incorrect.](./media/image92.png)

![](./media/image93.png)

![A screen shot of a computer program AI-generated content may be
incorrect.](./media/image94.png)

![A screenshot of a computer program AI-generated content may be
incorrect.](./media/image95.png)

![A screenshot of a computer program AI-generated content may be
incorrect.](./media/image96.png)

![A screenshot of a computer program AI-generated content may be
incorrect.](./media/image97.png)

![A screenshot of a computer program AI-generated content may be
incorrect.](./media/image98.png)

![A screenshot of a computer program AI-generated content may be
incorrect.](./media/image99.png)

![A screenshot of a computer program AI-generated content may be
incorrect.](./media/image100.png)

