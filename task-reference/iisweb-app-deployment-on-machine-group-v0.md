---
title: IISWebAppDeploymentOnMachineGroup@0 - IIS web app deploy v0 task
description: Deploy a website or web application using Web Deploy.
ms.date: 03/20/2025
monikerRange: "<=azure-pipelines"
author: juliakm
ms.author: jukullam
---

# IISWebAppDeploymentOnMachineGroup@0 - IIS web app deploy v0 task

<!-- :::description::: -->
:::moniker range="<=azure-pipelines"

<!-- :::editable-content name="description"::: -->
Use this task to deploy a website or web application using Web Deploy.
<!-- :::editable-content-end::: -->

:::moniker-end
<!-- :::description-end::: -->

<!-- :::syntax::: -->
## Syntax

:::moniker range="<=azure-pipelines"

```yaml
# IIS web app deploy v0
# Deploy a website or web application using Web Deploy.
- task: IISWebAppDeploymentOnMachineGroup@0
  inputs:
    WebSiteName: # string. Required. Website Name. 
    #VirtualApplication: # string. Virtual Application. 
    Package: '$(System.DefaultWorkingDirectory)\**\*.zip' # string. Required. Package or Folder. Default: $(System.DefaultWorkingDirectory)\**\*.zip.
  # Advanced Deployment Options
    #SetParametersFile: # string. SetParameters File. 
    #RemoveAdditionalFilesFlag: false # boolean. Remove Additional Files at Destination. Default: false.
    #ExcludeFilesFromAppDataFlag: false # boolean. Exclude Files from the App_Data Folder. Default: false.
    #TakeAppOfflineFlag: false # boolean. Take App Offline. Default: false.
    #AdditionalArguments: # string. Additional Arguments. 
  # File Transforms & Variable Substitution Options
    #XmlTransformation: false # boolean. XML transformation. Default: false.
    #XmlVariableSubstitution: false # boolean. XML variable substitution. Default: false.
    #JSONFiles: # string. JSON variable substitution.
```

:::moniker-end

<!-- :::syntax-end::: -->

<!-- :::inputs::: -->
## Inputs

<!-- :::item name="WebSiteName"::: -->
:::moniker range="<=azure-pipelines"

**`WebSiteName`** - **Website Name**<br>
`string`. Required.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Specifies the name of an existing website on the machine group machines.
<!-- :::editable-content-end::: -->
<br>

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="VirtualApplication"::: -->
:::moniker range="<=azure-pipelines"

**`VirtualApplication`** - **Virtual Application**<br>
`string`.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Specifies the name of an already existing Azure Virtual application on the target machines.
<!-- :::editable-content-end::: -->
<br>

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="Package"::: -->
:::moniker range="<=azure-pipelines"

