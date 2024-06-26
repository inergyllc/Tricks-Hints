# Tricks-Hints
Coding tricks and hints for the perplexed

# Linking External Folders to a Visual Studio Project

> **Modify Project File (Optional for more control):**
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

