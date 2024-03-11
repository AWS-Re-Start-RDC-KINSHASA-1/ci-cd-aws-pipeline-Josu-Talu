# CI/CD Amazon Web Services : create a pipeline to deploy code automatically after a push on Github
testaws

In this tutorial we gonna create a pipeline that will help us to update our static website each time we'll do a push on our local repository
it's a goof practice of CI/CD . it helps to be very quick deploy

Step 1

In this firts step, we must create a bucket S3 that will allos us to store our statcic website (It's just an Hello Word html file)
So, choose the S3 serice

![Alt Text](./assets/1.png)

Step 2
Créer un bucket

Step 3
Choose a name fot yor bucket and the type of bucket you want

Step 4
Here, it's important to pay attention, you must allow ou deny traffic to your bucket. if you use your bucket to store confidential data it's better for you block all public acces, but in this case we are host a webstite, visitor must have access to the website, youu must uncheck "Block public access"

Step 5
Create bucket

Step 6 
Now you can upload the code source of your application, with a drag and drop and go to properties

Step 7
Now, we must specify that our bucket is to host a static website
Go to properties and enable the "Static website hosting" and choose Host a static website, choose a name for you default file, and type a name the file who is gonna be shown in case of error

Step 8
Let's go to "permissions"

Step 9
Now we gonna edit bucket policy, click on policy

Step 11
Now you are in the zone of ediiting policy
Copy the bucket ARN

Step 10
Click on Policy generator

Step 12
You'll see a new console
select the type S3 Bucket policy
in : Add statement selet Effect : allow, znd Princiapal : *
in actions, slec GetObject

Setp 13
For Amazon Ressource NAme : paste the ARN you copied

Step 14
Clik on Add Statement

Step 15
Now click on Generate Policy

Step 16
Now you gonna see a a JSON code with configuration, copy all this code

Step 17
Paste the code on the zone "Edit bucket policy " of the step 11
We must modify a little bit the code, add a "/*" and the end of the value of "Ressource"

Setep 18
Click on Save changes

Step 19
Great, now we fonoshed to configure out s3 bucket, we must now create use the service CodePipeline to create our pipeloine that will hep us ton updates automaticaly out source code

Go search "CodePipeline" service and click on it

Step20
Create pipeline

Step 21
Choose a name for yout pipeline

Step 22 
For source provoider, choose GitHub
and click on "Connect to Github", after that you will called to log in to your guthub account

for change detections options, select "Githib webhooks (recommended)"

Step 23

You can pass the build stage, because our website don't need to be build, it's just a html code, if we used a react?js code, we hve been called to build the cdode.
In our case we can pass the step

Step 24 
Create pipeline

Step 25

You can see the configuration of our pipeline

Step 26
if you go back to s3 properties, yout'll see the link fot our website, and we can test it
You can now modify your code and do commits, once yout do a push, yout webiste will be update 







