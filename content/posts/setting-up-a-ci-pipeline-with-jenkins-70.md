---
title: "Setting Up a CI Pipeline with Jenkins DRAFT"
slug: "setting-up-a-ci-pipeline-with-jenkins"
tags: ["Jenkins", "Docker", "Git", "apprenticeship"]
date: 2018-05-11
---

By focusing on continuous integration this week, I totally get out of my comfort zone, it's been a tough week. Honestly, I am writing this blog post while my computer is burning because of the Chrome with 30+ tabs opened.

I tried to create a Jenkins pipeline which is triggered by commits in the repository. It was way easier on TravisCI, since Travis handles almost everything for you. From where I stand, I don't exactly understand why Jenkins is complex this much. Maybe it's more configurable, I will find out in future blog posts.

First thing I've needed was to create a connection between our git server and Jenkins instance. It turned out to be an easy step, after struggling for two hours. As always, it gets easier after you learn how to do it.

To create a pipeline in Jenkins, you need to create a `Jenkinsfile` in the root of the project. You need to use Groovy scripting language to define the steps for the pipeline. It seemed intimidating at first, but Jenkins has good documentation, at least for basic steps. After establishing the connection between git and Jenkins it was too easy to checkout the latest version. A simple `checkout scm` comment successfully pulls the code from repository.

According to Jenkins documentation, following code snippet creates stages on your project.

```groovy
pipeline {
  agent any

  stages {
    stage('Build') {
      steps {
          echo 'Building..'
      }
    }
    stage('Test') {
      steps {
          echo 'Testing..'
      }
    }
    stage('Deploy') {
      steps {
          echo 'Deploying....'
      }
    }
  }
}
```

Applying this code to my Jenkinsfile yielded my first victory. After committing this, you will have first successful build with visual stage definitions.

I naively added the `sh 'npm install'` inside of the `testing` stage, of course, it failed. I realized the fact that I need to define environment which code snippet run on. After a quick search, I've installed the Node plugin and I've configured it to the version I need. In modern CI tools, like Travis, they find out the environment for you, you only need to configure if you need a specific version of the environment. This step exposed me a process done under the hood by other tools, it's important to realize this facts in order to grasp the concept itself.

I removed my `build` stage since I don't have anything other than `npm install` and my `test` stage became like this;

```groovy
stage('Test') {
  steps {
    dir('core') {
      nodejs(nodeJSInstallationName: 'Node-9.11.1') {
        sh 'npm install'
        sh 'npm run test || true'
      }
    }
  }
}
```

Since I use a monorepo, a wrapper repo with related projects, I need to move a spesific folder with `dir` command. Usage of this command felt counter-intuitive to me, I tried to use it as follows;

```groovy
dir('core')
nodejs(nodeJSInstallationName: 'Node-9.11.1') {
  sh 'npm install'
  sh 'npm run test || true'
}
```

You need to unlearn, before learn something new. Intuitiveness depends on your experience. Upside of this syntax is, you don't need to write something equivalent to `cd ..` in order to return to the previous folder. With this syntax, program knows exactly when to return to the previous folder.

Being able to run commands with `sh`, made me capable of run tests and create containers. After creating the container of my application, I was ready to deploy, until I ask a question to myself. It took hours of thinking and surfing on the internet to finally have an idea.

> Should I run the tests and create the container, or should I create the container first, then run the tests inside of the container?

I prefer the second approach, at least for now. If you don't create your container first, you need to provide your test environment via Jenkins. This increases the amount of configuration, but it's not that bad. The problem here is, if you change your dependency, even the node version, you also need to change that dependency in Jenkins. It feels like duplication, isn't it?

On the other hand, I don't want to increase my container size by including test dependencies on it. I found two separate `Dockerfile`s in some projects to overcome this issue, they simply create different containers for test project and the production. It seems reasonable, but I believe I need to run the tests on the container which will hit the production. I need to dig more to have a conclusion on this.
