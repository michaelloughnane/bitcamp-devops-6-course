## Create an issue comment

If you take a look at the [Octokit documentation](https://octokit.github.io/rest.js/v17#issues-create-comment) on how to create issue comments you are greeted with the following method:

**someFile.js**

```javascript
octokit.issues.createComment({
  owner,
  repo,
  issue_number,
  body
});
```

Okay, that doesn't seem so hard. Now that you know how to do it with Octokit, take a look at how to use GitHub Script to create an issue comment:

**my-workflow.yml**

```yaml
- uses: actions/github-script@0.8.0
  with:
    github-token: {% raw %}${{secrets.GITHUB_TOKEN}}{% endraw %}
    script: |
    github.issues.createComment({
        issue_number: context.issue.number,
        owner: context.repo.owner,
        repo: context.repo.repo,
        body: '👋 Thanks for reporting!'
    })
```

## Open a pull request

Now see what it's like to open a pull request with octokit/rest.js:

**someFile.js**

```javascript
octokit.pulls.create({
  owner,
  repo,
  title,
  head,
  base
});
```

Again, that's not too hard at all. Now, do the same thing, only using the GitHub Script action:

```yml
- uses: actions/github-script@0.8.0
  with:
    github-token: {% raw %}${{secrets.GITHUB_TOKEN}}{% endraw %}
    script: |
    github.pull.create({
        repo: github.context.repo.repo,
        owner: github.context.repo.owner,
        head: github.context.ref,
        base: "master",
        title: "from my action",
        body: "## I totally used GitHub Script to pull this off 🔥"
    })
```

_You may have noticed that when using GitHub Script the method call starts with `github` and not `octokit`. This is because GitHub Script provides you with a pre-authenticated octokit/rest.js client stored in a variable named `github`._