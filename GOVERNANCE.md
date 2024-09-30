# Governance for Azure AI Service

## Establish shared governance for all AI workloads

Governance is about enforcing guardrails in the cloud to manage risks. Effective governance eliminates all unapproved use of AI and aligns it with regulatory and organizational policies

- Centralized resource organization for AI workloads
- Centralized cost governance for AI workloads
- Centralized security governance for all AI workload
- Centralized operational governance for all AI workloads
- Centralized regulatory compliance for all AI workloads

## Centralized resource organization for AI workloads

| Recommendation                                              | Benefit                                                                                                           |
|-------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------|
| Use subscriptions to separate application environments      | Create separate subscriptions for development, test, and production environments to isolate and manage AI application resources. All the application environments for a single AI application should be in the same management group |
|Differentiate resources in terms of their connectivity and exposure to the Internet|The choice between using a "Corp" or "Online" management group within an Azure Landing Zone should be guided by the specific security requirements and the nature of cross-premises data consumption|
|Apply policies on the management group|Prefer audit policies (not deny) at the management group level. Audit policies allow application teams to manage their needs by creating sublevel policies or integrating audit requirements into their IaC deployment modules|
|Use subscriptions to separate application environments|Create separate subscriptions for development, test, and production environments to isolate and manage AI application resources. All the application environments for a single AI application should be in the same management group|
|Use resource groups for resources that share a common lifecycle.|A shared AI resource, such as Azure AI Studio or Azure OpenAI, should have its own subscription and resource group. Resource groups also provide additional governance (policy), security (RBAC), and cost (budget) boundaries.|
|Standardize AI naming conventions.|Use a standard naming convention for Azure AI and machine learning resources so you can easily track AI resources. Understand the naming rules and restrictions for each Azure resource to develop resource names. Use the recommended AI and machine learning abbreviations since resources have name-length restrictions.|
|Enforce tag usage.|Use Azure policy to enforce tags for categorizing resources according to criteria such as ownership, environment, or application. Tags facilitate governance tasks like cost tracking, reporting, and automated policy application. Tags also support automation efforts in resource provisioning and deprovisioning.|
|Protect resources.|Apply resource locks to safeguard critical shared services from accidental deletion. Use deny policies in conjunction with Azure role assignments to prevent unauthorized resource deployments and configurations|

## Centralized Cost governance for all AI workload  

| Recommendation                                              | Benefit                                                                                                           |
|-------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------|
|Use tags to allocate costs.|Configure an Azure Policy definition to enforce tagging on resources. Use tags to categorize resources by project, cost center, environment, and owner for better management and billing. |
|Use tag inheritance.|Use the tag inheritance setting in Cost Management. When enabled, tag inheritance applies billing, resource group, and subscription tags to child resource usage records|
|Manage billing accounts.|Use Microsoft Billing to manage your billing account and pay invoices. Ensure each AI project or team has a designated billing account to accurately track expenses. |
|Monitor costs.|Use Microsoft Cost Management to set budget alerts, cost anomaly alerts, and scheduled alerts for different AI projects. This helps in tracking spending against allocated budgets and maintaining financial discipline. |
|View spending patterns. |Use the Azure Cost analysis to tool to regularly review spending patterns to identify trends and areas for potential savings in VM usage. |
|Allow specific virtual machine SKUs. |Use Azure policy to allow only the virtual machines SKUs that align with your AI budget. The built-in policy definition Allowed virtual machine SKUs in Azure policy to allow the deployment of only the SKUs you need. |
|Block resources. |Use policies to prevent the deployment of certain expensive resources.|
|Block expensive models.|Understand the costs of different models vary depending on which model series you choose. For example, there might be charges per 1,000 tokens for both input and output tokens. Being aware of this can help you choose the most cost-effective model series for your needs. |
|Auto shutdown compute instances. |Configure the schedule and idle shutdown of compute instances. This can significantly reduce costs by ensuring you don't pay for unused compute time. |
|Monitor Costs and Set Up Alerts.|After you start using Azure AI services, use Cost Management features to set budgets, monitor costs, and set up cost alerts. You can review forecasted costs and identify spending trends to find areas where you might want to act. Additionally, set up cost alerts to notify you when you exceed your budgeted amount. This comprehensive approach will enable you to effectively manage and control your costs. |
|Understand the Azure OpenAI Full Billing Model.|You use Azure AI services in Azure AI Studio and costs for Azure AI services are only a portion of the monthly costs in your Azure bill. You're billed for all Azure services and resources used in your Azure subscription, including the third-party services. The charges for Azure OpenAI Service are based on the number of tokens processed by the models. <https://learn.microsoft.com/en-us/azure/ai-studio/how-to/costs-plan-manage>|
|Consider Commitment tier.|If you have predictable, steady-state workloads, consider buying Reserved commitment tiers. These can provide significant savings compared to pay-as-you-go pricing. Azure AI offers commitment tier pricing, allowing discounted rates compared to the pay-as-you-go pricing model. With commitment tier pricing, you can commit to using the following Azure AI services features for a fixed fee, enabling you to have a predictable total cost based on the needs of your workload. Refer : <https://learn.microsoft.com/en-us/azure/ai-services/commitment-tier>|

