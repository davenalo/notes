### Terraform


declarative statements for automate and manage infraestructure

is a tool for infrastructure provisioning

>Deploy microservices, spin up servers, docker and db containers... all express as code for deploy it.

>and set security

what is the diference between terraform and ansible?

it sound like the "same tool".
***
Ansible an Terraform are both IaC - Infrastructure as Code

but Terraform is mainly "infrastructure providing"
Ansible es more a "configuration tool", that shines when infrastructure is already up

Terraform is more new, and Ansible more madure and advanced in orchestration.
***

You can use both.

Set up Terraform for think in the better dev environment, then you can deploy it for have this environment in many machines.


### two main parts of terraform
Terraform Core: uses two input sources:
1. Terraform configuration
2. Terraform state

Providers for specific resources:
1. AWS
2. Azure
3. Kubernetes (Pass)
4. Fastly

Terraform example file:

```JSON
#Configure the AWS provider

provider "aws" {

    version = "~ 2.0"
    region = "us-east-1"
}

#Create VPC

resource "awc_vpc" "example" {

    cidr_block = "10.0.0.0/16"
}


```

### ...


### Declarative language

You define the "end state you need"

(similar to SQL i guess?)

#### some commands

execute commands for walk trough different stages

```
refresh     #refresh state
plan        #create an execution plan (a preview,
            non the execution)
apply       #the execution of the plan
destroy     #well, you know.

```
´´´
´´´

*.tfstate <-- the file for the State of terraform (JSON)

it declares the plan for reach the main.tf, the desired state

MANIPULATE IT ONLY THROUGH THE TERRAFORM COMMANDS

THE STATEFILE IS CREATED BY THE APPLY COMMAND, but if you work colaborative, you can configure a shared tfstate file.

use state locking if the update is full, before do the next command. Is important if you work in a team. (not all backends suppor locking)

if you lose your tfstate file enable versioning (like, git, i guess)

you must have an tfstate for each environment (dev, test, production...)

---

IaC trend: gitOPS

---

you must reviewing andtest your terraform states!!!! make teh same you do with code.

