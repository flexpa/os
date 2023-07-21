# 💾 Development

### Issues

Issues are the simplest unit of product development and change management. Changes are looked pull requests described in the [Merge process](development.md#merge-process). Issues match this template:

```
## Why
* Why we are making a change

## What
* What we are changing and how the change is being completed

## How
* The implementation specifics, if applicable
```

Issues can be assigned Assignees and Projects. We also have labels such as:

* **doc** for documentation issues
* **security** for SecOps issues
* **feat** for new product features

Most new issues should be created in advance of the [📅 EOW (End of week)](development.md#eow-end-of-week).

#### GitHub

Flexpa uses GitHub Enterprise for product development and change management.

* **Organization**: [github.com/flexpa](https://github.com/flexpa)
* **Teams**: [https://github.com/orgs/flexpa/teams](https://github.com/orgs/flexpa/teams)
* **Projects**: [github.com/orgs/flexpa/projects](https://github.com/orgs/flexpa/projects?type=beta)
* **flexpa/flexpa repository**: [github.com/flexpa/flexpa](https://www.github.com/flexpa/flexpa)

Our primary product project is [**📠 Product**](https://github.com/orgs/flexpa/projects/1)**.**

### Merge process

Merging code changes in any repository we maintain must follow this merge process.

#### Pull Request

A pull request must be created on GitHub. Each pull request must (don't worry this is mostly automated):

* Require **at least one approval** from another contributor. Requests for reviews appear in #git.
* **Be** **linked** back to an Issue unless otherwise approved by CTO. You can use [GitHub keywords](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/using-keywords-in-issues-and-pull-requests) to do this automatically.
* **Run tests** that test the changes made in the code (we use Jest and GitHub Actions to automate this)
* Verify **coding style** requirements from tools like ESLint (we use GitHub Actions here too)
* Should be **assigned** to the creator (and any co-authors)

After all checks are verified passing pull requests can be **Squashed and merged by the assignee.**&#x20;

![](<../../assets/merge.png>)

### Changelog

Flexpa's [Changelog](https://www.flexpa.com/docs/getting-started/changelog) provides a history of improvements to the customer-facing elements of Flexpa's product for developers and prospective customers alike. It is an opportunity to:

1. Formally document what changes were made and when
2. Explain the value each change brings in terms that can be easily understood by those less familiar with Flexpa
3. Showcase a consistent and frequent cadence of product improvements

To write a changelog entry, keep in mind the following order:

* The very first sentence of the changelog should be exactly "what" has changed. This should be as clear as possible.
* Additional context, like a "why", _must_ follow though. We use the changelog to provide written cues for the rest of the team to understand / announce the feature / talk about it consistently with customers.

### 📅 EOW (End of week)

* **Date**: Every Friday
* **Time:** 3:30EST - 4:30 EST
* **Purpose:** To review updates (especially what got shipped), write new issues, and celebrate wins/thank yous

### Systems hardening

Systems hardening means taking a methodological approach to the security and integrity of our information technology systems.&#x20;

There are several types of system hardening activities, including:

* Application hardening
* Server hardening

For each of these types, Flexpa takes (but is not limited to) the hardening measures described below.

#### Application hardening

* Detect dependency drift through automation
* Unused dependencies should be removed
* Unnecessary dependencies should not be added
* Prioritize and patch vulnerabilities
* Static code analysis should be used to detect common vulnerabilities

#### Server hardening

* Systems should be deployed in designated environments
* Systems should be segregated
* Rights and access should be in line with the principle of least privilege
* Network ports should be universally disabled and allow-listed only as appropriate/necessary
* Network traffic should be encrypted

