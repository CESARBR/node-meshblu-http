# Meshblu HTTP
A node package to use the Meshblu HTTP API...

[![Build Status](https://travis-ci.org/CESARBR/node-meshblu-http.svg?branch=master)](https://travis-ci.org/CESARBR/node-meshblu-http)
[![npm version](https://badge.fury.io/js/%40cesarbr%2Fmeshblu-http.svg)](https://badge.fury.io/js/%40cesarbr%2Fmeshblu-http.svg)

# Usage
### Install:
```shell
npm install --save @cesarbr/meshblu-http
```

### Use:
```javascript
var MeshbluHttp = require('@cesarbr/meshblu-http');

var meshbluHttp = new MeshbluHttp();

meshbluHttp.register({}, function(error, response) {
  // code goes here
})
```

# Functions
### Constructor
| Parameter | Type   | Required| Description                          |
| ----------| -------| --------| -------------------------------------|
| options   | object | no      | can contain any of these keys: bearerToken, uuid, token, hostname, port, protocol, domain, service, secure, resolveSrv, auth |
------------------------------------------
```javascript
var meshbluHttp = new MeshbluHttp({uuid: 'fancy_uuid', token: 'fancy_token'})
var meshbluHttp = new MeshbluHttp({bearerToken: 'some-bearer-token'})
```

### Authenticate
| Parameter | Type   | Required| Description                          |
| ----------| -------| --------| -------------------------------------|
| callback  |function| yes     | a function that returns error and response |
------------------------------------------
```javascript
meshbluHttp.authenticate(function(error, response) {
  // code goes here
})
```

### Create Hook
| Parameter | Type   | Required| Description                          |
| ----------| -------| --------| -------------------------------------|
| uuid      | string | yes     | a string containing the uuid         |
| type      | string | yes     | a string containing the type         |
| url       | string | yes     | a string containing the url          |
| callback  |function| yes     | a function that returns error          |
------------------------------------------
```javascript
meshbluHttp.createHook('fancy_uuid', 'fancy_token', 'fancy_url', function(error) {
  // code goes here
})
```

### Create Subscription
| Parameter | Type   | Required| Description                          |
| ----------| -------| --------| -------------------------------------|
| options   | object | yes     | an object containing three keys: subscriberUuid, emitterUuid, and type |
| callback  |function| yes     | a function that returns error and response |
------------------------------------------
```javascript
meshbluHttp.createSubscription(
  {
    subscriberUuid: 'fancy_uuid',
    emitterUuid: 'another_fancy_uuid',
    type: 'fancy_type'
  },
  function(error, response){
    // code goes here
  }
)
```

### Delete Subscription
| Parameter | Type   | Required| Description                          |
| ----------| -------| --------| -------------------------------------|
| options   | object | yes     | an object containing three keys: subscriberUuid, emitterUuid, and type |
| callback  |function| yes     | a function that returns error and response |
------------------------------------------
```javascript
meshbluHttp.deleteSubscription(
  {
    subscriberUuid: 'fancy_uuid',
    emitterUuid: 'another_fancy_uuid',
    type: 'fancy_type'
  },
  function(error, response){
    // code goes here
  }
)
```

### Delete Subscriptions
| Parameter | Type   | Required| Description                          |
| ----------| -------| --------| -------------------------------------|
| options   | object | yes     | an object containing three keys: subscriberUuid, emitterUuid, and type. Type and emitterUuid are optional and will be used to filter the subscriptions to delete. |
| callback  |function| yes     | a function that returns error and response |
------------------------------------------
```javascript
meshbluHttp.deleteSubscriptions(
  {
    subscriberUuid: 'fancy_uuid',
    emitterUuid: 'another_fancy_uuid',
    type: 'fancy_type'
  },
  function(error, response){
    // code goes here
  }
)
```

### Device
| Parameter | Type   | Required| Description                          |
| ----------| -------| --------| -------------------------------------|
| uuid      | string | yes     | a string containing the uuid of the device |
| metadata  | object | no      | an object containing metadata information |
| callback  |function| yes     | a function that returns error and response |
------------------------------------------
```javascript
meshbluHttp.device('fancy_uuid', {as: 'another_user_uuid'}, function(error, response){
  // code goes here
})
```

### Devices
| Parameter | Type   | Required| Description                          |
| ----------| -------| --------| -------------------------------------|
| query     | object | no      | an object containing the keys you want to search for |
| metadata  | object | no      | an object containing metadata information |
| callback  |function| yes     | a function that returns error and response |
------------------------------------------
```javascript
meshbluHttp.devices({type: 'drone'}, {as: 'another_user_uuid'}, function(error, response){
  // code goes here
})
```

### Find And Update
| Parameter | Type   | Required| Description                          |
| ----------| -------| --------| -------------------------------------|
| uuid      | string | yes     | a string containing the uuid of the device |
| params    | object | yes     | an object containing the new changes to the device |
| metadata  | object | no      | an object containing metadata information |
| callback  |function| yes     | a function that returns error and response |
------------------------------------------
```javascript
meshbluHttp.findAndUpdate('fancy_uuid', {type: 'new-type'}, function(error, response){
  // code goes here
})
```

### Generate And Store Token
| Parameter | Type   | Required| Description                          |
| ----------| -------| --------| -------------------------------------|
| uuid      | string | yes     | a string containing the uuid of the device |
| callback  |function| yes     | a function that returns error and response |
------------------------------------------
```javascript
meshbluHttp.generateAndStoreToken('fancy_uuid', function(error, response){
  // code goes here
})
```

### Generate And Store Token With Options
| Parameter | Type   | Required| Description                          |
| ----------| -------| --------| -------------------------------------|
| uuid      | string | yes     | a string containing the uuid of the device |
| options   | object | no      | an object containing the options for the token |
| callback  |function| yes     | a function that returns error and response |
------------------------------------------
```javascript
meshbluHttp.generateAndStoreTokenWithOptions('fancy_uuid', {expiresOn: '1485452874'},
  function(error, response){
    // code goes here
  }
)
```

### Generate Key Pair
| Parameter | Type   | Required| Description                          |
| ----------| -------| --------| -------------------------------------|
| none      |  |      |          |
------------------------------------------
```javascript
meshbluHttp.generateKeyPair()
```

### Health Check
| Parameter | Type   | Required| Description                          |
| ----------| -------| --------| -------------------------------------|
| callback  |function| yes     | a function that returns error, healthy, and code |
------------------------------------------
```javascript
meshbluHttp.healthcheck(function(error, healthy, code){
  // code goes here
})
```

### Message
| Parameter | Type   | Required| Description                          |
| ----------| -------| --------| -------------------------------------|
| message   | object | yes     | an object containing the message to send |
| metadata  | object | no      | an object containing metadata information |
| callback  |function| yes     | a function that returns error and response |
------------------------------------------
```javascript
meshbluHttp.message({data: 'hello_message'}, function(error, response){
  // code goes here
})
```

### My Devices
| Parameter | Type   | Required| Description                          |
| ----------| -------| --------| -------------------------------------|
| query     | object | no      | an object containing your query      |
| callback  |function| yes     | a function that returns error and response |
------------------------------------------
```javascript
meshbluHttp.mydevices({type: 'drone'}, function(error, response){
  // code goes here
})
```

### Public Key
| Parameter | Type   | Required| Description                          |
| ----------| -------| --------| -------------------------------------|
| uuid      | string | yes     | a string containing the uuid of the device |
| callback  |function| yes     | a function that returns error and response |
------------------------------------------
```javascript
meshbluHttp.publicKey('fancy_uuid', function(error, response){
  // code goes here
})
```

### Register
| Parameter | Type   | Required| Description                          |
| ----------| -------| --------| -------------------------------------|
| options   | object | yes     | an object containing properties that you would like your device to have. Can be empty object|
| callback  |function| yes     | a function that returns error and response |
------------------------------------------
```javascript
meshbluHttp.register({color: 'blue'}, function(error, response){
  // code goes here
})
```

### Reset Token
| Parameter | Type   | Required| Description                          |
| ----------| -------| --------| -------------------------------------|
| uuid      | string | yes     | a string containing the uuid of the device |
| callback  |function| yes     | a function that returns error and response |
------------------------------------------
```javascript
meshbluHttp.resetToken('fancy_uuid', function(error, response){
  // code goes here
})
```

### Revoke Token
| Parameter | Type   | Required| Description                          |
| ----------| -------| --------| -------------------------------------|
| uuid      | string | yes     | a string containing the uuid of the device |
| token     | string | yes     | a string containing the token of the device |
| callback  |function| yes     | a function that returns error and response |
------------------------------------------
```javascript
meshbluHttp.revokeToken('fancy_uuid', 'fancy_token', function(error, response){
  // code goes here
})
```

### Revoke Token By Query
| Parameter | Type   | Required| Description                          |
| ----------| -------| --------| -------------------------------------|
| uuid      | string | yes     | a string containing the uuid of the device |
| query     | object | yes     | an object containing your query      |
| callback  |function| yes     | a function that returns error and response |
------------------------------------------
```javascript
meshbluHttp.revokeTokenByQuery('fancy_uuid', {expiresOn: '1485452874'},
  function(error, response){
    // code goes here
  }
)
```

### Search
| Parameter | Type   | Required| Description                          |
| ----------| -------| --------| -------------------------------------|
| query     | object | yes     | an object containing your query      |
| metadata  | object | yes     | an object containing metadata information. Can be left empty |
| callback  |function| yes     | a function that returns error and response |
------------------------------------------
```javascript
meshbluHttp.search({type: 'drone'}, {as: 'another_uuid'},
  function(error, response){
    // code goes here
  }
)
```

### Search Tokens
| Parameter | Type   | Required| Description                          |
| ----------| -------| --------| -------------------------------------|
| query     | object | yes     | an object containing your query      |
| metadata  | object | yes     | an object containing metadata information. Can be left empty |
| callback  |function| yes     | a function that returns error and response |
------------------------------------------
```javascript
meshbluHttp.searchTokens({expiresOn: '1485452874'}, {as: 'another_uuid'},
  function(error, response){
    // code goes here
  }
)
```

### Set Private Key
| Parameter | Type   | Required| Description                          |
| ----------| -------| --------| -------------------------------------|
| privateKey| string/object | yes     | a string or object containing your privateKey  |
------------------------------------------
```javascript
meshbluHttp.setPrivateKey(privateKey)
```

### Sign
| Parameter | Type   | Required| Description                          |
| ----------| -------| --------| -------------------------------------|
| data      | object | yes     | an object containing the data you want to sign your privateKey with |
------------------------------------------
```javascript
meshbluHttp.sign(data)
```

### Subscriptions
| Parameter | Type   | Required| Description                          |
| ----------| -------| --------| -------------------------------------|
| uuid      | string | yes     | a string containing the uuid of the device |
| metadata  | object | no      | an object containing metadata information |
| callback  |function| yes     | a function that returns error and response |
------------------------------------------
```javascript
meshbluHttp.subscriptions('fancy_uuid', {as: 'another_uuid'},
  function(error, response){
    // code goes here
  }
)
```

### Unregister
| Parameter | Type   | Required| Description                          |
| ----------| -------| --------| -------------------------------------|
| device    | object | yes     | an object containing the device credentials |
| callback  |function| yes     | a function that returns error and response |
------------------------------------------
```javascript
meshbluHttp.unregister({uuid: 'abc', token: 'asd'}, function(error, response){
  // code goes here
})
```

### Update
| Parameter | Type   | Required| Description                          |
| ----------| -------| --------| -------------------------------------|
| uuid      | string | yes     | a string containing the uuid         |
| params    | object | yes     | an object containing the new changes to the device |
| metadata  | object | no      | an object containing metadata information |
| callback  |function| yes     | a function that returns error and response |
------------------------------------------
```javascript
meshbluHttp.update('fancy_uuid', {color: 'green'}, function(error, response){
  // code goes here
})
```

### Verify
| Parameter | Type   | Required| Description                          |
| ----------| -------| --------| -------------------------------------|
| message   | string/object | yes     | data for encrypting                  |
| signature | string | yes     | this can be obtained from sign()     |
------------------------------------------
```javascript
meshbluHttp.verify(message, signature)
```

### Whoami
| Parameter | Type   | Required| Description                          |
| ----------| -------| --------| -------------------------------------|
| callback  |function| yes     | a function that returns error and response |
------------------------------------------
```javascript
meshbluHttp.whoami(function(error, response){
  // code goes here
})
```
