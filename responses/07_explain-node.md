# Improving the issue comment

💡Did you know that GitHub Script also grants you access to a full Node.js environment?

Although we wouldn't recommend using GitHub Script to write the logic for complex actions, there are use cases where you may want to leverage using a little more than just the octokit/rest.js API.

One such use case is this issue comment. Right now it is pretty hard coded the way it is making it less than ideal. What if you wanted to display your contribution guide every time an issue was opened?

Instead of writing the guide directly into your workflow, you can use the Node.js File System module to read a file and use it as the body of your issue comment.

If you want access to the files within our repository, you need to make sure you include the `actions/checkout` action in your workflow as the first step.
