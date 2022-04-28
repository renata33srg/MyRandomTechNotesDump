# AWS Lambda

https://docs.aws.amazon.com/lambda/latest/dg/welcome.html

 - Lambda runs the function only when needed and scales automatically (from a few requests per day to thousands per second)  
 - Pricing schema is pay as you go (pay only for the compute time that is consumed, there is no charge when code is not running)  
 - Lambda functions can be invoked  using the Lambda API, or Lambda can run your functions in response to events from other AWS services  
 - Lambda is best suited for shorter, event-driven workloads, since Lambda functions run for up to 15 minutes per invocation  
 - You are responsible only for your code (because Lambda manages all computing resources, you cannot log in to compute instances or customize the operating system on provided runtimes)  

## Lambda Handler

The Lambda function handler is the method in your function code that processes events. When your function is invoked, Lambda runs the handler method. When the handler exits or returns a response, it becomes available to handle another event.  

### Function handler in Java  

>
> #### First Example - JSON Conversion
>
>> ```java
>> /*This handler receives an event as a JSON-formatted string and converts it into an object*/
>> package example;
>> import com.amazonaws.services.lambda.runtime.Context
>> import com.amazonaws.services.lambda.runtime.RequestHandler
>> import com.amazonaws.services.lambda.runtime.LambdaLogger
>> ...
>> 
>> // Handler value: example.Handler
>> public class Handler implements RequestHandler<Map<String,String>, String>{
>>   Gson gson = new GsonBuilder().setPrettyPrinting().create();
>>   @Override
>>   public String handleRequest(Map<String,String> event, Context context)
>>   {
>>     LambdaLogger logger = context.getLogger();
>>     String response = new String("200 OK");
>>     // Log execution details
>>     logger.log("ENVIRONMENT VARIABLES: " + gson.toJson(System.getenv()));
>>     logger.log("CONTEXT: " + gson.toJson(context));
>>     // Process event
>>     logger.log("EVENT: " + gson.toJson(event));
>>     logger.log("EVENT TYPE: " + event.getClass().toString());
>>     return response;
>>   }
>> }
>> ```
>>
>
> #### Second Example - Initialization code
> It's possible to add initialization code outside the handler method to reuse resources across multiple invocations. When the runtime loads the handler, it runs static code and the class constructor. Resources that are created during initialization stay in memory between invocations, and can be reused by the handler thousands of times. In the following example, the logger, serializer, and AWS SDK client are created when the function serves its first event. Subsequent events served by the same function instance are much faster because those resources already exist.  
>
>>```java
>> // Handler value: example.Handler
>> public class Handler implements RequestHandler<SQSEvent, String>{
>>   private static final Logger logger = LoggerFactory.getLogger(Handler.class);
>>   private static final Gson gson = new GsonBuilder().setPrettyPrinting().create();
>>   private static final LambdaAsyncClient lambdaClient = LambdaAsyncClient.create();
>>   ...
>>   @Override
>>   public String handleRequest(SQSEvent event, Context context)
>>   {
>>     String response = new String();
>>     // call Lambda API
>>     logger.info("Getting account settings");
>>     CompletableFuture<GetAccountSettingsResponse> accountSettings =
>>         lambdaClient.getAccountSettings(GetAccountSettingsRequest.builder().build());
>>     // log execution details
>>     logger.info("ENVIRONMENT VARIABLES: " + gson.toJson(System.getenv()));
>>     ...
>> ```
>>
>
  
### Function handler in Python  

>
> #### First Example - Returning a message
>
>> ```python
>> # This handler accepts an user input of a first and last name, and returns a message that contains data from the event it received as input
>> def lambda_handler(event, context):
>>     message = 'Hello {} {}!'.format(event['first_name'], event['last_name'])  
>>     return { 
>>         'message' : message
>>     }
>> ```
>>
>
> #### Second Example - Response parsing
>
>> ```python
>> # This handler uses event data passed by Lambda at runtime. It parses the environment variable in AWS_REGION returned in the JSON response.
>> import os
>> import json
>>          
>> def lambda_handler(event, context):
>>     json_region = os.environ['AWS_REGION']
>>     return {
>>         "statusCode": 200,
>>         "headers": {
>>             "Content-Type": "application/json"
>>         },
>>         "body": json.dumps({
>>             "Region ": json_region
>>         })
>>     }
>> ```
>>
>
> #### Third Example - Perform an increment action on a number
>
>> ```python
>> # This handler accepts an action and a single number, performs the specified action on the number, and returns the result. The only allowable action is 'increment'.
>> import logging
>> 
>> logger = logging.getLogger()
>> logger.setLevel(logging.INFO)
>> 
>> def lambda_handler(event, context):
>>     result = None
>>     action = event.get('action')
>>     if action == 'increment':
>>         result = event.get('number', 0) + 1
>>         logger.info('Calculated result of %s', result)
>>     else:
>>         logger.error("%s is not a valid action.", action)
>> 
>>     response = {'result': result}
>>     return response
>> ```
>>
>

## Lambda Context

When Lambda runs your function, it passes a context object to the handler. This object provides methods and properties that provide information about the invocation, function, and execution environment.  