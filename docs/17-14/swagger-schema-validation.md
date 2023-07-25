## Introduction

Within [Connection Builder](https://support.airkit.com/docs/connection-builder), there is a Data Operation step that can perform a Swagger validation.  
The most direct use of this feature is in conjunction with the App API to validate incoming requests. If you have a Swagger file, you can use that Swagger file to ensure that incoming data is valid before proceeding onto your application logic.

If you're unfamiliar with the specifics of Swagger you can read more here: <https://swagger.io/>

## Steps

**This is an example of how to perform validation on an object structure, based on a given Swagger schema.**

1. Within Studio, go to Connection Builder and create a new Data Operation. ![1111032121.png](./assets_v1714/swagger-schema-validation-v1714-0.png)
2. In the Data Operation steps, change the first step type to "Swagger Schema Validation". **This step has three configuration values to setup.** ![1111032128.png](./assets_v1714/swagger-schema-validation-v1714-1.png)

 ![1122533379.png](./assets_v1714/swagger-schema-validation-v1714-2.png)

What each of these mean:

- **Swagger API**: This is the schema that defines how valid data should be structured. It is the definition to which data will be checked against. The input for this value is a json Swagger schema. Usually Swagger schemas are built in yaml; if you have a yaml Swagger schema you can translate it to json using a tool like this: <https://onlineyamltools.com/convert-yaml-to-json>
- **Object to Validate**: The data (a variable or result of variable operations) that should be checked and validated.
- **Object Schema**: The specific namespace or level within the Swagger Schema that should be used for validation.

### Follow these steps to configure and run the Swagger schema validation step

1. Paste the following example Swagger schema into the field "Swagger API":

```json JSON
{
      "openapi":
        "3.0.1",
      "info":
        {
          "title":
            "AirKit Swagger Schema validation example",
          "description":
            "A simple Swagger Schema example to validate against and learn how to use Swagger validation within Connection Builder",
          "contact":
            { "name": "Airkit Support", "url": "https://www.airkit.com/", "email": "support@airkit.com" },
          "version":
            "1.0.4"
        },
      "components":
        {
          "schemas":
            {
              "UserData":
                {
                  "required":
                    \[ "username", "email" \],
                  "type":
                    "object",
                  "properties":
                    {
                      "name":
                        { "type": "string", "description": "the name of the user" },
                      "username":
                        { "type": "string", "description": "the username of the user" },
                      "email":
                        { "type": "email", "description": "the email of the user" }
                    }
                }
            }
        }
    }

```



2. Paste the following example object to validate into the field "Object to Validate":

```json JSON
{ 
    "username": "dlerner", 
    "name": "Daniel", 
    "email": "daniel@airkit.com" 
}
```



3. Paste the following value within the "Obeject Schema" field:

"UserData"

4. Now hit "Play" on the Data Operation step and you should see the following result:

```javascript JSON
{
    "isValid": true,
    "errors": null
}
```



## Explanation and further examples

### What happened here?

The object defined in "Object to Validate" gets validated against the schema on "Swagger API". This is done using the namespace that's defined on "Object Schema". So in the above example we see that an object with username, name and email gets validated against the definition of the "UserData" that lives in the Swagger definition on `components.schemas.UserData`.

Since the object has all the required fields (username, email) then the result given is that the object is valid.

We can remove the field "name" from the object to validate and we won't get an error, since it's not a required field.

**Let's try a case that fails**, paste this object into the field "Object to Validate":

```json JSON
{ 
    "username": "dlerner", 
    "name": "Daniel"
}
```



Now run the Data Operation step... you should see the following error:

```json JSON
{
    "isValid": false,
    "errors": [{
        "keyword": "required",
        "dataPath": "",
        "schemaPath": "spec#/components/schemas/UserData/required",
        "params": {
            "missingProperty": "email"
        },
        "message": "should have required property 'email'"
    }]
}
```



There are two main results from this operation:

1. If there is _any_ error on the validation, **isValid** will be **false**; otherwise it will be **true**.
2. **errors** holds a list with the details of all errors found.

***



## References

- [Connection Builder](https://support.airkit.com/docs/connection-builder)