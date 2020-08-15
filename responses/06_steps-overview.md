## Let's improve the workflow

@{{user.login}} it looks like you workflow has completed! Let's take a look at the results!

You should be pretty familiar with the first portion of the workflow - it's the same as the first time it ran, and it just creates a comment whenever a new issue has been created.

The second portion may exactly be clear to you, but this issue was added to a project board that is present in this repository. Checkout the [projects tab]({{projectTab}}) if you want to see that this issue has been added!

#### Multiple steps

One benefit of using actions is the ability to separate `jobs` into smaller units of work called `steps`. If we think about what our workflow is doing we can see that it makes more sense to have these two tasks take place across two steps.

As an added advantage, once we break the current workflow into multiple steps you can apply logic through expressions to them. This will let you create rules around when steps are allowed to run. Ultimately this allows you to optimize youworkflow run!

Since GitHub Script is simply an action, breaking each unique task into a new step works just fine! You'll do this in our next activity!
