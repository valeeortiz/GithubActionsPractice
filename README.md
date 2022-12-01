# GithubActionsPractice
 
<<<<<<< Updated upstream
## Before the practice make sure that the maven JDK and your local JDK are the same!

![](/Docs/Practice.png)

## 
=======
### Before the practice make sure that the maven JDK and your local JDK are the same!

![](/Docs/Practice.png)

### First we need to create a workflow file in the main branch:

``` 
file: .github/workflows/main.yml
```

### In main.yml file we start giving the actions name to the file and use the "pull request" event in the action "on" in the branch "main"

``` yaml
name: CI Testing Action

on:
  pull_request:
    branch:
    - main
```

### In main.yml file we start giving the actions name to the file and use the "pull request" event in the action "on" in the branch "main"

``` yaml
name: CI Testing Action

on:
  pull_request:
    branch:
    - main
```
>>>>>>> Stashed changes
