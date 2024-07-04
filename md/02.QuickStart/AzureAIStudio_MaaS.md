## Deploy Phi-3 models as serverless APIs

Phi-3 models (Mini, Small and Medium) in the [Azure model catalog](https://learn.microsoft.com/azure/machine-learning/concept-model-catalog?WT.mc_id=aiml-137032-kinfeylo) can be deployed as a serverless API with pay-as-you-go billing. This kind of deployment provides a way to consume models as an API without hosting them on your subscription, while keeping the enterprise security and compliance that organizations need. This deployment option doesn't require quota from your subscription.

### Prerequisites
- An Azure subscription with a valid payment method. Free or trial Azure subscriptions won't work. If you don't have an Azure subscription, create a paid Azure account to begin.
- An Azure AI Studio hub. The serverless API model deployment offering for Phi-3 is only available with hubs created in these regions:
    - East US 2
    - Sweden Central

** Note** For a list of regions that are available for each of the models supporting serverless API endpoint deployments, see Region availability for models in serverless API endpoints.
- An Azure AI Studio project.
- Azure role-based access controls (Azure RBAC) are used to grant access to operations in Azure AI Studio. To perform the steps in this article, your user account must be assigned the Azure AI Developer role on the resource group. 

### Create a new deployment
To create a deployment:

- Sign in to Azure AI Studio.
- Select Model catalog from the left sidebar.
- Search for and select the model you want to deploy, for example Phi-3-mini-4k-Instruct, to open its Details page.
- Select Deploy.
- Choose the option Serverless API to open a serverless API deployment window for the model.

Alternatively, you can initiate a deployment by starting from your project in AI Studio.

- From the left sidebar of your project, select Components > Deployments.
- Select + Create deployment.
- Search for and select Phi-3-mini-4k-Instruct to open the model's Details page.
- Select Confirm, and choose the option Serverless API to open a serverless API deployment window for the model.
- Select the project in which you want to deploy your model. To deploy the Phi-3 model, your project must belong to one of the regions listed in the [prerequisites section](https://learn.microsoft.com/azure/ai-studio/how-to/deploy-models-phi-3?WT.mc_id=aiml-137032-kinfeylo).
- Select the Pricing and terms tab to learn about pricing for the selected model.
- Give the deployment a name. This name becomes part of the deployment API URL. This URL must be unique in each Azure region.
- Select Deploy. Wait until the deployment is ready and you're redirected to the Deployments page. This step requires that your account has the Azure AI Developer role permissions on the Resource Group, as listed in the prerequisites.
- Select Open in playground to start interacting with the model.

Return to the Deployments page, select the deployment, and note the endpoint's Target URL and the Secret Key, which you can use to call the deployment and generate completions. For more information on using the APIs, see [Reference: Chat Completions](https://learn.microsoft.com/azure/ai-studio/reference/reference-model-inference-chat-completions?WT.mc_id=aiml-137032-kinfeylo).

You can always find the endpoint's details, URL, and access keys by navigating to your Project overview page. Then, from the left sidebar of your project, select Components > Deployments.

### Consume Phi-3 models as a service
Models deployed as serverless APIs can be consumed using the chat API, depending on the type of model you deployed.

- From your Project overview page, go to the left sidebar and select Components > Deployments.
- Find and select the deployment you created.
- Copy the Target URL and the Key value.
- Make an API request using the /v1/chat/completions API using <target_url>/v1/chat/completions. For more information on using the APIs, see the [Reference: Chat Completions](https://learn.microsoft.com/azure/ai-studio/reference/reference-model-inference-chat-completions?WT.mc_id=aiml-137032-kinfeylo)

### Cost and quotas
Cost and quota considerations for Phi-3 models deployed as serverless APIs

You can find the pricing information on the Pricing and terms tab of the deployment wizard when deploying the model.

Quota is managed per deployment. Each deployment has a rate limit of 200,000 tokens per minute and 1,000 API requests per minute. However, we currently limit one deployment per model per project. Contact Microsoft Azure Support if the current rate limits aren't sufficient for your scenarios.