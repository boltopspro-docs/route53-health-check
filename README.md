<!-- note marker start -->
**NOTE**: This repo contains only the documentation for the private BoltsOps Pro repo code.
Original file: https://github.com/boltopspro/route53-health-check/blob/master/README.md
The docs are publish so they are available for interested customers.
For access to the source code, you must be a paying BoltOps Pro subscriber.
If are interested, you can contact us at contact@boltops.com or https://www.boltops.com

<!-- note marker end -->

# Route53 Health Check CloudFormation Blueprint

[![BoltOps Badge](https://img.boltops.com/boltops/badges/boltops-badge.png)](https://www.boltops.com)

This blueprint provisions a Route53 Health Check example.

* Several [AWS::Route53::HealthCheck](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-route53-healthcheck.html) properties are configurable with [Parameters](https://lono.cloud/docs/configs/params/). Additionally, properties that require further customization are configurable with [Variables](https://lono.cloud/docs/configs/shared-variables/).

## Usage

1. Add blueprint to Gemfile
2. Configure: configs/route53-health-check values
3. Deploy

## Add

Add the blueprint to your lono project's `Gemfile`.

```ruby
gem "route53-health-check", git: "git@github.com:boltopspro/route53-health-check.git"
```

## Configure

First you want to configure the [configs](https://lono.cloud/docs/core/configs/) files. Use [lono seed](https://lono.cloud/reference/lono-seed/) to configure starter values quickly.

    LONO_ENV=development lono seed route53-health-check

The generated files in `config/route53-health-check` folder look something like this:

    configs/route53-health-check/
    ├── params
    │   └── development.txt
    └── variables
        └── development.rb

## Deploy

Use the [lono cfn deploy](http://lono.cloud/reference/lono-cfn-deploy/) command to deploy. Example:

    lono cfn deploy route53-health-check --sure

You can create specific overrides with specific params and variables files:

    configs/route53-health-check/
    ├── params
    │   └── health-check-demo-2.txt
    └── variables
        └── health-check-demo-2.rb

The stack name will be used as the config. In the deploy command you must specify the `--blueprint` option:

    lono cfn deploy health-check-demo-2 --blueprint route53-health-check --sure

