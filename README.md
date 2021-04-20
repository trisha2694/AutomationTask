# AutomationTask

## About the Repository
### This Repository explains:
..* The steps to automate AWS lambda provisioning through jenkins pipeline .
..* How to Automate Lambda Trigger using API Gateway.

### This Repository consists of multiple files :
..* EC2 Provisioning Templates : AWS CloudFormation templates is programmed to create EC2 in multiple region , should be deployed through stackset.
..* Lambda Provisioning Templates : AWS CloudFormation templates is programmed to create Lambda with python 3.8 as runtime .
..* Lambda Code : Python Code to list all the ec2 instances in multiple regions.
..* JenkinsFile : JenkinsFile to trigger the Lambda provisioning template.

## Automation Step by Step:
1. Run the EC2 Provisioning Templates through stackset in multiple region as per your requirement .
2. Trigger the Jenkins pipeline which will first copy the lambda zip file to the s3 then create/deploy the Lambda in us-east-1 region .
3. Create an API to automate the Lambda trigger .

## Pipeline Flow Chart :

![Jenkins Pipeline Flow Chart !!](https://github.com/trisha2694/AutomationTask/blob/main/PipelineFlowChart.png?raw=true)

## Lambda Triger Automation :
### Created an REST API to serve the purpose here !!
#### Steps to Create API and its Configuration :
1. Go to AWS Console and search **API Gateway**service
2. Then choose **APIs** from Left Pannel and the **REST API** __(with full control option one)__ among all other APIs type options and click on **Build**.
3. Choose Option **New API** and then give the __API Name__ as its mandatory parameter (Choose Name appropriate to your project) and choose __Endpoint Type__ as Regional.
4. Then Click on **Create API** box in the down right corner.
5. Then choose **Create Resource** for your API (from the **Actions** Drop down) and give name relevant to your requirement and check the **Enable CORS** checkbox.
6. Then **Create Method** (again from the **Actions** Drop down) Under that resource as per requirement(Like GET, POST and etc) here we are using **GET** method.
7. Then go to the method created and do its setup , as here we are creating this api to trigger lambda so we will choose Integration type as **Lambda Function** then check the box **Use Lambda Proxy integration** then choose the region in which your lambda function is and the your Lambda name and then click on **Save** .
8. After this one Checkbox will appear there click on **OK**
9. Again click on the method you have created and Choose the Deploy API (option from the **Actions** Drop down) , give deployment stage name (eg . test/dev/prod etc)

