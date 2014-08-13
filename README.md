my
==

JavaScript Component for Hybrid and Web App development

##APIs and Usage

### MY.Log
* MY.Log.flow(message);
* MY.Log.info(message);
* MY.Log.warn(message);
* MY.Log.error(message);
* MY.Log.exception(exception,message);
	* message   : string
	* exception : exception object.
* MY.Log.config(configParams)
  * *configParams* : Optional API Call and JSON Object with following JSON items
    ```
    {
       "logInBuffer" : variable,
       "buildType" : 1 to 4 values,
       "logLevel" : integer value
    }
    ```

  * *logInBuffer* : 
  * *buildType* : Possible values are 1 to 4 1 with all Logs enable and 4 with only exception logs enabled.
  * *logLevel* : Possible value is combination of following options
	- EXCEP = 0x01
	- ERROR = 0x02
	- WARN  = 0x04
	- INFO  = 0x08
	- FLOW  = 0x10
	- As the values are Bit wise enabled values, can pass combination of it.
	  For example if needs to enable WARN and ERROR, the can pass value (0x02 | 0x04)

### MY.Cache
* *available*: indicates whether current system support cache manifest mechanism
* *config* : JSON object will following callbacks
  ```
  {
      "cacheError" : callback,
      "cacheUpdate" : callback,
      "cacheChecking" : callback,
      "cacheInprogres" : callback,
      "cacheComplete" : callback
  }
  ```
  - *cacheError* : Callback called when cache Error.
  - *cacheUpdate* : Callback called when cache is updating. If this function returns false then a confirm message will be shown to user.
  - *cacheChecking* : Callback called when cache is checking.
  - *cacheInprogres* : Callback called when cache is in progress.
  - *cacheComplete* : Callback called when cache update is completed.

### MY.Connection
* sendRequest: After creating an instance of MY.Connection, can send the AJAX request
  - *config* : JSON object will following parameters and callbacks
    - *url* : URL value
    - *httpMethod* : HTTP method like, GET, POST, PUT, DELETE etc.
    - *postData* : JSON Data send as data in body for post method.
    - *headers* : JSON Object containing names of headers as Key and value.
    - *timeOut* : Connection Timeout value, if not passed will take as 30 seconds.
    - *onLoading* : Callback: when request is Loading.
    - *onLoaded* : Callback: when request is Loaded.
    - *onProgress* : Callback: when request in progress.
    - *onComplete* : Callback: When request is completed. User should use this to confirm request completion.
    - *onTimeOut* : Callback: When request is timedout.
    
  - For all Callbacks will get a object with following parameters.
    - *response* : Response data if any
    - *state* : HTTP State (0 to 4)
    - *httpCode* : HTTP Code like 200, 1xx, 2xx etc
    
* Usage: 
  ```
  var myAjaxRequest = new MY.Connection();
  if(myAjaxRequest) myAjaxRequest.sendRequest(config);
  ````
### MY Utility APIs
* *isNULL(obj)*: Returns true if obj is null.
* *isArray*: Returns true if object used is Array.
* *isEmpty(value,allowEmptyString)*: Returns true if value is NULL or empty.
* *isFunction(fun)*: Returns true if fun is function.
* *emptyFunction()*: General purpose empty function.
* *toNumber(value)*: Converts string to number.
* *validateEmail(email)*: Validates the Email and returns true or false.
* 
* *getKeys(obj)*: Returns the array of Keys of Object.
* *getKey(obj,value)*: Returns the Key of value in the object. Used for loop to get the key.
* *getValues(obj)*: Returns the array of values of the Object.
* 
* *createAsyncCallBack(scope,fn)*: Creates Async Callback function with provided scope and callback.
* *triggerAsyncCallBack(cb,data,timeout)*: Calls the Asyn Callback. cb is the return value of createAsyncCallBack.
* 
* *clonePropertiesFromSrc(obj1,obj2)*: Synanomous to MY.extend. obj1 will override any parameters in obj2.
* *getJSONObject(str)*: Converts JSON String to JSON object.
* *getJSONString(obj)*: Converts JSON object to JSON string.
* 
* *getBrowser*: Get the name of the Browser like Chrome, iPad, Opera, Safari, Firefox etc.
* *addEvent*: Add DOM events
* *createDomElement(config)*: Creates DOM element
* *addStyleTagToHead(src)*: Adds Style to Head.
* *addScriptTagToHead(src)*: Adds Scriptto Head.
* 
* *toggleSpinner*: Toggles the laoding spinner.
  - *state*: Optional, can pass the state as true or false.
  - *isWhite*: If true, then spinner will be white else gray.
* 
