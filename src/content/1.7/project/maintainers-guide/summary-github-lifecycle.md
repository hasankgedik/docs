---
title: Summary of how GitHub Issues and Pull Requests are processed
---

# Summary of how GitHub Issues and Pull Requests are processed

GitHub is the main tool used by maintainers to manage the PrestaShop project.

This page quickly describes how [Issues](https://guides.github.com/features/issues/) and [Pull Requests](https://docs.github.com/en/github/collaborating-with-issues-and-pull-requests/about-pull-requests) are processed on GitHub.

## The teams

On GitHub, there are mainly three teams working together on the project.

- Product Team: this team takes care of the product vision of the software. It has Product Managers, UX Designers and Wording Managers.
- Quality Assurance (QA) team: this team takes care of ensuring the quality of the software. It has QA analysts and QA automation engineers.
- Developers team a.k.a Core Team: this team takes care of the code and act as maintainer for the project.

A maintainer will naturally belong to the Developers team but can also assist and work with the Product Team and QA Team.

## Issues

Currently, there are 4 different types of Issues submitted by users on GitHub.

### Feature Request

When a user submits a Feature Request, it can be either a Product feature request (example: add a new Back office page) or a Technical feature request (example: support PostgreSQL).

Product feature requests are labelled "Waiting for PM" while Technical feature request are labelled "Waiting for dev".

The team in charge will then analyse the request and either reject it or accept it. Rejected feature requests are closed while accepted feature requests are added to the roadmap and labelled. Labels will help triaging the backlog.

### Bug report

When a user submits a bug report, the QA team will analyse it and attempt to reproduce it. If it can be reproduced and is confirmed to be an issue, it will be labelled and added to the roadmap.

If it cannot be reproduced, QA team will attempt to explore the issue with the contributor to isolate the very settings responsible for the buggy behavior.

If the user does not answer for 30 days or after multiple attempts, it cannot be reproduced on our side, the issue is closed.

#### Regressions

If the bug report is confirmed, one of the key elements to evaluate is whether it is a regression. A regression is a bug that cannot be observed in the previous PrestaShop version, it means the software quality level has decreased instead of increasing. Regressions are usually milestoned to be fixed in the next patch version.

#### This is not easy

The work of analyzing and testing all submitted bug reports is a very complex one, because there might be a very diverse range of reports. Moreover quite a huge number of them are actually not related to the software but to how the shop is being used: the server configuration, the shop configuration, the installed modules and the installed theme might introduce buggy behaviors that the user mistakenly believes come from the software.

This is why so much Issues cannot be reproducted on our side, but to find it out multiple explorations and attempts are necessary.

### Support request

We sometimes receive support requests on GitHub, ranging from questions about the software to "please help me to do X in my shop" requests. GitHub is for the software development so we usually redirect users to other channels using the [Support template](https://github.com/PrestaShop/PrestaShop/issues/new?template=3_support_question.md).

### Other

There are some Issues which do not fit in the previous categories, such as [releases Issues](https://github.com/PrestaShop/PrestaShop/issues/20804). They serve a specific purpose.

## Projects

Available in the ‘[Projects](https://github.com/PrestaShop/PrestaShop/projects)’ tab of the PrestaShop’s GitHub repository, versions kanbans organize the Core team’s work. Both the product and the tech teams use it to prepare and plan the next developments and, since we deal with an open source project, the purpose of having those kanbans public is to help the community and the external mainteners to know what is at stake.

### Definition of states

A ticket can either be an issue or a pull request. Most of the time, pull requests fix issues so it is most likely that you run into issues while browsing the kanban. A ticket should always have an owner, be it a PM or a developer.

Community contributions are no longer part of the kanban. Only tickets developed or fixed by the Core team are included in the kanban, as it should reflect the Core team’s work. For example, an issue reports a bug prioritized for the 1.7.8.0, the ticket must appear in the 1.7.8 kanban while the linked pull request must have the 1.7.8.0 milestone.

Community contributions must be approved by the Core product team. Ideally before being reviewed, at least before being merged. Here is why:

It is a bug? It must be reported in the functional specifications.
It is an improvement? It must be validated, prioritized, and specified.

A pull request that shown no activity for more than three months must be closed. If it is fixing a major bug or any topwatcher ticket, it will be back in the to do column again to be completed by the core team.

Also, an important notion to keep in mind is the definition of ready. Several elements must be prepared upstream to get the ticket ready to be coded, otherwise it will not take part in the backlog.

A ready ticket must contain an explicit title and description referring to:
- validated & available specifications
- validated & available mockups
- validated & available wording
- available acceptance tests

#### Not ready

**All the prioritized tickets to include in this version** but that need to be prepared by the core team - assigned to a PM or the lead dev as owner.

_Who adds tickets to this column?_ Mostly the PM once they approved the ticket, but it could also be the developers.

#### Backlog

**All the ready tickets reviewed during the grooming** by the lead PM and the lead dev and discussed/assigned to a developer during the sprint planning.

_Who adds tickets to this column?_ It is the lead PM with the approval of the lead dev.

#### To do

**All the ready tickets to be developed**, presented by the owners during the sprint planning.

_Who adds tickets to this column?_ It is the lead PM with the approval of the lead dev. 

#### Blocked / Need specs

**All the tickets that lack information and need to be respecified** or that are waiting for some previous ticket to be merged.

_Who adds tickets to this column?_ It is the lead PM, with the approval of the lead dev, after the PM/dev assigned to the ticket has raised the blocking element. Add a comment to precise what is expected.

#### In progress

**All the tickets that are being coded**, assigned to a developer.

_Who adds tickets to this column?_ It is the assigned developer, once he/she starts working on it.

#### To be reviewed

**All the tickets whose code needs to be reviewed** - at least two approvals from core-developers are required.

_Who adds tickets to this column?_ It is the developer assigned to the ticket.

#### To be tested

**All the tickets approved that need to be tested** by the QA team.

_Who adds tickets to this column?_ It is the second developer who reviews and approves the ticket, he must also add the 'waiting for QA' label.

#### To be merged

**All the tickets that are ready to be merged** because approved by the QA team.

_Who adds tickets to this column?_ It is the QA team that has just validated the ticket.

#### Done

All the tickets that are now part of the history, great work to all! 

## Pull Requests

When a contributor submits a Pull Request, it goes through multiple stages.

### Is it eligible

Maintainers must first validate that the Pull Request is eligible to review (the template is filled, the license headers are correct, the target branch is the right one ...).

If there is an issue with the Pull Request and it is not eligible, maintainers kindly ask the contributor to fix it.

### About the intent

If the Pull Request is eligible, maintainers can evaluate if the changes brought by the Pull Request are desirables.

- If the Pull Request brings in changes in design, they can ask the validation of UX designers by adding the label "Waiting for UX".
- If the Pull Request brings in changes to the product, they can ask the validation of Product managers by adding the label "Waiting for PM".
- If the Pull Request brings in changes in wording, they can ask the validation of UX designers by adding the label "Waiting for wording".

If one "Waiting for ..." label has been applied, the team in charge will process the Pull Request and then add a "... approved" label. For example if Product team validates the new behavior implemented in a Pull Request, they will remove the "Waiting for PM" label and add the "PM approved" label instead.

There are some automated bots running on GitHub that will help maintainers to label the Pull Requests. For example Prestonbot is able to extract the new wordings and add the "Waiting for wording" label. You can read more about them [here]({{< ref "/1.7/contribute/contribution-process/how-pull-requests-are-processed.md" >}}).

### About the code

If the Pull Request is validated and there are no more "Waiting for ..." labels, then it awaits a [code review]({{< ref "/1.7/project/maintainers-guide/reviewing-pull-requests.md" >}}). Maintainers provide this code review.

A maintainer can choose to
- Ask for changes in the Pull Request (which blocks merging)
- Provides comments wihout blocking or approving
- Approve the Pull Request

When the Pull Request has been approved (it needs two approvals on the Core repository), the Pull Request must be tested. It is labelled "Waiting for QA".

### Testing the Pull Request

On regular Pull Requests, the QA team is in charge of testing the Pull Request. They will use the "How to test" part of the Pull Request description to validate the behavior implemented, and also run some more tests to validate there are no regressions.

Some Pull Requests however cannot be tested by QA team, the Developers team might validate them.

If the Pull Request is tested successfully, the label "QA approved" is applied. Else, the author is notified about the Issues found by the tests.

### Merging the Pull Request

Pull Requests that have been validated by QA can be merged. They must also be milestoned, and if they fix an issue, the issue must be labelled, milestoned, and closed.