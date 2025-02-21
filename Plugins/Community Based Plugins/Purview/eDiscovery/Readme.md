# eDiscovery Plugin for Security Copilot
Author: Amit Singh

This custom Security Copilot plugin enhances your organization's eDiscovery capabilities in Microsoft Purview. It is designed for workflows where you create a case and export artifacts directly. You can initiate an export from Search after indexing and estimating the artifacts. However, this plugin does not support workflows that involve attaching searches to a review set for further analysis in eDiscovery. Attaching searches to a review set is a manual process that must be completed within the case in the Purview portal.

### Prerequisites for Using Security Copilot

- **Ensure Security Copilot is Enabled**  
  Before you start, make sure Security Copilot is enabled in your environment. Follow the onboarding steps here:  
  [Get Started with Security Copilot](https://learn.microsoft.com/en-us/security-copilot/get-started-security-copilot#onboarding-to-microsoft-security-copilot)

- **Check Your Access to Upload Custom Plugins**  
  To use custom plugins, you need the proper permissions to upload them in Security Copilot. Learn how to manage and enable this feature here:  
  [Managing Custom Plugins](https://learn.microsoft.com/en-us/security-copilot/manage-plugins?tabs=securitycopilotplugin#managing-custom-plugins)

- **Set Up the Required Permissions for Your Application**  
  Your application must have the following permissions for Microsoft Graph (`https://graph.microsoft.com`):  
  - `offline_access`  
  - `user.read`  
  - `eDiscovery.Read.All`  
  - `eDiscovery.ReadWrite.All`  

  To register your application and configure these permissions, follow the steps here:  
  [Register an Application in Entra ID](https://learn.microsoft.com/en-us/graph/auth-register-app-v2#register-an-application)

## Setting Up the Custom Plugin in Security Copilot

### Uploading the Custom Plugin  

1. **Download the Required File**  
   - Obtain the file **[`eDiscovery_OAuth_API_manifest.yaml`](https://github.com/samitks77/Copilot-For-Security/blob/main/Plugins/Community%20Based%20Plugins/Purview/eDiscovery/eDiscovery_OAuth_API_manifest.yaml)** from the designated directory. This YAML file will be uploaded to **Security Copilot** during the setup process.
   
2. **Add Client ID & Tenant ID**  
   - From your **Entra ID App Registration**, make sure to add your **Client ID** and **Tenant ID** before proceeding with the 
   upload.    
   ![alt text](EntraID-ClientID-TenantID.png)  
   
3. **Generate and Copy Your Secret Value**
   - During the plugin upload process in **Security Copilot**, you will need a **Secret Value** from **Certificates & Secrets** in your Entra ID App.  
   - This **Secret Value** acts as your **API key** for the plugin to function correctly.  
   - **Important:** Copy your **Secret Value** immediately after creating it. If you navigate away from the page, the value will no longer be readable.
     
     ![alt text](EntraID-SecretValue.png)

4. **Create Secrets in Entra ID**

   - Follow these steps to create and manage secrets for your application: 
   **[`How to Add Credentials in Entra ID`](https://learn.microsoft.com/en-us/graph/auth-register-app-v2#add-credentials)**

5. **Navigate to Custom Plugins**

   - Go to the **Manage Sources** on the home page of **Security Copilot**, and scroll down to the **Custom Plugins** section.

   ![alt text](scp-upload-custom-plugins.png)

   ![alt text](scp-upload-custom-plugins-2.png)
6. **Upload the Plugin File**

   - Click on **Security Copilot Plugin**, then upload the **`eDiscovery_OAuth_API_manifest.yaml`** file.

   ![alt text](scp-upload-custom-plugins-api-manifest.png)

7.  **Enter the Client Secret and Connect**
   
    - Paste the **Client Secret Value** from your **Entra ID App Registration**.  
    - Click **Connect** to proceed.

     ![alt text](CfS-Secret.png)

8.  **Sign-In**

    Once you click **Connect**, a new window will open where you will need to sign in with your credentials.

### Plugin Setup Complete  

You have successfully set up the **eDiscovery Plugin** in **Security Copilot**. With the plugin uploaded, Client ID, Tenant ID, and Secret Value configured, and authentication completed, your integration is now ready to use. Security Copilot can now leverage this plugin for enhanced **eDiscovery capabilities**, allowing you to streamline investigations and data retrieval processes. If you encounter any issues, verify your Entra ID settings, ensure your Client Secret is valid, and check your Security Copilot permissions. 

### Skills & Prompts

These are sample prompts that you can use to interact with this plugin in Security Copilot. Each prompt is designed to help you execute specific eDiscovery actions efficiently. You can modify these prompts based on your use case and organizational requirements. Below, you'll find structured input fields required for each action, ensuring precise execution of eDiscovery tasks.

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>eDiscovery Skills & Prompts</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 40px;
            background-color: #f4f4f4;
        }
        .container {
            max-width: 800px;
            background: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
        }
        h2 {
            color: #333;
        }
        .prompt {
            margin-bottom: 20px;
            padding: 15px;
            border-left: 5px solid #0078D4;
            background: #eef5ff;
            border-radius: 5px;
        }
        .prompt h3 {
            margin: 0;
            color: #005A9E;
        }
        .prompt p {
            margin: 10px 0;
        }
        .inputs {
            font-weight: bold;
            color: #333;
        }
    </style>
</head>
<body>
    <div class="container">
        <h2>eDiscovery Skills & Prompts</h2>

        <div class="prompt">
            <h3>1. Create eDiscovery Case</h3>
            <p><strong>Example Prompt:</strong> Create an eDiscovery case in Purview with the Case name "Test-123", response should be a bulleted list.</p>
            <p class="inputs">Inputs: [Case name]</p>
        </div>

        <div class="prompt">
            <h3>2. Add Custodian to eDiscovery Case</h3>
            <p><strong>Example Prompt:</strong> Add a custodian to the eDiscovery case in Purview, use the Case ID "1xxxx234-XXXX-XXXX-a1cd-fxxxxxxxxxx0" and add this email "test@test123.com".</p>
            <p class="inputs">Inputs: [Email], [Case ID]</p>
        </div>

        <div class="prompt">
            <h3>3. Apply Hold on eDiscovery Custodian</h3>
            <p><strong>Example Prompt:</strong> Apply hold on eDiscovery custodian using the Custodian ID "2xxxxxxxxxxxxxxxxxxxxxxxxxxxxxx6".</p>
            <p class="inputs">Inputs: [Custodian ID]</p>
        </div>

        <div class="prompt">
            <h3>4. Add New userSource Objects to Custodians</h3>
            <p><strong>Example Prompt:</strong> Add new userSource object associated with Custodian ID "2xxxxxxxxxxxxxxxxxxxxxxxxxxxxxx6", include custodian email "test@test123.com" and specify sources as Mailbox, Site.</p>
            <p class="inputs">Inputs: [Custodian ID], [Email]</p>
        </div>

        <div class="prompt">
            <h3>5. Add New eDiscovery Search Object to the Case</h3>
            <p><strong>Example Prompt:</strong> Add a new eDiscovery Search object with Case ID "1xxxx234-XXXX-XXXX-a1cd-fxxxxxxxxxx0" with the display name "Test-123-search", and add dataSourceScopes to allTenantMailboxes, allTenantSites, allCaseCustodians.</p>
            <p class="inputs">Inputs: [Case ID], [Display Name]</p>
        </div>

        <div class="prompt">
            <h3>6. Run an Estimate on eDiscovery Case</h3>
            <p><strong>Example Prompt:</strong> Run an estimate of the number of emails and documents in eDiscovery with Search ID "2xxxxxxx-xxx4-xxxd-4xxx-5xxxxxxxxxxx".</p>
            <p class="inputs">Inputs: [Search ID]</p>
        </div>

        <div class="prompt">
            <h3>7. Create New eDiscovery ReviewSet</h3>
            <p><strong>Example Prompt:</strong> Create a new eDiscovery ReviewSet for Case ID "1xxxx234-XXXX-XXXX-a1cd-fxxxxxxxxxx0" with Display Name "Test-123-reviewset".</p>
            <p class="inputs">Inputs: [Case ID]</p>
        </div>

        <div class="prompt">
            <h3>8. Initiate an Export in eDiscovery</h3>
            <p><strong>Example Prompt:</strong> Use Case ID "1xxxx234-XXXX-XXXX-a1cd-fxxxxxxxxxx0" and ReviewSet ID "dxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx" to initiate an export.</p>
            <p class="inputs">Inputs: [Case ID], [Review Set ID]</p>
        </div>

        <div class="prompt">
            <h3>9. Initiate an Export in eDiscovery Search</h3>
            <p><strong>Example Prompt:</strong> Initiate an export from the Search with Case ID "1xxxx234-XXXX-XXXX-a1cd-fxxxxxxxxxx0" and Search ID "dxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx". Additional parameters: displayName="Export 1 - simple PST-V2", exportCriteria="searchHits", additionalOptions="none", exportFormat="pst".</p>
            <p class="inputs">Inputs: [Case ID], [Search ID]</p>
        </div>

        <div class="prompt">
            <h3>10. Update Index on Custodian/s</h3>
            <p><strong>Example Prompt:</strong> Use the Case ID from above or use this Case ID "1xxxx234-XXXX-XXXX-a1cd-fxxxxxxxxxx0", and update index on Custodian.</p>
            <p class="inputs">Inputs: [Case ID]</p>
        </div>

        <div class="prompt">
            <h3>11. Get a List of Case Operations in eDiscovery</h3>
            <p><strong>Example Prompt:</strong> Use the Case ID from above or use this Case ID "1xxxx234-XXXX-XXXX-a1cd-fxxxxxxxxxx0", get a list of the caseOperation objects and their properties.</p>
            <p class="inputs">Inputs: [Case ID]</p>
        </div>
    </div>
</body>
</html>
 


### eDiscovery prompt book based on variables like CaseID etc
![alt text](CfS-Prompt-Sample.png)




