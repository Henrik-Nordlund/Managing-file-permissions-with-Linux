<b>Project description</b><br>
As a security analyst, I am responsible to manage proper authorization and permissions in an ongoing research study from a safety perspective.
The permissions of who gets to read or make changes to certain files in the project folder for one of the researchers, and in some cases even hidden assets, are not set as they should be.
Correcting this will help to keep their system more secure.


<b>Objective: check file and directory details</b><br>
The command pwd displayed in which directory the user wrting this report were, and then the command ls display the content in that directory, i.e., the project subdirectory.
The command cd projects then changed directory to the directory projects. 
The commands ls -l and ls -la then revealed all files and their permission structure.

Permissions of the files in the projects directory shown below as well as the the commands needed to show to get there.
<img src = "https://github.com/Henrik-Nordlund/Managing-file-permissions-with-Linux/blob/f70bc0c7d176ee4771aae93a4bca01433d3124cb/Permissions%20of%20the%20files%20in%20the%20projects%20directory.PNG"/>

<b>Objective: describe the permissions string</b><br>
Each files, or directory, has a 10-character string before it.
One example taken from the screenshot Permissions of the files in the project’s directory shown above:
-rw-rw-rw- for project_k.txt

where (from left to right):<br>
minus sign = simple file (a directory would have been a d)<br>
r = read permission (for user researcher2)<br>
w = writing permission, i.e., make changes to file (for user researcher2)<br>
minus sign = no permission given to execute any executable function (for user researcher2)<br>
r = permission to read the file (for any other member of research_team)<br>
x = writing permission, i.e., make changes to file (for any other)<br>
minus sign = no permission given to execute any executable function (for any other)<br>
r = permission to read the file (for any other)<br>
w = permission to read the file (for any other)<br>
minus sign = no permission to given to execute any executable function (for any other)<br>

This is of course a simple txt file, but it could have been an executable file (such as .exe, .xlsm, or even a python file .py)



<b>Change file permissions</b><br>
The organization determined that none outside the research team should have access to change any of their files. To comply with this, all files were listed, with command ls -la, and as noticable, project_.txt fell short of this. This privilege was removed with the chmod o-w project_.txt command.

<img src ="https://github.com/Henrik-Nordlund/Managing-file-permissions-with-Linux/blob/f70bc0c7d176ee4771aae93a4bca01433d3124cb/Writing%20permissions%20for%20others.PNG"/> 

The research team recently archived the file project_x.txt. No further changes should be made, but both the user and wider research team should be able to read it.
This writing privilege for both groups was removed with the chmod u-w, g-w project_x.txt command, and the reading previlege was reinstated with the command chmod g+r project_x.txt command.

<img src = "https://github.com/Henrik-Nordlund/Managing-file-permissions-with-Linux/blob/f70bc0c7d176ee4771aae93a4bca01433d3124cb/Correcting%20permissions%20for%20an%20hidden%20file.PNG"/>

<b>Change directory permissions</b><br>
There is subdirectory named drafts in the projects folder where none other then then researcher2 should have any access to execute any file, according to my organization. However the research team still had access so thw privilege level x. The command chmod g-x drafts changed this.

<img src = "https://github.com/Henrik-Nordlund/Managing-file-permissions-with-Linux/blob/f70bc0c7d176ee4771aae93a4bca01433d3124cb/Permission%20for%20the%20drafts%20folder.PNG"/>

<b>Summary</b><br>
I changed permissions for multiple files to get the level of authorization my organization desired to match reality in the current project folder, for one of the researchers. Usually that required using the Linux commands ls -l or ls -la to check permission status. Then I changed permissions using the Linux command chmod in appropriate forms as needed.
