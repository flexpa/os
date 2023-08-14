# 💾 Product Development
This document exists as a comprehensive version of Flexpa's product development process, including meetings, artifacts, and workflows.

## Ideation and Prioritization Processes
### Issues
**Purpose**: The atomic unit of work in our development process. Issues are the ideas - features, bugs, and backlog items to be planned. Issues are closed by PRs or when they are no longer relevant. 

**Output**: Github Issues at Flexpa match this template:

```
## Why
* Why we are making a change

## What
* What we are changing and how the change is being completed

## How
* The implementation specifics, if applicable
```

Issues come from several sources:
* **OKR items** - Cross-functional collaboration on quarterly OKRs is central at Flexpa and drives the majority of the work we do.
* **Roadmap items** - Work related to longer initiatives derived from the roadmap are broken down into issues using milestones
  * We use tags specific to each initiative to organize these, such as `prom`
* **Customer Request** - Explicit asks from customers for features that can be fulfilled short term. 
  * These should be tagged with the `customer` tag
* **Support Requests** - Explicit asks from customers or prospects for assistance or bug resolution that requires development
* **Internal Requests** - Asks from Flexpa team members for features to reduce toil or improve work efficiency
* **Monitoring** - Issues may be generated from logging, observability, and other tooling we have, typically focused around exceptions and errors
* **Implementer Insight** - In the course of writing software, it’s very common to be writing code and realize that other code could be written.

Special Consideration: Not every request becomes an issue. Those that would require a quarter or more of work or represent a new product are treated differently.

### Needs
**Purpose**: These represent customer desires that lie outside of the current solution and would represent a new product or significant work. They are considered separately to avoid cluttering the backlog and to provide insights into future challenges and opportunities.

**Output**: The details of Customer Needs are maintained in Hubspot, specifically in the Needs field of the Customers page.

### Roadmap 
#### Document
**Purpose**: To outline the product strategy and plan for the future, giving a clear direction and focus for the entire team. This typically includes key features, enhancements, and initiatives.

**Output**: A strategic document that lays out the direction and plans for the product over the next 9-12 months. This document is maintained and versioned through Github, so it can be updated on a regular cadence. Major changes are also communicated to the team on Slack for review and discussion.

#### Quarterly Presentation
**Purpose**: To share updates on the progress of the roadmap, key achievements, challenges encountered, and plans for the upcoming quarter.

**Output**: A presentation to stakeholders that includes updates and plans for the next quarter, potentially leading to new ideas and feedback. This presentation should represent a snapshot in time of the roadmap document.

### OKRs
**Purpose**: Product will often own key Objectives or underlying KRs, with a collaborative/supporting role for other Objectives. OKRs are today not distinct from product goals and should be aligned with product work. They drive the majority of our work for a given quarter.

**Output**: 
* Quarterly collaboration with other roles on a list of objectives and associated key results that serve as measurable goals for the team 
* Product OKRs defined in Github with an OKR tag 
* OKR progress is shown in Admin.
* Product direction based on OKR progress
* Weekly maintenance and updating of OKRs

