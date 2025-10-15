Confirm AWS key access via CLI is set up properly for Terraform to be able to connect to your AWS console  
   
Make sure terraform is installed via gitbash: 'terraform --version'  
   
.tf is terraform file  
First file that should be created is an authentication file for terraform to authenticate to your AWS console, numbered starting with 0:  
0-auth.tf  
   
Open VSCode via gitbash by typing 'code .'  
   
You can even clone the example repo [https://github.com/tre-6radshaw/class5.git](https://github.com/tre-6radshaw/class5.git) from class 5 to view the .tf files side by side with your own project  
   
Save your terraform file before you deploy it!  
To open terminal in VSCode, go to view > Terminal, or Terminal > New Terminal  
Start terraform via terminal in VScode by typing 'terraform init'  
Notice the folder titled .terraform and file title .terraform.lock.hcl <-- DO NOT TOUCH  
Also do not touch the .gitignore file  
   
At any time, run ls command to see your files and changes in the vscode terminal