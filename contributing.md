# Contributing

Open Data Hub is open source, but many of the people working on it do so as their day job.
In order to avoid forcing people to be "at work" effectively 24/7, we want to establish some semi-formal protocols around development.
Hopefully, these rules make things go more smoothly.
If you find that this is not the case, please complain loudly.

As a potential contributor, your changes and ideas are welcome at any hour of the day or night, weekdays, weekends, and holidays.
Please do not ever hesitate to ask a question or send a pull request.

Beginner focused information can be found below in [Open a Pull Request](#open-a-pull-request) and [Code Review](#code-review).

For quick reference on contributor resources, we have a handy [contributor cheatsheet](contributor-cheatsheet.md).

## Communication

It is best to contact your [SIG](./sigs.yaml) for issues related to the SIG's topic. Your SIG will be able to help you much more quickly.

For general questions and troubleshooting, use the [standard lines of communication](./README.md).

## Opening a Pull Request

Pull requests are often called a "PR".
Open Data Hub generally follows the standard [github pull request](https://help.github.com/articles/about-pull-requests/) process.

Common new contributor PR issues are:

* finding the right SIG or reviewer(s) for the PR (see [Code Review](#code-review) section) and following any SIG or repository specific contributing guidelines.
* dealing with test cases which fail on your PR, unrelated to the changes you introduce.
* Include mentions (like @person) and [keywords](https://help.github.com/en/articles/closing-issues-using-keywords) which could close the issue (like fixes #xxxx) in commit messages.

## Code Review

To make it easier for your PR to receive reviews, consider the reviewers will need you to:

* write [good commit messages](https://chris.beams.io/posts/git-commit/).
* break large changes into a logical series of smaller patches which individually make easily understandable changes, and in aggregate solve a broader issue.
* label PRs with appropriate SIGs and reviewers.

Reviewers, the people giving the review, are highly encouraged to revisit the [Code of Conduct](https://github.com/opendatahub-io/opendatahub-community/blob/master/CODE_OF_CONDUCT.md) and must go above and beyond to promote a collaborative, respectful community.
When reviewing PRs from others [The Gentle Art of Patch Review](http://sage.thesharps.us/2014/09/01/the-gentle-art-of-patch-review/) suggests an iterative series of focuses which is designed to lead new contributors to positive collaboration without inundating them initially with nuances:

* Is the idea behind the contribution sound?
* Is the contribution architected correctly?
* Is the contribution polished?

Note: If your pull request isn't getting enough attention, you can use the [slack channel](https://odh-io.slack.com) to get help finding reviewers.

## Best practices

- Write clear and meaningful git commit messages.
- If the PR will *completely* fix a specific issue, include `fixes #123` in the PR body (where 123 is the specific issue number the PR will fix. This will automatically close the issue when the PR is merged.
- Make sure you don't include `@mentions` or `fixes` keywords in your git commit messages. These should be included in the PR body instead.
- When you make a PR for small change (such as fixing a typo, style change, or grammar fix), please squash your commits so that we can maintain a cleaner git history.
- Make sure you include a clear and detailed PR description explaining the reasons for the changes, and ensuring there is sufficient information for the reviewer to understand your PR.
- Additional Readings: 
    - [chris.beams.io/posts/git-commit/](https://chris.beams.io/posts/git-commit/)
    - [github.com/blog/1506-closing-issues-via-pull-requests ](https://github.com/blog/1506-closing-issues-via-pull-requests)
    - [davidwalsh.name/squash-commits-git ](https://davidwalsh.name/squash-commits-git)
    - [https://mtlynch.io/code-review-love/](https://mtlynch.io/code-review-love/)

## Testing

Testing is the responsibility of all contributors and is in part owned by all SIGs.

There are multiple types of tests.
The location of the test code varies with type, as do the specifics of the environment needed to successfully run the test:

*TODO: Add information about how to submit tests and viewing results*

Continuous integration will run these tests either as pre-submits on PRs, post-submits against main/release branches, or both.

## Documentation

Consider contributing to documentation to improve install instructions, tutorials, examples and more by adding content to [opendatahub.io](https://github.com/opendatahub-io/opendatahub.io).  If new features or components are being submitted, it is expected that proper documentation will accompany it.

## Issues Management or Triage

Helping to manage or triage open issues in repositories can be a great contribution and a great opportunity to learn about the various areas of the project.

Triaging is the word we use to describe the process of adding multiple types of descriptive labels to GitHub issues, in order to speed up routing issues to the right folks.  If you experience any issues affecting the Open Data Hub community or the components, please file an issue under the [opendatahub-community](https://github.com/opendatahub-io/odh-dashboard/issues).  The issue will be reviewed and triaged by the relevant component owners and transfered to the affected code repositories under the [opendatahub-io organization](https://github.com/opendatahub-io).
