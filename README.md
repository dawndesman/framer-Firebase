

# framer-Firebase

The **Firebase module** allows your Framer prototype to **load**, **save** and **sync** data effortlessly between multiple sessions and devices.
<br />

## Demo Projects

| Simple                                                           | Advanced                                                          |
| :---:                                                            | :---:                                                             |
| ![gif](http://i.giphy.com/l0K40AVo2PF0usMuY.gif)                 | ![gif](http://i.giphy.com/3o7qE5fsbV3QqzyOZi.gif)                 |
| Loads, saves and syncs *slider.value* w/ 2 lines of code         | World's first(?) bubble popping MMO                               |
| Live @ [firebaseSlider](https://framer.cloud/ljPWN/)             | Live @ [firebaseBubbles](https://framer.cloud/Pfkqn)              |

| Placeholder                                                      | Advanced                                                          |
| :---:                                                            | :---:                                                             |
| ![png](http://i.imgur.com/DJt6U3a.png)                           | ![gif](http://i.giphy.com/l0K4lktvDV129Jl8k.gif)                  |
|                                                                  | *Like*-counts, three of them                                      |
|                                                                  | Live @ [firebaseLikes](https://framer.cloud/vrEdo)                |

These examples include access to a public demo database for the purpose of demonstration.
> **Please DON'T use this demo database for your projects! Your data will be deleted.**

<br />

## Getting started in under 5 minutes

I'd also like to recommend reading [*Supercharge your Framer prototype with Firebase, pt.1*](https://medium.com/@marc_krenn/framerfirebase1-e7d13a939cf4) on Medium, if you haven't already.

| Step    | Instruction                                                                                                                                                                                                            |
| :---:   | :---                                                                                                                                                                                                                   |
| **1**   | Download the [Firebase module](https://github.com/marckrenn/framer-Firebase/archive/master.zip) and unzip the downloaded archive                                                                                       |
| **2**   | Put `firebase.coffee` into your prototype's `modules`-folder or *drag'n'drop* it onto the Framer window                                                                                                                |
| **3**   | Add or change the autogenerated `require`-line to `{Firebase} = require 'firebase'`                                                                                                                                    |
| **4**   | Reload (*CMD+R*) or save (*CMD+S*) your project to get Framer to load the module                                                                                                                                       |
| **-!-** | Or start by using this [template file](http://share.framerjs.com/ltqk90uuqym2/)                                                                                                                                        |
| **5**   | Go to https://firebase.google.com → *Login* → *Console* → *Create New Project*                                                                                                                                         |
| **6**   | Back in Framer, add `firebase = new Firebase` and set the required [Class Properties](https://github.com/marckrenn/framer-Firebase#1-properties)                                                                       |
| **7**   | Save, load and sync data using the available [Class Methods](https://github.com/marckrenn/framer-Firebase#2-methods). Also, check out the [Demo Projects](https://github.com/marckrenn/framer-Firebase#demo-projects). |


### Tips

| Tip   |                                                                                                                                                                                                                                     |
| :---: | :---                                                                                                                                                                                                                                 |
| **1** | You can use a single database to store data for multiple Framer prototypes.                                                                                                                                                         |
| **2** | Use https://firebase.google.com → *Console* → *YourProject* → *Database* to see realtimes changes made to your database. This will give you a better understanding of how Firebase methods alter your data.                       |
| **3** | Framer's *Auto Refresh* can cause some unwanted behavior in combination with this module, hence why I'd suggest turning it off and to reload manually (*CMD+R*).                                                                   |
| **4** | Anti-Virus software like [Avast](https://www.avast.com) seem to interfere with the **.onChange()**-method, as it looks like a potential Cross-Site-Scripting-attack. [This will hopefully be fixed soon by the Firebase team.](http://i.imgur.com/DeX4Pok.png) |
| **5** | Try to limit **put**- / **post**- / **patch**- serverrequests to a reasnobable refresh rate (either by syncing at the end of interaction or by using [Utils.debounce](https://github.com/koenbok/Framer/blob/master/framer/Utils.coffee#L100)). Data flooding can cause severe lags. |


### Data
Data on Firebase is stored as **JSON**, the *supported data types* are: *Number*, *String*, *Boolean*, *Array*, *Object* and *Null*.
For more information on *JSON data types*, please refer to the [JSON article on Wikipedia.org](https://en.wikipedia.org/wiki/JSON#Data_types.2C_syntax_and_example).

The database used for the provided [Demo Projects](https://github.com/marckrenn/framer-Firebase#demo-projects) looks something like this:
![database](http://i.imgur.com/7e40dX5.png)


### Contact & Help
If you need further assistance or want to leave me some feedback, <br />
you can reach me via [Twitter](https://twitter.com/marc_krenn), [Facebook](https://www.facebook.com/groups/framerjs/permalink/1111435055650231/) or [Slack](https://framer-slack-signup.herokuapp.com/).

<br />
---
---
<br />

## Firebase Class Reference
This module is based on [Firebase's REST API](https://firebase.google.com/docs/reference/rest/database/).

| Table of contents                                                                                                                                       |
| :---                                                                                                                                                    |
| [**1) Properties**](https://github.com/marckrenn/framer-Firebase#1-properties)                                                                          |
| \|--- [firebase**.projectID**, **.secret**](https://github.com/marckrenn/framer-Firebase#-firebaseprojectid-firebasesecret)                             |
| \|--- [firebase**.secret**](https://github.com/marckrenn/framer-Firebase#-firebasesecret)                                   |
| \|--- [firebase**.debug**](https://github.com/marckrenn/framer-Firebase#-firebasedebug)                                                                |
| \|--- [firebase**.status**](https://github.com/marckrenn/framer-Firebase#-firebasestatus-read-only)                                                     |
| [**2) Methods**](https://github.com/marckrenn/framer-Firebase#2-methods)                                                                                |
| \|--- [firebase**.get**()](https://github.com/marckrenn/framer-Firebase#-firebasegetpath-callback-parameters)                                           |
| \|--- [firebase**.put**()](https://github.com/marckrenn/framer-Firebase#-firebaseputpath-data-callback-parameters)                                      |
| \|--- [firebase**.post**()](https://github.com/marckrenn/framer-Firebase#-firebasepostpath-data-callback-parameters)                                    |
| \|--- [firebase**.patch**()](https://github.com/marckrenn/framer-Firebase#-firebasepatchpath-data-callback-parameters)                                  |
| \|--- [firebase**.delete**()](https://github.com/marckrenn/framer-Firebase#-firebasedeletepath-callback--parameters)                                    |
| \|--- [firebase**.onChange**()](https://github.com/marckrenn/framer-Firebase#-firebaseonchangepath-or-connection-callback)                              |
| [**3) Parameters**](https://github.com/marckrenn/framer-Firebase#3-parameters)                                                                          |
| \|--- [**OrderBy**- and **Limit**-parameters](https://github.com/marckrenn/framer-Firebase#-orderby--and-limit--paramters)                              |

<br />
<br />

### 1) Properties

#### • firebase.projectID, firebase.secret
---
The property **projectID** is required for the module to work.

**secret** is now an optional property and it can be either set (see below) or it can be substitued by [changing your database access rules](https://github.com/marckrenn/framer-Firebase#-firebasesecret).

The required information is located at https://firebase.google.com → *Console* → *YourProject* → ...

```coffee
firebase = new Firebase
	projectID: ___________ # 1) ... Database → first part of URL
	secret: ______________ # 2) ... Project Settings → Service Accounts → Database Secrets → Show (mouse-over)
```
  

| 1) projectID                                                 | 2) secret                                                     |
| :---:                                                        | :---:                                                         |
| ![gif for ants I](http://i.giphy.com/xT4uQFz8q6HAHKkfi8.gif) | ![gif for ants II](http://i.giphy.com/3o6ZtnLC6wkxSZLY0U.gif) |

> **Protip:** Contrary to what I did in the gif, I advise you **NOT** to share your Firebase *secret* publicly, as it allow others to alter the data stored in your database. If you do so by accident, you can always revoke access by deleting the shared *secret* and creating a new one at https://firebase.google.com → *Console* → Project Settings → Service Accounts → Database Secrets.

<br />

#### • firebase.secret
---
**Optional**:
If you wish not to use and share your database *secret* in your Framer project like [shown above](https://github.com/marckrenn/framer-Firebase#-firebaseprojectid-firebasesecret), you can do the following instead:

| Steps |                                                                                                                                                                                                                                            |
| :---: | :---                                                                                                                                                                                                                                        |
| **1** | Go to *Console* → *YourProject* → *Database* → *RULES*                                           |
| **2** | Change the rules of `.read` and `.write` to `true` like this:                                    |

```json
{
  "rules": {
    ".read": "true",
    ".write": "true"
  }
}
```

| Step |                                                                                                                                                                                                                                             |
| :---: | :---                                                                                                                                                                                                                                       |
| **3** | If you've already set the *secret*-property before, you can remove it as it's no longer needed. |

> **Caution:** Similar to sharing your database secret key publicly, this will grant everyone on the web with write-access, which will allow everyone to read and modify data saved in your database! Please only share your projects (and Firebase projectIDs) with people you trust.  

<br />

#### • firebase.debug
---
If set to **true**, relevant connection messages will be logged to the console.

<br />

#### • firebase.status (*read only*)
---
Returns the current connection status, either *"connected"* or *"disconnected"*.

<br />


### 2) Methods
---
**Overview**

| Method                                                                                                             | Arguments                              | Use case                       |
| ---:                                                                                                               | :---                                   | :---                           |
| [firebase**.get**](https://github.com/marckrenn/framer-Firebase#-firebasegetpath-callback-parameters)              | (path, callback, *parameters*)         | Retreives data                 |
| [firebase**.put**](https://github.com/marckrenn/framer-Firebase#-firebaseputpath-data-callback-parameters)         | (path, data, *callback*, *parameters*) | Writes / updates data          |
| [firebase**.post**](https://github.com/marckrenn/framer-Firebase#-firebasepostpath-data-callback-parameters)       | (path, data, *callback*, *parameters*) | Writes data using a random key |
| [firebase**.patch**](https://github.com/marckrenn/framer-Firebase#-firebasepatchpath-data-callback-parameters)     | (path, data, *callback*, *parameters*) | Updates data                   |
| [firebase**.delete**](https://github.com/marckrenn/framer-Firebase#-firebasedeletepath-callback--parameters)       | (path, *callback*,  *parameters*)      | Deletes data                   |
| [firebase**.onChange**](https://github.com/marckrenn/framer-Firebase#-firebaseonchangepath-or-connection-callback) | (path or "connection", callback)       | Monitors / syncs data          |

> **Protip:** As a beginner, you can ignore separated *callback*-functions and *parameters*.

<br />

| Note  |                                                                                                                                              |
| :---: | :---                                                                                                                                         |
| **1** | **Sent** and **received** data is either **plain** (single value) or **JSON encoded** (dataset)                                              |
| **2** | The use of the *parameters*-argument requires a *callback*-function to be set                                                                |
| **3** | The otherwise optional *callback*-function always returns a server response confirming the request                                           |
| **4** | Multiple *paramters* can be set by using curly braces (eg. ` firebase.get("/values", callback, {parameter1: true, parameter2: 3})`)          |


<br />

#### • firebase.get(path, callback, *parameters*)
---
Retrieves data from the database.

**Examples:**
```coffee
# Simple 1, expecting single value
firebase.get "/value", (value) ->
	print value

# Simple 2, expecting dataset
firebase.get "/names", (names) ->
	namesArray = _.toArray(names) # converts JSON to array
	print name for name in namesArray

# Advanced
response = (names) ->
	namesArray = _.toArray(names)
	print name for name in namesArray

firebase.get("/names",response,{orderBy: "$key", limitToFirst: 5})

```
<br />

#### • firebase.put(path, data, *callback*, *parameters*)
---
Writes data to the database.

If the *path* **does not** exist, it will be created, if it **does** exist, the specified node will be updated with the new data.

The following data types are supported: *Number*, *String*, *Boolean*, *Array*, *Object* and *Null*. <br />
For more information on *JSON data types*, please refer to the [JSON article on Wikipedia.org](https://en.wikipedia.org/wiki/JSON#Data_types.2C_syntax_and_example).

**Tip:** To update data without deleting omitted *children*- or *sibling*-nodes, use [firebase.patch()](https://github.com/marckrenn/framer-Firebase#-firebasepatchpath-data-callback-parameters) instead.

**Examples:**
```coffee

# Simple
firebase.put("/value", true)

# Advanced
response = (confirmation) ->
	print confirmation

firebase.put("/values", {"foo": true, "bar": false}, response)

```
<br />


#### • firebase.post(path, data, *callback*, *parameters*)
---
Adds data to the specified *path* using a random key (eg. `"/addressBook/-KIU9s3bWOpODk9cai_n/"`).

This is useful when adding new data to a node (eg. adding a new entry to an address book).
The random key also prevents possible data interference between multiple, concurrent users.

The following data types are supported: *Number*, *String*, *Boolean*, *Array*, *Object* and *Null*. <br />
For more information on *JSON data types*, please refer to the [JSON article on Wikipedia.org](https://en.wikipedia.org/wiki/JSON#Data_types.2C_syntax_and_example).

**Examples:**
```coffee

# Simple
firebase.post("/value", true)

# Advanced
firebase.post("/addressBook", { # JSON encoded:
							"name" : 	{
										"forename" : "Jane",
										"surename" : "Doe"
										}

							"birthday" : 	{
											"day"  : 4,
											"month": 7,
											"year" : 1976
											}

							"tel" : "202-555-0101"
							})

```
<br />


#### • firebase.patch(path, data, *callback*, *parameters*)
---
Updates data of the specified *path*, without deleting omitted *sibling*-nodes.

**Example:**
```coffee

firebase.patch("/values/foo", false) # `/values/bar´ persists

```
<br />


#### • firebase.delete(path, *callback*,  *parameters*)
---
Deletes the node and *children* of the specified *path*.

**Example:**
```coffee

firebase.delete("/values")

```
<br />


#### • firebase.onChange(path or "connection", callback)
---

**Monitoring a database path:** <br />
Fires, when the Framer project is loaded (returns all current data of the path) and whenever some of its data was changed (returns only the newly added or changed data), across multiple devices or browser windows. If it returns *null*, the node has been deleted.

**Example:**
```coffee

# Simple
firebase.onChange "/values", (value) ->
	print value

# Advanced
response = (data, method, path, breadcrumbs) ->
	# method returns either `put´ or `patch´, depending on what method changed the data
	# path returns the path that was changed
	# breadcrumbs returns the path as segments (array)
	print "received #{data} via #{method}"

firebase.onChange("/values", response)

```
<br />


**Monitoring the connection status:** <br />
First argument must be set to *"connection"*. <br />
Fires, whenever the connection status to Firebase has changed.

**Example:**
```coffee

firebase.onChange "connection", (status) ->
	# status is either `connected´ or `disconnected´
	print "Hooray, we're connected to Firebase" if status is "connected"

# Or

firebase.onChange "connection" -> print "Current connection status: #{firebase.status}"

```
<br />


### 3) Parameters:
---

**Available parameters:**

| Parameter | Value     | Type       | Compatible w/                                                    | Description                                                                                                                       |
| ---:      | :---      | :---       | :---                                                             | :---                                                                                                                              |
| shallow:  | true      | *Boolean*  | **.get**()                                                       | Returns the data of the specified node without its *children*. **Note:** *Shallow* cannot be mixed with any other parameters      |
| print:    | "pretty"  | *String*   | **.get**(), **.put**(), **.post**(), **.patch**(), **.delete**() | Returns the data in a human-readable format                                                                                       |
| print:    | "silent"  | *String*   | **.get**(), **.put**(), **.post**(), **.patch**()                | Surpresses response from the Firebase server, virtually identical to not setting a callback function                              |
| format:   | "export"  | *String*   | **.get**()                                                       | Include priority information in the response                                                                                      |
| download: | *path*    | *String*   | **.get**()                                                       | Will trigger a download if pointed to a file stored on the Firebase server (*YourProject* → *Console* → *Storage*)                |

#### • *OrderBy*- and *Limit*-parameters:
---
For further information on how to order or limit requests please refer to [Firebase REST Guide / Retriving data](https://www.firebase.com/docs/rest/guide/retrieving-data.html).


##### *orderBy*-parameter
---
| Parameter | Type       | Description                                                                                       |
| ---:      | :---       | :---                                                                                              |
| orderBy:  | *String*   | *"$key"* requires an index to be set at *Console* → *Database* → *Rules*. See example below.      |

**Indexing example:**

```JSON

{
	"rules": 	{
				".read": "auth != null",
				".write": "auth != null",
				"routes": {".indexOn": ["distance"]}
				}
}

```
<br />

##### *Limit*-paramters
---
> **Note:** *Limit*-parameters require the *orderBy*-parameter to be set.

| Parameter     | Type       |
| ---:          | :---       |
| limitToFirst: | *Number*   |
| limitToLast:  | *Number*   |
| startAt:      | *Number*   |
| endAt:        | *Number*   |
| equalTo:      | *Number*   |

