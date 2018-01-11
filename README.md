# strangelove
Postman collection for easy Mulesoft CH API use

To generate the encrypted value for encPassword in the Postman environment, run the below;


```$ printf "myPasswordIs" | openssl enc -e -base64 -A -aes-256-cbc -pass pass:"secret key 123"```

Paste the output into the Postman environment variable encPassword

Note: This is not a secure password store as the JS script needs to know the pass used to encrypt the password. It will help prevent passby eyes only password theft
