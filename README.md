<h1>Linux - Manage file permissions</h1>

<h2>Scenario</h2>
This scenario is based on a fictional company: <br/>
<br/>
I am a security professional at a large organization, mainly work with their research team. Part of the job is to ensure users on this team are authorized with the appropriate permissions. This helps keep the system secure. <br/>
<br/>
The task is to examine existing permissions on the file system and need to determine if the permissions match the authorization that should be given. If they do not match, the permissions need to be modified to authorize the appropriate users and remove any unauthorized access. <br/>

<h2>Project description</h2>

The research team at my organization needs to update the file permissions for certain files and directories within the projects directory. The permissions do not currently reflect the level of authorization that should be given. I performed the following tasks to checking and and updating these permissions:

<h2>Environment</h2>

- <b>Qwiklabs - Linux (Bash shell)</b>

<h2>Task walk-through:</h2>

- <b>Check file and directory details:</b>

I used the following Linux commands to determine the existing permissions set for a specific directory in the file system: <br/>
<p align="center">
<img src="https://i.imgur.com/4Bwwzo5.png" height="60%" width="60%" alt="LinuxComm"/>
<br />
<p align="left">
The first line of the screenshot displays the command I entered, and the other lines display the output. The code lists all contents of the "projects" directory.
I used the ls command with the "-la" option to display a detailed listing of the file contents that also returned hidden files.
The output of my command indicates that there is one directory named "drafts", one hidden file named ".project_x.txt", and five other project files.
The 10-character string in the first column represents the permissions set on each file or directory. <br />
<br />
<p align="left">
Then, I used a with statement to open the file:  <br/>
<p align="center">
<img src="https://i.imgur.com/4Bwwzo5.png" height="60%" width="60%" alt="LinuxComm"/>
<br />
<p align="left">
In the this algorithm, the with statement is used with the .open() function in read mode opens the allow list file for reading purposes. It allows me to access the IP addresses stored in the allow list file. The with keyword will help manage the resources by closing the file after exiting the with statement.
<br />
<br />
  
- <b>Read the file contents:</b>

In order to read the file contents, I used the .read() method to convert it into the string: <br/>
<p align="center">
<img src="https://i.imgur.com/4Bwwzo5.png" height="60%" width="60%" alt="LinuxComm"/>
<br />

<p align="left">
The .read() method converts the file into a string and allows me to read it. I have called the .read() function in the body of the with statement. Then, I assigned the string output of this method to the variable ip_addresses. <br />
<br />
In summary, this code reads the contents of the "allow_list.txt" file into a string format that allows me to later use the string to organize and extract data in my Python program.
<br />
<br />

- <b>Convert the string into a list:</b>

I wanted it in list format so that I could individually delete IP addresses from the allow list. So next, I used the .split() method to turn the ip_addresses string into a list:  <br/>
<p align="center">
<img src="https://i.imgur.com/4Bwwzo5.png" height="60%" width="60%" alt="LinuxComm"/> <br/>
<p align="left">
The purpose of splitting ip_addresses into a list is to make it easier to remove IP addresses from the allow list. By default, the .split() function splits the text by whitespace into list elements. In this algorithm, the .split() function takes the data stored in the variable ip_addresses, which is a string of IP addresses that are each separated by a whitespace, and it converts this string into a list of IP addresses. To store this list, I reassigned it back to the variable ip_addresses.
<br />
<br />

- <b>Iterate through the remove list:</b>

A crucial part of my algorithm is to iterate over the elements of the list, which in our case are IP addresses. To do this, I incorporated a for loop: <br/>
<p align="center">
<img src="https://i.imgur.com/4Bwwzo5.png" height="60%" width="60%" alt="LinuxComm"/> <br />
<p align="left">
The overall purpose of the for loop in a Python algorithm like this is to apply specific code statements to all elements in a sequence. After the for keyword, there is the loop variable element, followed by the keyword in. That indicates to iterate through the sequence ip_addresses and assign each value to the loop variable element. 
<br />
<br />

- <b>Remove IP addresses that are on the remove list:</b>

My algorithm requires removing any IP address from the allow list, ip_addresses, that is also contained in remove_list.  As there was no duplication in ip_addresses, I was able to use the following code to do this:  <br/>
<p align="center">
<img src="https://i.imgur.com/4Bwwzo5.png" height="60%" width="60%" alt="LinuxComm"/> <br />
<p align="left">
First, within my for loop, I created a conditional that evaluated whether or not the loop variable element was found in the ip_addresses list. I did this because applying .remove() to elements that were not found in ip_addresses would result in an error. <br />
Then, within that conditional, I applied .remove() to ip_addresses. I passed in the loop variable element as the argument so that each IP address that was in the remove_list would be removed from ip_addresses.
<br />
<br />

- <b>Update the file with the revised list of IP addresses:</b>

As a final step, I needed to update the allow list file with the revised list of IP addresses. To do so, I first needed to convert the list back into a string. I used the .join() method for this:  <br/>
<p align="center">
<img src="https://i.imgur.com/4Bwwzo5.png" height="60%" width="60%" alt="LinuxComm"/> <br />
<p align="left">
I used the .join() method in order to join all elements of list ip_addresses into a string so that I could pass it as an argument to the .write() method when writing to the file "allow_list.txt". I made use of the string ("\n") as a separator to instruct Python to place each element on a new line.  <br />
Then, I used another with statement and the .write() method to update the file: <br/>
<p align="center">
<img src="https://i.imgur.com/4Bwwzo5.png" height="60%" width="60%" alt="LinuxComm"/> <br />
<p align="left">
This time, I used a second argument of "w" with the open() function in the with statement to call the .write() function in the body of the with statement. The .write() function writes string data to a specified file and replaces any existing file content. <br />
In this case I wanted to write the updated allow list as a string to the file "allow_list.txt". This way, the restricted content will no longer be accessible to any IP addresses that were removed from the allow list.
<br />
<br />

<h2>Summary:</h2>

I created an algorithm that removes IP addresses identified in a remove_list variable from the "allow_list.txt" file of approved IP addresses. This algorithm involved opening the file, converting it to a string to be read, and then converting this string to a list stored in the variable ip_addresses. I then iterated through the IP addresses in remove_list. With each iteration, I evaluated if the element was part of the ip_addresses list. If it was, I applied the .remove() method to it to remove the element from ip_addresses.. After this, I used the .join() method to convert the ip_addresses back into a string so that I could write over the contents of the "allow_list.txt" file with the revised list of IP addresses.

</p>
