# OpenWhisk Starter Overview

# Preparation

1. Go to your dashboard and click on the Cloudant NoSQL DB you created in the previous lab

2. Click on "Service Credentials" then on "New Credential" and finally click "Add" (this will allow OpenWhisk to connect to that DB instance)

3. Go to the creation page of Watson Language Translator service using [this](https://console.ng.bluemix.net/catalog/services/language-translator) link or search for "translator" in the Bluemix catalog 

4. Click on the "Create" button to add the new service

# Creating the mediating actions

1. Go to the [OpenWhisk editor](https://console.ng.bluemix.net/openwhisk/editor) and create a new action (use the default settings) with any name of your choosing

2. Replace the main function with the one below -

```
function main(params) {
	//translateTo values can be any one of the supported 62 languages
	//in this case we use French ("fr") but you can choose any of the other supported ISO 639-1 codes
	return { payload: params['id'], translateTo: "fr" };
}
```

Note that the changes are auto-saved but not live. In order to publish them you will need to click the "Make it Live" button on the bottom right

1. Create yet another new action, same as before and replace the main function with the one below - 

```
function main(params) {
	return { doc: { _id: params.payload } };
}
```

# Creating the sequence

1. Next, click on "Link into a Sequence"

2. Scroll down and choose "Watson Translator" and then choose "translator" under "Select an Action in this Package"

3. Select the Blue "Language Translator" binding on the bottom left

4. Click on "Add to Sequence" (note the flow of the sequence) and then click on "This Looks Good" to confirm

5. Finally click on "Save Action Sequence" (you can change the sequence name if you like) and "Done" to finish creating the sequence

# Seeing it in action

1. Select the sequence you just created uner "My Sequences" and click on "Run this Sequence"

2. Provide the following JSON input -

```
{
    "id": "Hello"
}
```

Finally, click on "Run with this Value" and you should see the translated *Bonjour* response

# Creating the trigger

1. Select the sequence you created in the previous step again and then click on "Automate"

2. Choose "Cloudant Changes" and then click on the Green "New Trigger"

3. Provide a name for the trigger and proceed to select the instance of Cloudant you created earlier (note that it selected the "phrases" dbname by default since that is the only one available)

4. Click on "Save Configuration" and "Next" (note that the new flow now includes the trigger as well)

5. Finally, click on the "This Looks Good" button and "Save Rule" (you can change the rule name if you like)


# Testing the whole flow

1. Go to the [monitor screen](https://console.ng.bluemix.net/openwhisk/dashboard) and note the Activity Log on the right

2. Go to the web applicaton you created in the [previous lab](https://github.com/amirkeren/bluemix-lab1) and proceed to add a new phrase

3. Refresh the Activity Log and you should see the entire sequence was triggered due to the change in the "phrases" DB and the translation of the new phrase you added appears as the output
