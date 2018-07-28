# Ballerina Crypto Utility Functions

This Ballerina extension is created due to some issues regarding generating HMAC with Base64 encoded keys. More can be read here:
1. https://groups.google.com/forum/#!topic/ballerina-dev/ROqBZFWltS4


Generating HMAC using plain text key:

```ballerina
import ballerina/io;
import in2/crypto;

function main(string[] args) {
  string stringToSign = "test";
  string signingKey = "test";

  string result = crypto:hmac(stringToSign, signingKey, crypto:SHA256);
  io:println(result);
}
```

Generating HMAC using Base64 encoded key:

```ballerina
import ballerina/io;
import in2/crypto;

function main(string[] args) {
  string stringToSign = "test";
  string signingKey = "dGVzdA==";

  string result = crypto:hmac(stringToSign, signingKey, crypto:SHA256, keyType = crypto:BASE64);
  io:println(result);
}
```