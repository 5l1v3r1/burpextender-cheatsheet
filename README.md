* IBurpExtender  : Must Provide 

```python
class BurpExtender(IBurpExtender):
  def registerExtenderCallbacks(self,callbacks):
   ######## CODE HERE ###########
  return
  ```
  
* IBurpExtenderCallbacks : Pass in registerExtenderCallbacks Method .
```python
def registerExtenderCallbacks(self,callbacks):
```
> contains lot of feature's to build extension .

```python
  def registerExtenderCallbacks(self, callbacks):
	  self._callbacks = callbacks # CALLBACKS
	  self._callbacks.setExtensionName("NAME") # SET NAME OF EXTENSION
	  self._helpers = self._callbacks.getHelpers() # Use IExtensionHelpers Method , HELP FEATURE TO ADD FUNCTIONALITY TO EXTENSION 
    self._registerScannerCheck = self._callbacks.registerScannerCheck() # Used to Register Extension for scanner check
    self._applymarkers = self._callbacks.applyMarkers() # Used to Highlight or Mark Area's of Request's & Response 
    
    callbacks.registerHttpListener(self) # HTTP LISTENER
    
```

* IExtensionHelpers

```python
from burp import IExtensionHelpers #(optional) 

self._helpers = self._callbacks.getHelpers()

self._helpers.analyzeRequest() # HTTP REQUEST
self.helpers.analyzeResponse() # RESPONSE
self.helpers.urlEncode() # URL ENCODE 
self.helpers.bytesToString() # Converts data from array of bytes to String .

```

* IScannerCheck

```python
from burp import IScannerCheck

def consolidateDuplicateIssues(self,existingIssue,newIssue): # Check Mutiple issues for same URL 

def doActiveScan(self,baseRequestResponse,insertionPoint): # Invoked thisd method to active scan

def doPassiveScan(self,baseRequestResponse):
  return None
```
* IHttpListener 
```python
from burp import IHttpListener

callbacks.registerHttpListener(self)

def processHttpMessage(self,toolFlag,messageIsRequest,currentRequest):
```


IHttpRequestResponse – Representation of an HTTP message
IHttpService – Representation of an HTTP service, to which requests can be sent
IRequesetInfo – Representation of an HTTP request
IParameter – Representation of an HTTP request parameter





  
