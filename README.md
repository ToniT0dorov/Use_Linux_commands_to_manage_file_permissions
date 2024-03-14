
<h1>Use Linux commands to manage file permissions</h1>



<h2>Scenario</h2>
You are a security professional at a large organization. You mainly work with their research team. Part of your job is to ensure users on this team are authorized with the appropriate permissions. This helps keep the system secure. 

Your task is to examine existing permissions on the file system. You’ll need to determine if the permissions match the authorization that should be given. If they do not match, you’ll need to modify the permissions to authorize the appropriate users and remove any unauthorized access.

Note: This scenario involves investigating and updating the same file permissions as the ones in the 
Manage authorization
 lab.  You can revisit the lab to get screenshots to include in your portfolio document. If you choose, it's also possible to complete this activity without revisiting the lab by typing your commands in the template.  

<br />


<h2>Supporting materials</h2>

- [Applying the NIST CSF ](https://docs.google.com/document/d/15yCDbDCOAcJw-LTz2DeCA7UeLRfvsf176T6MA6ku6ok/template/preview?usp=sharing)
- [Example of an incident report analysis ](https://docs.google.com/document/d/11eTIo1igTRFrY279DG9tHTO3tB3bugSGyknZxsvY5vI/template/preview?usp=sharing&resourcekey=0-97MA-eOwoGtqcfqky0vjmg)

<h1>File permissions in Linux</h1>
<h2>Project description</h2>
<p>The research team at my organization needs to update the file permissions for certain files and directories within the <i>projects</i> directory. The permissions do not currently reflect the level of authorization that should be given. Checking and updating these permissions will help keep their system secure. To complete this task, I performed the following tasks:</p>
<h2>Check file and directory details</h2>
<p>The following code demonstrates how I used Linux commands to determine the existing permissions set for a specific directory in the file system.</p>
<p align="center">

<img src="https://i.imgur.com/R7GFt7V.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<p>The first line of the screenshot displays the command I entered, and the other lines display the output. The code lists all contents of the projects directory. I used the ls command with the -la option to display a detailed listing of the file contents that also returned hidden files. The output of my command indicates that there is one directory named drafts, one hidden file named .project_x.txt, and five other project files. The 10-character string in the first column represents the permissions set on each file or directory.</p>
<h2>Describe the permissions string</h2>
<p>The 10-character string can be deconstructed to determine who is authorized to access the file and their specific permissions. The characters and what they represent are as follows:</p>
<ul>
<li><strong>1st character</strong>: This character is either a d or hyphen (-) and indicates the file type. If it&rsquo;s a d, it&rsquo;s a directory. If it&rsquo;s a hyphen (-), it&rsquo;s a regular file.</li>
<li><strong>2nd-4th characters</strong>: These characters indicate the read (r), write (w), and execute (x) permissions for the user. When one of these characters is a hyphen (-) instead, it indicates that this permission is not granted to the user.</li>
<li><strong>5th-7th characters: </strong>These characters indicate the read (r), write (w), and execute (x) permissions for the group. When one of these characters is a hyphen (-) instead, it indicates that this permission is not granted for the group.</li>
<li><strong>8th-10th characters: </strong>These characters indicate the read (r), write (w), and execute (x) permissions for other. This owner type consists of all other users on the system apart from the user and the group. When one of these characters is a hyphen (-) instead, that indicates that this permission is not granted for other.</li>
</ul>
<p>For example, the file permissions for project_t.txt are -rw-rw-r--. Since the first character is a hyphen (-), this indicates that project_t.txt is a file, not a directory. The second, fifth, and eighth characters are all r, which indicates that user, group, and other all have read permissions. The third and sixth characters are w, which indicates that only the user and group have write permissions. No one has execute permissions for project_t.txt.</p>
<h2>Change file permissions</h2>
<p>The organization determined that other shouldn't have write access to any of their files. To comply with this, I referred to the file permissions that I previously returned. I determined project_k.txt must have the write access removed for other.</p>
<p>The following code demonstrates how I used Linux commands to do this:</p>
<p align="center">

<img src="https://i.imgur.com/GcIvYAu.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>The first two lines of the screenshot display the commands I entered, and the other lines display the output of the second command. The chmod command changes the permissions on files and directories. The first argument indicates what permissions should be changed, and the second argument specifies the file or directory. In this example, I removed write permissions from other for the project_k.txt file. After this, I used ls -la to review the updates I made.</p>
<h2>Change file permissions on a hidden file</h2>
<p>The research team at my organization recently archived project_x.txt. They do not want anyone to have write access to this project, but the user and group should have read access.</p>
<p>The following code demonstrates how I used Linux commands to change the permissions:</p>
<p align="center">

<img src="https://i.imgur.com/soDavTM.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>The first two lines of the screenshot display the commands I entered, and the other lines display the output of the second command. I know .project_x.txt is a hidden file because it starts with a period (.). In this example, I removed write permissions from the user and group, and added read permissions to the group. I removed write permissions from the user with u-w. Then, I removed write permissions from the group with g-w, and added read permissions to the group with g+r.</p>
<h2>Change directory permissions</h2>
<p>My organization only wants the researcher2 user to have access to the drafts directory and its contents. This means that no one other than researcher2 should have execute permissions.</p>
<p>The following code demonstrates how I used Linux commands to change the permissions:</p>
<p align="center">

<img src="https://i.imgur.com/pZVEa2x.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>The first two lines of the screenshot display the commands I entered, and the other lines display the output of the second command. I previously determined that the group had execute permissions, so I used the chmod command to remove them. The researcher2 user already had execute permissions, so they did not need to be added.</p>
<h2>Summary</h2>
<p>I changed multiple permissions to match the level of authorization my organization wanted for files and directories in the projects directory. The first step in this was using ls -la to check the permissions for the directory. This informed my decisions in the following steps. I then used the chmod command multiple times to change the permissions on files and directories.</p>




