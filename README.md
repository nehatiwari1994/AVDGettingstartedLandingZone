# Title: Getting started with AVD landing Zone on Azure 
This template allows you to create one Additional Domain controller Server(ADC) instance on Virtual Machine which will be later configured or promoted as an additional domain controller for authetication and two virtual networks acting as Hub & Spoke vnets and one storage account for storing the vhds of the vms. ADC will automatically deployed in management subnet of Hub Vnet.



# Solution overview and deployed resources. 
This template helps you to quickly deploy the landing zone for your First AVD workload on Azure assuming you already have PDC setup (If you have no domain controller in your environemnt in that case also this server can be promoted as primary domain controller as we have kept it greenfiled). 



## Target audience
Infrastructure Architect

Application Developer

IT Professional

Cloud Solution Architect


# Architecture



![alt image]()



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


## Azure services and related products


## Deployment steps



## Related references


## License & Contribute

You are responsible for the performance, the necessary testing, and if needed any regulatory clearance for any of the models produced by this toolbox.
Please refer [LICENSE](LICENSE) &  [Contribute](https://github.com/Ganapathivarma07/LRS-Migration-AzureSQLMI/blob/master/Contribute.md) for more details


