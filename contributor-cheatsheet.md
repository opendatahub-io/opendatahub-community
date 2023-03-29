# Open Data Hub Contributor Cheat Sheet

A list of common resources when contributing to Open Data Hub, tips, tricks, and
common best practices used within the Open Data Hub project. It is a "TL;DR" or
quick reference of useful information to make your GitHub contribution experience
better.

## Helpful Resources

### Getting Started

- [Contributor Guide](./contributing.md) - Guide on how to begin contributing to Open Data Hub
  Project.

### SIGs and Other Groups

- [Master Group List](./sigs.yaml)

### Community

- [Calendar](https://calendar.google.com/calendar/u/0/embed?src=opendatahub.community@gmail.com&ctz=America/New_York) - View all the Open Data Hub Community events (SIG meetings,
  events etc.)
- [odh-community@googlegroups.com](mailto:odh-community@googlegroups.com) - The Open Data Hub development mailing list
- [Slack channels](https://odh-io.slack.com) - Official Open Data Hub Slack.

## Communicating Effectively on GitHub


### How to be Excellent to Each Other

As a first step, familiarize yourself with the [Code of Conduct](https://github.com/opendatahub-io/opendatahub-community/blob/master/CODE_OF_CONDUCT.md).


#### Examples of Good/Bad Communication

When raising an issue, or seeking assistance, please be polite with your request:

  🙂 “X doesn’t compile when I do Y, do you have any suggestions?”

  😞 “X doesn’t work! Please fix it!”

When closing a PR, convey an explanatory and cordial message explaining
why it does not meet the requirements to be merged.

🙂 “I’m closing this PR because this feature can’t support the use case X. In
   it's proposed form, it would be a better to be implemented with Y tool. Thank
    you for working on this.”

😞 “Why isn’t this following the API conventions? This should be done elsewhere!”

## Submitting a Contribution

### Opening and Responding to Issues

GitHub Issues are the primary means of tracking things such as bug reports,
enhancement requests, or reporting other issues such as failing tests.

### Opening a Pull Request

Pull requests (PR) are the main means of contributing code, documentation or
other forms of work that would be stored within a git repository.

## Working Locally

Before you propose a pull request, you will have to do some level of work
locally. If you are new to git, the [Atlassian git tutorial](https://www.atlassian.com/git/tutorials) is a good starting
point. As an alternative, Stanford's [Git magic](http://www-cs-students.stanford.edu/~blynn/gitmagic/) tutorial is a good
multi-language option.

### Branch Strategy

The Open Data Hub project uses a _"Fork and Pull"_ workflow that is standard to
GitHub. In git terms, your personal fork is referred to as the _"`origin`"_ and
the actual project's git repository is called _"`upstream`"_. To keep your
personal branch (`origin`) up to date with the project (`upstream`), it must be
configured within your local working copy.


#### Adding Upstream

Add `upstream` as a remote, and configure it so you cannot push to it.

```
# replace <upstream git repo> with the upstream repo url
# example:
#  https://github.com/opendatahub-io/opendatahub.io.git
#  git@github.com/opendatahub-io/opendatahub.io.git

git remote add upstream <upstream git repo>
git remote set-url --push upstream no_push
```

This can be verified by running `git remote -v` which will list your configured
remotes.


#### Keeping Your Fork in Sync

Fetch all the changes from `upstream` and _"rebase"_ them on your local `main`
branch. This will sync your local repo with the `upstream` project. Push the local changes to your `remote main`.

```
git fetch upstream
git checkout main
git rebase upstream/main
git push origin main
```

You should do this minimally before creating a new branch to work on your
feature or fix.

```
git checkout -b myfeature
```

#### Squashing Commits

The main purpose of squashing commits is to create a clean readable git
history or log of the changes that were made. Usually this is done in last
phase of a PR revision. If you are unsure if you should squash your commits, it
is better to err on the side of having more and leave it up to the judgement of
the other contributors assigned to review and approve your PR.

Perform an interactive rebase to choose which commits you want to keep and which you want to squash, then force push your branch:

```
git rebase main -i
...
git push origin myfeature --force
```