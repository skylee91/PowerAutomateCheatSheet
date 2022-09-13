# Power Automate Cheat Sheet
A cheat sheet for Microsoft Power Automate ( last known as Microsoft Flow) or Microsoft Logic Apps

## Get value

### From variable
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


### From trigger
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







## References
https://docs.microsoft.com/en-us/azure/logic-apps/workflow-definition-language-functions-reference
