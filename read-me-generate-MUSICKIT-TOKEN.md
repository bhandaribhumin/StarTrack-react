user need to create .env file and create one variable
REACT_APP_MUSICKITTOKEN = YOUR_TOKEN 

YOUR_TOKEN : token is for get data from musickit api.
##How to generate token?
1) REF: https://developer.apple.com/documentation/applemusicapi/getting_keys_and_creating_tokens

## Get Problem to generate token?

1) create file: 
musickit-token-encoder.js 

paste below code

```
"use strict";

const fs = require("fs");
const jwt = require("jsonwebtoken");
// AuthKey_ID.p8: download from developer apple
const privateKey = fs.readFileSync("AuthKey_ID.p8").toString();
const teamId = "YOUR_TEAM_ID";
const keyId = "YOUR_KEY_ID";

const jwtToken = jwt.sign({}, privateKey, {
    algorithm: "ES256",
    expiresIn: "180d",
    issuer: teamId,
    header: {
        alg: "ES256",
        kid: keyId
    }
});

console.log(jwtToken);
```
Run using command 
> node musickit-token-encoder.js

