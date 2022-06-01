# Apps Script TriggerHandler

TriggerHandler for easily manipulating time-based triggers with Google Apps Script for any task that is taking longer usually.

If the task is taking longer than usual, make it hang in the queue and go ahead. Do not stop :p 


## Install as a Google Apps Script Library

Script ID:  
```sh
1yHp1htl1hq2Vvh6pU5Re11UgDFUqxtgy88ByR20iq0hJiUHgX-jhByMs
```

This is probably the easiest way to use TriggerHandler and ensure you are always using the latest version.

NOTE: If you use it as a library, you must use the library name first, as all libraries are automatically namespaced:
```
TriggerHandler // Using it as a library
```

## Manual Install Into Your Own Google Apps Script

If you don't want to use a Library file and need the script to be local within your own project, Create a new file named `TriggerHandler.gs` in your Google Apps Script project. Copy the contents of `TriggerHandler.gs` into that file.

## Important

Ideally, we cannot pass a parameter when a function is launched from a trigger.

We have to store this information somewhere to allow script find it. For example, here, we are storing the information in `PropertiesService.getScriptProperties()` by storing triggerId

And when we need to retrieve the arguments, we pass the trigger id and get the argument list.



## Install Trigger and Set Arguments 

- Note : Need to pass parameters inside array only.

```javascript
const ONE_MINUTE = 60 * 1000;

const trigger = ScriptApp.newTrigger("runTrigger").timeBased()
    .after(ONE_MINUTE)
    .create();

setupTriggerArguments(trigger, ["Maulik", "Surat", "Searce"], false);
```

## Running Trigger

The name specified as argument in newTrigger() is run here and we can get trigger arguments 

```javascript
function runTrigger(event) {
  const functionArgs = getTriggerArguments(event.triggerUid);
  const [name, city, org] = functionArgs;
  console.log(name);
  console.log(city);
  console.log(org);
}
```
