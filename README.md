
# Serverless framework
**The Serverless Framework** – Build applications on AWS Lambda and other next-gen cloud services, that auto-scale and only charge you when they run. This lowers the total cost of running and operating your apps, enabling you to build more and manage less.

The Serverless Framework is a command-line tool that uses easy and approachable YAML syntax to deploy both your code and cloud infrastructure needed to make tons of serverless application use-cases. It's a multi-language framework that supports Node.js, Typescript, Python, Go, Java, and more. It's also completely extensible via over 1,000 plugins that can add more serverless use-cases and workflows to the Framework.

Actively maintained by [Serverless Inc](https://www.serverless.com/).

## Preparing environment for Serverless framework

**[nvm](https://github.com/nvm-sh/nvm)** is a version manager for [node.js](https://nodejs.org/en/), designed to be installed per-user, and invoked per-shell. `nvm` works on any POSIX-compliant shell (sh, dash, ksh, zsh, bash), in particular on these platforms: unix, macOS, and [windows WSL](https://github.com/nvm-sh/nvm#important-notes).

## Installing the latest Node.js LTS version using NVM
![[1 nvm.png]]


### Installing Serverless framework 

```bash
npm install -g serverless
```

![[Pasted image 20220202185259.png]]


### Creating a new serverless project on AWS using Node.js

![[3 Create a new serverless project on AWS using Node.png]]

Here we specified that we will use `aws-nodejs` as template, which will be stored in `~/Mentorship/`, and the name of our project is `SLSFunc`. 
`handler.js` - has our JavaScript code. Event handlers are **the JavaScript code that invokes a specific piece of code when a particular action happens on an HTML element**. The event handler can either invoke the direct JavaScript code or a function.
`serverless.yml` - the main config file for your our. For full config options, check the [docs](https://www.serverless.com/framework/docs/).

### Deployin the code.

![[4 deploy.png]]

#### How serverless deploy works
When you run `serverless deploy`, two steps are run behind the scenes. Serverless Framework first runs `serverless package` to package your code and build a CloudFormation template. By default, the artifact is generated in the `.serverless/` directory of your project root with the following contents:

1.  A zip file with the Lambda code for your service. Or a zip file for each Lambda function in your service if individual packaging is turned on.
2.  A CloudFormation template file that describes the resources defined in your `serverless.yml`.
3.  A `serverless-state.json` file that is used internally by Serverless Framework.

After the artifact is generated, Serverless then deploys this package by:

1.  Uploading the zip file to S3.
2.  Updating the CloudFormation template with S3 paths for the Lambda zip files.
3.  Submitting the template to CloudFormation to kick start the deployment.

![[Pasted image 20220202194735.png]]

### Invoking the request

We can trigger Lambda functions from the CLI with the following syntax:

```bash
sls invoke -f <$FUNCTION> --aws-profile <$PROFILEE>
```

or locally:

```bash
sls invoke local -f <fuction>
```

![[5 invoke.png]]

### Reading Cloudwatch logs using serverless cli

 We can read Cloudwatch logs from the CLI with the following syntax:
 ```bash
 sls logs -f <$FUNCTION> --aws-profile <$PROFILE>
 ```


![[6 Get Cloudwatch logs from Serverless cli.png]]

### Modifying and updating the code


![[7 modify .png]]


![[8 update & invoke.png]]
