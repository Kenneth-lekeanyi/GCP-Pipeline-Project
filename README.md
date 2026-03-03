# DevOpsProjectWithGCP

In this project, you will build a continuous integration pipeline using Cloud Source Repositories, Cloud Build, build triggers, and Container Registry.

<img width="1149" height="620" alt="Image" src="https://github.com/user-attachments/assets/126e06de-fb43-473a-91f3-1f7a9a9cca56" />

- As you can see, the DevOps Engineer will push the Source Code into a Repository in GCP (known as Cloud Source Repository). This code will automatically trigger a build using a Trigger that is found inside CloudBuild. When it goes to the CloudBuild, CloudBuild will perform the build process and build the image of the Application. This image will be sent and stored in a Container Registry.
- And from that Container Registry, you can create a VM and it will deploy in it.

**Prerequisites**

1) Google Cloud tools Cloud Source Repositories.
2) Cloud Build.
3) Build triggers. 
4) Container Registry. 

**Objectives **

1) Create a Git repository
2) Create a simple Python application
3) Test Your web application in Cloud Shell
4) Define a Docker build
5) Manage Docker images with Cloud Build and Container Registry
6) Automate builds with triggers
7) Test your build changes
8) You have done a great job! Pat ya back!

**Task Distribution**

**Task 1. Create a Git Repository**

First, you will create a Git Repository using the **Cloud Source Repositories** service in Google Cloud. This Git Repository will be used to store your source code. Eventually, you will create a Build Trigger that starts a continuous integration pipeline when a code is pushed to it.

1) In the Cloud Console, on the Navigation menu, click "Source Repositories". A new tab will open. it says "There is no repositories for this project".
2) Locate and click on "Add repository" at the top far right corner of the page.
3) Now, click on "Create new repository" and click on "Continue".
4) Name the repository: **devops-repo**.
5) Select your current project ID from the list by clicking inside the box of "Project".
6) Click now on "Create".
7) Now, Locate the CloudShell icon at the top right beside the small Bell icon and click on it to activate CloudShell. It will take a moment to come up.
8) If prompted, click on "Continue".
9) Now, enter the following command in CloudShell to create a folder called "gcp-course". So do:
- `mkdir gcp-course`
11) Do `ls` to ensure that the gcp-course Folder has been created succesfully.
12) Now, change your location into the folder you just created. so do this to get inside this Folder:
- `cd gcp-course`
13) Now, clone the empty devops-repo Repository that you just created in Cloud Source Repository into this gcp-course Folder. So do:
- `gcloud source repos clone devops-repo`
13) if a warning pops up, just click on "Authorize".
14) The previous command created an empty folder called devops-repo. Now, change to that folder. So do this to get into that repo:
- `cd devops-repo`
15) Do `pwd` to ensure that you are creating it inside the "devops-repo cloned Repository.

**Task 2. Create a simple Python application or that which is sent to you by the Developpers**

You need some Source Code to manage. So, you will create a simple Python Flask Web Application. The Application will be only slightly better than "hello world", but it will be good enough to test the pipeline you will build.

1) In Cloud Shell, click on "Open Editor" to open the Editor. This icon is located just directly above the CloudShell Terminal. If prompted click Open in a new window. Wait for it to connect and open the Editor. It will open the gcp-course Folder, wherein, inside that Folder, we have our empty devops-repo that we had cloned.
2) Now, select the {gcp-course > devops-repo} folder in the explorer tree on the left, just like in V.S Code. Do so by clicking on it. It is just located above README.Cloudshell.txt
3) Click now on "devops-repo"
4) Now, locate "**File**" just above "EXPLORER" and click on it. Then on the options, click on "New File", so that you have to write the code inside the Editor.
5) Go to this Github link, ***https://github.com/Kenneth-lekeanyi/GCP-Pipeline-Project/blob/main/main.py*** and use the clipboard to copy the code under main.py and you come and paste it here in this Editor that you just created.
6) To save your changes. Press **CTRL + S**,
    - it ask you "Save As"
    - Click to select "home"
    - Then you click on "gcp-course"
    - Then you click to select "devops-repo"
    - Then you click on "Save".
    - It will appear in Green. Click on "Untitled-1" and click on "rename" to rename it.
    - Rename it as "main.py"
    - Then click on "O.K"
