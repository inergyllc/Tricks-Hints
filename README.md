Tricks and hints by - Amram E. Dworkin
## Azure Tips & Tricks
<table style="width:100%">
  <tr>
    <th style="width:50%"><a href="#azure-resource-tagging-automation">Azure Resource Tagging Automation</a></th>
    <th style="width:50%"><a href="#azure-key-vault-secret-versioning">Azure Key Vault Secret Versioning</a></th>
  </tr>
  <tr>
    <td>Automatically apply tags to Azure resources based on policies to manage and organize resources more efficiently.</td>
    <td>Use versioning in Azure Key Vault to manage different versions of secrets efficiently.</td>
  </tr>
  <tr>
    <td>Tags: Azure, Resource Management, Policy, Tagging</td>
    <td>Tags: Azure, Secret Management, Key Vault, Security</td>
  </tr>
  <tr>
    <td><a href="#azure-resource-tagging-automation">Read more</a></td>
    <td><a href="#azure-key-vault-secret-versioning">Read more</a></td>
  </tr>
  <tr style="background-color:#f0f0f0;"><td /></td>tr>
  <tr>
    <th style="width:50%"><a href="#azure-function-proxies">Azure Function Proxies</a></th>
    <th style="width:50%"><a href="#azure-blob-storage-static-website-hosting">Azure Blob Storage Static Website Hosting</a></th>
  </tr>
  <tr>
    <td>Use Azure Function Proxies to create a unified API surface for multiple backend services.</td>
    <td>Host a static website directly from Azure Blob Storage.</td>
  </tr>
  <tr>
    <td>Tags: Azure, Functions, API Management, Development</td>
    <td>Tags: Azure, Blob Storage, Static Websites, Web Hosting</td>
  </tr>
  <tr>
    <td><a href="#azure-function-proxies">Read more</a></td>
    <td><a href="#azure-blob-storage-static-website-hosting">Read more</a></td>
  </tr>
  <tr style="background-color:#f0f0f0;"><td /></td>tr>
  <tr>
    <th style="width:50%"><a href="#azure-devtest-labs-for-cost-management">Azure DevTest Labs for Cost Management</a></th>
    <th style="width:50%"></th>
  </tr>
  <tr>
    <td>Use Azure DevTest Labs to create and manage cost-efficient development and test environments.</td>
    <td></td>
  </tr>
  <tr>
    <td>Tags: Azure, DevTest Labs, Cost Management, Development</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="#azure-devtest-labs-for-cost-management">Read more</a></td>
    <td></td>
  </tr>
</table>

## Uncategorized Tips & Tricks
<table style="width:100%">
  <tr>
    <th style="width:50% important!"><a href="#linking-external-folders-to-a-visual-studio-project">Linking External Folders to a Visual Studio Project</a></th>
    <th style="width:50% important!"><a href="#bing-search-modifiers">Bing Search Modifiers</a></th>
  </tr>
  <tr>
    <td>Link a non-project folder to a VS Studio project4.  Can edit, include, etc. files in external folder.  Shows as a regular folder called LinkedFolder (can change name)</td>
    <td>Bing search modifiers for more efficent searching.  I just need these a lot</td>
  </tr>
  <tr>
    <td>Tags: C#, Development, VS 2022, CSPROJ, Project Management</td>
    <td>Tags: Bing, Search, Efficiency</td>
  </tr>
  <tr>
    <td><a href="#azure-resource-tagging-automation">Read more</a></td>
    <td><a href="#azure-key-vault-secret-versioning">Read more</a></td>
  </tr>
  <tr style="background-color:#f0f0f0;"><td /></td>tr>
  <tr>
    <th style="width:50%"><a href="#azure-function-proxies">Azure Function Proxies</a></th>
    <th style="width:50%"><a href="#azure-blob-storage-static-website-hosting">Azure Blob Storage Static Website Hosting</a></th>
  </tr>
  <tr>
    <td>Use Azure Function Proxies to create a unified API surface for multiple backend services.</td>
    <td>Host a static website directly from Azure Blob Storage.</td>
  </tr>
  <tr>
    <td>Tags: Azure, Functions, API Management, Development</td>
    <td>Tags: Azure, Blob Storage, Static Websites, Web Hosting</td>
  </tr>
  <tr>
    <th style="width:50% important!"><a href="#linking-external-folders-to-a-visual-studio-project">Read more</a></th>
    <th style="width:50% important!"><a href="#bing-search-modifiers">Read more</a></th>
  </tr>
</table>




---
## Azure Resource Tagging Automation
Automatically apply tags to Azure resources based on policies to manage and organize resources more efficiently.

