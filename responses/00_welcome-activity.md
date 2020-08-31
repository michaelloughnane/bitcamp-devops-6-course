## Using GitHub Script in a workflow

Actions are enabled on your repository by default, but we still have to tell our repository to use them. You can do this by creating a workflow file in our repository.

This take should be quite familiar to you.

📖 Read more about [workflows](https://help.github.com/en/actions/automating-your-workflow-with-github-actions/configuring-a-workflow#choosing-the-type-of-actions-for-your-workflow)

### :keyboard: Activity: Respond to an issue when it gets opened

1. Create a new workflow file titled `.github/workflows/my-workflow.yml` with the following contents:
   You can use [this quicklink]({{quicklink}}) to easily create this file:

   ```yaml
   name: Learning GitHub Script

   on:
     issues:
       types: [opened]

   jobs:
     comment:
       runs-on: ubuntu-latest
       steps:
         - uses: actions/github-script@0.8.0
           with:
             github-token: {% raw %}${{secrets.GITHUB_TOKEN}}{% endraw %}
             script: |
               github.issues.createComment({
                 issue_number: context.issue.number,
                 owner: context.repo.owner,
                 repo: context.repo.repo,
                 body: "🎉 You've created this issue comment using GitHub Script!!!"
               })
   ```

2. Commit the workflow to a new branch.
3. Create a pull request. A suggestion for title could be **Automate issue responses**.
4. Supply the pull request body content and click **Create pull request**.

<details><summary>About pull request titles and content</summary>

It is important to place meaningful content into the body of the pull requests you create. This repository will stay with you long after you complete the course. We recommend you use the body of your pull requests as a way to take long lived notes about thing you want to remember.

In practice, good pull request titles and content convey information efficiently to your collaborators.

You can fill the body of this pull request with the following recommended content:

> Workflow files are the recipe for task automation. This is where actions are placed if I want to use them for a task.

</details>

---

Create a new pull request, then the lesson will continue.
