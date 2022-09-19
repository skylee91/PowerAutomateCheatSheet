# Power Automate Cheat Sheet
A cheat sheet for Microsoft Power Automate (last known as Microsoft Flow) or Microsoft Logic Apps

- [Power Automate Cheat Sheet](#power-automate-cheat-sheet)
  * [Get Value](#get-value)
    + [From Variable](#from-variable)
    + [From Trigger](#from-trigger)
    + [From Output](#from-output)
  * [Connectors](#connectors)
    + [SharePoint REST API](#sharepoint-rest-api)
      - [GetFolderByServerRelativeUrl](#getfolderbyserverrelativeurl)
      - [GetFileByUrl + Properties](#getfilebyurl--properties)
      - [GetFileByServerRelativePath + Properties](#getfilebyserverrelativepath--properties)
  * [References](#references)


[<small><a href='http://ecotrust-canada.github.io/markdown-toc/'>Table of contents generated with markdown-toc</a></small>]

## Get Value

### From Variable
e.g. you have intialized a variable of `object` type
```
{
  "Photo": {
    "Format": "image/jpeg"
  }
}
```
`variables('varValidationRule')?['Photo']?['Format']`
OR
`variables('varValidationRule')?['Photo/Format']`


### From Trigger
e.g. you have a trigger, 
When a new response is submitted

`triggerOutputs()?['body/resourceData/responseId']`

OR you can use `triggerBody()` a shorthand for

`triggerBody()?['resourceData/responseId']`


### From Output

`body('Parse_JSON')?['driveId']`

`body('Send_an_HTTP_request_to_SharePoint')`

`outputs('Compose')`

`equals(outputs('Compose')?['ApplyFor'], 'Myself')`

`if(equals(outputs('Compose')?['ApplyFor'], 'Myself'), '', outputs('Compose')?['ApplicantEmail'])`


## Connectors

### SharePoint REST API

#### GetFolderByServerRelativeUrl

`https://tenant.sharepoint.com/sites/SiteName/_api/web/GetFolderByServerRelativeUrl('Shared%20Documents/Apps/Microsoft%20Forms/filename.jpg')`

#### GetFileByUrl + Properties

`https://tenant.sharepoint.com/sites/SiteName/_api/Web/GetFileByUrl(@url)/Properties?@url='https://tenant.sharepoint.com/sites/SiteName/Shared%20Documents/Apps/Microsoft%20Forms/filename.jpg'`

#### GetFileByServerRelativePath + Properties

`https://tenant.sharepoint.com/sites/SiteName/_api/Web/GetFileByServerRelativePath(decodedurl='/sites/SiteName/Shared%20Documents/Apps/Microsoft%20Forms/filename.jpg')/Properties`


## References
https://docs.microsoft.com/en-us/azure/logic-apps/workflow-definition-language-functions-reference
