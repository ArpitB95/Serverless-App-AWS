# Serverless_App_AWS


## What is Serverless ?
- Serverless is a cloud computing execution model where the cloud provider manages the infrastructure and automatically provisions and scales resources as needed. It allows developers to focus on writing and deploying code without worrying about server management.

- In a traditional server-based model, developers have to provision, configure, and manage servers to run their applications. With serverless, developers can write their code in the form of functions or services that are executed in a stateless manner, triggered by specific events or requests.


## Benefits of the serverless model:
- Event-driven execution: Functions or services are triggered by specific events such as HTTP requests, database changes, file uploads, or scheduled events.

- Automatic scaling: The cloud provider dynamically scales the resources based on the incoming workload, ensuring optimal performance and cost efficiency.

- Pay-per-use pricing: You only pay for the actual execution time and resources consumed by your functions or services, rather than paying for idle infrastructure.

- Managed infrastructure: The cloud provider takes care of server provisioning, maintenance, and operational tasks, allowing developers to focus on writing code.

- Backend services integration: Serverless architectures often leverage managed backend services like databases, storage, queues, and authentication services provided by the cloud provider.



## Serverless Framework:
- The Serverless Framework is an open-source framework that simplifies the development, deployment, and management of serverless applications. It provides a command-line interface (CLI) and a set of tools and abstractions to help developers build serverless applications across different cloud providers.

## Key features and benefits of the Serverless Framework include:

- Multi-cloud support: The Serverless Framework supports multiple cloud providers such as AWS, Azure, Google Cloud, and more. It allows you to write your serverless application code once and deploy it to different cloud environments without vendor lock-in.

- Application structure: The framework helps you organize your serverless application by providing a structure that separates functions, resources, and configuration. This makes it easier to manage and scale your application as it grows.

- Configuration as code: You can define your serverless application's infrastructure, function triggers, and other resources using a declarative configuration file (usually in YAML or JSON format). This enables infrastructure-as-code practices and version control for your application's configuration.

- Local development and testing: The Serverless Framework includes a local development environment that allows you to test and debug your serverless functions locally before deploying them to the cloud. This helps streamline the development and debugging process.

- Deployment automation: The framework automates the deployment process by handling the provisioning of cloud resources, packaging your application code, and setting up necessary permissions and event triggers. This simplifies the deployment workflow and reduces the chance of errors.

- Plugin ecosystem: The Serverless Framework has a rich plugin ecosystem that extends its capabilities. Plugins provide additional functionalities, integrations, and customization options, allowing you to tailor the framework to your specific needs.

- Monitoring and logging: The framework integrates with popular monitoring and logging services, making it easier to monitor the performance, errors, and logs of your serverless applications.


### In this project, I have deployed a task_master_app on AWS with serverless framework and deployed lambda function and dynamodb table. I have used Windows machine in this project.

- The Serverless Framework provisions the necessary AWS resources for your application based on your configuration. This can include creating and configuring resources such as API Gateway, S3 buckets, event triggers, IAM roles, and more
- Serverless eliminates the maintanance of instances and only runs when needed so also eliminates the cost.
- Integration with other AWS services: The Serverless Framework integrates with various AWS services, such as CloudFormation, CloudWatch, X-Ray, and more, to provide a seamless experience in managing and monitoring your serverless applications.



## STEPS:

- Download Node.JS (To run serverless framework)
   https://nodejs.org/en#home-downloadhead  (Install node.js into your local machine and set it's path as environment variable)
  
- Install NPM (npm comes with node.js package installer)
  Check version
  
```
   node -- version
   npm - version
```
    
- Install Serverless Framework
  Create an account on
  https://app.serverless.com/?view=register

  Now, run this command to install serverless
  ```
  npm install -g serverless
  ```
  
- Install AWS CLI
  https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html

  
- Configure AWS
  
  ```
  aws configure
  ```
  - Insert your AWS Access key and Secret key.
    
- Create serverless.yml file

```
org: your serverless framework account name
app: serverless-taskmaster-app
service: serverless-taskmaster-app

provider:
  name: aws
  region: eu-west-2
  runtime: nodejs14.x
  iamRoleStatements:
    - Effect: Allow
      Action:
        - dynamodb:*
      Resource:
        - arn:aws:dynamodb:eu-west-2:aws account number:table/KaamKaro
functions:
  hello:
    handler: src/hello.handler
    events:
      - httpApi:
          path: /hello
          method: get
  KaamBharo:
    handler: src/KaamBharo.handler
    events:
      - httpApi:
          path: /KaamBharo
          method: get

  KaamDikhao:
    handler: src/KaamDikhao.handler
    events:
      - httpApi:
          path: /KaamDikhao
          method: get

  KaamKhatamKaro:
    handler: src/KaamKhatamKaro.handler
    events:
      - httpApi:
          path: /KaamKhatamKaro
          method: get

resources:
  Resources:
    KaamKaro:
      Type: AWS::DynamoDB::Table
      Properties:
        TableName: KaamKaro
        BillingMode: PAY_PER_REQUEST
        AttributeDefinitions:
          - AttributeName: id
            AttributeType: S
        KeySchema:
          - AttributeName: id
            KeyType: HASH
```

- Login to your serverless by running
  
  ```
  serverless login
  ```


  ![serverless login](https://github.com/ArpitB95/Serverless_App_AWS/assets/110182832/9cb55a57-dc0f-4a9e-9514-b03112edc998)





- Open the given link in browser, you should get this login page




  ![serverless cli login](https://github.com/ArpitB95/Serverless_App_AWS/assets/110182832/1ae3818a-30f3-4f09-9829-058193fd396c)




- Now, go to your serverless dashboard and go to apps --> create app --> existing project



  ![app1](https://github.com/ArpitB95/Serverless_App_AWS/assets/110182832/f06b6c7a-2697-4012-826e-67fbf8fd29fe)






  Now run the shown command in the terminal






  ![Inkedapp2](https://github.com/ArpitB95/Serverless_App_AWS/assets/110182832/7d21adde-c43c-4bfd-966a-2fddeccd69c9)





  ![sls org](https://github.com/ArpitB95/Serverless_App_AWS/assets/110182832/96fccc09-24ae-44a3-bc2e-5085582b0543)




- Run "serverless deploy"




  ![sls deploy](https://github.com/ArpitB95/Serverless_App_AWS/assets/110182832/72440601-9b02-48ff-8626-164ad0176a8c)




 ### Congratulations! Your app has been deployed.

 - Go to AWS account and check the CloudFormation stack
   
   ![cloudformation stack](https://github.com/ArpitB95/Serverless_App_AWS/assets/110182832/683c1e65-805c-4c5f-bc60-feae50e2f7ae)


   
### serverless will automatically create S3 bucket to store it's state file and maintain versions there.

![DeploymentArchitecture](https://github.com/ArpitB95/Serverless_App_AWS/assets/110182832/a930a35e-be05-4a70-a2be-cf445b6f149a)

            


       

  
