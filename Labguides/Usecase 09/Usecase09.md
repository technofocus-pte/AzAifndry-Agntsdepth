---
lab:
  title: Usecase 09- Building Multimodal AI Applications Using GPT-4o with Azure OpenAI
  description: In this use case, participants explored how to build an end-to-end AI workflow using Azure OpenAI and Azure AI Foundry. The lab demonstrated how to create and configure cloud resources, deploy AI models, and interact with them using Python notebooks. Participants learned how multimodal AI models can process both text and images, enabling advanced AI-driven applications. By integrating these capabilities into a development environment and a simple web application, the lab showcased how organizations can build intelligent media and video generation solutions using Azure AI services
  duration: 5 minutes
  level: 300
  islab: true
  primarytopics:
    - Azure
    - Azure AI services
---

## Usecase 09- Building Multimodal AI Applications Using GPT-4o with Azure OpenAI
**Introduction**

This use case demonstrates how to build an AI-powered workflow for video
and multimodal content generation using Azure OpenAI capabilities.
Participants will learn how to configure Azure resources, deploy AI
models, and interact with advanced multimodal models to analyze images
and generate AI-driven outputs. The lab guides users through setting up
an Azure OpenAI resource, deploying a model, configuring the development
environment in Visual Studio Code, and running Python notebooks to
interact with the model. By integrating AI services with application
code, users can explore how multimodal models process text and images,
enabling the creation of intelligent applications that support advanced
media generation workflows

**Objectives**

By completing this use case, participants will be able to:

- Understand the lab environment, credentials, and Azure resources
  required for AI development.

- Register required Azure resource providers and configure the necessary
  cloud services.

- Create and configure an Azure OpenAI resource within Azure AI Foundry.

- Deploy and manage AI model deployments for multimodal AI workloads.

- Configure a development environment using Visual Studio Code, Python,
  and Jupyter notebooks.

- Execute Python scripts to interact with the deployed AI model using
  API calls.

- Analyze images using multimodal capabilities and generate AI-driven
  responses.

- Integrate AI functionality into a simple web application workflow.

- Clean up Azure resources after completing the lab

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

1.  In Azure portal, search box, type **+++Foundry+++** and then click
    on the Microsoft Foundry.

![](./media/image13.png)

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

3)  Region: Sweden Central

4)  Name: aoaisoraXXXXX (XXXXX can be Lab instant ID)

5)  Pricing tier: Select Standard S0

Note: To find your lab instant ID, select 'Help' and copy the instant
ID.

![](./media/image16.png)

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

1.  On the **Microsoft Foundry** **| Azure Open AI** homepage, navigate
    to Components section and click on **Deployments.**

![](./media/image25.png)

2.  In the Deployments window, drop down the +Deploy model and
    select Deploy base model.

![](./media/image26.png)

3.  In the Select a model dialog box, navigate and carefully
    select **gpt-4o**, then click on **Confirm** button.

![](./media/image27.png)

4.  In the Deploy model **sora** dialog box, under the Deployment
    name field, ensure that **sora**, select the Deployment type
    as **Standard**. Then click on the **Deploy** button.

![](./media/image28.png)

![](./media/image29.png)

## Task 4: GPT-4o model with Azure OpenAI

1.  In your Windows search box, type Visual Studio, then click on Visual
    Studio Code.

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image30.png)

2.  In the Visual Studio Code editor, click on File, then navigate and
    click on Open Folder.

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image31.png)

3.  Navigate and select **sora** folder from C**:\LabFiles** and click
    on the **Select** **Folder** button.

![](./media/image32.png)

4.  If you see a dialog box - **Do you trust the authors of the files in
    this folder?**, then click on **Yes, I trust the author**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image33.png)

![](./media/image34.png)

5.  In Visual Studio Code dropdown the **GPT-4O**, click
    on **azure.env** file.

![](./media/image35.png)

6.  Update the parameters, replace  **Azure OpenAI Endpoint, Azure
    OpenAI Key** (The values that you have saved in your notepad in
    Task 2) and Save the file.

![](./media/image36.png)

7.  Select the **Extensions** icon in the left hand panel.

8.  Search for and select +++Jupyter+++.

9.  On the **Jupyter** page, select **Install**.

10. After **Jupyter** installs, select the **Uninstall** dropdown and
    select **Install specific version**.

11. Select version **2024.11.0**.

12. Once that version finishes installing, select **Restart
    Extensions**.

13. Search for and select +++Python+++ in the **Extensions** seatch bar.

14. Select **Install**.

15. In Visual Studio Code dropdown the **GPT-4o** and select **GPT-4o
    model with AzureOpenAI.ipynb** notebook.

![](./media/image37.png)

16. In the main page of Visual Studio Code editor, scroll down
    to **install requirements** heading and run the 1^(st) cell. If
    prompted to select the environment, then select **Python
    Environments** as shown in the image.