See also: [OKRs](https://github.com/flexpa/os/blob/master/docs/process/okrs.md)

### Milestones
**Purpose**: Milestones are larger groupings of planned work, generally in regards to specific projects such as PROM or Portal refresh. Milestones should be longer than a week and shorter than a month (i.e. 2-4 weeks). See also the Milestone planning meeting (below).

**Output**: Github Milestones are the feature we use to group such planned work. 

### Kanban Board
**Purpose**: Work is organized using Kanban. Kanban is a visual tool that helps in the management of workflow, emphasizing continuous delivery without overloading the team members. 

* **On deck**: This is typically where new issues are captured. New Github issues are placed here as they are created.
* **In Progress**: Issues that are currently being worked on by team members. This might include any issue that is actively being worked on but hasn't been completed.
* **In Review**: Once an issue has been completed, it can be moved to a review phase where other team members can assess the work. See Peer Reviews below.
* **Shipped**: Once the issue has one or more PRs that solve it, it can be moved to the Shipped column, indicating successful completion.
* **Closed**: Some issues, upon investigation and work, may be completed without shipping code. This may be due to re-evaluation of the value of the work as part of the investigation, change in priorities, or non-technical solutions to the problem.

Kanban is integrated with sprints at Flexpa, where work is planned and committed to for a set period (a week, in this case). This provides a structure and cadence to the work, while still maintaining the flexibility and visibility that Kanban offers. Sprint outcomes are discussed each week in Product EOW.

**Output**: 
* The Github Project #product board contains all active and near-term work
* The Current tab of the #product board represents the current week-long sprint
* The Next tab of the  #product board represents the upcoming week-long sprint
* Github Issues have the “Week” attribute to delineate the sprint.

## Development Processes

### Pull Request
**Purpose**: The solution to Issues. Pull requests are proposed changes to the codebase that are reviewed by other team members. They provide a structured way to introduce new features, fix bugs, or make other changes to the project. Pull requests also help us satisfy change management policies. Pull requests should:

* Require **at least one approval** from another contributor. Requests for reviews appear in #git.
* **Be** **linked** back to an Issue unless otherwise approved by CTO. You can use [GitHub keywords](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/using-keywords-in-issues-and-pull-requests) to do this automatically.
* **Run tests** that test the changes made in the code (we use Jest and GitHub Actions to automate this)
* Verify **coding style** requirements from tools like ESLint (we use GitHub Actions here too)
* Should be **assigned** to the creator (and any co-authors)

**Output**: Pull requests in Github. These requests include the code changes, a description of what has been done, and why, and often a link back to the related issue. They provide an opportunity for other team members to review and comment on the proposed changes before they are merged into the main codebase.

Pull Request titles follow a standard format:
```
feat|chore|bug(project): Description
```
Where:
* **feat**: A new feature introduced in the codebase. This is typically a change that adds functionality or improves user experience.
* **chore**: Maintenance or routine tasks that need to be performed, like code refactoring or updating dependencies. This doesn't change the application's functionality but keeps the codebase healthy and up-to-date.
* **bug**: A fix to a known defect in the code. This addresses problems that are causing incorrect behavior or other unexpected results.

Pull Request descriptions follow a standard template, similar to Issues:
```
## Why
* Reference to the related Issue using #issue syntax with automation keywords such as Closes

## What
* A brief description of the code changed, typically taken exactly from the commit description
* Testing notes 
* Screenshots
```

### Peer Reviews
**Purpose**: Peer reviews function as a quality assurance check, improve the cohesiveness of our codebase, and also form an important security control preventing unilateral changes.

**Output**: Flexpa requires at least one approving review to merge a pull request. Mostly, anyone who is an active contributor (i.e. part of the product team) can complete a peer review. Peer reviews can end with either a comment, approval, or request for changes. We bias towards identifying feedback as “blocking” or “non-blocking”. Peer reviews are not individually assigned automatically but may be individually requested.

### Status Checks / CICD
**Purpose**: Status checks on a pull request are automated tests and validations that ensure the proposed code changes meet specific criteria before merging, such as the build working or tests passing. By enforcing these checks, we maintain code quality and prevent potential issues from being integrated into the monorepo. Any time we have a “checklist” item required to merge or do a deployment, we try to build that into our automated status checks.

**Output**: Status checks appear on every pull request. They are configured in the monorepo at .github/workflows. Status checks that do not pass prevent pull requests from being merged.

### Merging
**Purpose**: Merging is the final event of our product development process. Merging, also known as “shipping”, is performed on individual pull requests once they have received an approving review and all status checks are passing. 

**Output**: The author of a pull request has the responsibility to merge the pull request. Unless explicitly requested, individual contributors should never merge a pull request on behalf of someone else. This is critically important because after the merge it is similarly the responsibility of the author to verify the successful deployment of the code. When merging, commit messages follow [a standard format](https://www.conventionalcommits.org/en/v1.0.0/#summary):

```
feat|chore|fix(project): Title matching pull request title

A single, tidy commit description (do not merge multiple commit descriptions without editing)

Co-authored-by: <coauthor@flexpa.com>
Co-authored-by: <another-coauthor@flexpa.com>
```

### Changelog

Flexpa's [Changelog](https://www.flexpa.com/docs/getting-started/changelog) provides a history of improvements to the customer-facing elements of Flexpa's product for developers and prospective customers alike. It is an opportunity to:

1. Formally document what changes were made and when
2. Explain the value each change brings in terms that can be easily understood by those less familiar with Flexpa
3. Showcase a consistent and frequent cadence of product improvements

To write a changelog entry, keep in mind the following order:

* The very first sentence of the changelog should be exactly "what" has changed. This should be as clear as possible.
* Additional context, like a "why", _must_ follow though. We use the changelog to provide written cues for the rest of the team to understand / announce the feature / talk about it consistently with customers.

## Meetings
### Weekly
#### W4H
* **Date**: Every Monday
* **Time**: 12:00EST - 1:00 EST

**Purpose**: Identify problems that need more clarity. Addressing any blockers or dependencies. To prioritize upcoming work (at least next week and beyond) and who will be responsible.

**Output**: The primary outputs of this meeting are Github Issues of various kinds: issues that have moved into a “ready” state, issues that need to be further edited, issues that weren’t written down now are.

#### Product EOW
* **Date**: Every Friday
* **Time**: 3:30EST - 4:30 EST

**Purpose**: Public commitment to work to allow for better planning. Ensuring accountability (that commitments are met). Promoting cross-functional awareness of key work and progress - GTM, user testing, and product. To celebrate wins and collaboration across the team. 

**Output**: The primary outputs of this meeting are:
* Written commitments by individual team members
* Items added to the “Next Week” of our Github Project
* Notes and the Fireflies recording to allow for asynchronous communication.

#### HOP <> CTO Review
* **Date**: Every Wednesday
* **Time**: 4:00EST - 5:00 EST

**Purpose**: Every week, we will meet to discuss at least three of the following topics. We will prepare items together in advance. We will talk about all of them at least once a month:

* Process changes
* Mutual feedback
* Engineering team project ownership
* Recent roadblocks
* Customer input

**Output**: Recording, notes, issues.

#### HOP <> HOD Review

* **Date**: Every Monday
* **Time**: 1:00EST - 1:30 EST

**Purpose**: Product and Design have heavy collaboration and overlap. Regular thought partnership and brainstorming accelerate and align each other’s work.

Typical agenda items are:
* KACHUA review
* User testing issues
* Design considerations for the upcoming roadmap
* Product ideation

**Output**: Meeting notes, varied tactical decisions, and progress

#### CTO Pairing
* **Duration**: 60 to 90 minutes

**Purpose**: To engage in cooperative development and problem-solving. A chance for the CTO to provide guidance and share insights with other team members and vice versa.

**Output**: Ideas and insights are exchanged, specific issues or problems are addressed and/or solved, and potential new strategies or processes are discussed.

Details on pairing here.

### Biweekly
#### Product/engineering feedback and pairing sessions
* **Date**: Every other Thursday typically
* **Duration**: 30 minutes
**Purpose**: Collaborative ideation and roadmap discussion to allow team input and understanding. Pairing and testing on recent work to inform HoP. Feedback to improve product process

**Output**: The primary outputs of this meeting are meeting notes, issues created, and issue/PR progress.

### Monthly
#### Regulatory Check-in
* **Duration**: 30 minutes
**Purpose**: Discussion of regulatory and legislative requirements at the national and regional level with Tusk, one of our investors.

**Output**:  Ongoing notes. Action items on specific regulatory changes as needed.

### Ad-hoc
#### Milestone planning
* **Duration**: As long as it takes (typically starting with 60 minutes)

**Purpose**: To break down a bigger product feature into manageable issues that a group of people can get done by a goal date. The primary purpose of the meeting is to brainstorm what we need to do to actually achieve some future state in the product and to transform those ideas into written issues. The secondary purpose is to align the group of contributors and to delegate issues after they are written.

**Output**: A milestone which consists of a set of issues with a goal completion date assigned to individual contributors. There should be a clear understanding of who is working on what, within the context of the project.

## Former Processes
### Goals
**Purpose**: Goals were groupings of issues. Goals detail the overall arc of an initiative, whereas the individual Issues document discrete, atomic work to be done. Goals have largely been superseded by Milestones.

**Output**: Github Goals are a type of Github Issue we create to document these larger initiatives.

### RFCs

**Purpose**:   Requests for Comment were a type of issue intended to solicit broad feedback on overarching architectural proposals or principles. They did not typically have a strong timebound nature and were somewhat open-ended. 

**Output**: The output would be the discussion and decisions that formed in the issue. However, RFCs lack of time sensitivity and priority led to many never formally resolving.
