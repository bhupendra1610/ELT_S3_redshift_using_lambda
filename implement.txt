First make the S3 bucket.( assignmnet-raw-1)
     set the S3 events for the lambda to trigger the S3 object 
     go to properties:
                     create Event
                     select the put and post
  
Make the lambda function (codefors3) and set the role to give the permission ( AdminstratorAccess )
  Make changes in the lambda function:
  1. Configuration : general configuration set the time limit to 5 min.
  2. Set the Environment Variable (optional for security purpose)
      AWS_Access_Secrete	: this is access_key password ( Go to IAM then create a access key )
      AWS_Access_key	    : Access key
      dbname	            : dev
      host	              : for host post the endpoint ( only upto amazon.com not the :567/dev)
      password            : password for the redshift database 
      user	              : redshift ( generally admin or you can change it)
      tablename           : for this we have to make the same name table in the redshift cluster and then give the name 
       
  3. VPC  : add the same vpc as the redshift and set the inbound roles to be  all allow

  Code of the lambda it show the Error for the psycopg2 :
        to solve this go to cloud9 and then past the cmds
        
        1.sudo amazon-linux-extras install python3.8
        
        2. curl -O https://bootstrap.pypa.io/get-pip.py
        
        3. python3.8 get-pip.py --user
        
        4. sudo python3.8 -m pip install psycopg2-binary -t python/
        
        5. zip -r dependancies.zip python

        then dependancies zip file is created left click to download it 
        
  Layers: 
        Go to layers section 
          create a  layer and then insert the dependancies (zip) files that we have downloaded using the Cloud9
          go to lambda then add the layer 

Redshift :
         make the free-tier cluster and choose the custome for the user and password to create
         make the default workshop or you can change the name and create the namespace 
         select the query data and create the table using the sql cmd
         create table tablename(
                  id VARCHAR(100) not null,
           
                  name VARCHAR(100) not null,
          )

        the tablename should be same as the tablename we given in the environment variable for the lambda function
        
