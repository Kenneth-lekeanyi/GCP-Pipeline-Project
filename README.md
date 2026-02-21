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

**Objective:** ***To deploy Applications on GKE Cluster using CloudBuild and Cloud-Deploy.***
- Here, we are implementing a complete automation or CICD Pipeline automation where users will push an Application Source Code to a git repository. Once it is pushed, it will trigger a CloudBuild to start the build automatically. This is done using a Build Trigger.
- Here CloudBuild will build and push a docker image using the Application code and once it is done, it will pushed that image to an Artifactual Registry or Container Registry.
- And that will also trigger a Cloud-Deploy pipeline. Cloud-Deploy will first deploy the latest container image or docker image to the Dev GKE Cluster. And when everything is tested in the Dev Kubernetes Cluster, then you can promote it to Production in the Prod Cluster. 
- But before it goes to production, there is an option that we set up which is "**Manual Approval**" before it proceeded into the Production Environment.
And once the approval is done it will then be diploid into a cognitive engine.
- So, Cloud-Deploy is a managed service that automates delivery of your Applications to a series of environments such a GKE and cloud-Run.
- Therefore in cloud-Deploy, we basically create a Pipeline wherein, in that Pipeline we mention the target. This target is nothing but a GKE Cluster. And so anytime that you want to deploye a new code you just create a release. And a release is nothing but diploying or promoting your code or releasing a new code to the existing application.
- Then we have Cloud-Deploy that we can use manifest files to push it to the Cluster. And with that action at the back in it will create your community scaffold file itself for the application.
- We shall have two clusters wherein cluster1 will be the Dev Cluster while Cluster2 will be the Prod Cluster.
- So, go to the Kubernetes Engine console and create 2 clusters first.

