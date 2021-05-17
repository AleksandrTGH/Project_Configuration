## Project description
![](https://github.com/AleksandrTGH/Project_Configuration/blob/main/Scheme.png)

<ins>Code_job:

1. User modifies code in the Project_Code repository.<br>
2. The Code_job is triggered by GitHub webhook.<br>
3. Jenkins checkout the code in the Project_Code repository.<br>
4. Building, testing and deploying the application.<br>
5. The resulting application is published in the s3 bucket.<br>
6. Building a Docker image with an application.<br>
7. Pushing a Docker image with an application on DockerHub.<br>
8. Sending a message to Slack about the deployment of the application. Request to start or cancel deployment.<br>
9. Slack sends a request to proceed or abort a Code_job.<br>
10. If you chose to proceed then Jenkins checkout the code in the Project_Configuration repository.<br>
11. Ansible playbook starts.<br>
12. Docker is installed.<br>
13. The image with an application is pulled and launched.<br>

<ins>Infrastructure_job:

A. User modifies code in the Project_Infrastructure repository.<br>
B. The Infrastructure_job is triggered by GitHub webhook.<br>
C. Jenkins checkout the code in the Project_Infrastructure repository.<br>
D. <terraform init> and <terraform plan> commands are executed.<br>
E. Sending a message to Slack about infrastructure changes. Request to apply or cancel changes.<br> 
F. Slack sends a request to proceed or abort an Infrastructure_job.<br>
G. If you chose to proceed then the <terraform apply> command is executed.<br>

## Repository description 

A repository that contains ansible files for Jenkins Pipeline which configures created EC2 instances on AWS.

## Structure

The workspace contains files, where:

- `group_vars` : directory with variables to particular groups
- `roles` : directory with automatically loaded files of related tasks and variables that are associated with this role
- `ansible.cfg` : Ansible configuration file with some settings 
- `hosts.txt` : file that contains groups of hosts and hosts within these groups
- `site.yml` : master playbook file
