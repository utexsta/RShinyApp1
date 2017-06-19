# Shiny Web App Hosting On Github

http://abiyug.github.io/2016-04-05-shiny-web-app-hosting-on-github

Abiyu Giday
Home
My Data Services
About Me
Author's home
 
Shiny Web App Hosting On Github
Posted on April 5, 2016 
Running Shiny Web Application on Github
Abiyu Giday
April 5, 2016
Motivation
Steps
Conclusion
Assumptions
Credit
Motivation
Wouldn’t it be nice to quickly test your web applications without having to worry about the meter running on your ‘paid’ hosted web app account? Or, you may want to visualize a web app concept quickly before finalizing the production version. Or you want to demo a product proof-of-concept to a customer on the fly. A Combination of Github, R console and shiny framework applied sequentially gives you exactly that! A web app can be launched from any machine with internet access. The objective of this blog is to show how one can use few steps to launch a web app from anywhere. There may be alternative ways of launching a web app, but I find this capability very handy and useful.
Before diving to the nity-grity of how to, lets expand briefly on the pillars that make this possible. Github, is a web-based source code management system repository hosting service available for free. Github has a reputation of being unfriendly to users, but if you know which knobs to dial, it has more to offer in terms of software development and hosting than any other free service I know. Couple that with R programming, a language and environment for statistical computing and graphics, and RStudio’s shiny framework, a package from RStudio that build interactive web applications with R, you are in good shape to try out web applications relatively quickly.
Steps
The following are the steps to follow to launch a web app from your machine that has R console, internet access and web browser supporting HTML5 installed.
Step 1. Create a Repository on github. Here are the step to open account on github
Step 2. Create shiny’s required scripts and store them in a directory on your machine (MAC OSX is what I have). Showing you how to write shiny script is outside the scope of this blog, but Google and there are plenty of tutorials. On this example there are only three files, REAMDE.md, ui.R and server.R, but you may have only an app.R or more files .
# On MAC OSX
# This are example's. A user may have diffrent file names.
$ pwd
/tmp/testShiny123
$ ls -lrt

Feb  5 07:53 README.md
Feb  5 07:55 ui.R
Feb  5 07:56 server.R
Step 3. Create a directory where the shiny server files are located and name it archive. It has to be named “archive”.
$mkdir archive

cd archive

pwd
/tmp/testShiny123/archive
Step 4: Compress the all files under /tmp/testShiny123 and move the compressed files to the archive directory on your machine.
# creates the compressed file for the entire directory
tar -cv testShiny123.tar testShiny123    
# move the compressed file to the archive directlry
mv testShiny123.tar testShiny123.tar/archive                          
Step 5: Push all of the files including the ‘archive’ directory to github. To perform this step a github account must have been created. If you don’t have an account, follow the procedure on a link from step 1. Then apply the following github command to push the files to your github repository.
#This commands pushes your compressed file to your github account
git init
git commit -m "pushing tar files for shiny app"
git remote add origin git@githhub.com:username:/testShiny123.git
git push -u origin master          

github.com/your-github-username/testShiny123/archive/testShiny123.tar.gz     #you should be able to see the file on github
Step 6: From any R console with internet access run the following commands to launch your app.
# Assumed 'shiny' package is installed from https://cran.r-project.org/web/packages/shiny/index.html
library(shiny)     
#name of the app dir and username
runGitHub("testShiny123", "your-github-username")  
If all goes right, you should see the following lines on your R console.
Downloading https://github.com/your-github-username/testShiny123/archive/testShiny123.tar.gz
Listening on http://127.0.0.1:5792
And your browser will launch the shiny app directly on your machine using your default browser. Make sure your default browser is one that supports HTML5. I have successfully tested latest versions of Firefox, Safari and Chrome web browsers. Test your browser with this link to make sure it is in compliance.
Conclusion
Working with Github, RStudio’s Shiny apps and R programming one can quickly visualize product concepts right off the R console without having to host on a paid cloud account. Hope the above steps gives developers and users the opportunity to test web apps for free without having to fully deploy it in production from any R console with a machine that has a web browser supporting HTML5. Feel free to contact me if you have comments or questions.
Assumptions
This blog assumes the reader is familiar with Github, R programming, and shinyapps from RStudio. And that a user has account on github. Familiarity with MAC OSX (or Linux) command line admin task are also required to compress and move files.
Credit
RStudio 
Github 
Html Test 
Wikepedia 
? Previous Post
Next Post ?






Abiyu Giday  •  2017  •  abiyug.github.io 
Theme by beautiful-jekyll 