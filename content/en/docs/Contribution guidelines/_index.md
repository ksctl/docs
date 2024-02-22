---
title: Contribution Guidelines
weight: 10
description: How to contribute to the docs
---

{{% pageinfo %}}
You can do almost all the tests in your local except e2e tests which requires you to provide cloud credentials
{{% /pageinfo %}}

Provide a generic tasks for new and existing contributors

## Types of changes

There are many ways to contribute to the ksctl project. Here are a few examples:

* **New changes to docs:** You can contribute by writing new documentation, fixing typos, or improving the clarity of existing documentation.
* **New features:** You can contribute by proposing new features, implementing new features, or fixing bugs.
* **Cloud support:** You can contribute by adding support for new cloud providers.
* **Kubernetes distribution support:** You can contribute by adding support for new Kubernetes distributions.

Phases a change / feature goes through

1. Raise a issue regarding it (used for prioritizing)
2. what all changes does it demands
3. if all goes well you will be assigned
4. If its about adding Cloud Support then usages of CloudFactory is needed and sperate the logic of vm, firewall, etc. to their respective files and do have a helper file for behind the scenes logic for ease of use
5. If its about adding Distribution support do check its compatability with different cloud providers vm configs and firewall rules which needs to be done

## Formating for PR & Issue subject line

### Subject / Title

```markdown
# Releated to enhancement
enhancement: <Title>

# Related to feature
feat: <Title>

# Related to Bug fix or other types of fixes
fix: <Title>

# Related to update
update: <Title>
```

### Body

Follow the PR or Issue template
add all the significant changes to the PR description

### Commit messages

mention the detailed description in the git commits.
what? why? How?

**Each commit must be sign-off and should follow conventional commit guidelines.**

### Conventional Commits

The commit message should be structured as follows:

```
<type>(optional scope): <description>

[optional body]

[optional footer(s)]
```

For more detailed information on conventional commits, you can refer to the [official Conventional Commits specification](https://www.conventionalcommits.org/en/v1.0.0/).

### Sign-off

Each commit must be signed-off. You can do this by adding a sign-off line to your commit messages.
When committing changes in your local branch, add the -S flag to the git commit command:

```bash
$ git commit -S -m "YOUR_COMMIT_MESSAGE"
# Creates a signed commit
```

You can find more comprehensive details on how to sign off git commits by referring to the [GitHub section on signing commits](https://docs.github.com/en/authentication/managing-commit-signature-verification/signing-commits).

### Verification of Commit Signatures

You have the option to sign commits and tags locally, which adds a layer of assurance regarding the origin of your changes. GitHub designates commits or tags as either "Verified" or "Partially verified" if they possess a GPG, SSH, or S/MIME signature that is cryptographically valid.

**GPG Commit Signature Verification**

To sign commits using GPG and ensure their verification on GitHub, adhere to these steps:

* Check for existing GPG keys.
* Generate a new GPG key.
* Add the GPG key to your GitHub account.
* Inform Git about your signing key.
* Proceed to sign commits.

**SSH Commit Signature Verification**

To sign commits using SSH and ensure their verification on GitHub, follow these steps:

* Check for existing SSH keys.
* Generate a new SSH key.
* Add an SSH signing key to your GitHub account.
* Inform Git about your signing key.
* Proceed to sign commits.

**S/MIME Commit Signature Verification**

To sign commits using S/MIME and ensure their verification on GitHub, follow these steps:

* Inform Git about your signing key.
* Proceed to sign commits.

For more detailed instructions, refer to [GitHub's documentation on commit signature verification](https://docs.github.com/en/authentication/managing-commit-signature-verification/about-commit-signature-verification)

# Development

First you have to fork the ksctl repository. [fork](https://github.com/ksctl/ksctl/fork)

```bash
cd <path> # to you directory where you want to clone ksctl
mkdir <directory name> # create a directory
cd <directory name> # go inside the directory
git clone https://github.com/${YOUR_GITHUB_USERNAME}/ksctl.git # clone you fork repository
cd ksctl # go inside the ksctl directory
git remote add upstream https://github.com/ksctl/ksctl.git # set upstream
git remote set-url --push upstream no_push # no push to upstream
```

## Trying out code changes

Info | data
-|-
Url | `https://jenkins.ksctl.com/`
UserName | `ksctl`
pass | `77777`

Before submitting a code change, it is important to test your changes thoroughly. You can do this by running the unit tests and integration tests.

## Submitting changes

Once you have tested your changes, you can submit them to the ksctl project by creating a pull request.
Make sure you use the provided PR template

## Getting help

If you need help contributing to the ksctl project, you can ask for help on the kubesimplify Discord server, ksctl-cli channel or else raise issue or discussion

## Thank you for contributing!

We appreciate your contributions to the ksctl project!

Some of our contributors [ksctl contributors](https://github.com/ksctl/ksctl/graphs/contributors)
