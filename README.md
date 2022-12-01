# GithubActionsPractice
 
### Before the practice make sure that the maven JDK and your local JDK are the same!

![](/Docs/Practice.png)

### First we need to create a workflow file in the main branch:

``` 
file: .github/workflows/main.yml
```

### In main.yml file we start giving the actions name to the file and use the "pull request" event in the action "on"

``` yaml
name: CI Testing Action

on:
  pull_request:
    branch:
    - main
```

### Configures the job to run on the latest version of an Ubuntu Linux runner. This means that the job will execute on a fresh virtual machine hosted by GitHub.

``` yaml
jobs:
  build:
    runs-on: ubuntu-latest
```

### Groups together all the steps that run in the check-bats-version job. Each item nested under this section is a separate action or shell script. The uses keyword specifies that this step will run v3 of the actions/checkout action. This is an action that checks out your repository onto the runner, allowing you to run scripts or other actions against your code . You should use the checkout action any time your workflow will run against the repository's code.

``` yaml
    steps:
    - uses: actions/checkout@v3
    - name: Set up JDK 11
      uses: actions/setup-java@v3
      with:
        java-version: '11'
        distribution: 'temurin'
        cache: maven
```
### This step uses the actions/setup-java@v3 action to install the specified version of java. This puts both the node and npm commands in your PATH.

``` yaml
    - name: Build with Maven
      run: mvn -B package --file GithubActionsPractice/pom.xml
```

### The run keyword tells the job to execute a command on the runner. In this case, you are using mvn to install the file testing package.
<hr>

## This should be the result:

``` yaml
name: Java CI with Maven

on:
  pull_request:
    branch:
    - main
  push:
    branch:
    - main

jobs:
  build:

    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v3
    - name: Set up JDK 11
      uses: actions/setup-java@v3
      with:
        java-version: '11'
        distribution: 'temurin'
        cache: maven

    - name: Build with Maven
      run: mvn -B package --file poobank/pom.xml
```