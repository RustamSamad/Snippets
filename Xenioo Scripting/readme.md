# Xenioo Scripting
Xenioo cloud scripting action uses Javascript as a server side scripting language to extend even further your chatbot functions. 
Here you can find some examples of how Xenioo Cloud scripting can be used to create higly dynamic chatbot contents.

In addition to standard JavaScript functions and objects, Xenioo's cloud scripting also provides the global conversation object, which supports the following methods.


## GetVariable
This method will return the current value of a specified variable. If the variable does not exist, an empty string is returned.
```javascript
conversation.GetVariable( variablename );
```  
---
## SetVariable  
This method will update the value of a variable with a given name. Multiple overloads are available for additional call details.
```javascript
conversation.SetVariable( variablename, variablevalue );
conversation.SetVariable( variablename, variablevalue, setmode );
conversation.SetVariable( variablename, variablevalue, replacewith, setmode );
```  

The **setmode** parameter defines the mode used to update the target variable. You can use the followin table as a reference for the parameter.  

|value|mode|
|-----------------|-----------------|
|0|Default. The value will be overwritten|
|1|Append. The value wil be added to the end of the current value|
|2|Concatenate. The value wil be added to the end of the current value, separated by a comma|
|3|Add. Xenioo will attempt to sum the given value to the current value of the variable|
|4|Subtract. Xenioo will attempt to subtract the given value from the current value of the variable|
|5|Divide. Xenioo will attempt to divide current value of the variable by the given value|
|6|Multiply. Xenioo will attempt to multiply current value of the variable by the given value|
|7|ReplaceString. All occurences of the given value inside the current value will be replaced by replacewith value|
|8|RemoveString. The given value will be removed from the current variable value|
|9|ClearValue. The current value of the variable will be set to an empty string value|
---
## SetTag  
This method will create a new tag and attach it to the current conversation.
```javascript
conversation.SetTag( tagname );
```  
---
## DropTag  
This method will drop a specified tag from the current conversation. No error is returned if the tag does not exist.
```javascript
conversation.DropTag( tagname );
```  
## HasTag
This method will check the existance of specific tag and return true if found otherwise false.
```javascript
conversation.HasTag( tagname );
```  
---
## GoTo  
This method will redirect the conversation to the behaviour specified in targetbehaviour and the interaction specified in targetinteraction. If targetinteraction is empty or null, the convesation will be redirected to the start interaction of targetbehaviour.
Conversation will be redirected as soon as the script action completes. No additional operations or actions will be executed, even if child of the current scripting action.
```javascript
conversation.GoTo( targetbehaviour, targetinteraction );
```  
---
## GetNextRandom  
This method can generate a random integer number randing from min to max value (both included).
```javascript
conversation.GetNextRandom( minvalue, maxvalue );
```  
---
## Log  
This method will log a user text to the current chat execution diagram. The log will be displayed as system, following the standard script action logging.
```javascript
conversation.Log( text );
```  
---
## LogIssue  
This method will log an issue text to the current chat execution diagram. The log will be displayed as system, following the standard script action logging. An issue text is displayed with an alert and a red color accent.
```javascript
conversation.Log( text );
```  
---
## AddReplyPart  
This method will add a new reply part to the current conversation block. You can use this method to add new text or advanced controls to the current conversation. The added parts are volatile and will not become part of the runtime chatbot build design.
This method has multiple overloads that can be used to further define you action.

```javascript
conversation.AddReplyPart( text );
conversation.AddReplyPart( type, text, command );
conversation.AddReplyPart( type, text, command, commandvariable );
conversation.AddReplyPart( type, text, command, commandvariable, targetbehaviour, targetinteraction );
```  
The **type** parameter defines the tipe of chat content that the method should add to the current conversation. Refer to the table below for a list of all types supported bu this method.

|Type value|Content Type|
|-----------------|-----------------|
|0|Text
|1|Quick Button
|3|Image
|6|Question (Blocking)
|9|Video
|10|Audio
|11|File
|17|Url
---
## XmlToJSon  
This method will try to parse a given XML source text and transform it into a valid JSON representation. The JSON representation can then be transformed to an ojbect instance using standard JavaScript parse method.

```javascript
conversation.XmlToJSon( xmlsource );
```
---
## Connect  
Returns a virtual Firebase database instance that can be further used to manipulate remote data. You can [find here all methods](firebase.md) supprted by the returned connection.

```javascript
conversation.Connect( accountjson, projectid, databasename );
```
---
