### Enhance Cloud Security with AWS IAM


You've just joined our dynamic team as a DevOps engineer, and we're thrilled to have you on board.👋

1. Boost our computing power to match increased traffic to the website. Lots of new students want to learn with NextWork over the break!
2. Onboard an intern that's working at NextWork - you're asked to make sure they have the right permission settings to contribute while keeping the company's resources secure.



### Project Design & High Level Technical Overview:


![image](https://github.com/MdShafiurRahman0/enhance-cloud-security-with-aws-iam/assets/113176437/6674d174-fa42-454c-a921-9f48f49cb1d5)


### Get ready to create (and learn from scratch):

💻 EC2 instances
📏 IAM Policies
👩‍👩‍👧‍👧 IAM Users and User Groups
🔖 AWS Account Alias


### Step 1: Create 2 Instance's  one for devlopment and production & Add tag for your EC2 instance


![2024-07-09_17h09_51](https://github.com/MdShafiurRahman0/enhance-cloud-security-with-aws-iam/assets/113176437/ff1f992d-f7c1-4cce-9dbd-2c2e9e598f7d)


![2024-07-09_17h10_17](https://github.com/MdShafiurRahman0/enhance-cloud-security-with-aws-iam/assets/113176437/4023b72a-e916-4ec2-9fc4-0e07b721a4de)


![2024-07-09_17h11_37](https://github.com/MdShafiurRahman0/enhance-cloud-security-with-aws-iam/assets/113176437/3717a006-1450-41b1-832d-215d4a70d4bb)

![2024-07-09_17h09_51](https://github.com/MdShafiurRahman0/enhance-cloud-security-with-aws-iam/assets/113176437/299e9b0a-3fa4-49b9-b89b-ffdfcb60b726)


![2024-07-09_17h08_57](https://github.com/MdShafiurRahman0/enhance-cloud-security-with-aws-iam/assets/113176437/e0b45ec0-ebca-408c-9d87-252b351981db)


![2024-07-09_17h01_21](https://github.com/MdShafiurRahman0/enhance-cloud-security-with-aws-iam/assets/113176437/9768d9c3-cc33-4dfe-ac94-b58595d8d381)





![2024-07-09_17h21_51](https://github.com/MdShafiurRahman0/enhance-cloud-security-with-aws-iam/assets/113176437/08f895ee-60bb-48b6-8ed1-c7898b863896)





### Step 2: Create an IAM Policy

![image](https://github.com/MdShafiurRahman0/enhance-cloud-security-with-aws-iam/assets/113176437/5080daa4-b937-496c-9620-5882b4749922)


```json
{    
  "Version": "2012-10-17",    
  "Statement": [        
    {            
      "Effect": "Allow",            
      "Action": "ec2:*",            
      "Resource": "*",            
      "Condition": {                
        "StringEquals": {                    
          "ec2:ResourceTag/Env": "development"                
        }            
      }        
    },        
    {            
      "Effect": "Allow",            
      "Action": "ec2:Describe*",            
      "Resource": "*"        
    },        
    {            
      "Effect": "Deny",            
      "Action": [                
        "ec2:DeleteTags",                
        "ec2:CreateTags"            
      ],            
      "Resource": "*"        
    }    
  ] 
}
```






1. This policy allows some actions (like starting, stopping, and describing EC2 instances) for instances tagged with "Env = development" while denying the ability to create or delete tags for all instances.

2. An extra for the curious: how JSON policies are structured Version

3‍.This means 2012-10-17 is the date of the latest policy version. This tells you whether the policy is up to date with the latest standards and practices.

4‍. Statement
‍The main part of the policy structure and defines a list of permissions.

5‍. Effect
‍This can have two values - either Allow or Deny - to indicate whether the policy allows or denies a certain action. Deny has priority. Looking at the first statement, "Effect": "Allow" means this statement is trying to allow for an action.

6‍. Action
‍A list of the actions that the policy allows or denies. In this case, "Action": "ec2:*" means all actions that you could possibly take on EC2 instances are allowed. Woohoo!

7‍. Resource
‍Which resources does this policy apply to? Specifying "*" means all resources within the defined scope (see the next point).


8. Condition Block (optional)
‍The circumstances under which the policy is in action. In this case, the condition is that the resource is tagged Env - development. This means specifying "Resource": "*" in the line above means all resources with the Env - development tag are impacted by your statement.



![2024-07-09_17h30_41](https://github.com/MdShafiurRahman0/enhance-cloud-security-with-aws-iam/assets/113176437/c5d79ec3-8f6d-47dc-9ac7-8500d457d0c1)




![2024-07-09_17h35_29](https://github.com/MdShafiurRahman0/enhance-cloud-security-with-aws-iam/assets/113176437/649783c1-0af3-4595-b77a-e03d0e7da32a)







![2024-07-07_16h48_32](https://github.com/MdShafiurRahman0/host-a-website-on-aws-S3/assets/113176437/5dab4e3f-911f-45bb-ab40-eff51f4f5d89)

![2024-07-07_17h17_08](https://github.com/MdShafiurRahman0/host-a-website-on-aws-S3/assets/113176437/181ed07d-5754-40b3-aba1-298248af72d6)

![image](https://github.com/MdShafiurRahman0/host-a-website-on-aws-S3/assets/113176437/2da1daf8-a084-4183-838f-c141e9109826)





### Step 3: Create an AWS Account Alias


![image](https://github.com/MdShafiurRahman0/enhance-cloud-security-with-aws-iam/assets/113176437/ba7648f2-fb91-402d-a975-7e76e52a4b4a)



![2024-07-09_19h43_07](https://github.com/MdShafiurRahman0/enhance-cloud-security-with-aws-iam/assets/113176437/8f9293cc-f4e1-40f6-ab57-41467313c7b4)





### Step 3: Create IAM Users and User Groups

1.Choose User groups in your left-hand navigation panel.

2.Choose Create group.

3.Let's create your first user group!


![2024-07-09_19h47_31](https://github.com/MdShafiurRahman0/enhance-cloud-security-with-aws-iam/assets/113176437/f70a8f43-0252-419a-b4eb-e2397932c549)

![2024-07-09_19h54_20](https://github.com/MdShafiurRahman0/enhance-cloud-security-with-aws-iam/assets/113176437/6a0d6d11-1f98-4f4e-8730-5929a46daace)


![2024-07-09_22h19_46](https://github.com/MdShafiurRahman0/enhance-cloud-security-with-aws-iam/assets/113176437/dbfa4e4f-4ed8-4e57-8160-dc015d51376f)









### Step 4: Test  user's access


![2024-07-09_22h28_47](https://github.com/MdShafiurRahman0/enhance-cloud-security-with-aws-iam/assets/113176437/9b5293b4-7760-43d9-a9d9-231b9c28f4b5)


![2024-07-09_22h30_46](https://github.com/MdShafiurRahman0/enhance-cloud-security-with-aws-iam/assets/113176437/862f563a-b703-4424-b561-7a10150d6514)


![2024-07-09_22h34_00](https://github.com/MdShafiurRahman0/enhance-cloud-security-with-aws-iam/assets/113176437/cb73892b-be39-403b-a799-17a2c9048e6f)



Head to your EC2 console, and make sure you're in the same Region as the one where you deployed your two production and development instances.
Head to Instances.
Select your production instance, and in the Actions dropdown, select Manage instance state.



![image](https://github.com/MdShafiurRahman0/enhance-cloud-security-with-aws-iam/assets/113176437/5529a07f-2909-47ce-8608-44f301a55b5a)


Let's try to stop this instance. Select the Stop option, then Change state.


![image](https://github.com/MdShafiurRahman0/enhance-cloud-security-with-aws-iam/assets/113176437/641accf9-fda7-47d9-a7ae-1b8c6adb1727)



![2024-07-09_22h46_37](https://github.com/MdShafiurRahman0/enhance-cloud-security-with-aws-iam/assets/113176437/5657e334-2955-4243-9df7-6265b52faae7)


![2024-07-09_22h46_46](https://github.com/MdShafiurRahman0/enhance-cloud-security-with-aws-iam/assets/113176437/812f6375-407a-4cef-a6cd-e7e1eb2f47b4)


You'll see that are denied. ❌

Woahhhhh, you even get to see exactly which statement in the IAM policy you've created (NextWorkDevEnvironmentPolicy) is blocking your user from deleting tags. Pretty handy!





### But you can delete the Devlopment instances 


![2024-07-09_22h49_09](https://github.com/MdShafiurRahman0/enhance-cloud-security-with-aws-iam/assets/113176437/52e59a71-39b2-43a3-9274-93da690238ba)

