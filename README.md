# DevOpsProjectWithGCP

In this project, you will build a continuous integration pipeline using Cloud Source Repositories, Cloud Build, build triggers, and Container Registry.

![0hYrmLCtV96fbLY7rct7Ue94xgf6OUG+O930FbxOeuA=](https://github.com/logicopslab/DevOpsProjectWithGCP/assets/82759985/c1dcc6c3-abb7-4925-8a71-b00b60ddbf80)

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
    - `git config --global user.name "Kenneth" enter
25) Now, commit the changes to our local Repo. So, do
- `git commit -a -m "Initial Commit"`
26) With this, you have committed the changes locally, but have not push to the Cloud Source Repository you created earlier.
27) You can see the Branch where the code is current in it by doing `git status` {You see that it says that "your branch  is based on 'origin/master' but the upstream is gone}.
28) Now, enter the following command to push your changes to the Cloud Source Repository. So, do
- `git push origin master`
29) Now, go to the Cloud Source Repository and refresh the Cloud Source Repositories page. You should see the files "devops-repo" that you just created there.

**Task 3. Define a Docker build**

The first step to using Docker is to create a file called Dockerfile. This file defines how a Docker container is constructed. You will do that now.

1) In the Cloud Shell Code Editor, expand the gcp-course/devops-repo folder. With the devops-repo folder selected, on the File menu, click New File and name the new file Dockerfile.
The file Dockerfile is used to define how the container is built.
https://github.com/logicopslab/DevOpsProjectWithGCP/blob/main/Dockerfile

**Task 4. Manage Docker images with Cloud Build and Container Registry**

The Docker image has to be built and then stored somewhere. You will use Cloud Build and Container Registry.

1) Return to Cloud Shell. Make sure you are in the right folder:
cd ~/gcp-course/devops-repo
2) The Cloud Shell environment variable DEVSHELL_PROJECT_ID automatically has your current project ID stored. The project ID is required to store images in Container Registry. Enter the following command to view your project ID:
echo $DEVSHELL_PROJECT_ID
3) Enter the following command to use Cloud Build to build your image:
gcloud builds submit --tag gcr.io/$DEVSHELL_PROJECT_ID/devops-image:v0.1 .
Notice the environment variable in the command. The image will be stored in Container Registry.
4) If asked to enable Cloud Build in your project, type Yes. Wait for the build to complete successfully.
**Note #1**: If you receive the error "INVALID_ARGUMENT: unable to resolve source", wait a few minutes and try again.
**Note**: In Container Registry, the image name always begins with gcr.io/, followed by the project ID of the project you are working in, followed by the image name and version.

The period at the end of the command represents the path to the Dockerfile: in this case, the current directory.

5) Return to the Cloud Console and on the Navigation menu ( Navigation menu icon), click Container Registry. Your image should be on the list.
6) Now navigate to the Cloud Build service, and your build should be listed in the history.

You will now try running this image from a Compute Engine virtual machine.

7) Navigate to the Compute Engine service.
8) Click Create Instance to create a VM.
9) On the Create an instance page, specify the following, and leave the remaining settings as their defaults:
<img width="438" alt="image" src="https://github.com/logicopslab/DevOpsProjectWithGCP/assets/82759985/5cbedb42-bfdf-42fb-a7da-ca7298a69caf">

10) Click Create.
11) Once the VM starts, create a browser tab and make a request to this new VM's external IP address. The program should work as before.
**Note**: You might have to wait a minute or so after the VM is created for the Docker container to start.
12) You will now save your changes to your Git repository. In Cloud Shell, enter the following to make sure you are in the right folder and add your new Dockerfile to Git:
cd ~/gcp-course/devops-repo
git add --all
13) Commit your changes locally:
git commit -am "Added Docker Support"
14) Push your changes to Cloud Source Repositories:
git push origin master
15) Return to Cloud Source Repositories and verify that your changes were added to source control.

**Task 5. Automate builds with triggers**

1) On the Navigation menu (Navigation menu icon), click Container Registry. At this point, you should have a folder named devops-image with at least one container in it.
2) On the Navigation menu, click Cloud Build. The Build history page should open, and one or more builds should be in your history.
3) Click the Triggers link on the left.
4) Click Create trigger.
5) Name the trigger devops-trigger.
6) Select your devops-repo Git repository under repository dropdown.
7) Select .*(any branch) for the branch.
8) Choose Dockerfile for Configuration and select the default image.
9) Accept the rest of the defaults, and click Create.
10) To test the trigger, click Run and then Run trigger.
11) Click the History link and you should see a build running. Wait for the build to finish, and then click the link to it to see its details.
12) Scroll down and look at the logs. The output of the build here is what you would have seen if you were running it on your machine.
13) Return to the Container Registry service. You should see a new folder, devops-repo, with a new image in it.
14) Return to the Cloud Shell Code Editor. Find the file main.py in the gcp-course/devops-repo folder.
15) In the main() function, change the title property to "Hello Build Trigger." as shown below:

@app.route("/")
def main():
    model = {"title":  "Hello Build Trigger."}
    return render_template(`index.html`, model=model)

16) Commit the change with the following command:
cd ~/gcp-course/devops-repo
git commit -a -m "Testing Build Trigger"

17) Enter the following to push your changes to Cloud Source Repositories:
git push origin master
18) Return to the Cloud Console and the Cloud Build service. You should see another build running.

**Task 6. Test your build changes**

1) When the build completes, click on it to see its details. Under Execution Details, copy the Image link, format should be gcr.io/qwiklabs-gcp-00-f23112/devops-repoxx34345xx.
2) Go to the Compute Engine service. As you did earlier, create a new virtual machine to test this image. Click DEPLOY CONTAINER and paste the image you just copied.
3) Select Allow HTTP traffic.
4) When the machine is created, test your change by making a request to the VM's external IP address in your browser. Your new message should be displayed.
**Note**: You might have to wait a few minutes after the VM is created for the Docker container to start.

**Congratulations!**
In this lab, you built a continuous integration pipeline using the Google Cloud tools Cloud Source Repositories, Cloud Build, build triggers, and Container Registry.

**Credits:-**

Lab link - https://partner.cloudskillsboost.google/course_templates/41
Disclaimer - I do not own the code/process/tech material used in this project. This code/process is taken from QuickLabs for studying/information purposes.
Website - https://go.qwiklabs.com/