![](./media/image38.png)

![](./media/image39.png)

17. If prompted to select the path, then select the **Python version
    3.11.9 or later version** path as shown in the image.

![](./media/image40.png)

18. In the main page of Visual Studio Code editor, scroll down
    to **install requirements** heading and run the 2nd cell

![](./media/image41.png)

19. To verify the version, select the cell and execute it by clicking
    the **Start (Run)** icon.

![](./media/image42.png)

![](./media/image43.png)

20. Select the cell, update your **endpoint** and **API key**, and then
    execute the cell by clicking the Start icon.

![](./media/image44.png)

21. To test the model, select the cell and execute it by clicking the
    **Start (Run)** icon.

![](./media/image45.png)

![](./media/image46.png)

![](./media/image47.png)

22. This example demonstrates how to call the GPT‑4o model using an
    image URL by sending both a text prompt and the image reference
    within the chat completion request.

23. Select the cell and execute it by clicking the **Start (Run)** icon.

![](./media/image48.png)

![](./media/image49.png)

![](./media/image50.png)

![](./media/image51.png)

24. This section explains how to load and display a local image file
    using Python before sending it to the GPT‑4o model for analysis

25. Select the cell and execute it by clicking the **Start (Run)** icon.

![](./media/image52.png)

![](./media/image53.png)

26. Select the example cell and execute it by clicking the **Start
    (Run)** icon.

![](./media/image54.png)

![](./media/image55.png)

![](./media/image56.png)

27. Select the example2 cell and execute it by clicking the **Start
    (Run)** icon.

![](./media/image57.png)

![](./media/image58.png)

28. Select the example3 cell and execute it by clicking the **Start
    (Run)** icon.

![](./media/image59.png)

![](./media/image60.png)

![](./media/image61.png)

29. Select the example 4 cell and execute it by clicking the **Start
    (Run)** icon.

![](./media/image62.png)

![](./media/image63.png)

![](./media/image64.png)

![](./media/image65.png)

30. Select the example 5 cell and execute it by clicking the **Start
    (Run)** icon.

![](./media/image66.png)

![](./media/image67.png)

31. Select the example 6 cell and execute it by clicking the **Start
    (Run)** icon.

![](./media/image68.png)

![](./media/image69.png)

32. Select the example 7 cell and execute it by clicking the **Start
    (Run)** icon.

![](./media/image70.png)

![](./media/image71.png)

![](./media/image72.png)

33. Select the example 8 cell and execute it by clicking the **Start
    (Run)** icon.

![](./media/image73.png)

![](./media/image74.png)

![](./media/image75.png)

34. Select the example 9 cell and execute it by clicking the **Start
    (Run)** icon.

![](./media/image76.png)

![](./media/image77.png)

![](./media/image78.png)

35. Select the example 10 cell and execute it by clicking the **Start
    (Run)** icon.

![](./media/image79.png)

![](./media/image80.png)

36. Select the example 11 cell and execute it by clicking the **Start
    (Run)** icon.

![](./media/image81.png)

![](./media/image82.png)

![](./media/image83.png)

![](./media/image84.png)

![](./media/image85.png)

![](./media/image86.png)

![](./media/image87.png)

![](./media/image88.png)

37. This section demonstrates how to integrate the GPT‑4o model into a
    web application by converting an uploaded image to Base64 and
    sending it along with a prompt for analysis.

![](./media/image89.png)

![](./media/image90.png)

![](./media/image91.png)

38. Select the cell and execute it by clicking the **Start (Run)** icon.

39. After the application has been successfully deployed, click
    the **URL**

![](./media/image92.png)

![](./media/image93.png)

40. Upload any image to the VM’s lab files folder and then review the
    generated output.

![](./media/image94.png)

![](./media/image95.png)

![](./media/image96.png)

## Task 5: Delete the resources

1.  Navigate back to the Azure home page.

2.  Select **Resource Group**.

3.  Select **@lab.CloudResourceGroup(ResourceGroup1).Name**.

4.  Select all the reosources
    in **@lab.CloudResourceGroup(ResourceGroup1).Name**.

5.  Select **Delete resource group**.

6.  Enter <+++@lab.CloudResourceGroup>(ResourceGroup1).Name+++ in the
    text box to confirm deletion.

7.  Select **Delete**.

**Summary**

In this use case, participants explored how to build an end-to-end AI
workflow using Azure OpenAI and Azure AI Foundry. The lab demonstrated
how to create and configure cloud resources, deploy AI models, and
interact with them using Python notebooks. Participants learned how
multimodal AI models can process both text and images, enabling advanced
AI-driven applications. By integrating these capabilities into a
development environment and a simple web application, the lab showcased
how organizations can build intelligent media and video generation
solutions using Azure AI services