> ### How to Do It:
> 1. **Create an Azure Policy**:
>   - Go to the Azure portal and navigate to "Policy".
>   - Click "Definitions" and then "New policy definition".
>   - Define a policy to automatically add tags, for example, to add a tag `environment=production`.
>   - Use the following policy rule:
>     ```json
>     {
>       "if": {
>         "field": "location",
>         "equals": "westus"
>       },
>       "then": {
>         "effect": "modify",
>         "details": {
>           "roleDefinitionIds": [
>             "/providers/microsoft.authorization/roleDefinitions/00000000-0000-0000-0000-000000000000"
>           ],
>           "operations": [
>             {
>               "operation": "addOrReplace",
>               "field": "tags.environment",
>               "value": "production"
>             }
>           ]
>         }
>       }
>     }
>     ```
> 2. **Assign the Policy**:
>   - Go to "Assignments" and click "Assign policy".
>   - Select the policy definition created and assign it to the appropriate scope (subscription/resource group).
> 
> **Source**: [Microsoft Documentation - Azure Policy](https://docs.microsoft.com/en-us/azure/governance/policy/overview)

---

## Azure Key Vault Secret Versioning
Use versioning in Azure Key Vault to manage different versions of secrets efficiently.
> 
> ### How to Do It:
> 1. **Create a Secret**:
>   - Navigate to your Key Vault in the Azure portal.
>   - Click on "Secrets" and then "Generate/Import".
>   - Create a secret with a unique name.
> 
> 2. **Add a New Version of the Secret**:
>   - Click on the secret name.
>   - Click "New Version" and enter the new value.
> 
> 3. **Accessing Specific Versions**:
>   - Use the Azure CLI to retrieve a specific version:
>     ```sh
>     az keyvault secret show --vault-name <YourKeyVaultName> --name <YourSecretName> --version <SecretVersion>
>     ```
> 
> **Source**: [Microsoft Documentation - Azure Key Vault](https://docs.microsoft.com/en-us/azure/key-vault/secrets/about-secrets)

---

## Azure Function Proxies
Use Azure Function Proxies to create a unified API surface for multiple backend services.

> ### How to Do It:
> 1. **Create an Azure Function App**:
>    - In the Azure portal, create a new Function App.
> 
> 2. **Enable Proxies**:
>    - In the Function App, go to "Proxies" and click "Add".
>    - Configure a new proxy to forward requests to your backend service. For example:
>      ```json
>      {
>        "$schema": "http://json.schemastore.org/proxies",
>        "proxies": {
>          "myProxy": {
>            "matchCondition": {
>              "route": "/api/{*path}"
>            },
>            "backendUri": "https://mybackend.azurewebsites.net/api/{path}"
>          }
>        }
>      }
>      ```
> 
> 3. **Test the Proxy**:
>    - Deploy the function app and test the proxy endpoint to ensure it forwards requests correctly.
> 
> **Source**: [Microsoft Documentation - Azure Function Proxies](https://docs.microsoft.com/en-us/azure/azure-functions/functions-proxies)

---

## Azure Blob Storage Static Website Hosting
Host a static website directly from Azure Blob Storage.

> ### How to Do It:
> 1. **Enable Static Website Hosting**:
>    - Go to your storage account in the Azure portal.
>    - Navigate to "Static website" under the "Settings" section.
>    - Enable static website hosting and specify the index document and error document.
> 
> 2. **Upload Your Website Files**:
>    - Upload your static website files (HTML, CSS, JS, etc.) to the `$web` container created in your storage account.
> 
> 3. **Access Your Website**:
>    - Access your static website using the primary endpoint URL provided in the static website configuration page.
> 
> **Source**: [Microsoft Documentation - Static Website Hosting in Azure Storage](https://docs.microsoft.com/en-us/azure/storage/blobs/storage-blob-static-website)

---

## Azure DevTest Labs for Cost Management
Use Azure DevTest Labs to create and manage cost-efficient development and test environments.

> ### How to Do It:
> 1. **Create a DevTest Lab**:
>    - In the Azure portal, search for "DevTest Labs" and create a new lab.
> 
> 2. **Configure Cost Management Policies**:
>    - Set up policies for automatic shutdown and start-up of virtual machines to save costs.
>    - Configure quotas to limit the number of VMs, environments, and resources.
> 
> 3. **Use Formulas and Artifacts**:
>    - Define reusable formulas and artifacts to quickly create VMs with pre-installed software and configurations.
> 
> **Source**: [Microsoft Documentation - Azure DevTest Labs](https://docs.microsoft.com/en-us/azure/devtest-labs/devtest-lab-overview)


## Linking External Folders to a Visual Studio Project

To include an external folder in your Visual Studio project, you can modify the project file to link the folder. This ensures that the files in the external folder are included in the project and can be accessed and managed within Visual Studio.

> **Modify Project File:**
> 
> 1. **Unload the Project**:
>    - Right-click on your project in Solution Explorer and select "Unload Project".
> 
> 2. **Edit the Project File**:
>    - Right-click again and select "Edit [YourProjectName].csproj".
> 
> 3. **Add the Following Lines**:
>    ```xml
>    <ItemGroup>
>      <None Include="..\Path\To\External\Folder\**\*" Link="LinkedFolder\%(RecursiveDir)%(FileName)%(Extension)" />
>    </ItemGroup>
>    ```
> 
> 4. **Save and Reload Your Project**:
>    - Save the changes to the project file.
>    - Right-click on the unloaded project and select "Reload Project".

## Bing Search Modifiers

Bing search modifiers allow you to refine your searches to get more specific results. Here is an extensive list of Bing search modifiers with examples of how to use each:

> ## Basic Modifiers
> 
> - **`" "` (Quotes)**: Search for an exact phrase.
>   - **Example**: `"artificial intelligence"`
>   
> - **`+` (Plus)**: Ensure a specific word is included in the results.
>   - **Example**: `coffee +recipe`
> 
> - **`-` (Minus)**: Exclude a specific word from the results.
>   - **Example**: `apple -fruit`
> 
> ## Date Modifiers
> 
> - **`before:`**: Find results published before a specific date.
>   - **Example**: `climate change before:2023-01-01`
>   
> - **`after:`**: Find results published after a specific date.
>   - **Example**: `renewable energy after:2022-01-01`
> 
> ## Site Modifiers
> 
> - **`site:`**: Search within a specific website.
>   - **Example**: `site:wikipedia.org artificial intelligence`
>   
> - **`inurl:`**: Find pages with a specific word in the URL.
>   - **Example**: `inurl:blog healthy recipes`
>   
> - **`intitle:`**: Find pages with a specific word in the title.
>   - **Example**: `intitle:science news`
>   
> - **`inbody:`**: Find pages with a specific word in the body text.
>   - **Example**: `inbody:machine learning`
> 
> ## File Type Modifiers
> 
> - **`filetype:`**: Search for specific file types.
>   - **Example**: `project plan filetype:pdf`
> 
> ## Location Modifiers
> 
> - **`loc:`**: Find results from a specific location.
>   - **Example**: `loc:deutschland beer`
> 
> ## Language Modifiers
> 
> - **`language:`**: Search for results in a specific language.
>   - **Example**: `language:en space exploration`
> 
> ## Social Media Modifiers
> 
> - **`@`**: Find social media profiles.
>   - **Example**: `@elonmusk`
>   
> - **`hashtag:`**: Search for a specific hashtag.
>   - **Example**: `hashtag:#ThrowbackThursday`
> 
> ## Boolean Modifiers
> 
> - **`AND`**: Combine multiple terms and require all of them to appear.
>   - **Example**: `climate change AND global warming`
>   
> - **`OR`**: Combine multiple terms and require at least one of them to appear.
>   - **Example**: `solar energy OR wind energy`
> 
> ## Numeric Range Modifiers
> 
> - **`..`**: Search within a numeric range.
>   - **Example**: `smartphones $200..$500`
> 
> ## Special Modifiers
> 
> - **`define:`**: Get the definition of a word.
>   - **Example**: `define:quantum`
>   
> - **`weather:`**: Get the weather forecast for a location.
>   - **Example**: `weather:New York`
>   
> - **`map:`**: Find maps of a location.
>   - **Example**: `map:London`
> 
> - **`movie:`**: Search for information about a movie.
>   - **Example**: `movie:Inception`
> 
> - **`music:`**: Search for information about music or a song.
>   - **Example**: `music:Bohemian Rhapsody`
> 
> - **`related:`**: Find sites related to a specified URL.
>   - **Example**: `related:cnn.com`
> 
> ## Usage Examples
> 
> 1. **Combining Modifiers**: Use multiple modifiers to refine your search even further.
>    - **Example**: `site:nytimes.com climate change after:2022-01-01 intitle:report`
>    
> 2. **Filtering Results by Date and Location**:
>    - **Example**: `loc:france wine production after:2020-01-01`
> 
> 3. **Finding Specific File Types on a Site**:
>    - **Example**: `site:example.com report filetype:pdf`
> 
> By using these Bing search modifiers, you can tailor your search queries to find the most relevant and specific information.
> 
