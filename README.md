HOME WORK SUMMARY

Assuming that git,docker and Jenkins are installed in the user respective system.

In this project there are two environment created using docker

1.TESTING ENVIRONMENT(USER CAN TEST THE PROJECT BEFORE COMMITING INTO PRODUCTION ENVIRONMENT)
2.PRODUCTION ENVIRONMENT(AS THIS IS A PRODUCTION ENVIRONMENT, SO ONLY SUCCESSFULLY BUILD PROJECT AND VERIFIED BUILD IS ALLOWE

For making this AUTOMATED(END-END) we are using jenkins

IN GIT HUB REPO :
Consider there are two branches master and deploy according to my repository and whatever happen in the master is showed in Production Environment and changes made in deploy is shown in Testing Environment

IN GIT BASH:
Supposing user has created two branches in git bash and using remote linked to the origin account github/user_name/user_content/branch_name/.com 
supposing user commit and pushed into github


STEPS TO MAKE END TO END AUTOMATE:

PreRequisite:
Server OS(REHL8/etc)
install httpd
Run httpd command (systemctl start httpd) 
docker should be installed
GIT Bash
In RHEL8.0 Firewall should be stop (systemctl stop firewalld)



1.CREATE GIT REPOSITORY


2.GIVING JENKINS POWER TO RUN COMMAND ON REDHAT LINUX 8

  Editing the file *sudoers* in your RHEL8.0
  
  
3.TUNNELING
  For tunneling I'm using ngrok you can use this application or similar application in RHEL8
  *./ngrok https 80* this command will help to run a tunnel which will help to connect this red hat linux to outside world.
 
4.WEBHOOK
  In your repository there is an option of settings go to settings/WEBHOOK and add webhook there 
  For adding webhook use the tunneling ip which was provided by ngrok
  https:/Ngrok_ip/github-webhook/
  
 5.creating the production job in jenkins
    create a job and go to configure of your job and fill the data provided in image and give url of your *Git repository/master branch* in SCM and select the branch master.
    Next go to pollscm 
    
    IN EXECUTE SHELL FOLLOW THESE COMMANDS PROVIDED IN IMAGE

6.Creating the developer Job in Jenkins
  Same as Production Job only there is a difference is select the branch to deploy
  Remote trigger in Build trigger because with this we can trigger this job remotely and as soon as we push this job will run automatically.
  
  
7.MERGING JOB in jenkins
  Again create a job in jenkins and in git url provide a url of master branch because it is our production system.
  If and only if testing build/Developer build successfully runs.
  This concept is known as chaining as soon as developer build job will run successfully this build will start automatically
  In this build we will merge the content of the deploy branch with master.
  
  Provide these commands in your configure section 
  
  
  
