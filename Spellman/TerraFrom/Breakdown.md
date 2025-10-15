create folder in TheoWAF > class7 > AWS > Terraform > 01-week-14-oct  
  
touch 0-auth.tf  
  
- fork [https://github.com/chewbaccawaf/class7](https://github.com/chewbaccawaf/class7)  
- clone into your project folder  
  
- copy 0-auth template  
  
Aaron's terraform git.ignore:  
curl -O [https://raw.githubusercontent.com/aaron-dm-mcdonald/aws-image-resizer/refs/heads/main/.gitignore](https://raw.githubusercontent.com/aaron-dm-mcdonald/aws-image-resizer/refs/heads/main/.gitignore)  
           
           
ALWAYS SAVE YOUR TERRAFORM FILE BEFORE YOU DEPLOY!!!!!!  
  
terraform init  
  
DO NOT TOUCH OR ERASE THESE TERRAFORM CONFIG FILES!!!!  
DO NOT TOUCH TERRAFORM STATE (.tfstate) FILES!!!  
DO NOT TOUCH THE TERRAFORM GITIGNORE!  
.terraform.lock.hcl  
.terraform  
  
  
  
mkdir 5 && cd 5  
  
touch theo.json   giggity (just kidding dont do this)  
touch 0-auth.tf  
copy and paste from original and SAVE 0-auth.tf  
terraform init  
terraform validate  
terraform plan  
terraform apply