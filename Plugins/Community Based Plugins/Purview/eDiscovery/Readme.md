# eDiscovery Plugin for Copilot for Security
Author: Amit Singh

This custom Copilot for Security plugin enhances your organization's eDiscovery capabilities in Microsoft Purview. It is designed for workflows where you create a case and export artifacts directly. You can initiate an export from Search after indexing and estimating the artifacts. However, this plugin does not support workflows that involve attaching searches to a review set for further analysis in eDiscovery. Attaching searches to a review set is a manual process that must be completed within the case in the Purview portal.

Pre-requisites

* [Copilot for Security Enabled](https://learn.microsoft.com/en-us/security-copilot/get-started-security-copilot#onboarding-to-microsoft-security-copilot)
* [Access to upload custom plugins](https://learn.microsoft.com/en-us/security-copilot/manage-plugins?tabs=securitycopilotplugin#managing-custom-plugins)
* Make sure your application has the following delegated graph (https://graph.microsoft.com) permissions: offline_access user.read eDiscovery.Read.All & eDiscovery.ReadWrite.All. See this link for App registration [EntraID Application Registration created](https://learn.microsoft.com/en-us/graph/auth-register-app-v2#register-an-application) 

### Instructions
#### Upload the Custom Plugin

* Obtain the file [eDiscovery_OAuth_API_manifest.yaml](https://github.com/samitks77/Copilot-For-Security/blob/main/Plugins/Community%20Based%20Plugins/Purview/eDiscovery/eDiscovery_OAuth_API_manifest.yaml) from this directory. This is the yaml that you will upload in Copilot for Security. From your EntraID App registration, add the ClientId & tenant ID.
![alt text](EntraID-ClientID-TenantID.png)
* During the upload process as a custom plugin in Copilot for Security you will need to have your Secret Value from Certificates & secrets. This will be your API key for this plugin to work. Copy your secret value once the secret is created because if you navigate away from this screen, your secret value will not be human readable ![alt text](EntraID-SecretValue.png) Follow these steps to create the secrets(https://learn.microsoft.com/en-us/graph/auth-register-app-v2#add-credentials).
* Upload eDiscovery_OAuth_API_manifest.yaml to Copilot for Security by navigating to custom plugins at the bottom of the Manage Sources page. ![alt text](CfS-add-plugin.png)
* Upload the file by clicking on Copilot for Security plugin. ![alt text](CfS-add-plugin-part2.png)
* Paste the Client Secret Value from EntraID App Registration & click connect ![alt text](CfS-Secret.png) It should open another window where you will sign in. 

### Skills & Prompts

#### 1. Create eDiscovery Case  
   - **Example Prompt(s):**  
     - Create eDiscovery case in Purview with the Case name "Test-123", response should be a bulleted list  
   - **Inputs:**  
     - [Case name]  

#### 2. Add Custodian to eDiscovery Case  
   - **Example Prompt(s):**  
     - Add custodian to the eDiscovery case in Purview, use the case ID from above or use this Case ID `"1xxxx234-XXXX-XXXX- 
       a1cd-fxxxxxxxxxx0"` and add this email for the custodian `"test@test123.com"`  
   - **Inputs:**  
     - [Email]  
     - [Case ID]  

#### 3. Apply Hold on eDiscovery Custodian  
   - **Example Prompt(s):**  
     - Apply hold on eDiscovery custodians using the custodian ID from above or use this Custodian ID 
       `"2xxxxxxxxxxxxxxxxxxxxxxxxxxxxxx6"`  
   - **Inputs:**  
     - [Custodian ID]  

#### 4. Add New userSource Objects to Custodians  
   - **Example Prompt(s):**  
     - Add new userSource object associated with the eDiscovery custodian ID `"2xxxxxxxxxxxxxxxxxxxxxxxxxxxxxx6"`, include this custodian email `"test@test123.com"` and specify sources as **Mailbox, Site**.  
   - **Inputs:**  
     - [Custodian ID]  
     - [Email]  

#### 5. Add New eDiscovery Search Object to the Case  
   - **Example Prompt(s):**  
     - Add a new `ediscoverySearch` object with this Case ID `"1xxxx234-XXXX-XXXX-a1cd-fxxxxxxxxxx0"` with the display name 
       `"Test-123-search"`, also add `dataSourceScopes` to **allTenantMailboxes, allTenantSites, allCaseCustodians**.  
   - **Inputs:**  
     - [Case ID]  
     - [Display Name]  

#### 6. Run an Estimate on eDiscovery Case  
   - **Example Prompt(s):**  
     - Run an estimate of the number of emails and documents in eDiscovery with this Search ID `"2xxxxxxx-xxx4-xxxd-4xxx- 
       5xxxxxxxxxxx"` or the Search ID from above.  
   - **Inputs:**  
     - [Search ID]  

#### 7. Create New eDiscovery ReviewSet  
   - **Example Prompt(s):**  
     - Create a new `ediscoveryReviewSet` for the above case ID or use this Case ID `"1xxxx234-XXXX-XXXX-a1cd-fxxxxxxxxxx0"` 
       with the Display Name `"Test-123-reviewset"`.  
   - **Inputs:**  
     - [Case ID]  

#### 8. Initiate an Export in eDiscovery  
   - **Example Prompt(s):**  
     - Use this Case ID `"1xxxx234-XXXX-XXXX-a1cd-fxxxxxxxxxx0"` or the Case ID from above & this ReviewSet ID `"dxxxxxxx- 
       xxxx-xxxx-xxxx-xxxxxxxxxxxx"` or the ReviewSet ID from above and initiate an export.  
   - **Inputs:**  
     - [Case ID]  
     - [Review Set ID]

#### 9. Initiate an Export in eDiscovery Search 
   - **Example Prompt(s):**  
     - Initiate an export from the above Search, Use this Case ID `"1xxxx234-XXXX-XXXX-a1cd-fxxxxxxxxxx0"` or the Case ID from 
       above & this Search ID `"dxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"` or the Search ID from above and initiate an export. 
       Additional parameters include, displayName= "Export 1 - simple PST-V2", exportCriteria = "searchHits", additionalOptions 
       = "none" and exportFormat = "pst"  
   - **Inputs:**  
     - [Case ID]  
     - [Search ID]
     
#### 11. Update index on Custodian/s  
   - **Example Prompt(s):**  
     - Use the Case ID from above or use this Case ID `"1xxxx234-XXXX-XXXX-a1cd-fxxxxxxxxxx0"`, and update index on Custodian
   - **Inputs:**  
     - [Case ID]  

#### 12. Get a List of Case Operations in eDiscovery  
   - **Example Prompt(s):**  
     - Use the Case ID from above or use this Case ID `"1xxxx234-XXXX-XXXX-a1cd-fxxxxxxxxxx0"`, get a list of the 
       `caseOperation` objects and their properties.  
   - **Inputs:**  
     - [Case ID]  


### eDiscovery prompt book based on variables like CaseID etc
![alt text](CfS-Prompt-Sample.png)




