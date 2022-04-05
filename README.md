# AWS Amazon Linux EC2 Instance

Terraform module to create Security Group and Amazon Linux 2 EC2 instance

## Usage with minimal customisation

This will generate 3 characters random string and append it to the IAM role name and instance profile name.
IAM role name = "ssm-role-nnn"
IAM instance profile name = "ssm-instance-profile-nnn"

```hcl
module "ssm_instance_profile" {
  source  = "bayupw/ssm-instance-profile/aws"
  version = "1.0.0"
}

resource "aws_instance" "ec2_instance" {
  # ...
  iam_instance_profile = module.ssm_instance_profile.aws_iam_instance_profile
  # ...
}

```

## Usage with name customisation

```hcl
module "ssm_instance_profile" {
  source  = "bayupw/ssm-instance-profile/aws"
  version = "1.0.0"

  random_suffix = true
  random_string_length = 4
  ssm_instance_role_name = "my-ssm-role"
  ssm_instance_profile_name = "my-ssm-instance-profile
}

resource "aws_instance" "ec2_instance" {
  # ...
  iam_instance_profile = module.ssm_instance_profile.aws_iam_instance_profile
  # ...
}
```

## Contributing

Report issues/questions/feature requests on in the [issues](https://github.com/bayupw/terraform-aws-amazon-linux-2/issues/new) section.

## License

Apache 2 Licensed. See [LICENSE](https://github.com/bayupw/terraform-aws-amazon-linux-2/tree/master/LICENSE) for full details.