# SWE 645 - ASSIGNMENT 1
# SANJANA GOVINDU | G01380306 | sgovindu@gmu.edu

# This is a README.md file which contains information about the 2 webpages in this assignment created in AWS console

STEPS FOLLOWED:

# PART 1 -- sanjana.html - Student web page which uses W3 CSS templates which contains basic description and picture of the student redirected to survey form.
http://swe645-g01380306-assignment1.s3-website.us-east-2.amazonaws.com/ 


# PART 2 -- FEEDBACK PAGE - feedbackpage.html - It contains the survey page table with fields and required specifications mentioned in the assignment along with the comments.

EC2: http://ec2-3-17-208-176.us-east-2.compute.amazonaws.com/DisplayAllHeaders/feedbackpage.html 

1. Create the web pages using HTML, CSS, Bootstrap and use W3 templates if needed.
2. Then install JDK java in your local using homebrew.
3. Install Apache Tomcat server version 10.1 in your local (will work if you have JDK)
4. Install Eclipse workspace.
5. Create dynamic project in eclipse workspace and give it a name.
6. After creating the dynamic project we need to upload the feedback page form html file in webapps folder.
Now go to File > Export > Web > War file and need to create a WAR file -> in out local tomcat/webapps folder in your local.
7. A WAR file with a name should be created and copied for future use.
8. Then now lets create a .pem file using EC2 instance in AWS console
9. Steps to host on EC2 instance:

* Login to AWS Console in your brower
* Then let us Create an EC2 Instance in AWS
  * Click on Launch Instance and give it a name
  * Select the OS as tomcat in options and keep everything else and default
  * Create a Key-pair to login to the instance and this will download a .pen file in your local and keep it aside for future reference.
  * Click on Review and Launch now
  * Then click EC2 instance button and click on create
  * then after creation click on Public IPv4 DNS and check if tomcat is running or not.
  * Then using the Winscp we create an EC2 instance by locating the .pem file and WAR file from our local and get the EC2 link which is -> http://ec2-3-17-208-176.us-east-2.compute.amazonaws.com/DisplayAllHeaders/feedbackpage.html 
  * Now we need to paste that EC2 link for feedback page in our home website which is a redirection link.

10. Now lets go to AWS console and create a S3 bucket. Give a unique bucket name, disable permissions, upload all the html files needed.
11. Set the default permissions and properties for the files and go to Bucket Permissions and edit the permissions and make it publicly accessible by changing the code and saving the changes.
json
    {
        "Version": "2012-10-17",
        "Statement": [
            {
                "Sid": "PublicReadGetObject",
                "Effect": "Allow",
                "Principal": "*",
                "Action": [
                  "s3:GetObject"
                ],
                "Resource": [
                  "arn:aws:s3:::<My-Bucket-Name>/*"
                ]
            }
        ]
    }

12. Now finally we created an S3 instance with EC2 instance for feedback page.
13. Now go to Properties -> Static website hosting and copy the webpage link which is the link to the homepage of the assignment when opened also has the link to feedback form.
14. Now finally we have a hosted webpage.
