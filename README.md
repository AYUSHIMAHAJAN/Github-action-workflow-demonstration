# Introduction:

GitHub Actions is a continuous integration and continuous delivery (CI/CD) platform that allows you to automate your build, test, and deployment pipeline.These Actions are used to create workflows that run tests whenever you push a change to your repository, or that deploy merged pull requests to production.Setting up Continuous Integration (CI) ensures that code is automatically built and tested whenever changes are pushed to the repository.I will be focusing on Github Actions that create Workflows

# What are Workflows?

A workflow is a configurable automated process that will run one or more jobs. Workflows are defined by a YAML file checked into your repository and will run when triggered by an event in your repository, or they can be triggered manually, or at a defined schedule.
Workflows are defined in the .github/workflows directory in a repository, and a repository can have multiple workflows, each of which can perform a different set of tasks. For example, you can have one workflow to build and test pull requests, another workflow to deploy your application every time a release is created, and still another workflow that adds a label every time someone opens a new issue.


# Basics of Workflows:
A workflow must contain the following basic components:<br>
* One or more events that will trigger the workflow.
* One or more jobs, each of which will execute on a runner machine and run a series of one or more steps.
* Each step can either run a script that you define or run an action, which is a reusable extension that can simplify your workflow. 

# Let’s start with creating first workflow:
1)In a repository on GitHub.com, create a workflow file called github-actions-demo.yml in the .github/workflows directory. 
# To do this:
* If the .github/workflows directory already exists, navigate to that directory on GitHub, click Add file, then click Create new file, and name the file github-actions-demo.yml.
* If your repository doesn't have a .github/workflows directory, go to the main page of the repository on GitHub, click Add file, then click Create new file, and name the file .github/workflows/github-actions-demo.yml. This creates the .github and workflows directories and the github-actions-demo.yml file in a single step.

2)Copy the following YAML contents into the github-actions-demo.yml file for ex:<br>

name: GitHub Actions Demo<br>
run-name: ${{ github.actor }} is testing out GitHub Actions 🚀 <br>
on: [push] <br>
jobs: <br>
  Explore-GitHub-Actions: <br>
    runs-on: ubuntu-latest <br>
    steps: <br>
      - run: echo "🎉 The job was automatically triggered by a ${{ github.event_name }} event." <br>
      - run: echo "🐧 This job is now running on a ${{ runner.os }} server hosted by GitHub!" <br>
      - run: echo "🔎 The name of your branch is ${{ github.ref }} and your repository is ${{ github.repository }}." <br>
      - name: Check out repository code <br>
        uses: actions/checkout@v4 <br>
      - run: echo "💡 The ${{ github.repository }} repository has been cloned to the runner." <br>
      - run: echo "🖥️ The workflow is now ready to test your code on the runner." <br>
      - name: List files in the repository <br>
        run: | <br>
          ls ${{ github.workspace }} <br>
      - run: echo "🍏 This job's status is ${{ job.status }}." <br>
    
3)Click Commit changes.<br>
4)In the "Propose changes" dialog, select either the option to commit to the default branch or the option to create a new branch and start a pull request. Then click Commit changes or Propose changes.


Committing the workflow file to a branch in your repository triggers the push event and runs your workflow.If you chose to start a pull request, you can continue and create the pull request, but this is not necessary for the purposes of this quickstart because the commit has still been made to a branch and will trigger the new workflow.

# You can View the workflow using given steps:
1)On GitHub.com, navigate to the main page of the repository.<br>
2)Under your repository name, click  Actions.<br>
3)In the left sidebar, click the workflow you want to display, in this example "GitHub Actions Demo."
4)From the list of workflow runs, click the name of the run you want to see, in this example "AYUSHIMAHAJAN is testing out GitHub Actions."
5)In the left sidebar of the workflow run page, under Jobs, click the Explore-GitHub-Actions job.
6)The log shows you how each of the steps was processed. Expand any of the steps to view its details.

# For example, you can see the list of files in your repository:

* Hence Workflows using Github Action is successfully implemented.
