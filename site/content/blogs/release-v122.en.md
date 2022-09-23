---
title: 'AWS Copilot v1.22: Try out IAM Permission Boundaries and more!'
twitter_title: 'AWS Copilot v1.22'
image: ''
image_alt: ''
image_width: '1051'
image_height: '747'
---

# AWS Copilot v1.22: Try out IAM Permission Boundaries and more!

Posted On: Sep 27, 2022

The AWS Copilot core team is announcing the Copilot v1.22 release.  
Special thanks to [@jterry75](https://github.com/jterry75), [@gabrielcostasilva](https://github.com/gabrielcostasilva), [@shingos](https://github.com/shingos), and [@hkford](https://github.com/hkford) who contributed to this release.
Our public [сommunity сhat](https://gitter.im/aws/copilot-cli) is growing and has over 300 people online and over 2.4k stars on [GitHub](http://github.com/aws/copilot-cli/).
Thanks to every one of you who shows love and support for AWS Copilot.

Copilot v1.22 brings several new features and improvements:

- **IAM Role Permissions Boundary**: [See detailed section](#iam-role-permissions-boundary).
- **FIFO SNS/SQS**: [See detailed section](#fifo-snssqs).
- **CloudFront TLS Termination**: You can now use CloudFront to perform faster TLS termination! [See detailed section](#cloudfront-tls-termination).

???+ note "What’s AWS Copilot?"

    The AWS Copilot CLI is a tool for developers to build, release, and operate production ready containerized applications on AWS.
    From getting started, pushing to staging, and releasing to production, Copilot can help manage the entire lifecycle of your application development.
    At the foundation of Copilot is AWS CloudFormation, which enables you to provision infrastructure as code.
    Copilot provides pre-defined CloudFormation templates and user-friendly workflows for different types of micro service architectures,
    enabling you to focus on developing your application, instead of writing deployment scripts.

    See the section [Overview](../docs/concepts/overview.en.md) for a more detailed introduction to AWS Copilot.

## IAM Role Permissions Boundary

## FIFO SNS/SQS

## CloudFront TLS Termination

You can now configure your env manifest to have CloudFront terminate TLS for your Load Balanced Web Services (LBWS):

```yaml
cdn:
  tls_termination: true
```

The configuration above uses CloudFront for TLS termination, which means the traffic from `CF → ALB → ECS` will be HTTP only. This brings faster TLS termination and shorter page loading for viewers, since the CloudFront edges are usually geographically closer to them.

However, if your services have HTTPS enabled (you have either an app domain or imported certificates in the environment), you must turn off ALB http redirect by updating your [Load Balanced Web Service manifests](../docs/manifest/lb-web-service.en.md).

```yaml
http:
  redirect_to_https: false
```

And then redeploy the services with `svc deploy` before using `env deploy` to enable CloudFront TLS termination.

## What’s next?

Download the new Copilot CLI version by following the link below and leave your feedback on [GitHub](https://github.com/aws/copilot-cli/) or our [Community Chat](https://gitter.im/aws/copilot-cli):

- Download [the latest CLI version](../docs/getting-started/install.en.md)
- Try our [Getting Started Guide](../docs/getting-started/first-app-tutorial.en.md)
- Read full release notes on [GitHub](https://github.com/aws/copilot-cli/releases/tag/v1.21.0)