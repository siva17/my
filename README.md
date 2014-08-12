my
==

JavaScript Framework for Hybrid and Web App development

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
		```{
			"logInBuffer" : variable,
			"buildType" : 1 to 4 values,
			"logLevel" : integer value
		}```
  * *logInBuffer* : 
  * *buildType* : Possible values are 1 to 4 1 with all Logs enable and 4 with only exception logs enabled.
  * *logLevel* : Possible value is combination of following options
	- EXCEP = 0x01
	- ERROR = 0x02
	- WARN  = 0x04
	- INFO  = 0x08
	- FLOW  = 0x10
	  As the values are Bit wise enabled values, can pass combination of it.
	  For example if needs to enable WARN and ERROR, the can pass value (0x02 | 0x04)
