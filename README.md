# How To Set Up

## Basics
* Server 2012 R2
* [Windows Management Framework 5 - February Preview](http://www.microsoft.com/en-us/download/details.aspx?id=45883) (The April preview and Production Preview from August break Test-Kitchen).
* [A recent ChefDK (newer than 0.6.0 ](https://downloads.chef.io/chef-dk/windows/)
* This repository

## Setting the stage
* Before each of the following (if you are on separate machines)
```powershell
Find-Module ChefConfSamples | Install-Module

chef shell-init powershell | invoke-expression
```
Change directories into the Website_Samples directory from the repository

### Running the DSC Sample

```powershell
. ./Examples/simple_webserver.ps1
SimpleWebserver -ConfigurationData $ConfigurationData
Start-DscConfiguration -path ./SimpleWebserver -verbose -wait
```

### Running the "traditional Chef recipe"
```powershell
chef-client -z -o basic_website
```

### Running a recipe with "dsc_script"
```powershell
chef-client -z -o 'basic_website::dsc_script'
```

### Running a recipe with "dsc_resource"
```powershell
chef-client -z -o 'basic_website::dsc_resource'
```
