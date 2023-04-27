# Terraform

* [Documentation](https://registry.terraform.io/)

### Infrastructure as Code

* Declarative vs imperative

#### Imperative &#x20;

Very procedural and everything must be set in order, eg. making a taco:

`get shell` \
`get beans` \
`get lettuce` \
`get cheese` \
`get salsa`

`put beans on shell` \
`put lettuce on beans` \
`put cheese on lettuce` \
`put salsa on cheese`

#### Declarative

The software already kind of know show to make food, eg.

`food taco "bean-taco" {`&#x20;

&#x20;    `ingredients = [ "beans", "lettuce", "cheese", "salsa"]`

`}`



**What is Terraform?**&#x20;

A tool to automate the deployment and management of infrastructure - any layer of technology a developer consumes without having to depoy or manage it, eg networking, containers

Uses Hashicorp Configuration Language (very like JSON)

Terraform is declarative.

IaC needs to be idempotent & consistent. If nothing has changed in the code and apply it to the same environment, nothing will change in the environment because the code matches the infrastructure that exists

Push/pull configuration - Terraform is a push model, so the configuration that the code has is pushed regularly.

#### Core Components

1. Executable single binary file invoked to run Terraform
2. Configuration files typically .tf files
3. Provider plugins

#### Terraform Object Types

1. Provider - eg. Azure, AWS
2. Resources - things you create in a target environment and are bulk of code each resource has a provider. eg. a resource could be an EC2 network
3. Data sources - associated with a provider to eg. list of availability zones in a region

#### Terraform Syntax

`block_type "label" "name_label" {`&#x20;

&#x20;   `key = "value"`

&#x20;   `nested_block {`

&#x20;       `key = "value"`

&#x20;   `}`

`}`

eg.

resource "aws\_instance" "web\_server" { name = "web-server"

```
resource "aws_instance" "web_server" {
    name = "web-server"
    ebs_volume {
	size = 40
    }
}
```

Terraform Object Reference:&#x20;

`<resource_type>.<name_label>`

`aws_instance.web_server.name`

#### Terraform Workflow

1. `terraform init:` Fetches provider plugins, looks for config files inside current working directory and checks for plugins, then downloads them. Also needs to store state data about config
2. `terraform plan`: Terraform will look at current config and contents of state data, determine the differences between the two and then plan how to update one to the other. You can check this to see what terraform is planning to do and approve.
3. `terraform apply`: Executes changes from plan with the provider plugins
4. `terraform destroy:`If you are done with the environment, this will destroy everything in the target envitronmet

#### Variables and outputs

_Input variables:_ used to pass information to a terraform config. They are defined inside the config and supplied when terraform is executed

_Local values_: values inside the program that are computed inside the program (like regular variable)

_Output values:_ output depends on what's constructed or supplied to the file

Variables are defined inside a variable block

`variable "name_label" {`&#x20;

&#x20;   `type = value`&#x20;

&#x20;   `description = "value"`&#x20;

&#x20;   `default = "value"`&#x20;

&#x20;   `sensitive = true | false`&#x20;

`}`

If sensitive terraform will not log the variable

Example:&#x20;

`variable "aws_region" {`&#x20;

&#x20;   `type = string`&#x20;

&#x20;   `description = "Region to use for AWS resources"`&#x20;

&#x20;   `default = "us-east-1"`&#x20;

&#x20;   `sensitive = false`&#x20;

`}`

Variable references: `var.<name_label>`, so the example would be `var.aws_region`

#### Terraform data types

* Primitive - String, number, boolean&#x20;
* Collection - List, set, map&#x20;
* Structural - tuple, object

Local values are values computed inside the config Starts with keyword locals

locals { key = value }

eg.

`locals {`&#x20;

&#x20;   `instance_prefix = "globo"`&#x20;

&#x20;   `common_tags = {`&#x20;

&#x20;       `company = "Globomantics"`&#x20;

&#x20;       `project = var.project`

&#x20;   `}`&#x20;

`}`

Name of each key much be unique within variable.

`local.<name_label>` eg. `local.instance_prefix` or `local.common_tags.company`

#### Terraform Locals

Terraform locals are named values which can be assigned and used in your code. Mainly used to reduce duplication and increase readability.

#### Locals vs. Variables

Local is only accessible within the local module vs. a Terraform variable is scoped globally. A local also can't change its value once assigned, whereas can be manipulated via expressions.

* [Article on locals](https://spacelift.io/blog/terraform-locals)

#### Outputs syntax&#x20;

Output values are how we get information out of terraform. They are printed to the terminal window at the end of a configuration run.

`output "name_label" {`&#x20;

&#x20;   `value = output_value`&#x20;

&#x20;   `sensitive = true | false`&#x20;

`}`&#x20;

`output "public_dns_hostname" {`&#x20;

&#x20;   `value = aws_instance.web_server.public_dns`&#x20;

`}`

#### Validate command&#x20;

Before applying update use the validate command to ensure the config syntax is correct

Run: `terraform init`, `terraform validate`

Errors and the line of errors get printed

#### How to set Variable Values

1. Default argument
2. Set on the command line with -var flag
3. Have variable values in a file you can use on command line with -var-file flag
4. If there's a file called terraform.tfvars/terraform.tfvars.json terraform will use that
5. file ending in .auto.tfvars or auto.tfvars.json
6. Environment variable TF\_VAR\_

If you set the variable in different places there's an order of precedence: TF\_VAR .tfvars .auto.tfvars -var-file flag -var flag command line prompt

So that last one will override all of them

#### Resources dependencies&#x20;

Terraform creates resources in parallel and can automatically handle resources dependencies in most cases using implicit dependencies. If not specified, Terraform can’t know if a resource must be created before or after another one if there is no clear relationship within the Terraform code itself. To create a relationship between multiple resources, we must always use implicit or explicit dependencies between resources.

Implicit dependencies are those in which a resource references another resource through its name eg. example\_folder.environment.name, rather than just using the string

Sometimes, a resource can depend on another one but not reference it. In this case, we can create an explicit dependency using the depends\_on key in a Terraform resource. Explicitly specifying a dependency is only necessary when a resource relies on some other resource’s behavior but doesn’t access any of that resource’s data in its arguments.

#### Terraform State

Terraform State data is the may terraform maps what's in your config to the actual deployment on target environment The state data is stored in JSON. Stores resources mappings and metadata Each plan and apply refreshes this state data Stored locally by default, but a remote location can be specified for it too State is in a .tfstate file

#### State commands&#x20;

* terraform state list - see all state resources
* terraform state show \<address> - show specific resource
* terraform state mv \<source> \<destination> - Move an item in state
* terraform state rm \<address> - remove an item in state
