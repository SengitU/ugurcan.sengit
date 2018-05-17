---
title: "Providing AWS Credentials with Jenkins"
slug: "providing-aws-credentials-with-jenkins"
tags: ["CI", "AWS", "Jenkins", "apprenticeship"]
date: 2018-05-16
---

I needed to create a connection with the AWS services in order to receive the data. It's easy to create a connection if you have your credentials. Since every individual's credentials are unique, you should avoid committing them. There are various ways to overcome this problem, you can create a file and use that file to provide credentials in development, so that everyone can use their own credentials. Another way to provide these credentials is using the environmental variables.

We wanted to do both, providing a file makes development easier, but in the production, we should avoid using our own credentials. On the other hand, production credentials are usually restricted for couple people. We've needed a solution which would work both with the file and with the environmental variables. To overcome this, we've used a great module called [dotenv](https://www.npmjs.com/package/dotenv). `dotenv` module injects the content of the `.env` file to the environmental variables for development purposes.

How would you store these credentials in Jenkins? It was quite easy actually, but still, it was hard until I learnt how to do it. In order to provide these secret credentials from Jenkins, you can apply following steps;

* In your Jenkins home page, select the project
* Select **Pipeline Syntax** from the menu
* Select **Snippet Generator** from the menu

Snippet generator will help us to generate necessary groovy script to provide the variables. In the snippet generator;

* From **Sample Steps** menu, select **withCredentials**
* In **Bindings** section, select **Add** to create a new binding
* Select the type of the binding, in my case, it was **Secret Text**
* Provide a variable name for the secret you want to use
* Provide the secret text to Jenkins by clicking **Add** button

By following the steps above, you can inject your secrets as variables. After creating your variables, click the **Generate Pipeline Script** and let the Jenkins do the work for you. In my case, Jenkins created a script as follows;

```groovy
withCredentials([
  string(credentialsId: 'xxx', variable: 'awsAccessKeyId'),
  string(credentialsId: 'yyy', variable: 'awsSecretAccessKey')
]) {
  echo awsAccessKeyId
  echo awsSecretAccessKey
}
```

Inside of the `withCredentials` scope provided by the Jenkins, you will be able to use these variables. I've provided these variables to my Docker container with `-e` flag.
