# bluemix-lab2

#Preparation

1. Go to your [dashboard](https://console.ng.bluemix.net/dashboard/services) and click on the Cloudant NoSQL DB you created in the [previous lab](https://github.com/amirkeren/bluemix-lab1)
2. Click on "Service Credentials" then on "New Credential" and finally click "Add" (this will later allow OpenWhisk to connect to that DB instance)

#Creating the action

1. Go to the [OpenWhisk editor](https://console.ng.bluemix.net/openwhisk/editor) and create a new action (use the default settings)
2. Replace the main function with the one below -

```
function main(params) {
	return { student_added: params['id'] };
}
```

#Creating the trigger

1. 
