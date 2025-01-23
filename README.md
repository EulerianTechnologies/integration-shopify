# ![Eulerian logo](/img/eulerian_logo.png) 
# Install Eulerian on your Shopify store
### Structure of this repository
Only files in config and snippets directory are needed for the installation
### Prerequisites
* Your website in Eulerian should be already setup
* Your tracking subdomain should be fully functional, you will need to specify it in your custom settings_schema.json file
### Note
The installation varies wether you have a **Basic** or **Plus** plan on your Shopify account. The **Basic** installation only has one extra step to properly track the checkout tunnel.
## Steps
### 1. Adding the settings panel. 
You need to navigate to Config/settings_schema.json and open it in the editor. To do that follow Online Store -> Themes -> Actions -> Edit code:

At this point, scroll down the code folders to locate the Config folder, locate the settings_schema.json file and edit it by double clicking on it.
In the editor, **locate the last closing curly bracket**. 

At this point, add a comma after the closing curly bracket, copy the code below and paste it into the editor:

  ```json

  {
    "name": "Eulerian Technologies",
    "settings": [
      {
        "type": "text",
        "id": "tracking_subdomain",
        "label": "Tracking subdomain",
        "info": "If you don't know it, contact your Eulerian Consultant"
      },
      {
        "type": "checkbox",
        "id": "eulerian_enabled",
        "label": "Enable",
        "default": false,
        "info": "Check to enable Eulerian tracking"
      }
    ]
  }
	
  ```
This code can also be found, in the config folder of this repository, in the file setting_schema.json. 

Don't forget to save your modifications.

### 2. Configuring the module
Go to the configuration panel which has been created with the step 1. You can do that via Online Store -> Themes -> Customize

You'll see a new entry in the Theme settings menu.

Click on it and you'll get to the Eulerian Technologies configuration panel you just added in the previous step.

Paste your tracking subdomain in the according text input, check the Enable button, and save your changes.

### 3. Adding the container
1. Navigate this repository to snippets/eulerian-tag.liquid 
2. Copy the content of the file into the clipboard.
3. Go back to the Theme Code edit section, as you did in Step 1. 
4. Scroll to Snippets -> Add a new snippet and create a snippet with exactly the same filename as the file  in the repository, i.e. "eulerian-tag.liquid" 
5. Paste the code in the editor and save
	
### 4. Adding the datalayer
Create a new snippets, much the same way as you did in "Adding the container" step, using the content of this repository's file Snippets/ea_datalayer.liquid

Use the exact same filename "ea_datalayer.liquid"
### 5a. Including the setup on the pages and checkout tunnel - Shopify **Plus**
Go back to the Theme Code edit section, as you did in Step 1.
1. Scroll to Layout. You'll see the layout files.
2. Copy the following two lines into the clipboard

	```twig
		<!-- inclusion of Eulerian -->
		{% include 'eulerian-tag' %}  
	```
3. Paste the code in the theme.liquid and checkout.liquid templates, just above the closing ```</body>``` tag and save the layout:

### 5b. Including the setup on the checkout tunnel - Shopify **Basic**
Go back to the Theme Code edit section, as you did in Step 1.
1. Scroll to Layout. You'll see the layout files. Typically you'll have theme.liquid
2. Copy the following two lines into the clipboard

	```twig
		<!-- inclusion of Eulerian -->
		{% include 'eulerian-tag' %}  
	```
3. Paste the code in the theme.liquid template, just above the closing ```</body>``` tag and save the layout:

4. Go to Admin->Settings->Checkout as shown below
	
5. In the Checkout section, scroll down to "Order Processing" and paste the code of the snippet ea_datalayer_checkout_basic.liquid into the field "additional scripts" as shown below:

6. Manually edit this line at the very beginning of the code to replace 'dem.eulerian.net' with your own tracking subdomain:

	```twig
		{% assign ea_tracking_subdomain = "dem.eulerian.net" %}
	```
7. Scroll down and save

**Congratulations! You have installed Eulerian in your Shopify store !**
		
## Licence
See the LICENCE file for details.
