# OpenWhisk Starter Overview

# Preparation

1. Go to the creation page of Watson Language Translator service using [this](https://console.ng.bluemix.net/catalog/services/language-translator) link or search for "translator" in the Bluemix catalog 

2. Click on the "Create" button to add the new service

# Creating the action

1. Go to the [OpenWhisk editor](https://console.ng.bluemix.net/openwhisk/editor) and create a new action (use the default settings) with any name of your choosing

2. Replace the main function with the one below -

```
function main(params) {
	//translateTo values can be any one of the supported 62 languages
	return { payload: params['id'], translateTo: "fr" };
}
```

# Creating the sequence

1. Click on the action you created earlier and then click on "Link into a Sequence"

2. Scroll down and choose "Watson Translator" and then choose "translator" under "Select an Action in this Package"

3. Click on the Green "New Binding" on the bottom left, provide a name for the binding and select the instance of Watson Translator you created earlier

4. Click on "Add to Sequence" and "This Looks Good"

5. Finally click on "Save Action Sequence" (you can change the sequence name if you like) to finish creating the sequence

# Seeing it in action

1. Select the sequence you just created and click on "Run this Sequence"

2. Provide the following JSON input -

```
{
    "id": "Hello"
}
```

3. Finally, click on "Run with this Value" and you should see the translated *Bonjour* response

# Creating the trigger

1. Select the sequence you created in the previous step and then click on "Automate this Action"

2. Choose "Cloudant Changes" and then click on the Green "New Trigger"

3. Provide a name for the trigger and proceed to select the instance of Cloudant you created earlier (note that it selected the "phrases" dbname by default since that is the only one available)

4. Click on "Save Configuration" and "Next"

5. Finally, click on the "This Looks Good" button and "Save Rule" (you can change the rule name if you like)


# Testing the whole flow

1. Go to the [monitor screen](https://console.ng.bluemix.net/openwhisk/dashboard) and note the Activity Log on the right

2. Go to the web applicaton you created in the [previous lab](https://github.com/amirkeren/bluemix-lab1) and proceed to add a new phrase

3. Refresh the Activity Log and you should see the entire sequence was triggered due to the change in the "phrases" DB and the translation of the new phrase you added appears as the output
