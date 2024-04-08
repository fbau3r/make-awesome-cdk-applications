# Make awesome AWS CDK applications

This repository is a curated collection of resources that depict my personal best practices in creating AWS CDK applications.

For some Architecture Decision Records about this subject, see file [Architecture Decision Records](./docs/architecture-decision-records.md).

## Table of contents

- [AWS CDK Toolkit](#aws-cdk-toolkit)
- [Initialize repository](#initialize-repository)
- [Templates for README](#templates-for-readme)
- [Update package dependencies](#update-package-dependencies)
- [Useful AWS CDK documentation links](#useful-aws-cdk-documentation-links)

## AWS CDK Toolkit

Read more about [AWS CDK Toolkit](https://docs.aws.amazon.com/cdk/v2/guide/cli.html).

### Install AWS CDK Toolkit

```bash
npm install -g aws-cdk
```

### Update AWS CDK Toolkit

```bash
npm update -g aws-cdk
```

### Check installed AWS CDK Toolkit version

You can check the globally installed package version with this command:

```bash
npm list -g aws-cdk
```

## Initialize repository

I always certainly start a new repository as described in the following steps.

> _♻️ Shortcut:_
>
> Use this "one-liner" to execute _Step 1_ to _Step 5_ altogether.
>
> Replace "new-project" with your desired project directory name. Use `Ctrl-W` to _delete word on the left_.
>
> ```bash
> _f{
>   project_dir="$1"
>   mkdir ${project_dir:?} && cd $_
>   git init && git commit --allow-empty -m "Initial commit"
>   cdk init app --language typescript &&\
>   npm remove @types/jest jest ts-jest &&\
>   rm -fR test/ jest.config.js
> }; _f "new-project"
> ```
>
> _Continue with **Step 6**._

1. Create directory and change into it

    ```bash
    mkdir new-project && cd $_
    ```

2. Initialize git repository

    ```bash
    git init
    ```

3. Create empty initial commit

    ```bash
    git commit --allow-empty -m "Initial commit"
    ```

4. Initialize CDK repository

    ```bash
    cdk init app --language typescript
    ```

5. _🫣 Optional:_ Remove jest tests

    ```bash
    npm remove @types/jest jest ts-jest &&
    rm -fR test/ jest.config.js
    ```

    Instead, you might want to read more at [Testing constructs](https://docs.aws.amazon.com/cdk/v2/guide/testing.html).

6. _✍️ Manual:_ Open code files, format them in VS Code then commit as `Format code`

7. _✍️ Manual:_ Configure attributes `stackName` and `tags` in `StackProps`.

8. _🫣 Optional:_ Use custom `StackProps` if you see fit.

9. _✍️ Manual:_ Update README: Add title and general description. Copy from section [Templates for README](#templates-for-readme) as you see fit.

## Templates for README

Why bother writing README sections over and over again?
Copy, paste then adapt:

### Prerequisites Template

````markdown
## Prerequisites

- Install or upgrade
    [Node.js](https://nodejs.org/en/download/)
    20.11.1 or later. We recommend a version in
    [active long-term support](https://nodejs.org/en/about/releases/).
- Install or upgrade the AWS CDK CLI.
    For installation instructions, see
    [Install the AWS CDK](https://docs.aws.amazon.com/cdk/v2/guide/getting_started.html#getting_started_install).
- Establish authentication with AWS.
    For general instructions, see
    [Authentication with AWS](https://docs.aws.amazon.com/cdk/v2/guide/getting_started.html#getting_started_auth).
- Install package dependencies:

    ```bash
    npm install
    ```
````

### Deploy Template

````markdown
Ensure [prerequisites](#prerequisites) are met.

To deploy CDK application changes, run these commands:

1. _**Recommended**_: preview your deployment with this command:

    ```bash
    cdk diff
    ```

2. Deploy your stack with this command:

    ```bash
    cdk deploy
    ```

3. A successful deployment should reach status `CREATE_COMPLETE` or `UPDATE_COMPLETE`.

4. Congratulations! 🎉

    Your stack was successfully deployed!

    Inspect the results in _CloudFormation AWS Console_.
````

### Cleanup Template

````markdown
## Cleanup

Ensure [prerequisites](#prerequisites) are met.

If you want to **remove** the CDK application changes, run this command:

```bash
cdk destroy
```
````

## Update package dependencies

Generally speaking, `npm install` installs the latest version of everything that matches the ranges in `package.json`.

Still, you might want to update your `package.json` file and set new minimum versions for the installed modules. Use [npm-check-updates](https://www.npmjs.com/package/npm-check-updates) for this:

```bash
npx npm-check-updates --upgrade
```

Read more about [Installing and updating dependencies](https://docs.aws.amazon.com/cdk/v2/guide/work-with-cdk-typescript.html#work-with-cdk-typescript-dependencies).

## Useful AWS CDK documentation links

In [AWS Cloud Development Kit (AWS CDK) v2 documentation](https://docs.aws.amazon.com/cdk/v2/guide/home.html) there are some very helpful sections I revisit rather frequently:

- [**API reference**](https://docs.aws.amazon.com/cdk/api/v2/docs/aws-construct-library.html)
- [**Best practices** for developing and deploying cloud infrastructure with the AWS CDK](https://docs.aws.amazon.com/cdk/v2/guide/best-practices.html)
- [**Troubleshooting** common AWS CDK issues](https://docs.aws.amazon.com/cdk/v2/guide/troubleshooting.html)
- [AWS CDK concepts](https://docs.aws.amazon.com/cdk/v2/guide/core_concepts.html)
