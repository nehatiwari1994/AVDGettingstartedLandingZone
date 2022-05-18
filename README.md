# Title: Getting started with AVD landing Zone on Azure 
This template allows you to create one Additional Domain controller Server(ADC) instance on Virtual Machine which will be later configured or promoted as an additional domain controller for authetication and two virtual networks acting as Hub & Spoke vnets and one storage account for storing the vhds of the vms. ADC will automatically deployed in management subnet of Hub Vnet.



# Solution overview and deployed resources. 
This template helps you to quickly deploy the landing zone for your First AVD workload on Azure assuming you already have PDC setup (If you have no domain controller in your environemnt in that case also this server can be promoted as primary domain controller as we have kept it greenfiled). Deploys Hub & spoke Vnet in your landing zone subscription with 4 subnets (LAN, WAN, Protected & MANAGMENT Subnet) in the Hub Vnet so that in case you plan to deploy a FW this landing zone setup can take care of your subnet requirment. 3 Subnets in spoke vnet (App, DB & Session Host SUBNETS) Along with one storage account to store the vhds.



## Target audience
Infrastructure Architect

Application Developer

IT Professional

Cloud Solution Architect


# Architecture



![alt image](https://github.com/nehatiwari1994/AVDGettingstartedLandingZone/blob/master/Images/AVD%20Architecture%20with%20Azure%20Landing%20Zone.png)



[Template.json](https://github.com/Ganapathivarma07/LRS-Migration-AzureSQLMI/blob/master/template.json) can be modified to match your current infrastructure needs.

## One Click Deploying Template
<!-- Powershell command for Translating Git URL for template.json
    $url = "https://raw.githubusercontent.com/Ganapathivarma07/LRS-Migration-AzureSQLMI/master/template.json"
    [uri]::EscapeDataString($url)
    >> uri = https%3A%2F%2Fgithub.com%2FGanapathivarma07%2FLRS-Migration-AzureSQLMI%2Fblob%2F
master%2Ftemplate.json

Base URL: https://portal.azure.com/#create/Microsoft.Template/uri
Final URL: <Base URL>/<uri>
-->
[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fnehatiwari1994%2Ftest%2Fmaster%2Ftemplate.json)


## Deploying an ARM Template using the Azure portal

Visit portal.azure.com
search for the templates 
add new template (define a name, description & Copy the code from the json file to the ARM template) 
wait for few mins for the Template to be ready to use 
got to the created template and click to deploy & then pass the required parameters 
wait for around 10 mins for the deployment to get completed 

## Azure services and related products
Resource Group

Azure virtual Network (HUB & Spoke with Subnets)

Azure Storage Account 

Azure Virtual Machine 


## Deployment steps

Make sure you have azure subscription ready to use and atleast contributor role on the subscription for avoiding any issue with the deployment permissions 

You can use click to deploy button for the Vnets and ADC vm to get deployed 

once deployment completes you can follow below step for promoting the server to Aditional domain controller 

Make sure you have provisoned the connectivity from onpre to Azure if its hybrid deployment and you already have PDC onpremises 

add the DNS server of the PDC in the vnet for the ADC server to join to domian 

Join the ADC server to domain 

Open Server Manager → Roles Summary → Add roles and feature

Select the roles you want to install on this server. The basic requirement to promote this server into a domain controller is Active Directory Domain Services.

The features for this role are ready to be installed. The basic features required for this service are selected by default. Click next.

Confirm your installation selections.

Note: It is recommended to select the "Restart the destination server automatically if required" option.

Click the Install button. Once installation is complete, close the window.

Once the ADDS role is installed in this server, you will see a notification flag next to the Manage menu. Select "Promote this server to a domain controller"

This fires up the ADDS configuration wizard. On the Deployment configuration page, select "Add Domain controller to an existing domain" . You need to specify the name 
of the domain in which the new DC will be added.

The "Domain controller options" page appears next. Options to make this DC a DNS server and a Global Catalog are selected by default. You can choose to make this DC a read-only DC if you want. Select the site name for the DC and a unique password for the DSRM mode.

Note: DSRM mode helps gain access to an environment if all domain administrator accounts lose access or in case of DC failure.

Since a DNS Server is being configured as part of our efforts, you’ll be warned that a delegation for this DNS server cannot be created. This can be safely ignored.Additional options: Choose where you want your DC to replicate from. Active Directory can replicate from any domain controller or a specific one.

On the "Paths" page, confirm the location for ADDS database files, log files and SYSVOL. You can either use the default < location or folder or selection→, or select another folder of your choice.Review your selections in the next screen and click Next. Windows will then perform a prerequisites check. Once it is done, click Install.

Your system will be rebooted after replication has taken place. Verify the health of the new domain controller by running dcdiag /v from the command line.
Once done you have your initial landing zone ready for deploying and getting started with the Host pool and session host additions 


## Related references
https://docs.microsoft.com/en-us/azure/virtual-desktop/overview

https://docs.microsoft.com/en-us/azure/cloud-adoption-framework/ready/landing-zone/

https://docs.microsoft.com/en-us/azure/architecture/example-scenario/wvd/windows-virtual-desktop?context=%2Fazure%2Fvirtual-desktop%2Fcontext%2Fcontext

## License & Contribute

You are responsible for the performance, the necessary testing, and if needed any regulatory clearance for any of the models produced by this toolbox.
Please refer [LICENSE](LICENSE) &  [Contribute](https://github.com/nehatiwari1994/AVDGettingstartedLandingZone/blob/master/Contribute.md) for more details


