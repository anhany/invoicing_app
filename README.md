#Getting Started:
-----------------------

Assuming you have git and npm installed:

1. git clone https://github.com/atomicjolt/react_firebase_starter_app.git my_project_name
2. Rename .env.example to .env and change the values as desired. The default should be fine.
3. npm install
4. Sign up for a [Firebase](https://www.firebase.com/) account
5. Copy your Firebase database url and add it to .env
6. Start server with:

  `npm run hot`

then visit http://localhost:8080


#Development:
-----------------------
Source code lives in the client directory. Modify html and js files in that directory to build your 
application.


#Tests
-----------
  `npm run test`
    

#Check for updates
-----------
Inside the client directory run:

  `npm-check-updates`


#Setup Deploy:
-----------------------

  1. Install the s3_website gem:
  
    `gem install s3_website`

  2. Create s3_website.yml:

    `s3_website cfg create`

  3. Setup and AWS user:

    1. Login to your AWS console
    2. Find Identity & Access Management (IAM)
    3. Click 'Users'
    4. Click 'Create New Users'
    5. Save the user's credentials
    6. Click on the user
    7. Click the permissions tab.
    8. Under 'Inline Policies' create a new custom policy and paste in the policy below. Be sure to change the domains:

    For more details see the [s3_website gem instructions](https://github.com/laurilehmijoki/s3_website).

    ###IAM Policy:
    ```json

      {
        "Statement": [
            {
                "Action": [
                    "s3:ListBucket"
                ],
                "Effect": "Allow",
                "Resource": "arn:aws:s3:::www.reactclientstarterapp.com"
            },
            {
                "Action": "s3:*",
                "Effect": "Allow",
                "Resource": [
                    "arn:aws:s3:::www.reactclientstarterapp.com",
                    "arn:aws:s3:::www.reactclientstarterapp.com/*"
                ]
            }
        ]
      }
    ```

  4. Configure bucket as website:

    `s3_website cfg apply`
   

#Deploy to S3:
-----------------------

  Build a release without deploying:

  `npm run build`
  

  Build a release and deploy:
  
  `npm run release`

#Deploy to Firebase:
-----------------------
(Firebase hosting quickstart)(https://www.firebase.com/docs/hosting/quickstart.html)

  Install the Firebase tools:

  `npm install -g firebase-tools`


  Build the app:
  
  `npm run build`

  Deploy the app:

  `firebase deploy`

firebase.json contains the configuration for the deployment. If you need to customize the 
deployment configuration check out the (advanced hosting guide)[https://www.firebase.com/docs/hosting/guide/full-config.html].

License and attribution
-----------------------
MIT