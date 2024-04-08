# Architecture Decision Records

## CDK-001 Use TypeScript

Choose _working with the AWS CDK in TypeScript_ for the following reasons:

1. AWS CDK Toolkit is a Node.js application itself hence using AWS CDK in TypeScript will not introduce additional ecosystem requirements
2. "_The AWS CDK is developed in one language, TypeScript. To support the other languages, the AWS CDK utilizes a tool called JSII to generate language bindings._"[¹](https://docs.aws.amazon.com/cdk/v2/guide/languages.html)

    This means that TypeScript is the first-class citizen considering features, documentation, support, and examples.

    Why settle for less?

Read more at [Working with the AWS CDK in supported programming languages](https://docs.aws.amazon.com/cdk/v2/guide/work-with.html).

## CDK-002 Use package manager npm

When initializing a repository with `cdk init app --language typescript`, the package manager `npm` is chosen and pre-configured for the initialized repository.

Avoid changing the pre-configured package manager for the following reasons:

1. It would require additional code after initialization
2. It would introduce another dependency/prerequisite
3. It would need additional documentation that deviates from the established original documentation
4. It might introduce the need for additional adaption when using samples

## CDK-003 Use Powertools for AWS Lambda Functions

Avoid undifferentiated heavy lifting when you can just use the layer and configure it for your needs!

From <https://docs.powertools.aws.dev/lambda/typescript/latest/>:

> Powertools for AWS Lambda (TypeScript) is a developer toolkit to implement Serverless best practices and increase developer velocity.
>
> [...]
>
> | Utility | Description |
> | ------- | ----------- |
> | Tracer | Decorators and utilities to trace Lambda function handlers, and both synchronous and asynchronous functions |
> | Logger | Structured logging made easier, and a middleware to enrich structured logging with key Lambda context details |
> | Metrics | Custom Metrics created asynchronously via CloudWatch Embedded Metric Format (EMF) |
> | Parameters | High-level functions to retrieve one or more parameters from AWS SSM Parameter Store, AWS Secrets Manager, AWS AppConfig, and Amazon DynamoDB |
> | Idempotency | Class method decorator, Middy middleware, and function wrapper to make your Lambda functions idempotent and prevent duplicate execution based on payload content. |
> | Batch Processing | Utility to handle partial failures when processing batches from Amazon SQS, Amazon Kinesis Data Streams, and Amazon DynamoDB Streams. |
>
> [...]

## CDK-004 Use node version manager (nvm)

> `nvm` allows you to quickly install and use different versions of node via the command line.
>
> -- <https://github.com/nvm-sh/nvm?tab=readme-ov-file#intro>

This allows the installation and use of multiple Node.js versions on the same machine at the same time.

For installation instructions, see [Install Node Version Manager](https://github.com/nvm-sh/nvm?tab=readme-ov-file#installing-and-updating) (0.39.7 or newer).
