# Static Website Gitlab Project

The objective is to create a static website using the Gatsby CLI and Surge.sh to deploy the website through the terminal, and then running the CI/CD Pipeline for the website in Gitlab.

## Tools you'll need

1. Gitlab
2. Surge.sh
3. Node.js and Npm
4. Gatsby CLI
5. Homebrew
6. Text Editor (VS Code, in this case)

## Installing Homebrew, Node.js and Npm

Use this comamnd to install homebrew on your terminal: ```  /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)" ```

Verify your Homebrew by checking its version ``` brew -v ```

To install Node.js and Npm, use this command: ``` brew install node ```

Verify Node.js and Npm, use this command: ``` node -v ``` and ``` npm -v ```

It should look like this when done correctly:

<img width="582" alt="Screenshot 2022-11-04 at 10 48 00 AM" src="https://user-images.githubusercontent.com/100259466/200004270-7d6aa4bb-63c2-44a3-8cd6-b9b0b13a748a.png">

## Installing Gatsby CLI and creating a new website

Use this command in your root terminal to install Gatsby: ``` npm install -g gatsby-cli ```

Once it's installed, you can create a new website by using this command:  ``` gatsby new [static-website] ``` 

Next, you want to CD into your static-website directory on your terminal.  ``` cd static-website ```

To deploy the website once you have CD into your directory, type in ``` gatsby develop ```
Once it's deployed, you will be able to visit your local website at http://localhost:8000/

It should look like this when you log into the website:

<img width="1626" alt="Screenshot 2022-11-04 at 12 22 32 PM" src="https://user-images.githubusercontent.com/100259466/200025791-25c10e4b-afa7-4590-a6fb-8d43af02b982.png">


## Creating a Gitlab Project

1. Log into your Gitlab account.
2. Click "New Project."
3. Label it "my static website"
4. Make sure it's marked as public and that the box is unmarked for initizliating a README.

Make sure that your git project is linked and you can do so by going into your static-website directory, and then typing in ``` git status ```
You want to make sure that the branch says "master" and not "main." If it says main, you can switch it to the master branch by using this command: ``` git branch -m main master ```

Next you want to add the git remote command into your terminal: ``` git remote add origin https://gitlab.com/testprojects35/my-static-website.git ```
Followed by ``` git push -u origin master ```

This will allow the files from your "terminal" to be uploaded it to your Gitlab Repository.

Once you do that, you should have the following files added to your Gitlab Project as shown below:

<img width="1614" alt="Screenshot 2022-11-04 at 12 37 15 PM" src="https://user-images.githubusercontent.com/100259466/200028625-4413571d-e908-4abe-a868-ba86e9b19bb7.png">


## Creating a .gitlab-ci.yml file to run a basic Pipeline locally

1. In your terminal in your static-website directoy, type in ``` gatsby build ``` 
2. CD into your "public" folder from your static-website directoy ``` cd public ```
3. Type ``` ls ``` and look for the "index.html" file.
4. CD back into your static-website directory and open up a IDE (integrated Developement Environemt, like visual code used in this example): ``` code . ```

From there, we will begin to build our CI/CD Pipeline.

Create a .gitlab-ci.yml file in your text editor, and copy and paste the following code to get your pipeline working:

<img width="1027" alt="Screenshot 2022-11-04 at 1 03 10 PM" src="https://user-images.githubusercontent.com/100259466/200033843-7e499256-688d-49b2-ba61-f2f0ba851634.png">

      
     
 Once it is succesfully deployed in Gitlab, it should look something like this: 
     

<img width="1633" alt="Screenshot 2022-11-04 at 1 01 57 PM" src="https://user-images.githubusercontent.com/100259466/200033935-b65dfff6-d2c2-487f-92eb-caf79cd07885.png">

# Deploying the static website through Surge.sh. 

This allows this website to become accessible by anyone with the URL (that you make yourself)

1. Install Surge.sh on your terminal on the Public folder of your static-website directory: ``` cd public ```  ``` npm install --global surge ```
2. Once it is installed, type in ``` surge ``` on your terminal, and then it will prompt you to log in using your email and a password you can set then and there.
3. It will then ask you to put in a domain name, it needs to be unique! Example: jasmyns.surge.sh.

# Managing secrets in Gitlab

1. Log into your Gitlab project, and on the left side go to "settings" and then "CI/CD". From there, you will see a tab that says "Variables." Click "Expand."
2. For the first variable, the name will be SURGE_LOGIN and the "value" will be your "email." Uncheck "Protect Variable."
3. For the second variable, the name will be SURGE_TOKEN and the token can be found from this command in your terminal ``` surge token ``` Copy and paste that Token into the "value" box for the second variable. Uncheck "Protect variable" and check "Mask Variable."

This is what it will look like when done successfully:

<img width="1622" alt="Screenshot 2022-11-04 at 1 35 04 PM" src="https://user-images.githubusercontent.com/100259466/200039903-5dbce82f-8e50-4114-b63d-f01accf63c79.png">

These variables add security in automation so that it does not need to be revealed in any text that could potentially be used against you. It ideal for storing secrets on your Gitlab CLI.

# Deploying the project using the Gitlab CLI

1. Add the following to your .gitlab-ci.yml file to deploy through Surge:

 [ deploy to surge:
  stage: deploy
  script:
    - npm install --global surge
    - surge --project ./public --domain jasmyns.surge.sh]
    
 - Use the domain name you created when you created your Surge account.
 
 From there, commit and push your new code to your Gitlab CI/CD Pipeline and it should run successfully. It will look like this when it is done.
 
<img width="1627" alt="Screenshot 2022-11-04 at 1 42 36 PM" src="https://user-images.githubusercontent.com/100259466/200041239-ac39e5d0-bbcc-4752-ab9d-ec91eec808ca.png">









