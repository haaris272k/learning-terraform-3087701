# Terraform learning plan

Goal: explain Terraform clearly in interviews and use it to plan, create, update, and remove AWS infrastructure with confidence.

We will work through each level in the same cycle: explain the idea in plain language, read a small example, run the relevant commands, change it yourself, and answer a few interview questions. Move on when you can explain and repeat the exercise without copying the steps.

| Level | Objective | Practice and evidence of completion | Course alignment |
| --- | --- | --- | --- |
| 0. Setup and safety | Confirm Terraform CLI, AWS identity, region, and repository hygiene. | Run `terraform version` and `aws sts get-caller-identity`; identify the AWS account and region; add appropriate ignores before generating state. | Chapter 1 |
| 1. Foundations | Understand infrastructure as code, declarative configuration, providers, resources, data sources, and the dependency graph. | Explain each block in the starting `main.tf` and `providers.tf`; sketch what Terraform will need to read and create. | Chapters 1–2 |
| 2. Core workflow | Use `init`, `fmt`, `validate`, `plan`, `apply`, `output`, and `destroy`; understand configuration versus state versus real infrastructure. | Run the workflow on a small example; predict a plan, make one change, inspect the new plan, and clean up. | Chapter 2 |
| 3. AWS resource | Write a small AWS configuration with version constraints, a variable, a tag, and an output. | Create a tagged security group with no inbound rules in an existing VPC, inspect it in AWS, change a tag, and destroy it. Then adapt the course EC2 example after checking AMI availability, permissions, and costs. | Chapters 2–3 |
| 4. Reuse and environments | Understand variables, locals, outputs, modules, registry modules, versioning, and separate environment configurations. | Refactor the small example into a local module; pass inputs and read outputs; compare the course's `dev`, `qa`, and `prod` branches. | Chapters 3–4 |
| 5. State and interview readiness | Understand state security, locking, drift, imports, dependencies, troubleshooting, and team workflows. | Diagnose a changed resource, explain when import or a refresh-only plan is needed, design a remote state setup on paper, and answer scenario questions without notes. | Chapter 4 plus current Terraform documentation |

## Repository starting point

- `main` contains one AWS AMI data source and one `aws_instance` resource. The provider is set to `us-west-2`.
- `variables.tf` and `outputs.tf` contain commented examples. The starting configuration has no Terraform or AWS provider version constraint, no `.gitignore`, and no lock file yet.
- Course snapshots are available as remote branches such as `origin/02_05`, `origin/03_04`, `origin/04_06`, and `origin/end`. The README calls the completed branch `final`, but this clone has `end` instead.
- Treat the course code as a lesson snapshot. Review its plan and current provider documentation before applying it to an AWS account, especially the EC2, load balancer, and autoscaling examples.

## Session 1

1. Confirm which terminal has access to `terraform` and `aws`, then verify the AWS identity and intended region without sharing credentials.
2. Explain the four blocks in the starter configuration: `terraform`, `provider`, `data`, and `resource`.
3. Add safe ignores and provider version constraints to a separate practice configuration, then run `terraform fmt`, `terraform init`, and `terraform validate`.
4. Predict what `terraform plan` would propose. Run it only after confirming the identity, region, and example configuration.
5. Finish with short questions on providers, state, and the `init`/`plan`/`apply` sequence.

## References

- [LinkedIn Learning course](https://www.linkedin.com/learning/learning-terraform-15575129)
- [HashiCorp AWS getting started tutorials](https://developer.hashicorp.com/terraform/tutorials/aws-get-started)
- [HashiCorp Terraform CLI tutorials](https://developer.hashicorp.com/terraform/tutorials/cli)