**`Package`** - **Package or Folder**<br>
`string`. Required. Default value: `$(System.DefaultWorkingDirectory)\**\*.zip`.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Specifies the file path to the package or folder generated by MSBuild or a compressed archive file. Variables ( [Build](/azure/devops/pipelines/build/variables) | [Release](/azure/devops/pipelines/release/variables#default-variables)) and wildcards are supported. For example, `$(System.DefaultWorkingDirectory)\**\*.zip`.
<!-- :::editable-content-end::: -->
<br>

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="SetParametersFile"::: -->
:::moniker range="<=azure-pipelines"

**`SetParametersFile`** - **SetParameters File**<br>
`string`.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Optional. Specifies the location of the `SetParameters.xml` file to use.
<!-- :::editable-content-end::: -->
<br>

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="RemoveAdditionalFilesFlag"::: -->
:::moniker range="<=azure-pipelines"

**`RemoveAdditionalFilesFlag`** - **Remove Additional Files at Destination**<br>
`boolean`. Default value: `false`.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Selects the option to delete files on the Web App that have no matching files in the Web App zip package.
<!-- :::editable-content-end::: -->
<br>

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="ExcludeFilesFromAppDataFlag"::: -->
:::moniker range="<=azure-pipelines"

**`ExcludeFilesFromAppDataFlag`** - **Exclude Files from the App_Data Folder**<br>
`boolean`. Default value: `false`.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Selects the option to prevent files in the `App_Data` folder from being deployed to the Web App.
<!-- :::editable-content-end::: -->
<br>

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="TakeAppOfflineFlag"::: -->
:::moniker range="<=azure-pipelines"

**`TakeAppOfflineFlag`** - **Take App Offline**<br>
`boolean`. Default value: `false`.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Selects the option to take the Web App offline by placing an `app_offline.htm` file in the root directory of the Web App before the sync operation begins. The file will be removed after the sync operation completes successfully.
<!-- :::editable-content-end::: -->
<br>

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="AdditionalArguments"::: -->
:::moniker range="<=azure-pipelines"

**`AdditionalArguments`** - **Additional Arguments**<br>
`string`.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Specifies additional Web Deploy arguments that are applied when deploying the Azure Web App. For example, `-disableLink:AppPoolExtension` or `-disableLink:ContentExtension`.

For a list of Web Deploy arguments, see [Web Deploy Operation Settings](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd569089(v=ws.10)).
<!-- :::editable-content-end::: -->
<br>

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="XmlTransformation"::: -->
:::moniker range="<=azure-pipelines"

**`XmlTransformation`** - **XML transformation**<br>
`boolean`. Default value: `false`.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Specifies the config transforms that are run for `*.Release.config` and `*.<EnvironmentName>.config` on the `*.config file`. Config transforms are run prior to the Variable Substitution. XML transformations are only supported on Windows.
<!-- :::editable-content-end::: -->
<br>

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="XmlVariableSubstitution"::: -->
:::moniker range="<=azure-pipelines"

**`XmlVariableSubstitution`** - **XML variable substitution**<br>
`boolean`. Default value: `false`.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Specifies the variables defined in the build or release pipeline. These variables are matched against the `key` or `name` entries in the appSettings, applicationSettings, and connectionStrings sections of any config file and `parameters.xml`. Variable Substitution is run after config transforms.

*Note:* If the same variables are defined in the release pipeline and in the environment, then the environment variables will supersede the release pipeline variables.
<!-- :::editable-content-end::: -->
<br>

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="JSONFiles"::: -->
:::moniker range="<=azure-pipelines"

**`JSONFiles`** - **JSON variable substitution**<br>
`string`.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Specifies a new line separated list of JSON files to substitute the variable values. File names must be relative to the root folder.

To substitute JSON variables that are nested or hierarchical, specify them using JSONPath expressions. For example, to replace the value of `ConnectionString` in the sample below, you must define a variable as `Data.DefaultConnection.ConnectionString` in the build or release pipeline (or in the release pipeline's stage).

```
{  
  "Data": {  
    "DefaultConnection": {  
      "ConnectionString": "Server=(localdb)\SQLEXPRESS;Database=MyDB;Trusted_Connection=True"  
    }  
  }  
}
```
 Variable Substitution is run after configuration transforms.

*Note:* Pipeline variables are excluded in substitution.
<!-- :::editable-content-end::: -->
<br>

:::moniker-end
<!-- :::item-end::: -->

### Task control options

All tasks have control options in addition to their task inputs. For more information, see [Control options and common task properties](/azure/devops/pipelines/yaml-schema/steps-task#common-task-properties).
<!-- :::inputs-end::: -->

<!-- :::outputVariables::: -->
## Output variables

:::moniker range="<=azure-pipelines"

None.

:::moniker-end
<!-- :::outputVariables-end::: -->

<!-- :::remarks::: -->
<!-- :::editable-content name="remarks"::: -->
## Remarks

Use this task to deploy a website or web app using WebDeploy.
<!-- :::editable-content-end::: -->
<!-- :::remarks-end::: -->

<!-- :::examples::: -->
<!-- :::editable-content name="examples"::: -->
<!-- :::editable-content-end::: -->
<!-- :::examples-end::: -->

<!-- :::properties::: -->
## Requirements

:::moniker range="<=azure-pipelines"

| Requirement | Description |
|-------------|-------------|
| Pipeline types | Classic release |
| Runs on | Agent, DeploymentGroup |
| [Demands](/azure/devops/pipelines/process/demands) | None |
| [Capabilities](/azure/devops/pipelines/agents/agents#capabilities) | This task does not satisfy any demands for subsequent tasks in the job. |
| [Command restrictions](/azure/devops/pipelines/security/templates#agent-logging-command-restrictions) | Any |
| [Settable variables](/azure/devops/pipelines/security/templates#agent-logging-command-restrictions) | Any |
| Agent version |  2.104.1 or greater |
| Task category | Deploy |

:::moniker-end

<!-- :::properties-end::: -->

<!-- :::see-also::: -->
<!-- :::editable-content name="seeAlso"::: -->
<!-- :::editable-content-end::: -->
<!-- :::see-also-end::: -->
