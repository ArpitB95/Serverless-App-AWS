# Serverless_App_AWS


## What is Serverless ?


## Benifits of Serverless


### In this project, I have deployed a task_master_app on AWS with serverless and lambda function. I have used Windows machine in this project.
- Serverless eliminates the maintanance of instances and only runs when needed so also eliminates the cost.


### STEPS:
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

            


       

  
