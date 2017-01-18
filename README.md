# bluemix-lab2

#Preparation

1. Go to your [dashboard](https://console.ng.bluemix.net/dashboard/services) and click on the Cloudant NoSQL DB you created in the [previous lab](https://github.com/amirkeren/bluemix-lab1)
2. Click on "Service Credentials" then on "New Credential" and finally click "Add" (this will later allow OpenWhisk to connect to that DB instance)

#Creating the action

1. Go to the [OpenWhisk editor](https://console.ng.bluemix.net/openwhisk/editor) and create a new action (use the default settings) with any name of your choosing
2. Replace the main function with the one below -

```
function main(params) {
	return { student_added: params['id'] };
}
```

#Creating the trigger

1. Select the action you created in the previous step on the left and then click on "Automate this Action"
2. Choose "Cloudant Changes" and then click on the green "New Trigger"
3. Provide a name for the trigger and proceed to select the instance of the Cloudant you created earlier (note that it selected the "students" dbname by default since that is the only one we have available)
4. Click on "Save Configuration" and "Next"
5. Finally, click on the "This Looks Good" button and "Save Rule" (you can change the rule name if you like)

#Test the flow

1. 
