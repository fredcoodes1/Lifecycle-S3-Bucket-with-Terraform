# Lifecycle-S3-Bucket-with-Terraform
Managing AWS S3 Lifecycle and Glacier Integration with Terraform

In this project I use Terraform to manage S3 Lifecycle and Glacier integration

First thing I do is go to the CloudShell.

I then run the command: git clone https://github.com/tfutils/tfenv.git ~/.tfen which will clone the repo that hosts terraform

Next you run the following commands which will install Terraform:

mkdir ~/bin

ln -s ~/.tfenv/bin/* ~/bin/

tfenv install 1.2.5

And then the final command:

tfenv install 1.2.5 will confirm if Terraform has been installed.

Press enter or click to view image in full size

You then run:
git clone https://github.com/pluralsight-cloud/LAB-Managing-AWS-S3-Lifecycle-and-Glacier-Integration-with-Terraform.git

This will bring in the repo that will host the terraform file, that you will use to create your S3 bucket and the lifecycle policy.

You then change into the new Git repo with this command: cd LAB-Managing-AWS-S3-Lifecycle-and-Glacier-Integration-with-Terraform/

Then CD into the lifecycle folder: cd lifecycle

Press enter or click to view image in full size

I then type the command cat main.tf to look at the file we will be using

Here you can see that after 30 days it’s going to transition any objects in the S3 bucket into a storage class called ‘Standard IA’ and after 60 days it will move to a storage class called “Glacier”

In order for the script to work you need to change the bucket name to something that is globally unique or otherwise you will get an error.

To do that you want to run the command nano main.tf

Press enter or click to view image in full size

Now that’s done we can actually run the script!

The first command is ‘terraform init’ which will create a working directory

Then the next command is ‘terraform apply’ when you run this you will see a message prompting you to enter a value in which you will type ‘yes’ and then type enter.

Press enter or click to view image in full size

With that you should have your S3 bucket created

If you go to S3 buckets, you shall see the bucket your created and go to management tab go on archive and then you should be to see the lifecycle rule.

Press enter or click to view image in full size

Terraform benefits the lifecycle by making infrastructure predictable, safe to change, easy to scale, and easy to retire all while keeping it version controlled and auditable.