8) Click on "SAVE"
9) Now, click on the "devops-repo" folder again.
10) And then, you click on the File menu again, And then you click "New Folder". Now, Enter folder name as "templates".
11) Click on "OK"
12) Now, right-click on the "templates" folder and create a new file again called "layout.html".
13) Make sure that the layout.html file is inside the template Folder.
14) Now, go copy the code in this link ***https://github.com/Kenneth-lekeanyi/GCP-Pipeline-Project/blob/main/layout.html*** under layout.html and come paste in this layout editor as you did above.
15) Also in the templates folder, add another new file called index.html.
16) Then go copy the code in this link ***https://github.com/Kenneth-lekeanyi/GCP-Pipeline-Project/blob/main/index.html*** under index.html and come paste in this index.html editor as you did above.
17) Also, in Python, Application prerequisites are managed using **pip***. Now you will add a file that lists the requirements for this Application.
18) So, in the "devops-repo" folder ***(NOT inside the templates folder)***, create a New File There and name it as "requirements.txt"
19) Now, add the code in this link ***https://github.com/Kenneth-lekeanyi/GCP-Pipeline-Project/blob/main/requirements.txt*** to that requirements.txt Editor and save it by doing **Command+S**:
20) At this point, you have some files. So, save them to the repository.
21) First, you need to add all the files you have created to your local Git repo. For that, go back to Cloud Shell. In CloudShell, first ensure that you are in the right location by doing;
    - `cd ~/gcp-course` enter
    - `cd ~/devops-repo` enter
22) You will now be seated inside the "devops-repo" location. Now, while currently seating inside this devops-repo location, run this command to add those files to the Repo in our local staging area.
    - `git add --all`
23) This will add all the files inside the devops-repo local staging area. To see them, do
 - `git status`
- You will see those files all lined up, that need to be committed and push to the Cloud Source Repository.
24) To commit the changes to our Cloud Source Repository, you have to first identify yourself. So, enter the following commands with your information. (you can just use your Gmail address or any other email address):
    - `git config --global user.email "kenneth@gmail.com"` enter
    - `git config --global user.name "Kenneth"` enter
25) Now, commit the changes to our local Repo. So, do
- `git commit -a -m "Initial Commit"`
26) With this, you have committed the changes locally, but have not push to the Cloud Source Repository you created earlier.
27) You can see the Branch where the code is current in it by doing `git status` {You see that it says that "your branch  is based on 'origin/master' but the upstream is gone}.
28) Now, enter the following command to push your changes to the Cloud Source Repository. So, do
- `git push origin master`
29) Now, go to the Cloud Source Repository and refresh the Cloud Source Repositories page. You should see the files "devops-repo" that you just created there.

**Task 3. Define a Docker Build**

The first step for using Docker is to create a file called Dockerfile. This file defines how a Docker container is constructed. You will do that now.

1) In the CloudShell Code Editor, expand the gcp-course/devops-repo folder. With the devops-repo folder selected,
2) Select "devops-repo" and rightclick on it to populate the options.
3) Click on "New File" and name it as "Dockerfile" and click on "OK".
4) make sure that it is not created in the "template" Folder.
5) Create this Dockerfile Folder in the "devops-repo" Folder.
6) Now, paste the content of this Dockerfile in this link ***https://github.com/Kenneth-lekeanyi/GCP-Pipeline-Project/blob/main/Dockerfile*** inside the text editor of this created Dockerfile.
7) This Dockerfile has to build and store the image somewhere. For that, we shall use CloudBuild.

**Task 4. Manage Docker images with CloudBuild and Container Registry**

The Docker image has to be built and then stored somewhere. You will use CloudBuild and Container Registry.

