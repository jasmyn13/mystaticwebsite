## Static Website Gitlab Project

# Tools you'll need

1. Gitlab
2. Surge.sh
3. Node.js and Npm
4. Gatsby CLI
5. Homebrew

# Installing Homebrew, Node.js and Npm

Use this comamnd to install homebrew on your terminal: ```  /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)" ```

Verify your Homebrew by checking its version ``` brew -v ```

To install Node.js and Npm, use this command: ``` brew install node ```

Verify Node.js and Npm, use this command: ``` node -v ``` and ``` npm -v ```

It should look like this when done correctly:

<img width="582" alt="Screenshot 2022-11-04 at 10 48 00 AM" src="https://user-images.githubusercontent.com/100259466/200004270-7d6aa4bb-63c2-44a3-8cd6-b9b0b13a748a.png">

# Installing Gatsby CLI and creating a new website

Use this command in your root terminal to install Gatsby: ``` npm install -g gatsby-cli ```

Once it's installed, you can create a new website by using this command:  ``` gatsby new [static website] ``` 

Next, you want to CD into your static-website directory on your terminal.  ``` cd static-website ```

To deploy the website once you have CD into your directory, type in ``` gatsby develop ```
Once it's deployed, you will be able to visit your local website at http://localhost:8000/

It should look like this when you log into the website:

<img width="1626" alt="Screenshot 2022-11-04 at 12 22 32 PM" src="https://user-images.githubusercontent.com/100259466/200025791-25c10e4b-afa7-4590-a6fb-8d43af02b982.png">


# Creating a Gitlab Project

1. Log into your Gitlab account.
2. Click "New Project."
3. Label it "my static website"
4. Make sure it's marked as public and that the box is unmarked for initizliating a README.

# Creating a .gitlab-ci.yml file to run a basic Pipeline




