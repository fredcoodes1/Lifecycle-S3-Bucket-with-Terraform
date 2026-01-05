# Managing AWS S3 Lifecycle and Glacier Integration with Terraform

This project shows how I used Terraform to manage an Amazon S3 lifecycle policy that automatically moves data into cheaper storage over time. The main goal here was to practice infrastructure as code while also understanding how AWS handles long-term storage using Glacier.

---

##  What This Project Does

Using Terraform, I created:

* An S3 bucket with a **unique name**
* A lifecycle rule that:

  * Moves objects to **Standard-IA** after 30 days
  * Moves objects to **Glacier** after 60 days

This helps reduce storage costs automatically without manual intervention.

---

## Tools Used

* AWS CloudShell
* Terraform (installed via tfenv)
* Amazon S3
* Git

---

##  How I Set This Up

### 1️⃣ Installing Terraform

I started by opening **AWS CloudShell** and installing Terraform using `tfenv`.

```bash
git clone https://github.com/tfutils/tfenv.git ~/.tfenv
mkdir ~/bin
ln -s ~/.tfenv/bin/* ~/bin/
tfenv install 1.2.5
tfenv use 1.2.5
```

I then confirmed Terraform was installed correctly:

```bash
terraform --version
```

---

### 2️⃣ Cloning the Lab Repository

Next, I cloned the repository that contains the Terraform configuration:

```bash
git clone https://github.com/pluralsight-cloud/LAB-Managing-AWS-S3-Lifecycle-and-Glacier-Integration-with-Terraform.git
```

Then I navigated into the lifecycle directory:

```bash
cd LAB-Managing-AWS-S3-Lifecycle-and-Glacier-Integration-with-Terraform/lifecycle
```

---

### 3️⃣ Reviewing and Updating the Terraform File

Before running anything, I looked through the Terraform file:

```bash
cat main.tf
```

The lifecycle rule in this file transitions objects:

* To **Standard-IA** after 30 days
* To **Glacier** after 60 days

Because S3 bucket names must be globally unique, I updated the bucket name in the file:

```bash
nano main.tf
```

---

### 4️ Deploying the Infrastructure

Once everything was ready, I initialised Terraform:

```bash
terraform init
```

Then I applied the configuration:

```bash
terraform apply
```

When prompted, I typed `yes` to confirm.

---

## Verifying the Setup

After Terraform finished, I:

1. Opened the AWS Console
2. Navigated to **S3**
3. Selected the newly created bucket
4. Went to the **Management** tab
5. Checked the **Lifecycle rules** section

The lifecycle policy was visible and correctly configured.

---

## Why Terraform Was Useful Here

Terraform made this setup much easier to manage. Everything is defined in code, which means:

* The infrastructure is predictable
* Changes are easy to track
* Resources can be updated or removed safely
* The setup can be reused or shared

This also makes the project easy to version control and audit.


---

## 📘 What I Learned

* How S3 lifecycle policies work in practice
* How to transition data between storage classes automatically
* How Terraform manages AWS resources end to end
* Why infrastructure as code is important for repeatable deployments

---

This project was completed using **AWS CloudShell** and Terraform as part of hands-on cloud learning.

