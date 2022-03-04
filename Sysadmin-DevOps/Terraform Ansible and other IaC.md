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

---
---
---
---

Ansible

Ansible automate IT tasks using YAML file, installing the agent only in the control machine (and can work on the target servers, is "agentless")

Ansible works with Modules; do their job on the target server and are removed. The modulo made a very specific task "install nginx server" or "start docker contaniner", etc.

### exemple Jenkins Module

```YAML
# Create a jenkins job using basic authentication

- jenkings_job:
    config: "{{ lookup("file", "templates/test.xml") }}"
    name: test
    password: admin
    url: http://localhost:8080
    user: admin

# Delete a jenkins job using the token

- jenkins_job:
    name: test
    token: blablablablabla
    state: absent
    url: localblablabla
    user: admin
    
```

You need make the modules and the correct SEQUENCE for make their work well.

Ansible Playbooks make the tasks easy

```
hosts: databases
remote_user: root
task:
    Modules:
        Arguments of that module:
    Modules:
        Arguments of that module: 
    Modules:
        Arguments of that module:       

```

you can use "vars" to make variables and therefore easy the modules read/write process for humans.

Playbook: can contain many plays, tasks, on diferents hosts.

The hosts are configured with the "ansible hosts file" which contain a "Inventory" it is: all the machines involved in tasks executions.
###### example
```
[webservers] #multiple url or ip
web1.myserver.com
[databases]
10.24.0.7
```

YOU CAN DEPLOY AN ANGIBLE PLAYBOOK FROM TERRAFORM!