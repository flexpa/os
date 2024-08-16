# 💾 Product

This document exists as a comprehensive version of Flexpa's product development process, including meetings, artifacts, and workflows.

<figure><img src="../../.gitbook/assets/product-flow.jpg" alt=""><figcaption></figcaption></figure>

## OKRs

**Purpose**: Objectives or underlying KRs are the primary way we set goals at Flexpa - including product development goals.

**Output**:

All outputs for this process are part of our company level [OKR process](/process/okrs), which includes:

- Quarterly collaboration with other roles on a list of objectives and associated key results that serve as measurable goals for the team
- Product direction based on OKR progress
- Weekly maintenance and updating of OKRs

## Roadmap

**Purpose**: To outline the product strategy and plan for the future, giving a clear direction and focus for the entire team. This typically includes key features, enhancements, and initiatives.

**Output**: A strategic document that lays out the direction and plans for the product over the next 9-12 months. This document is maintained in the `docs` folder of the Flexpa repo.

## Issues

**Purpose**: The atomic unit of work in our development process. Issues are the ideas - features, bugs, and backlog items to be planned. Issues are closed by PRs or when they are no longer relevant.

**Output**: Github Issues at Flexpa match this template:

```
## Why

- You should fill this section with why we should do this work. All relevant background and context.
- It is on the issue writer (or other contributing authors) to explain importance in this section.

## What

- Outline the specific deliverables, tasks, or objectives that will be achieved upon completing the issue.
- This will vary to some degree, but may include specifications, user stories, acceptance requirements

## How
* Proposed implementation specifics to be used in linked PR, if applicable
```

Labels exist in Github and will vary over time. Labels are intended for use primarily with issues and not PRs.

Issues come from a variety of sources, including but not limited to:

- **OKR items** - Cross-functional collaboration on quarterly OKRs is central at Flexpa and drives the majority of the work we do.
- **Roadmap items** - Work related to longer initiatives derived from the roadmap are broken down into issues using milestones
  - We use tags specific to each initiative to organize these, such as `prom`
- **Customer Request** - Explicit asks from customers for features that can be fulfilled short term.
  - These should be tagged with the `customer` tag
- **Support Requests** - Explicit asks from customers or prospects for assistance or bug resolution that requires development
- **Internal Requests** - Asks from Flexpa team members for features to reduce toil or improve work efficiency
- **Monitoring** - Issues may be generated from logging, observability, and other tooling we have, typically focused around exceptions and errors
- **Implementer Insight** - In the course of writing software, it’s very common to be writing code and realize that other code could be written.

Special Consideration: Not every request becomes an issue. Those that would require a quarter or more of work or represent a new product are treated differently.

## Needs

**Purpose**: These represent customer desires that lie outside of the current solution and would represent a new product or significant work. They are considered separately to avoid cluttering the backlog and to provide insights into future challenges and opportunities.

**Output**: The details of Customer Needs are maintained in Hubspot, specifically in the Needs field of the Customers page.


## Pull Requests

**Purpose**: The solution to Issues. Pull requests are proposed changes to the codebase that are reviewed by other team members. They provide a structured way to introduce new features, fix bugs, or make other changes to the project. Pull requests also help us satisfy change management policies. Pull requests should:

- Require **at least one approval** from another contributor. Requests for reviews appear in #git.
- **Be** **linked** back to an Issue unless otherwise approved by CTO. You can use [GitHub keywords](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/using-keywords-in-issues-and-pull-requests) to do this automatically.
- **Run tests** that test the changes made in the code (we use Jest and GitHub Actions to automate this)
- Verify **coding style** requirements from tools like ESLint (we use GitHub Actions here too)
- Should be **assigned** to the creator (and any co-authors)

**Output**: Pull requests in Github. These requests include the code changes, a description of what has been done, and why, and often a link back to the related issue. They provide an opportunity for other team members to review and comment on the proposed changes before they are merged into the main codebase.

Pull Request titles follow a standard format:

```
feat|chore|fix(project): Description
```

Where:

- **feat**: A new feature introduced in the codebase. This is typically a change that adds functionality or improves user experience.
- **chore**: Maintenance or routine tasks that need to be performed, like code refactoring or updating dependencies. This doesn't change the application's functionality but keeps the codebase healthy and up-to-date.
- **fix**: A fix to a known defect in the code. This addresses problems that are causing incorrect behavior or other unexpected results.

Pull Request descriptions follow a standard template:

```
## Why
* Reference to the related Issue using #issue syntax with automation keywords such as Closes

## How
* Implementation details. Often a brief description of the code changed, typically taken exactly from the commit description
* Testing notes
* Screenshots
* Tradeoffs
```

## Peer Reviews

**Purpose**: Peer reviews function as a quality assurance check, improve the cohesiveness of our codebase, and also form an important security control preventing unilateral changes.

**Output**: Flexpa requires at least one approving review to merge a pull request. Mostly, anyone who is an active contributor (i.e. part of the product team) can complete a peer review. Peer reviews can end with either a comment, approval, or request for changes. We bias towards identifying feedback as “blocking” or “non-blocking”. Peer reviews are not individually assigned automatically but may be individually requested.

## Status Checks / CICD

**Purpose**: Status checks on a pull request are automated tests and validations that ensure the proposed code changes meet specific criteria before merging, such as the build working or tests passing. By enforcing these checks, we maintain code quality and prevent potential issues from being integrated into the monorepo. Any time we have a “checklist” item required to merge or do a deployment, we try to build that into our automated status checks.

**Output**: Status checks appear on every pull request. They are configured in the monorepo at .github/workflows. Status checks that do not pass prevent pull requests from being merged.

## Merging

**Purpose**: Merging is the final event of our product development process. Merging, also known as “shipping”, is performed on individual pull requests once they have received an approving review and all status checks are passing.

**Output**: The author of a pull request has the responsibility to merge the pull request. Unless explicitly requested, individual contributors should never merge a pull request on behalf of someone else. This is critically important because after the merge it is similarly the responsibility of the author to verify the successful deployment of the code. When merging, commit messages follow a standard format:

```
feat|chore|bug(project): Title matching pull request title

A single, tidy commit description (do not merge multiple commit descriptions without editing)

Co-authored by: <coauth@flexpa.com>
```

## Changelog

Flexpa's [Changelog](https://www.flexpa.com/docs/getting-started/changelog) provides a history of improvements to the customer-facing elements of Flexpa's product for developers and prospective customers alike. It is an opportunity to:

1. Formally document what changes were made and when
2. Explain the value each change brings in terms that can be easily understood by those less familiar with Flexpa
3. Showcase a consistent and frequent cadence of product improvements

To write a changelog entry, keep in mind the following order:

- The very first sentence of the changelog should be exactly "what" has changed. This should be as clear as possible.
- Additional context, like a "why", _must_ follow though. We use the changelog to provide written cues for the rest of the team to understand / announce the feature / talk about it consistently with customers.