## Centralized Security governance for all AI workload

| Recommendation                                              | Benefit                                                                                                           |
|-------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------|
|Centralize identity management. |Use Microsoft Entra ID as the central identity provider for all users, applications, and services. Have one team that manages identity for all AI workloads. This ensures a unified and consistent approach to identity management.|
|Have a central team create subscriptions for AI application resources. |Configure each subscription with the least privilege access. But allow the application team to manage their own resources using Azure roles.  |
|Configure least privilege access to centralized AI resources.|For centralized AI resources shared by multiple applications and application teams, start by granting minimum access, such as the Reader (Azure role) and elevating to Contributor (Azure role) if the limited permissions slow development too much. |
|Activate Azure Defender. |Enable Azure Defender to provide advanced threat protection for your workloads, including virtual machines, storage accounts, and databases.  |
|Implement distinct access controls for each environment. |Protect resources from accidental deployments by limiting each deployment pipeline's identity to its specific environment. |
|Govern infrastructure as code.|Govern IaC templates by using Microsoft Defender for Cloud to Detect IaC misconfigurations and enforce secure deployments. |

## Centralized operational governance for all AI workloads

| Recommendation                                              | Benefit                                                                                                           |
|-------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------|
|Configure alerts.|Enable recommended alert rules to receive notifications of metric deviations. |
|Use CI/CD pipelines. |Use CI/CD pipelines to automate the testing and deployment phases of your AI workloads. Automate the deployment of AI models and related infrastructure through GitHub to reduce manual errors and improve efficiency. Leverage release gates and approval workflows to maintain control over deployment processes. |
|Use infrastructure as code|Use IaC with tools like Azure Resource Manager templates or Terraform allows for the declarative and consistent provisioning of required infrastructure, adhering to best practices and compliance requirements.  |
|Version-control infrastructure changes. |Track and version-control IaC configurations in a source repository. This practice provides transparency in infrastructure changes and simplifies rollbacks in case of issues.   |

## Centralized Regulatory compliance for all AI workloads

| Recommendation                                              | Benefit                                                                                                           |
|-------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------|
|Develop industry-specific compliance checklists.|Compile thorough checklists reflecting the regulatory demands relevant to your industry, such as GDPR, HIPAA, or financial services regulations. This step helps ensure that your AI initiatives remain compliant from the onset. |
|Enforce data residency and handling policies.|Data residency requirements stipulate that data must be stored within specific geographic boundaries and handled following local laws. This is critical for multinational or multi-regional deployments of AI solutions on Azure. Utilize Azure's region-specific services and configurations to adhere to these regulations. |
|Azure Policy.|Enforce compliance with built-in policy definitions. Azure Policy Documentation.|
|Microsoft Purview Compliance Manager.|Manage compliance with a dashboard that offers insights and recommendations. Azure Compliance Manager Documentation.|
|Azure Machine Learning.|Features supporting responsible AI such as model interpretability and transparency. Azure Machine Learning documentation|

## Centralized Regulatory compliance for all AI workloads

| Recommendation                                              | Benefit                                                                                                           |
|-------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------|
|Use built-in regulatory compliance policies.|Use the applicable regulatory compliance initiatives for your industry.Apply additional policies based on the AI services you’re using.Azure Studio and AI services, see <https://learn.microsoft.com/en-us/azure/ai-services/security-controls-policy>. For Azure Machine Learning, see <https://learn.microsoft.com/en-us/azure/machine-learning/policy-reference>. For Azure Virtual Machines, see <https://learn.microsoft.com/en-us/azure/virtual-machines/policy-reference>.  |
|Consult common standards. |Use standards, such as ISO/IEC 23053:2022, Framework for Artificial Intelligence (AI) Systems Using Machine Learning (ML), to audit your policies applied to AI workloads. |
