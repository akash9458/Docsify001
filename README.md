# Docsify setup in podman and integrate with github

**Requirement of docsify setup:**

Docsify is a lightweight, flexible, and easy-to-set-up documentation generator that can turn your Markdown documentation into a website.

- Distributor ID: Ubuntu <br>
- Description: Ubuntu 20.04.6 LTS <br>
- Release: 20.04 <br>
- Codename: focal<br>

**Prerequisites tools:**
 
 - Podman <br>
 - Github
   

**Podman**

- Podman is a tool that helps you run and manage software packages called containers on your computer.

**Github**

- GitHub is an online software development platform. It's used for storing, tracking, and collaborating on software projects.
 
<br>  
Now start a setup by following these steps:
<br>


## Steps:- Install podman 

First update and upgrade by using this command :
```
sudo apt update 
sudo apt upgrade
  ```

Then use podman installation command:

**Step 1: Update Your System**

![Alt text](image-4.png)

**Step 2: Install Podman**
```bash
sudo apt-get install -y podman
```
- sudo : Superuser do

- apt : This stands for "Advanced Package Tool. apt is used to install, update, and manage software packages on your sysytem.

- -y : Automatically confirms the installation without asking for user input.

- podman : It is the name of the package you want to install.

**Step 3: Check Podman Version**

![Alt text](image-5.png)

**Step 4: Create a Directory**

```bash
mkdir docsify1
```
- mkdir : This command use for making a new directory
- docs : Name of new directory.
  
![Alt text](image-15.png)


**Step-5:- Create Dockerfile**

Add details in Dockerfile:


```bash
vim Dockerfile
```
- vim : Use for create and edit a file.

- Dockerfile : Name of file.

Add details in Dockerfile:

``` bash 
FROM node:latest
LABEL description="A demo Dockerfile for build Docsify."
WORKDIR /docs
RUN npm install -g docsify-cli@latest
EXPOSE 3000/tcp
ENTRYPOINT docsify serve .
  ```

**Step-4:-Create index.html**

```bash
vim index.html
```
![Alt text](image-17.png)

Add details in html file:

**Step-5:- Create new fil
e in md format**

```bash
touch README.md
```
- touch : Use for creating new file.
  
Here we can check all files by using this command:

- ls : It is a Linux shell command that lists directory contents of files and directories.
  
**Step-6:- Build docker image**
```bash 
 podman build -f Dockerfile -t docsify/demo .
 ```
![Alt text](image-18.png)
- podman build : Initiating the container image building process means starting the procedure to create a new container image.

- -f : It stands for file.

- Dockerfile : It specifies the name of the Dockerfile that should be used for the container image build.

- -t : It stands for tag.

- docsify : This is the name for the image.

- / : It uses for path separator in file and directory path.

- demo : This is the tag for the image.

This command is used to manage container images in Podman.

**Step-7:-Run podman**

Create a podman container for docsify.

```bash
 podman run -d -p 3000:3000 -v /home/tripathi/docsify1:/docs localhost/docsify/demo
```
![Alt text](image-19.png)

This command will run a container based on the docsify/demo image.

- Podman run : It is used to run a container from the docsify/demo image.

- -d (detach mode): It allows the container to run in the background. It's useful for users who don't want to see the container's output in the terminal.

- -p (port forwarding): It enables port forwarding between the container and the host system.

- -v : It indicates volume mounted from your host's into the container

```bash
podman ps -a
```
This command is used to see all containers on your system, both running and stopped.

**Step-8:- Preview Output**

![Alt text](image-20.png)

## GitHub

**GitHub Integration Steps:**

**Step-1:-Create repository**

Make a new repository with public account.<br>
Give a name to new repository.<br>
After entering the name, It will show like this:

![Alt text](image-21.png)

**Step-2:-Clone the repository**

Go to [GitHub] https://github.com/akash9458/Docsify001.git, click on "Sign up," and follow the prompts to create your GitHub account. Then, log in to GitHub.


**Step 2: Create a GitHub Repository**
- Click on the "+" icon in the top-right corner and select "New Repository."
- Choose a name for your repository.
- Write a short description of your project or documentation.
- Choose whether the repository should be public or private.
- Click "Create repository."

**Step 3: Set Up Your Local Git Repository**
```bash
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin 
https://github.com/your-username/your-repository.git
```

**Step 4: Generate a Personal Access Token**
- Go to your GitHub account settings.
- Select "Developer settings."
- Choose "Personal access token (Classic version)."
- Click "Generate new token" and follow the prompts to generate a token.

**Step 5: Clone the Repository and Push Changes**
```bash
git push -u origin main
```

Your Docsify documentation should now be hosted on GitHub and accessible through your repository's URL. You can continue to edit your documentation locally and push changes to GitHub as needed.
