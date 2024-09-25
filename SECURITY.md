<!-- BEGIN MICROSOFT SECURITY.MD V0.0.9 BLOCK -->

## Infrastructure Security for AI workloads

# Network Security
Where possible it is recommended to provision AI services in own Virtual Network (VNet Injection). Following are the advantages 

Virtual Network Injection: 

Dedicated Private Deployments: VNet injection allows you to deploy dedicated instances of a PaaS service into your own virtual network. This means the service instances are deployed into a subnet in your virtual network, and you can apply network policies and rules to these instances 

Network Isolation: This model provides network isolation by using private IP addresses within your virtual network. It allows resources within the virtual network to communicate privately and securely 

Complexity and Scalability: VNet injection can increase complexity and reduce scalability due to the need for managing dedicated instances and public IP addresses 

Dedicated Resources: VNet injection is suitable for services that require dedicated resources and can be deployed into the instance owner's VNet. This model is typically used for services that need to be isolated from other services 

Service Endpoints: VNet injection allows the use of service endpoints to secure access to Azure PaaS services from within your virtual network 

| Property                                            | VNet Injection                     |   Managed Vnet                |                                                                                                    
|-----------------------------------------------------|------------------------------------|--------------------------------|


| Completed isolation of VNET for the tenant          |        Yes                         | Partial |
|Customer access to VNET                              |        Yes                        | No       |
|Support for Private Link services                    |        Yes                         |  Yes    |
|Support for service endpoints |Yes | Yes|
|UDR support (Custom Routing) |Yes | No |
|NSG Support (Secured using NSG) |Yes | No|
|Azure Policy Support |Yes | Partial|
|Traffic Filtering | Yes | Partial|
|Integration with standard Hub and Spoke Network Architecture | Yes| Yes|
|Integration with vWAN Architecture |Yes |Yes |
|Azure DDoS support | Yes| Yes|
|Data Exfiltration risk |Extremely Low| Low|
|Network management Overhead |High |Low|
|Full control over IP address space | Yes |No|



# Compute Security 


# Software Vulnerabilities


# Defender for Cloud


# Data Exfiltration 


## Security

Microsoft takes the security of our software products and services seriously, which includes all source code repositories managed through our GitHub organizations, which include [Microsoft](https://github.com/Microsoft), [Azure](https://github.com/Azure), [DotNet](https://github.com/dotnet), [AspNet](https://github.com/aspnet) and [Xamarin](https://github.com/xamarin).

If you believe you have found a security vulnerability in any Microsoft-owned repository that meets [Microsoft's definition of a security vulnerability](https://aka.ms/security.md/definition), please report it to us as described below.

## Reporting Security Issues

**Please do not report security vulnerabilities through public GitHub issues.**

Instead, please report them to the Microsoft Security Response Center (MSRC) at [https://msrc.microsoft.com/create-report](https://aka.ms/security.md/msrc/create-report).

If you prefer to submit without logging in, send email to [secure@microsoft.com](mailto:secure@microsoft.com).  If possible, encrypt your message with our PGP key; please download it from the [Microsoft Security Response Center PGP Key page](https://aka.ms/security.md/msrc/pgp).

You should receive a response within 24 hours. If for some reason you do not, please follow up via email to ensure we received your original message. Additional information can be found at [microsoft.com/msrc](https://www.microsoft.com/msrc). 

Please include the requested information listed below (as much as you can provide) to help us better understand the nature and scope of the possible issue:

  * Type of issue (e.g. buffer overflow, SQL injection, cross-site scripting, etc.)
  * Full paths of source file(s) related to the manifestation of the issue
  * The location of the affected source code (tag/branch/commit or direct URL)
  * Any special configuration required to reproduce the issue
  * Step-by-step instructions to reproduce the issue
  * Proof-of-concept or exploit code (if possible)
  * Impact of the issue, including how an attacker might exploit the issue

This information will help us triage your report more quickly.

If you are reporting for a bug bounty, more complete reports can contribute to a higher bounty award. Please visit our [Microsoft Bug Bounty Program](https://aka.ms/security.md/msrc/bounty) page for more details about our active programs.

## Preferred Languages

We prefer all communications to be in English.

## Policy

Microsoft follows the principle of [Coordinated Vulnerability Disclosure](https://aka.ms/security.md/cvd).

<!-- END MICROSOFT SECURITY.MD BLOCK -->
