# strangelove
Postman collection for easy Mulesoft CH API use

To generate the encrypted value for encPassword in the Postman environment, run the below;


```$ printf "myPasswordIs" | openssl enc -e -base64 -A -aes-256-cbc -pass pass:"secret key 123"```

Paste the output into the Postman environment variable encPassword

Note: This is not a secure password store as the JS script needs to know the pass used to encrypt the password. It will help prevent passby eyes only password theft

### Configuring Postman

* Create a new environment
* Add the below variables to the environment;

![alt text](https://github.com/StuartMule/strangelove/blob/master/PostmanEnvVariables.png "Postman variable requirements")
* Import the collection

### Usage

* To get a access token run the `Get AnypointPlatform Access Token` request. This uses your username and password variables to retrieve an access token which is set as an environment variable and used in the Authorization header for further requests.

* Run the `Get My Details` request. This request will set environment variables for all the Organisations you are a member of. For example, if you are a member of an org named Mulesoft, then a variable named MulesoftOrgID will be created.  This allows you to refer to this org in future requests by variable rather than UUID, i.e. `{{MulesoftOrgID}}` rather than `b3a42760-24f2-4b58-ba39-b0dfe88a89f3`.

* Run the `Get Environment Details` request (you will need to change the variable name in the URL to one corresponding to an orgs you are a member of that were created in the previous step). This request will set environment variables for all of the environments in your org. For example, if you have a Sandbox environment, a variable named SandboxEnvID will be created. This allows you to refer to this environment in future requests by variable rather than UUID, i.e. `{{SandboxEnvID}}` rather than `c6a9bd04-c39a-4fa2-91fe-aa35f5cd2e47`.

* This pattern repeats with other requests. Try the `List API's for my Org' next.
