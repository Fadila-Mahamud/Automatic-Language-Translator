# AUTOMATIC-LANGUAGE-TRANSLATOR
Automatic Translation of text from English to German 


# INTRODUCTION

This project demonstrates a serverless, Infrastructure-as-Code (IaC) solution
 on AWS for automated language translation. Using Terraform, to provision
 S3 buckets, IAM roles, and a Lambda function integrated with AWS
 Translate. Request JSON files are uploaded to an S3 request bucket,
 automatically processed by Lambda, translated into German, and stored in
 a response bucket. The solution is cost-efficient under the AWS Free Tier,
 scalable, and fully automated, showcasing modern cloud-native practices
 for natural language processing.
 
 ---

 # ARCHITECTURAL DIAGRAM
<img width="393" height="249" alt="T1" src="https://github.com/user-attachments/assets/dbc81b07-ea80-449c-bd34-cda708f128df" />
---

# OBJECTIVES
 - Automate language translation using aserverless AWS pipeline 
 -  Deploy infrastructure with Terraform to ensure repeatability and scalabilitY
 -  Enable real-time processing of uploaded text files through S3 triggers
 -  Demonstrate cost-effective cloud-native design without managing servers
---

# Main.tf File
<img width="940" height="479" alt="image" src="https://github.com/user-attachments/assets/9823843e-b89c-46c8-ba96-682169389f9e" />

The image above shows a terraform code that sets up a serverless translation
 workflow on AWS. It creates request and response S3 buckets, an IAM
 role with Translate and S3 permissions, a Lambda function for
 processing translations, and an S3 trigger that automatically invokes
 Lambda when a JSON file is uploaded.
 
---

# LAMBDA FUNCTION
<img width="1017" height="528" alt="T2" src="https://github.com/user-attachments/assets/4025f9c0-85a0-416d-b413-13bf5389458e" />
The Lambda function is triggered when a JSON file is uploaded into
 the fadila-translate-requests S3 bucket, it reads the content,
 translates the text into German using AWS Translate, and saves the
 translated output back into the fadila-translate-responses S3
 bucket.

---

 # REQUEST IN JSON
<img width="1113" height="441" alt="image" src="https://github.com/user-attachments/assets/bfe05c2b-da06-42a6-afa1-260d3e825c7f" />
 This JSON (request_en_de.json)  file is an input request that asks the system to
 translate the sentences from English into German.

---

# LAMBDA ZIP AND TERRAFORM INIT
<img width="947" height="393" alt="image" src="https://github.com/user-attachments/assets/bc30dd91-2280-4d13-9b41-2ee409255b99" />
 After initializing Terraform to set up the project environment and
 download required providers, the Lambda function code was zipped into a
 deployment package. This package is then referenced in the Terraform
 configuration to create and deploy the Lambda function to AWS.

---

# PLANNING OF RESOURCES
<img width="919" height="426" alt="image" src="https://github.com/user-attachments/assets/9358f427-6239-4f6f-be24-8a0b23a5df56" />
The code (terraform plan) creates two secure, private S3 buckets with
 encryption and lifecycle rules for cost control, and define a least-privilege
 IAM role for Lambda with access only to TranslateText, specific S3 actions,
 and CloudWatch logs to ensure security best practices

---

# BUILDING RESOURCES WITH TERRAFORM
<img width="878" height="408" alt="image" src="https://github.com/user-attachments/assets/aa66231b-3431-47b3-b359-dc7fc0d53137" />
 
 It created IAM roles and policies, two S3 buckets (fadila-translate-requests
 & fadila-translate-responses), and a Lambda function with translation
 logic. It connected them so that any .json uploaded to the request bucket
 triggers the Lambda, which processes and stores the translated result in
 the response bucket.

---

# VERIFICATION OF RESOURCES IN THE AWS MANAGEMENT CONSOLE
<img width="959" height="397" alt="image" src="https://github.com/user-attachments/assets/7b22e73c-2abe-46f7-875c-544934db46e8" />

<img width="805" height="354" alt="image" src="https://github.com/user-attachments/assets/14bd42f9-7e53-4b78-805f-3e0d83d827b8" />

Lambda Function's Image

 Screenshot from the AWS Console showing that the S3 buckets(fadila
translate-requests and fadila-translate-responses) and policies along
with the lambda function (fadila-translate-lambda) were successfully
created.

---

# UPLOAD AND DOWNLOAD OF REQUEST AND RESPONSE
<img width="932" height="385" alt="image" src="https://github.com/user-attachments/assets/b7ad096f-f43f-4f4c-b013-973acb3f1fa4" />
uploaded the request_en_de.json to the request bucket
Downloaded The English to German translated response  from
the fadila-translate-responses S3 bucket.

---

# CLOUDWATCH LOGS
<img width="795" height="336" alt="image" src="https://github.com/user-attachments/assets/002bf813-c977-40a5-a66b-043fa478707f" />

---

# CONCLUSION
 This project successfully demonstrates a serverless
 architecture for automatic language translation using
 AWS. By integrating S3 buckets, IAM roles and policies,
 Lambda, and Amazon Translate, it provides a scalable,
 cost-efficient, and fully automated workflow. The solution
 does not only simplify language translation but it also
 highlights the power of Infrastructure as Code
 (Terraform) in deploying cloud-native applications.





