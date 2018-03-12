# API Gateway Modules

## Lambda Method

Creates an API Gateway Method that calls a Lambda function as a Lambda Proxy (passing through headers and body automatically).

Name Suffix: *ApiGatewayLambdaMethod*

### Properties:
#### Mandatory:
* HttpMethod
* ResourceId
* RestApiId
* Function: Will automatically append `LambdaFunction` to match the Lambda Module.

#### Optional:
* AuthorizationType
* AuthorizerId

### Example

```yaml
CreateMethod:
  From: ApiGateway::LambdaMethod
  Properties:
    HttpMethod: PUT
    ResourceId: !Ref CreateResource
    RestApiId: !Ref RestApi
    Function: CreateEvent
```

## Resources

Splits given paths and creates API Gateway Resources for you matching the path. This makes it easy to create a complex set of
APIG resources with just a few lines. It uses the path name and the suffic to name your resources so you can reference them
later in the Methods. Make sure each path name is unique, otherwise resources will be overwritten.

Name Suffix: *ApiGatewayResource*

### Properties:
#### Mandatory:
* RootId
* RestApiId

### Example

The following example will create 8 resources and a path that branches away after the `d` resource.

```yaml
APIResources:
  From: Apigateway::Resources
  Properties:
    Paths:
      - a/b/{c}/d/e/f
      - a/b/{c}/d/g/h
    Root: !GetAtt MyRestApi.RootResourceId
    RestApiId: !Ref MyRestApi
```