1) Return to CloudShell. Make sure you are in the right folder. So do:
- `cd ~/gcp-course/devops-repo`
2) The CloudShell environment variable **DEVSHELL_PROJECT_ID** automatically has your current project ID stored. The project ID is required to store images in the Container Registry. Enter the following command to view your project ID:
- `echo $DEVSHELL_PROJECT_ID`
3) Enter the following command to use CloudBuild to build your image. So, while seating inside the "devops-repo" Folder, do:
- `gcloud builds submit --tag gcr.io/$DEVSHELL_PROJECT_ID/devops-image:v0.1 .`
4) Notice the environment variable in the command. The image will be stored in Container Registry.
4) If asked to enable CloudBuild in your project, type **Yes**. Wait for the build to complete successfully.
**Note #1**: If you receive the error "**INVALID_ARGUMENT: unable to resolve source"**, wait a few minutes and try again.
**Note**: In Container Registry, the image name always begins with **gcr.io/**, followed by the project ID of the project you are working in, followed by the image name and version.

- The period at the end of the command represents the path to the Dockerfile: in this case, the current directory.

5) Now, return to the Cloud Console and on the Navigation menu ( Navigation menu icon), click Container Registry. Your image should be on the list.
6) Now navigate to the CloudBuild service, and your build should be listed in the history.

**You will now try running this image from a Compute Engine virtual machine.**
# Test by running the image in a VM.
7) Navigate to the Compute Engine service.
8) Click "Create Instance" to create a VM.
9) On the Create an instance page, specify the following, and leave the remaining settings as their defaults:
10) So, scroll down to locate "Containers" and then
11) Locate and click on "DEPLOY CONTAINER".
12) On the "configure container" page that pops up, go copy the container image in CloudShell and paste it here to appear as follows;-
    - Container image: ***gcr.io/qwiklabs-gcp-04-0e8678eb4e7/devops-image:v.0.1***
13) Leave all these settings as they are by default and click on "Select" below.
14) Now, scroll down to locate Firewall and
- Check the box on [Allow HTTP traffic] {We are checking this box because we have to test it on a web browser} inorder to check that everything is fine or not.
15) Now, Click on "Create" to create the VM.
16) Once the VM starts, create a browser tab and make a request to this new VM's external IP address. The program should work as before.
**Note**: You might have to wait a minute or so after the VM is created for the Docker container to start.
  
12) You will now save your changes to your Git repository. In CloudShell, enter the following to make sure you are in the right folder and add your new Dockerfile to Git. This is to add the Dockerfile into our devops-repo in Cloud Source Repository. So do:
- `cd ~/gcp-course/devops-repo`
13) Then run this command to add it to our staging area. So do
- `git add --all`
14) Now, commit your changes locally to our local staging area. So do:
- `git commit -am "Added Docker Support"`
15) Now, do `git status` to see the branch that you are in. which is "Master".
16) Now, push your changes to Cloud Source Repositories by doing:
- `git push origin master`
17) Now, return to Cloud Source Repositories and verify that your changes were added to source control.

**Task 5. Automate builds with triggers**

1) Go or navigate to the "Container Registry". At this point, you should have a folder named "devops-image" with at least one container inside it.
2) On the Navigation menu, click CloudBuild. The Build history page should open, and one or more builds should be in your history.
3) Click on "the Triggers link" on the left.
4) Click now on "Create trigger". {This is because we want to trigger every time that a Code lands in the Cloud Source Repository.}
5) Give this trigger a name: **devops-trigger**.
6) Keep these things like this as default, and scroll down to "Source"
7) Now, under "Repositories" box, use the drop down to Select your "devops-repo Git repository" under repository dropdown as follows.
   - ***devops-repo(Cloud Source Repositories)***
9) Select .*(any branch) for the branch. Branch: *
10) Choose Dockerfile for Configuration and select the default image. Our image just pops up here.
11) Accept the rest of the defaults, and click "Create."
    # Test the Trigger
13) To test the trigger, click on "RUN" and then click on "Run trigger", which is at the right on the trigger page.
14) Branch; **master**
15) Now, click on "RUN TRIGGER"
16) Click now on the History link and you should see a build running. Wait for the build to finish, and then click the link to it to see its details.
17) A pop up comes up saying "**Build started on branch master [SHOW]. Click on this [SHOW]
18) You can see that a Built has started.
19) Scroll down and look at the logs. The output of the build here is what you would have seen if you were running it on your machine.
20) Now, return to the Container Registry service. You should see a new folder, "devops-repo", with a new image in it.
21) Return to the CloudShell Code Editor. Find the file "main.py" in the gcp-course/devops-repo folder. So do `ls` to find or see it
22) In the main() function, change the title property to "Hello Build Trigger." as shown below:

@app.route("/")
def main():
    model = {"title":  "**Hello Build Trigger.**"}
    return render_template(`index.html`, model=model)

16) Commit the change with the following command:
- `cd ~/gcp-course/devops-repo`
17) Then run this git command to commit the changes to our staging area. So do
- `git commit -a -m "Testing Build Trigger"`
17) Enter the following git command to push your changes to Cloud Source Repositories. So run:
- `git push origin master`
18) Now, return to the Cloud Console and the Cloud Build service. You should see another build running.

**Task 6. Test your build changes**

1) When the build gets completes, click on it to see its details. Under Execution Details, copy the Image link, format should be like this ***gcr.io/qwiklabs-gcp-00-f23112/devops-repoxx34345xx***
2) To see the image such that you can copy it, go to the CloudBuild and
- Click on "History" at the left.
- Click now on the specific Build that you want.
- Then click on "EXECUTION DETAILS"
- You will see the image there. You can then copy it from here shown as follows
  - image: **gcr.io/qwiklabs-gcp-04-0e8678e4b4a7/devops-image:v0.1**
  - You can rightclick on it and copy the image.
4)  Now, go to the Compute Engine service. As you did earlier, create a new virtual machine to test this image.
  - Click on "DEPLOY CONTAINER" and paste the image you just copied there.
5) Select to Allow HTTP traffic.
6) Click now on "Create"
7) When the VM comes up, click on the External IP. It says "This site can't be reached", Which means that the VM is up, but the App is not coming up yet.
8) Wait for some time and refresh.
9) The Application comes up as "**Hello! Welcome to the GCP DevOps Project**"

**Note**: You might have to wait a few minutes after the VM is created for the Docker container to start.

# CICD PIPELINE TO DEPLOY APPLICATIONS ON GOOGLE KUBERNETES ENGINE (GKE) USING CLOUDBUILD $ CLOUD-DEPLOY.

[![YouTube](https://img.shields.io/badge/YouTube-Video-green)](https://youtu.be/L_1qbt-Iii0?feature=shared)

## Requirements

To achieve our goal, we have the following requirements:
- Deployment of two simple Flask applications (app1 & app2) on the GKE clusters.
- Automation of the entire deployment process, triggered by a developer’s code push.
- Dev-cluster deployment precedes production deployment, allowing for review before promoting to the prod-cluster.

## Architecture

![image](https://github.com/vishal-bulbule/gke-test/assets/143475073/66c914bb-4466-4a23-b977-f0880e1e1f12)

## Technical Stack Summary

This CI/CD pipeline leverages several key components:
- Google Kubernetes Engine (GKE): Google’s managed Kubernetes service, providing a scalable and reliable platform for deploying containerized applications.
- Cloud Build: A fully managed continuous integration and continuous delivery platform that allows developers to build, test, and deploy applications on Google Cloud Platform.
- Cloud Deploy: A service for continuous delivery that automates the deployment of containerized applications to Google Kubernetes Engine and other platforms.
- GitHub: A popular version control platform where developers collaborate, manage, and version control their codebase.

## Solution


**Objective:** ***To deploy Applications on GKE Cluster using CloudBuild and Cloud-Deploy.***
- Here, we are implementing a complete automation or CICD Pipeline automation where users will push an Application Source Code to a git repository. Once it is pushed, it will trigger a CloudBuild to start the build automatically. This is done using a Build Trigger.
- Here CloudBuild will build and push a docker image using the Application code and once it is done, it will pushed that image to an Artifactory Registry or Container Registry.
- And that will also trigger a Cloud-Deploy pipeline. Cloud-Deploy will first deploy the latest container image or docker image to the Dev GKE Cluster. And when everything is tested in the Dev Kubernetes Cluster, then you can promote it to Production in the Prod Cluster. 
- But before it goes to production, there is an option that we set up, which is "**Manual Approval or Promotion**" before it proceeded into the Production Environment.
And once the approval is done it will then be deployed into a GKE.
- So, Cloud-Deploy is a managed service that automates delivery of your Applications to a series of environments such a GKE and cloud-Run.
- Therefore in Cloud-Deploy, we basically create a Pipeline wherein, in that Pipeline we mention the target. This target is nothing but a GKE Cluster. And so anytime that you want to deploy a new code you just create a release. And a release is nothing but deploying or promoting your code or releasing a new code to the existing Application.
- Then we have Cloud-Deploy that we can use manifest files to push it to the Cluster. And with that action at the backend, it will create your kubernetes scaffold file itself for the Application.
- We shall have two clusters wherein cluster1 will be the Dev Cluster while Cluster2 will be the Prod Cluster.
- So, go to the Kubernetes Engine console and create 2 clusters first.

# Step One: Create 2 Clusters.
***To create a GK cluster.***
-	Navigate to the Console and type to search for "GKE" and click on "Kubernetes engine".
-	Enable the API
-	Now, locate and click on "clusters" at the left
-	Then you now click on "let's get started" since it is the first time to create the cluster,
  - At the top right hand side locate and click on "SWITCH TO STANDARD CLUSTER".
  - Then click on "switch to standard cluster" at the bottom of the poped up page.
-	***{This is because we are switching from standard to auto-pilot because here in auto-pilot it is best for Prod grade tasks. And in Standard, you have to manage more configuration settings in your cluster and Nodes called Node-Pool. And here under Auto-pilot, the minimum amount of Nodes that we can have here is 3. (which is a huge number of instances and thus so costly as well)}***. 
- ***That is the reason why we are switching to standard wherein here in standard you are the one to decide the number of Nodes that you want. And you are the one to decide the minimum that you want to create. If you want just one node for Dev/Test, you can do it. With Auto-pilot, it is good for Prods higher availability***.
-	So at the top right, it will give you the ability to switch from STANDARD to AUTO-PILOT.
-	Note however that with autopilot clusters Google Cloud takes care of the following:
      - Node: Automoted node creation scaling and maintenance
      - Networking: VPC-native traffic routing from public to private clusters
      - Security: Shield GKE Nodes and workloads identity
      - Telementary: Cloud operation logging and monitoring.
-	Name: **cluster1-def-cluster** 
-	location: zona [select this one]
              - regional ***{if you take Regional, it will add 3 clusters per region. so go with his zonal}***
-	Region: **US-east-1**
-	Version: ***{Select the specific GKE version that you want (default version is 1.29.6)}***
-	Click on "Node Pool"
-	Then click on "default-Pool"
-	Name of the pool: **default-Pool**
-	Size: **2**
-	[] Enable cluster auto-scaler: **Check this box**. ***{this will scale the Nodes depending on the usage, same behavior as in MIG Auto-scaler. So, you have the opportunity to scale the Nodes here. So too you can enable Pode auto-scaling under automation, so as to respectively scale the Pods using manifest files. Therefore, make sure that Auto-scaling is enabled both at the Node level an add a Pod level when creating the cluster, so as to smoothly permit perfect and smooth scaling by the orchestration tool using Replica set.}***
-	Now scroll up on the left and click on "Nodes" under default pool.
  - Image type: **Container-optimized OS with container (default)**
  - Machine Configuration: **General purpose**
  - Series: **E2**
  - Machine type: **E2-standard-2**
  - Boot Disk type: **Balanced Persistent Disk**
  - Boot Disk size: **60**
-	Now, scroll up and select the next option "Networking". This is the network that has to do with the cluster itself. So, Google cloud uses its own internal network. They don't use external network tools like [calico] and [flanel] this their network is to boost security so don't do anything here.
-	Scroll down and click on "Security"
  - Here leave everything as default
-	Scroll down and locate "metadata" and click on it
  - Nothing to add here as well
-	click on "Automation"
  - Auto-scaling
      - [] Enable Vertical Pod auto-scaling
      - [] Enable Node auto provisioning
      - [] Enable maintenance window: ***{this is for every upgrade to be implemented at the time it is made available}***.
-	[] Weekly editor customer editor. ***{Check this box on weekly editor}***
-	[] start time: ***12:00am***
-	[] Length: ***4hrs***
-	[] Days: ***Monday, Tuesday, Wednesday, Thursday, Friday, Saturday, Sunday***
-	Click on networking on the left
  - Network: ***default VPC***
  - Node subnet: ***default (10.28.0.0/20)*** {so this cluster will come up with VMs which will act as Worker Nodes. so there will be using this VPC and subnet}
  - IPV 4 network access
  - [] Public cluster {if your Pods will be accessible to users in the public check this one}
  - [] Private cluster
-	Now, scroll up and click on "security" on the left
  - [] Enable Binary Authorization {this is used in pulling the image from DockerHub. But we don't need it for now}
  - [] Enable Vulnerability Scanning {this is used to be scanning Pods}.
-	click now on "Backup plan"
-	click on "Features" now
   - [] Enable loggin
  - [] Enable Cloud Monitoring
  - [] Enable managed service for Prometheus
  - [] Enable compute engine persistent disk
-	Now click on "create" to create the cluster.

  
# Step Two: Logging into the Cluster:
-	There exist 3 ways to log into the cluster
1) login through Cloudshell in the console
2) login from your local machine using VS Code
3) login from a VM instance i.e from the deployer VM instance
   
-	# 1st Approach:connecting to the cluster from CloudShell.
1) click on those three dots at the right
2) connect to the cluster.
3) Edit this cluster or Delete this cluster 
-	Note: You can use this command to interact with a cluster locally so far as you have gcloud install in your local. However since the CLI for Kubernetes is kubectl, you need to have kubectl installed localy for it to be able to interact with this cluster from your local.
- So, you will be able to login but you will not be able to even see the Nodes.
-	So, at this point we can only run the commands from CloudShell and interact with the cluster from Cloudshell.
-	So, either you click on "RUN IN CLOUDSHELL" or you copy the command and go run it in Cloudshell.
-	Now, paste the command in Cloudshell and hit enter
-	Now, take "Authorize"
-	if you see this know that everything went through successfully
-	`kubconfig entry generated for test-envy-cluster`
-	Know that it has logged you into the cluster. So, run this command to see if you can reach the cluster itself
-	`kubectl get nodes`
-	`kubectl get namespace`
-	`kubectl get service`
-	You will see that you have one and that is the cluster IP.
-	
-	# 2nd Approach: Connecting to the  from our local VS Code.
-	Now we're going to log into the cluster from our local VS Code. This, we need to set up an install kubectl in your local machine.

-	**[For Windows:]**
-	To install the kubernetes CLI or kubectl on windows, first of all install chocolatey. So
-	Go to the taskbar down the screen and type to search for "PowerShell".
-	As it pops up, click on Powershell at the top.
-	Then right click on "Run as Administrator" to populate the PowerShell command-prompt
-	In the PowerShell command-prompt that comes up, run this command
-	`Set-ExecutionPolicy AllSigned`
-	Then type **y** to enter
-	Now, run this command
-	`Get-ExecutionPolicy`
  - it says ***AllSigned***
-	Now, run this command
-	`Set-ExecutionPolicy Bypass-Scop Process___'))`
-	See this command in the READMME.md File under "Replicaset" in VS Code and copy it from there.
-	Now, check to confirm that "chocolatey" is installed successfully. Type "Choco" [enter]
-	it says "chocolatey version 10.10.15
-	
-	Now, chocolatey is successfully installed in our window machine. Let's now proceed to install kubernetes CLI. So, run this command :
-	`choco install Kubernetes-CLI`
-	Type: **yes**
-	Now, check to confirm that kubectl is installed successfully. So do
-	`kubectl version --client`
-	Now, open a new PowerShell and run this command
-	`kubectl version --client`
-	
-	**[For MacOs;]**
-	To install kubernetes CLI or kubectl on Mac, lets first of all install "Homebrew"
-	So, run this command
-	`brew install kubectl`
-	Now, check to confirm that kubectl is installed successfully. So do
-	`kuctl version --client`
-	it version comes up
-	Meaning that kubectl has been installed succeasfully.
-	
-	Now, bring up your VS Code or PowerShell in windows open up your terminal
-	Now, we are going to create a folder called **.kube** in our Home Directory.
-	So, first of all go to Home Directory. So do
-	`cd` [enter]
-	***{At this time if you try to connect to the cluster that has just been created from your local V.S Code terminal, by copying the connect command in Cloudshell and running it in the V.S Code terminal, it will error out. So, we have to first of all install gcloud components in our local in order to be able to connect to the cluster from our local.}***
-	So first check to ensure that cloud SDK is installed successfully in your local system. Check it by doing
-	`gautile ls`
-	It says "updates are available to install them, run
-	`gcloud component updates`
-	So, Cloud SDK is installed successfully.
-	
-	Now, go back to the cluster in the console, click on "connect" and click on "RUN IN CLOUDSHELL"
-	As the Cloudshell terminal comes up, hit [enter] button in our keyboard
-	Then click on "Authorize"
-	As it is connected to the cluster from the Cloudshell terminal, do 
-	`ls .kube`
-	it says **"cache config gke_gcloud-auth-plugin_cache"**
-	so they have it in the cluster. So the ".kube" folder is there.
-	Now, cat the ".kube" directory. So, do
-	`cat .kube/config`
-	Now, copy the content of this file. Copy from
-	***API version: v1 ------------:true***
-	Now, go to your VS Code and bring up your VS Code terminal
-	Still in your Home Directory in your VS Code, do
-	`vi .kube/config`
-	***{so we are creating this ".kube/config" file is in our local. So as to have that content you saw in the cluster available in our local as well, for us to use it to connect to the cluster,}*** Follow this process.
-	Now change to ***insert*** mode
-	Paste that content that you copied from Cloudshell cluster here.
-	Now, change to escape mode then save and quit {:wq!}
-	It errors out
-	Paste the cluster connection command here and hit [enter]. It says
-	it says "error: again **Fetching Cluster endpoint and auth data cluster endpoint and author data**
-	Now, do this to log into gcloud
-	`gcloud auth login`
-	Now, follow the page and login to the Account that has Cluster there.
-	Once you are login;
-	Recall and run the command again (i.e the cluster connection command which is)
-	`gcloud container cluster get-cedentials gke-cluster --zone us-central1-c --project manifest-stream-424502-s1`
-	It says
-	{***CRITICAL: Action Required: gke-gcloud-auth-plugin, which --- in-gke --install gke-gcloud-auth-plugin for use with kubectl by following https://cloud.gcloud.com/blog/products/containers-kubernetes/kubectl-auth-changes-ingke***}
-	Now, we have to install one more plugin for gke (i.e the key component).
-	So, copy this URL above in the critical action from HTTPS all the way to the end
-	Bring up a new browser
  - Paste the URL in the search bar of a new Browser. ***{there is a gcloud command that we need from that URL page}***
-	It says "**Here is what to know about changes to kubectl authentication coming in GKE v1.26**"
  - Now screw down
  - Under "install using 'gcloud component installed', copy this commander there" `gcloud components install gke-cloud-auth-plugin`
-	Now, open your VS Code Terminal and run this command
-	`gcloud components install gke-cloud-auth-plugin`
-	it says ***"Do you want to continue (Y/N)?"***
-	Type **y** in your keyboard and hit enter
-	Now, try to loggin to the cluster now using the cluster connect command which is `gcloud container cluster get-cedentials gke-cluster --zone us-central1-c --project manifest-stream-424502-s1` ***{So this command fetches the Cluster credentials, and use it to log you into the cluster}***
-	Now, it says;
  - ***{fetching cluster endpoint and auth data. **kubeconfig entry generated for gke-cluster**.}***
  - [Now, it has logged you into the cluster successfully]
  - 
-	So, the "gke-gcloud-auth-plugin" is a pluggin used to authenticate you to the cluster. So, you need to have that available. Remember gcloud is just a utility for Cloud SDK.
-	 So, this "gke-gcloud-auth-plugin" is a utility for gcloud within cloud SDK. So, you have to install it, then you use it to log into the gke cluster. So, that is what we have just done to log into the cluster from our local rather than going to the browser every time to login from there. (it is a one time setup).
-	As we are now inside the cluster, Lets start testing things. So do
-	`kubectl get node`
-	You now see your Nodes which are ready, from your local.
-	Now, we are going to create a Kubernetes manifest file for specific kubernetes object which we shall be able to use it to do some testing.
Now, we are going to create a Replicaset for nginx and deploy that nginx Replicaset using the -f command.
So, first create a File in V.S Code and name it as
 - **nginx-replicaset.yaml**
 - ![Image](https://github.com/user-attachments/assets/ee36a8c6-7269-44e4-b759-0ee336e88ece)

- # Now, our gke Cluster is up and running. Lets proceed with the project

- So, the setup here is that, it will first deploy to Cluster1 as a Dev Cluster. And after an Approval(**Promotion**) is done, it will then deploy to Cluster2 as the Prod Cluster.
- At this time, the two clusters are already existing.
- So, when we go to Cloud-Deploy to creat a deliverer pipeline, we shall be asked to select a target. 
- Wherein, under 'Targets',
  - Target1 will be Cluster1 (or Dev Cluster)
  - Target2 will be Cluster2 (or Prod Cluster) ***{All these 2 clusters will be selected in Cloud-Deploy}***
- This will be done before creating the pipeline project. However this is a manual way of doing things.
- We are not going to do it this way. We are going to do it from our code or manifest files or yaml Files.
- Here is the Link to get all the manifest files and the Application Source Code [https://github.com/Kenneth-lekeanyi/Deployment-CICD-gcp-Pipeline]
- As seen in this GitHub Repository, we shall be deploying 2 applications. The first one is the "Hello World App1" and the second one is a "Hallo World App2" Application.
- App1 will be exposed on port=8080 while App2 will be exposed on port=8081
- We shall make the changes and push the Code from our GitHub Repository.
- But before that, we have to create a CloudBuild Trigger and thus it will create a CloudBuild Pipeline.
- So, let's start by going to the Cloud console also to create a CloudBuild trigger.
  
# Step One: Create a CloudBuild Trigger
- So, navigate to the CloudBuild Console.
- Locate and click on "Triggers" at the left.
- Then, in the middle at the bottom, click on "CREATE TRIGGER".
  - Name: **gke-cicd**
  - Region: **us-east-1**
  - Event: **(Repository event that invokes trigger)**
  - [] Push to a branch {select this one}
  - [] Push new tag
  - [] Pull request
- Source (Repository generation)
  - [] 1st gen {select this one}
  - [] 2nd gen
- Repository. ***{Here, we have to connect to our GitHub Repository}***
  - Click inside the box and click on “CONNECT NEW REPOSITORY”
  - On the “Connect repository” page that pops up at the right,
  - Select “GitHub” (CloudBuild GitHub App)
  - Then click on “Continue” {This will start the authorization process.}
  - Now, Authenticate with GitHub. You will be redirected to GitHub to authorize Google CloudBuild GitHub App
  - Choose to Grant Access to
    1)	[] All repositories
    2)	[] Only selected repositories {select this one}.
- Click now on “Install & Authorize”
  - Then click on “CONNECT”. It should appear like this
  - Repository
  - [Kenneth-lekeanyi/Deployment-CICD-gcp-pipeline(GitHub App]
  - Branch
  - [*]
- Configuration.
   - [] Autodetected
   - [] CloudBuild Configuration file (YAML or JSON). {select this one}
   - [] Dockerfile
   - [] Buildpacks
 - Cloud Build configuration file location
  - [/cloudbuild.yaml] ***{Note, this file is created in our VS Code and it is present in our GitHub Repo. So, it will check for this file}***
- Here is the content of this file
- **Cloudbuild.yaml**
  <img width="1615" height="809" alt="Image" src="https://github.com/user-attachments/assets/057c060e-2fe3-4e47-9ea9-df329757b0b2" />
- In line 1 - 5 of this file, CloudBuild will first be building a Docker image, using a Dockerfile that is present in App1.
- Then, in line 9 - 11 of this file, it is pushing that Docker image to the Artifactory Registry.
- Then it goes to App2, same thing in line 13-15, it is building a Docker image using a Dockerfile that is located inside App2.
- Then, it is pushing that image to the Artifactory Registry in line 20 – 22.
- In line 31, we are executing a gcloud deploy apply; wherein, we are applying the “Pipeline.yaml” file that is inside the “deploy” Folder
- So, the “Pipeline.yaml” file is simply creating a Pipeline that we usually create manually in Cloud Deploy. But here, we are creating it using a manifest file and deploying it using the “gcloud deploy apply” command in line 31.
- In line 32, we are executive the dev.yaml file (which is inside the deploy folder). And in line 33, we are executing the prod.yaml file (which is equally inside the deploy folder and pointing to cluster1 and cluster2 respectively in their line 9 of the dev & prod Folder).
- So, inside these files, we are creating a target that is first pointing at cluster1 and then we create another target inside the prod folder which is pointing at cluster2.
- After that, it will go to line 35 and create a release1 which is for my app1 yaml file (**app.yaml**). This file has a deployment that together with a container image inside it, (it is present on the the kubernetes folder). And it has a **Service** as well of type **Load balancer**. Same thing for App2, still inside the kubernetes folder.
- So, we are deploying 2 containers here. One for app1 and the other for App2. These will deploy as soon as we pushed the code using git commands. 
- So, first of all still on CloudBuilt, click on "save" to save the CloudBuild trigger.
- So, as soon as we push this Code from our local using Git, it will start a CloudBuild pipeline.
- So, 
- Bring up your VS Code Terminal or Gitbash and ensure that you are in the **Deployement-CICD-gcp-pipeline** folder. Open it in integrated terminal. So, do
 - `git add .`
 - `git commit -m “adding Pipeline”`
 - `git push`
 - 
- As Soon as we hit git push, it will trigger the gke-cicd pipeline. So,
- Go to the CloudBuild Console and click on "History"
- After a minutes, you will see that the gke-cicd pipeline has started.
- Now, go to the "Artifactory Registry" console and check if the images have been deployed there.
- So, 
  - Go to "Artifactory Registory" and click on "repository"
  - Then locate and click on **gke-repo** which is the name of the Artifactory Registory that we created.
  - You should see the images there which are:
    - **Flask-image**
    - **quickstart-image**   ***{These are the names that we gave to our images in line 10 and line 14 of our Cloudbuild.yaml file}***
- Now, go back to CloudBuild and click again on "History" to check if all stages have a green check pass or not.
- We realize that the last stage 4 has failed.
- Click on the last stage 4 (google/cloud-sdk-latest) to check the logs and see why it failed.
- Scroll down the logs, when we expand the last drop down, it says ***clouddeploy.deliveryPipeline.update denied on project...gke-cicd-pipeline.*** So Cloud Deploy denied permissions. so it is a permission error. (This is because maybe we are using a wrong Serviceaccount for our trigger)
- So, go to "CloudBuild" and click on "triggers" at the left. (We are going to check the Serviceaccount).
- While under "trigger", click on **gke-cicd** that we are using for our trigger.
- Scroll down to locate the Serviceaccount section
 - check if you have a Serviceaccount selected or not.
 - We see here that, we did not select any Serviceaccount.
- Now, select this Serviceaccount to appear as follows
- Service account email:
- [856008859364-compute@developer.gserviceaccount.com]
- So, at first, we did not select any Serviceaccount. That is the more reason why the last stage 4 failed.
- This Serviceaccount holds most of the editor role and will permit Cloudy-Deploy to deploy everything.
- Now, go to CloudBuilt and click on "History" again and then you click on "Retry" to retry the pipeline.
  - It will do everything again from stage 1 to stage 4
  - We see that all the stages have now succeeded.
- So, our CloudBuild pipeline has completed here
- 
- Now, go to **[Cloud deploy]***
- In the Cloud deploy console and click on "delivery pipelines"
- Then click on "REFRESH" at the top right.
- You mwill see that **gke-cicd-pipeline** has come up.
- Under it or when you click on it, you will see that, we have Apps deployed there which are;
    - **app2-release-ee793eo**
    - **app1-release-ee793eo**
- Note that, this is all deployed inside the dev cluster as you can see above.
- As we can see, it is deployed all the releases into a Dev Cluster under Cloud Deploy.
- And it is waiting for some kind of leadership to review it and click on **"Promote"** to promote it to Prod as seen above. (which is currently pending or at pending stage).
- But, before clicking on "Promote", to promote it the Production, we have to check first of all if our Application is running fine in a Dev Cluster.
 - For that, go back to "Google kubernetes Engine" console and click on cluster1 (which is our dev cluster).
 - There, locate and click on "Workloads".
 - Click on "flask deployment", we would try to access it.
 - Scroll down to locate and click on Endpoint (which is the flask Service Load balancer endpoint and appears like this.)
- **Exposing services**
- **Name			Type			Endpoints**
- Flask-service		Load balancer	104.197.252.145.8081 
- Click on this Endpoint to see if the Application comes up
   - [Success!!!! the Application comes up]
- So, the dev is working fine.
- Check that the other App2 is working fine as well.
   - Success!!!!!

- At this time, we can now promote this to our Prod Environment. So,
- Go to Cloud Deploy and click again on "Delivery pipeline" at the left.
- Now, click on "**Promote**". But before that let's check to ensure that nothing is actually running inside Cluster2. So,
- Go to "Google Kubernetes Engine" console and click on "Workloads" at the left.
- In the box of cluster, use the drop down to select cluster2 to appear as follows.
- Now, we see that nothing is inside the Cluster2.
- Now, go to "Cloud-Deploy" and under the "delivery pipeline", click on "**Promote**", (to promote from Dev to Prod" (serving as a manual approval stage).
- It will show a pop-up page known as "**Promote release app2-release-ee793eo**" for you to review some details there such as;
  - Target = **Prod**
  - Rollout name = **app2-release-ee793eo-to-prod-2001**
  - Phase = **Stable**
- Now, click on "**PROMOTE**" at the bottom.
- Now, under delivery pipelines it will ask for "Review" with the yellow colour painting on "pending". So
- Click on "review".
- Then as "app2" is highlighted, go to the right and click on "REVIEW".
- Here, the **Scaffold** file emerges. So, click below on "APPROVE".
- Now, under Cloud-Deploy and under "Delivery Pipeline", we see that it has now deployed to Prod.
- Now, go back to the "Google Kubernetes Engine" console and refresh. You will now see that Flask2 has appeared there.
- Now, click on it and then you click on its Endpoint as well.
  --- Application comes up successfully as well ----
- Now, any change that is done at the level of V.S Code and push to CloudBuild, you can then go to CloudBuild under "History" and see that the build has started.
- It will build the image, create the Pipeline and push the image to the Artifactory Registry, while the Application is deployed in Cloud-Deploy.
- And once done, we can promote it to production and we go to "Google Kubernetes Engine" console and test or confirm that Application is coming up as required.
- Note, that each build may take up to 10 minutes to complete.

