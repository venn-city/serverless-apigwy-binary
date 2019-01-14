# serverless-apigwy-binary

[Serverless framework](https://www.serverless.com) plugin to configure Binary responses in API Gateway

Original code from [codebox](https://github.com/craftship/codebox-npm/blob/master/.serverless_plugins/content-handling/index.js)

## Installation

Install to your Serverless project via npm

```bash
$ npm install --save serverless-apigwy-binary
```

## Usage

Add the plugin to your `serverless.yml`
The plugin assumes you have `apiGateway.restApiId` configuration in your serverless.yml, it won't work otherwise. 

```yaml
# serverless.yml

plugins:
  - serverless-apigwy-binary
```

Add the property `contentHandling: CONVERT_TO_BINARY` to an HTTP event

```yaml
# serverless.yml
provider:
  name: aws
    apiGateway:
      restApiId: {YOUR_REST_API_ID}
      restApiRootResourceId: {YUOR_ROOT_RESOURCE_ID}  
  ...
  functions:
    hello:
      handler: handler.hello
      events:
        - http:
            integration: lambda
            path: hello
            method: get
            contentHandling: CONVERT_TO_BINARY
```
