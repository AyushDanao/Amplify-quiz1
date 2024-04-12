# Getting Started with Create React App

This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

## Steps to host this front end application with cognito authentication in AWS Ammplify

Firstly you need to install the aws amplify cli globally...this cli allows us to interact with amplify and set basic features for the app
npm install @aws-amplify/cli -g ( Installing amplify cli globally)

Once the amplify cli is installed successfully, you need to do 
## amplify configure

This is to configure amplify ( This command launches the documentation we can refer)
We can navigate to IAM and create a new user and attach the amplify administrator access policy to the user
Then add the required access keys for the user we created and the region to be selected
After these steps we can interact with amplify with our local IDE

Once done, we need to initialize amplify in our React App saying
## amplify init
We need to name our project, set the default configuration,  authentication method (to be the profile we created earlier)


Then we need to add authnetication for our app using cognito

## amplify add auth
Go with a default config, use email for signing in.

Then push these changes

## amplify push

Then inside cognito, we would have a new user pool created for us...AWS works on the principal of user pools and set of users withing that can access the app.

Right now, the user pool is empty...there are no users. we can create a user inside that user pool with an email id...this actually sends a verification code so be sure to give authentic email id


The in our react app, we need the app to be wrapped with Amplify and make sure our created users can access this
So, we need to install a couple of packages

## npm install aws-amplify @aws-amplify/ui-react

Then in out App.js, we wrap the base or parent coponent to be routed via amplify, essentially login directs us to there
We use two imports
## import { Authenticator, withAuthenticator } from '@aws-amplify/ui-react'
Authenticator gives us the actual UI that contains the login screen and withAuthenticator wraps around the highest order component that enforces authentication


Test it out locally to see if the app works with cognito authentication.

Once done push the code to a remote github repository. We use this repo and hook up amplify to this repo host the front end via github so that any changtes to the repo will be automatically re-deployed.
Hence the task, Continuous Integration/Continuous Deployment (CI/CD)


So now go to amplify -> Hosting Environments -> connect the github repo and the branch you want to use, choose the required backend and give/create a new role with policy Amplify administrator access that allows amplify to deploy.
The click save and deploy which deploys the application and host the react app onto the cloud.
