<h1>Linux - Manage file permissions</h1>

<h2>Scenario</h2>
This scenario is based on a fictional company: <br/>
<br/>
I am a security professional at a large organization, mainly work with their research team. Part of the job is to ensure users on this team are authorized with the appropriate permissions. This helps keep the system secure. <br/>
<br/>
The task is to examine existing permissions on the file system and need to determine if the permissions match the authorization that should be given. If they do not match, the permissions need to be modified to authorize the appropriate users and remove any unauthorized access. <br/>

<h2>Project description</h2>

The research team at the organization needs to update the file permissions for certain files and directories within the `projects` directory. The permissions do not currently reflect the level of authorization that should be given. I performed the following tasks to checking and and updating these permissions:

<h2>Environment</h2>

- <b>Qwiklabs - Linux (Bash shell)</b>

<h2>Task walk-through:</h2>

- <b>Check file and directory details:</b>

I used the following Linux commands to determine the existing permissions set for a specific directory in the file system: <br/>
<p align="center">
<img src="https://i.imgur.com/4Bwwzo5.png" height="60%" width="60%" alt="LinuxComm"/>
<br />
<p align="left">

The first line of the screenshot displays the command I entered, and the other lines display the output. The code lists all contents of the `projects` directory.
I used the `ls` command with the `-la` option to display a detailed listing of the file contents that also returned hidden files.
The output of my command indicates that there is one directory named `drafts`, one hidden file named `.project_x.txt`, and five other project files.
The 10-character string in the first column represents the permissions set on each file or directory. <br />
<br />
<p align="left">
  
For example, the file permissions for `project_t.txt` are `-rw-rw-r--`. Since the first character is a hyphen `(-)`, this indicates that `project_t.txt` is a file, not a directory `(d)` like `drafts`. The second, fifth, and eighth characters are all `r`, which indicates that user, group, and other all have read permissions. The third and sixth characters are `w`, which indicates that only the user and group have write permissions. The fourth, seventh, and tenth characters are hyphens `(-)` instead of `(x)`, so no one has `execute` permissions.  <br/>
<br />
  
- <b>Change file permissions:</b>

The organization determined that other shouldn't have write access to any of their files. To solve this, I referred to the file permissions that I previously returned. I found out `project_k.txt` must have the write access removed for other. <br/>

I used the following Linux commands to do this:<br/>
<p align="center">
<img src="https://i.imgur.com/ErGJPEy.png" height="60%" width="60%" alt="LinuxComm"/>
<br />

<p align="left">
  
I removed write permissions from other for the `project_k.txt` file. After this, I used `ls -la` to review the updates I made.
The first two lines of the screenshot display the commands I entered, and the other lines display the output of the second command. The `chmod` command changes the permissions on files and directories. The first argument indicates what permissions should be changed, and the second argument specifies the file or directory. <br />
<br />

- <b>Change file permissions on a hidden file:</b>

The research team recently archived `project_x.txt`. They do not want anyone to have write access to this project, but the user and group should have read access. <br/>

The following code demonstrates how I used Linux commands to change the permissions: <br/>
<p align="center">
<img src="https://i.imgur.com/pmQLaWm.png" height="60%" width="60%" alt="LinuxComm"/> <br/>
<p align="left">
  
As before, the first two lines of the screenshot display the commands I entered, and the other lines display the output of the second command. <br />
I know `.project_x.txt` is a hidden file because it starts with a period `(.)`. <br />
I removed write permissions from the user with `u-w` and group `g-w`, and added read permissions to the group `g+r`. <br />
<br />

- <b>Change directory permissions:</b>

The organization only wants the `researcher2` user to have access to the `drafts` directory and its contents. In this case, I need to remove execute permissions from group. <br/>

I used the following Linux commands to do so: <br/>
<p align="center">
<img src="https://i.imgur.com/8hRKzBh.png" height="60%" width="60%" alt="LinuxComm"/> <br />
<p align="left">
  
As previously, the first two lines of the screenshot display the commands I entered, and the other lines display the output of the second command. <br />
Because the group had execute permissions, therefore I used the `chmod` command to remove them. The `researcher2` user already had execute permissions, so they did not need to be added. 
<br />
<br />

- <b>Summary:</b>

I changed multiple permissions to match the level of authorization the organization wanted for files and directories in the `projects` directory. The first step in this was using `ls -la` to check the permissions for the directory. This informed my decisions in the following steps. I then used the `chmod` command multiple times to change the permissions on files and directories.  <br/>

</p>
