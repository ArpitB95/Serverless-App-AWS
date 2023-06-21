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
  - node -- version
  - npm - version
    
- Install Serverless Framework
  '''
  npm install -g serverless
  '''
  
- Install AWS CLI
  https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html

  
- Configure AWS
  '''
  aws configure
  '''
  - Insert your AWS Access key and Secret key.
    
- Create serverless.yml file

"""
  org: arpit95
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
        - arn:aws:dynamodb:eu-west-2:683873876613:table/KaamKaro
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
"""
          
            


       

  
