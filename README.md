# StyleApiVariables.ado


## Pipeline Requirements

The setVariable pipeline requires the following parameters to be defined:
Paramaters:


| Name  | type | Default | Values | Opional/Required | Comments |
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
| enableApiAndWebsiteVariables | boolean | 'false' | 'true'/'false' | Required | This is a Boolean value to define whether to use this template or not  |
| enableWebsiteVariables | boolean | 'false' | 'true'/'false' | Required | This is a Boolean value to define whether to use this template or not  |
| enableStyleAPIVariables  | boolean | 'false' | 'true'/'false' | Required | This is a Boolean value to define whether to use this template or not  |
| websiteAppServiceNames | string | | | Optional | |
| websiteArchivePattern | string | | | Optional | |
| websiteExtractFolder | string | | | Optional | |
| websitePackageId | string | | | Optional | |
| websitePacakgeVersion | string | | | Optional | |
| websiteImage | string | | | Optional | |
| websiteAKSApps | string | | | Optional | |
| websiteAKSAppsForBlueGreen | string | | | Optional | |
| websiteWorkloadName | string | | | Optional | |
| product.name | string | | | Required | |

  These parameters provide multiple use case options for the setvariables templates pipeline, enable/disable flags for the utilization of different templates as per the requirements.


## Use Cases



### Direct use of templates

You can directly call a particular template as per the requirement. for example: 

```yaml

 # azure-pipeline.yml
  resources:
  repositories:
    - repository: Template
      type: github
      name: your_username/ADO.Pipelines.Templates
      ref: <respective branch name>
      endpoint: 'githubServiceConnectioNname'


  - template: frameWork/common/setVariables/SetStyleApiVariables.yml@Template
      parameters:
        ${{ insert }}: ${{ parameters }}
        apiArchivePattern: styleapi-party.$(build.configVersion).*
        apiExtractFolder: $(build.configVersion)/styleapi-party
        apiPackageId: styleapi-party
        apiPacakgeVersion: $(build.configVersion)

  ```

The parameters are provided to configure the setVariables pipeline according to the desired build configuration and stages.

Make sure to adjust the repository name, branch name, and parameter values according to your project's requirements.