# Step One: Create 2 Clusters.
***To create a GK cluster.***
-	Navigate to the Console and type to search for "GKE" and click on "Kubernetes engine".
-	Then you Enable the API
-	Now, locate and click on "clusters" at the left
-	then you now click on let's get started sing it is the first time to create the cluster
-	at the top right hand side look it and click on switch to standard cluster
-	then click on switch to standard cluster at the bottom of the popup page
-	. This is the cause we are switching from standard to autopilot because here in autopilot it is best for.
-	That is the reason why we are switching to standard wearing here in standard you are the one to decide the number of notes that you want no fixed minimum you can decide to just create only one note for death and test create note is common for prods higher availability.
-	So at the top right it will give you the ability to switch from standard to autopilot.
-	Not however that with autopilot clusters Google cloud takes care of
-	note automotive note creation scaling and maintenance
-	networking VPC net native traffic routing from public to private clusters
-	security sheer cheeky note and cook and workloads identity
-	elementary cloud pression logging and monitoring
-	nim cluster one def cluster 
-	location: zona regional
-	if you take original it will activate clusters per region so go with his owner
-	region:
-	vision:  that one
-	click on not pool
-	then click on default
-	name of the pool before pool
-	size 2
-	enable cluster auto scaler: this will scare the note depending on the usage same behavior as in managed instance group of this killer so you have the opportunity to scale the notes here so too you can enable Papa scaling under automation so as to respectively skill the port using manifest files so make sure that auto scaling is enabled both at the note level an add a port level when creating the cluster show us to smoothly permit perfect and smooth scaling by the orchestration to using replica set.
-	Now scroll up on the left and click on notes under default pool.
-	Image type: Cortana optimize OS with container default
-	machine configuration: general purpose
-	series: E2
-	missing type: E2 standard 2
-	would this type: balance persistent disk
-	boot pics size: 60
-	now scroll up and select the next option networking. This is the network that has to do with the cluster itself so Google cloud uses its own internal network they don't use those external network tools like calico and flanel this year network is to boost security so don't do anything here.
-	Scroll down and click on security
-	here leave everything as default
-	Scroll down and locate metadata and click on it
-	ah nothing to add here as well
-	click on automation
-	auto scaling
-	enable vertical port auto scaling
-	anyone know auto provisioning
-	enable maintenance window: this is for every upgrade to be implemented at the time it is made available.
-	Weekly editor customer editor
-	start time: 
-	length: for us
-	D days Monday Tuesday organization Thursday Friday Saturday Sunday
-	click on networking on the left
-	network: default VPC
-	not subnet: default
-	so this cluster will come up with VM's which we add as worker notes so there will be using the VPC and subnet
-	IPV 4 network access
-	public cluster
-	private cluster
-	if your pot will be accessible to users in the public check this one
-	now scroll up and click on security on the left
-	enable binary authorization {this is used in pulling the image from docker hub but we don't need it for now}
-	in a move enable vulnerability scanning {this is used to be scanning pots}
-	click now on backup plan
-	click on features now
-	enable login
-	enable cloud monitoring
-	enable managed service for Prometheus
-	enable compute engine persistent disk
-	now click on create to create a cluster
-	Step Two: Logging into the Cluster:
-	Did we exist to log into the cluster
-	one login through cloud share in the console
-	to log in from your local machine using VS code Terri creative VM instance and logging from the deployer VM instance
-	1st Approach:
-	To connect to the cluster,
-	click on those three dots at the right
-	connect to the cluster edit 
-	note you can use this command to interact with a cluster locally so far as you have G cloud install in your local however pay for cognitive is capacity are you need to have ***** ETL installed locali for it to be able to interact with this cluster from your local so you will be able to log in but you will not be able to even see the notes.
-	So at this point we can order from this in cloud shell and interact with the cluster from cloud shell
-	now paste the command in cloud share and hit enter
-	now take authorize
-	if you see this nor that everything went through successfully
-	keep config entry generated for test envy cluster
-	note that it has locked you into the cluster so run this command to see if you can reach the cluster itself
-	keep CTL get notes enter
-	keep CDN get namespace keep CTL get service
-	you will see that you have one and that is the cluster IP
-	2nd Approach:
-	Now we're going to look into the cluster from our local via scope. This we need to set up an install keep city L in your local machine.
-	For Windows:
-	to install keep CDL CLI or keep CDL on windows, first of all install chocolatey. So
-	go to the taskbar down the screen and type to search for PowerShell.
-	I see pop up click on power share at the top
-	then right click on run a sub ministrator to populate the PowerShell command prompt in the PowerShell command prompt that comes up run this command set execution policy or signed
-	yes or no tap why
-	run this command get execution policy
-	it says all signed
-	now from this command
-	set executionpolicy bypass coop process
-	see this command in the readme fire under replica set in VS code and copy it from there
-	no check to confirm that chocolatey is installed successfully. Type joko enter
-	it says chocolatey version 10.15
-	now chocolate is successfully installed in our window machine. Let's proceed to install keep CDL command or keep CDL. So run this command
-	choco install Kubernetes CLI
-	type yes
-	now check to confirm that keeps tell is installed successfully. So do keep city L vision dash dash client
-	now open a new PowerShell and run this command
-	keep still version does does client
-	division comes up there as well
-	For MacOs;
-	to install CLI or keep CTL on Mac, this first of all install homebrew
-	so run this command brew install keep city L enter
-	now check to confirm that keep CDL is installed successfully. So do keep CDL vision data client enter
-	it version comes up as virtual 2
-	this means that keeps your install successfully
-	now bring up your VS code or PowerShell in windows open up your terminal now we are going to create a folder called dot keep in our homebrew directory
-	so first of all go to home directory so do
-	cd enter.
-	At this time if you try to connect to the cluster that has just been created from your local via school terminal, by copying the connect command in the cluster and running it in the vehicle terminal, it will error out.
-	So we have to 1st install G key components in our local in order to be able to connect to the cluster from our local.
-	So first check to ensure that cloud SDK is installed successfully in your local system. Check it by twin
-	GSU TLS
-	it says updates are available to install them rogic clear component updates
-	so cloud SDK is installed successfully
-	now go back to the cluster in the console, click on connect and click on run in cloud share
-	as the closure terminal comes up, hit enter button in our keyboard
-	then click on authorize
-	as it is connected to the cluster from the cloud share terminal, 
-	do dot keep enter
-	it says catch config GKE dash cloud dash of dash plugin dash cash
-	so they have it in our cluster so doc folder is there now cut the dot cube directory so do
-	cat.com/config enter
-	now copy the content of this file. Copy from API version
-	now go to your VS code
-	stay in home directory do vi.com/config
-	so we are creating this doc slash config file locally or in our local so as to have that contender you saw in the cluster available in our local as well for us to use it to connect to the cluster.
-	Now change to insert mode
-	based that content that you copied from cloud share close to here
-	now change to escape mode then say fun quit
-	no it says error
-	paste the cluster connection command here and hit enter
-	it says error again fishing cluster endpoint and author data
-	not do this to look into G cloud
-	G cloud outlook in
-	follow the page unlocking to the accountant has disclosed today
-	once you are login
-	recall and run the command again that is the cluster connection command which is
-	it says critical action required
-	now we have to install one more plug in for G key that is the key component. So copy this URL above in the critical action from HTTPS all the way to the end
-	bring up a new browser
-	paste the URL in search bar of a new browser
-	there is a G club command that we need from that URL page
-	it says here is what to know about changes to keep CDL authentication coming in GTE version 1.26
-	now screw down
-	on that install using G cloud component installed
-	copy this commander G cloud component install GE cloud off plug in
-	now open your VS code terminal and run this command
-	G cloud component installed gke cloud off plug in
-	it says do you want to continue type way and hit enter
-	now try logging into the cluster now using the cluster connect command which is
-	G cloud container cluster get credential GK cluster
-	so this command fetches the cluster credential and use it to lock you in to the cluster
-	it says
-	fetching cluster endpoint and off data
-	keep config entry generated for GTE cluster
-	now it has locked you into the cluster successfully
-	So this GCG cloud of plug in is a utility for G cloud within cloud SDK so you have to install it then you use it to log in into the GT cluster so that is what we have just done talking to the cluster from our local Brandon going to the browser every time to lock it our own time set
-	as we are now inside the cluster Lester testing things do keep city L get notes
-	do not see your note which already from your locker
-	now we are going to create a cognitive manifest file for specific kinetic objects which we shall be able to use it to do some testing.

