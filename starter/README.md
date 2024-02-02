# Project Instructions

1. Open Azure CloudShell
1. Select `Bash`
1. You'll need to first create your storage account first time you launch the CloudShell. 
1. Leave the subscription the lab assigns you selected
1. Click advanced
1. Select Create New for the storage account and give the storage account a name such as `tscottoudacityazure`
1. Select Create New for the file share  and give the file share a name such as `tscottoudacityfile`
1. Click Create storage
2. Run the following in CloudShell: `git clone https://github.com/udacity/azure-api-management`
1. You'll be prompted for your github username and password
3. Navigate to the project starter folder `cd azure-api-management/starter`
1. Make the script executable `chmod +x setup.sh`
1. Run `./setup.sh`
1. The script will output a URL of the weather app. This is our backend of our API. Copy this URL. It will look something like this https://WeatherDataAPId72d5e4a32.azurewebsites.net/swagger/v1/swagger.json If you loose your URL you can find it by searching the Azure portal for "weatherdataapi" selecting the web app and copying the URL. Do not forget to append `/swagger/v1/swagger.json`
1. Now proceed with completing your tasks for the project and take screenshots of each step
    1. Create an API instance via PowerShell
    1. Import the weather API into API management using the OpenAPI standard
    1. Perform a GET operation on the API (such as `GetTodaysWeather`). Use 1 and 1 for the latitude and longitude. It does not actually check the weather so the numbers don’t really matter. Make sure you get a 200 response back indicating a successful response
    1. Apply policies that throttles traffic to the API to 3 calls every 50 seconds AND strips the following header from the API for ALL operations. 
        1. `X-Powered-By`
        1. Perform a test on any operation and show that the header has been removed from the response
        1. Use `context.Subscription.Id` as the counter key for throttling
        1. Perform a test to prove the throttling is working by performing 4 test operations quickly on any API endpoint
    1. Apply subscription authentication by assigning the API to a product called Udacity
        1. Perform the following curl test (change the URL to reflect your API) to prove the subscription authentication is working:
        ```
        curl -X GET https://udacity-tscotto.azure-api.net/weather  -H 'Ocp-Apim-Subscription-Key: <my-subscription-key>’
        ```
    1. Create an email alert when there are over 10 4xx alerts within a 1 minute period
        1. Test this alert by accessing an invalid path to your API 10 times in a row (generating a 404) and seeing the alert fire
1. Cleanup. Search for API management in the portal, find your API, select it and click delete