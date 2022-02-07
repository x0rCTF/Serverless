# Serverless framework

**The Serverless Framework** – Builds applications on AWS Lambda and other next-gen cloud services, that auto-scale and only charge you when they run. This lowers the total cost of running and operating your apps, enabling you to build more and manage less.

The Serverless Framework is a command-line tool that uses easy and approachable YAML syntax to deploy both your code and cloud infrastructure needed to make tons of serverless application use-cases. It's a multi-language framework that supports Node.js, Typescript, Python, Go, Java, and more. It's also completely extensible via over 1,000 plugins that can add more serverless use-cases and workflows to the Framework.

Actively maintained by [Serverless Inc](https://www.serverless.com/).

## [](https://github.com/x0rCTF/Serverless/tree/5bb2359947ef1081e0c0abcdfd7db35ffe643b4b#preparing-environment-for-serverless-framework)Preparing environment for Serverless framework

**[nvm](https://github.com/nvm-sh/nvm)** is a version manager for [node.js](https://nodejs.org/en/), designed to be installed per-user, and invoked per-shell. `nvm` works on any POSIX-compliant shell (sh, dash, ksh, zsh, bash), in particular on these platforms: unix, macOS, and [windows WSL](https://github.com/nvm-sh/nvm#important-notes).

## [](https://github.com/x0rCTF/Serverless/tree/5bb2359947ef1081e0c0abcdfd7db35ffe643b4b#installing-the-latest-nodejs-lts-version-using-nvm)Installing the latest Node.js LTS version using NVM

[![](https://github.com/x0rCTF/Serverless/raw/main/images/1%20nvm.png)](https://github.com/x0rCTF/Serverless/blob/main/images/1%20nvm.png)

### [](https://github.com/x0rCTF/Serverless/tree/5bb2359947ef1081e0c0abcdfd7db35ffe643b4b#installing-serverless-framework)Installing Serverless framework

npm install -g serverless

[![](https://github.com/x0rCTF/Serverless/raw/main/images/Pasted%20image%2020220202185259.png)](https://github.com/x0rCTF/Serverless/blob/main/images/Pasted%20image%2020220202185259.png)

### [](https://github.com/x0rCTF/Serverless/tree/5bb2359947ef1081e0c0abcdfd7db35ffe643b4b#creating-a-new-serverless-project-on-aws-using-nodejs)Creating a new serverless project on AWS using Node.js

[![](https://github.com/x0rCTF/Serverless/raw/main/images/3%20Create%20a%20new%20serverless%20project%20on%20AWS%20using%20Node.png)](https://github.com/x0rCTF/Serverless/blob/main/images/3%20Create%20a%20new%20serverless%20project%20on%20AWS%20using%20Node.png)

Here we specified that we will use `aws-nodejs` as a template, which will be stored in `~/Mentorship/`, and the name of our project is `SLSFunc`. `handler.js` - has our JavaScript code. The Lambda function handler is the method in your function code that processes events. When your function is invoked, Lambda runs the handler method. When the handler exits or returns a response, it becomes available to handle another event. `serverless.yml` - the main config file that defines your functions, events and resources. For full config options, check the [docs](https://www.serverless.com/framework/docs/).

### [](https://github.com/x0rCTF/Serverless/tree/5bb2359947ef1081e0c0abcdfd7db35ffe643b4b#deployin-the-code)Deployin the code.

[![](https://github.com/x0rCTF/Serverless/raw/main/images/4%20deploy.png)](https://github.com/x0rCTF/Serverless/blob/main/images/4%20deploy.png)

#### [](https://github.com/x0rCTF/Serverless/tree/5bb2359947ef1081e0c0abcdfd7db35ffe643b4b#how-serverless-deploy-works)How serverless deploy works

When you run `serverless deploy`, two steps are run behind the scenes. Serverless Framework first runs `serverless package` to package your code and build a CloudFormation template. By default, the artifact is generated in the `.serverless/` directory of your project root with the following contents:

1.  A zip file with the Lambda code for your service. Or a zip file for each Lambda function in your service if individual packaging is turned on.
2.  A CloudFormation template file that describes the resources defined in your `serverless.yml`.
3.  A `serverless-state.json` file that is used internally by Serverless Framework.

[![](https://github.com/x0rCTF/Serverless/raw/main/images/Pasted%20image%2020220202194735.png)](https://github.com/x0rCTF/Serverless/blob/main/images/Pasted%20image%2020220202194735.png)

After the artifact is generated, Serverless then deploys this package by:

1.  Uploading the zip file to S3.
2.  Updating the CloudFormation template with S3 paths for the Lambda zip files.
3.  Submitting the template to CloudFormation to kick start the deployment.

[![](https://github.com/x0rCTF/Serverless/raw/main/images/s3.png)](https://github.com/x0rCTF/Serverless/blob/main/images/s3.png)

[![](https://github.com/x0rCTF/Serverless/raw/main/images/CloudFormation.png)](https://github.com/x0rCTF/Serverless/blob/main/images/CloudFormation.png)

### [](https://github.com/x0rCTF/Serverless/tree/5bb2359947ef1081e0c0abcdfd7db35ffe643b4b#invoking-the-request)Invoking the request

We can trigger Lambda functions from the CLI with the following syntax:

sls invoke -f <$FUNCTION> --aws-profile <$PROFILEE>

[![](https://github.com/x0rCTF/Serverless/raw/main/images/inv0ke.png)](https://github.com/x0rCTF/Serverless/blob/main/images/inv0ke.png)

we can also test it locally before deploying within our environment:

sls invoke local -f <$FUNCTION>

[![](https://github.com/x0rCTF/Serverless/raw/main/images/invokelocal.png)](https://github.com/x0rCTF/Serverless/blob/main/images/invokelocal.png)

### [](https://github.com/x0rCTF/Serverless/tree/5bb2359947ef1081e0c0abcdfd7db35ffe643b4b#reading-cloudwatch-logs-using-serverless-cli)Reading Cloudwatch logs using serverless cli

We can read Cloudwatch logs from the CLI with the following syntax:

sls logs -f <$FUNCTION> --aws-profile <$PROFILE>

[![](https://github.com/x0rCTF/Serverless/raw/main/images/logcheckCLI.png)](https://github.com/x0rCTF/Serverless/blob/main/images/logcheckCLI.png)

CloudWatch check:

[![](https://github.com/x0rCTF/Serverless/raw/main/images/CloudWatch.png)](https://github.com/x0rCTF/Serverless/blob/main/images/CloudWatch.png)

### [](https://github.com/x0rCTF/Serverless/tree/5bb2359947ef1081e0c0abcdfd7db35ffe643b4b#modifying-and-updating-the-code)Modifying and updating the code

To modify the code we can use pretty much any text editor, in this case, I am just going to do that using nano.

[![](https://github.com/x0rCTF/Serverless/raw/main/images/7%20modify%20.png)](https://github.com/x0rCTF/Serverless/blob/main/images/7%20modify%20.png)

To update the code we are going to deploy again and invoke the function to see its output.

[![](https://github.com/x0rCTF/Serverless/raw/main/images/8%20update%20%26%20invoke.png)](https://github.com/x0rCTF/Serverless/blob/main/images/8%20update%20%26%20invoke.png)

To confirm that our code is successfully modified and updated, we can also check it on CloudWatch.

[![](https://github.com/x0rCTF/Serverless/raw/main/images/ffff.png)](https://github.com/x0rCTF/Serverless/blob/main/images/ffff.png)

### [](https://github.com/x0rCTF/Serverless/tree/5bb2359947ef1081e0c0abcdfd7db35ffe643b4b#cleaning-up)Cleaning up..

After we successfully created the environment, installed Serverless Framework to create our project, deployed the code, invoked the request, read logs using the serverless CLI and CloudWatch - it is time to clean up!

[![](https://github.com/x0rCTF/Serverless/raw/main/images/clean.png)](https://github.com/x0rCTF/Serverless/blob/main/images/clean.png)
