---
title: Pull Requests & Reviews
description: Principles for developers (maintainers and contributors)
layout: default
---

> disclaimer: If you are reading this, I am SORRY for my miscommunication. I am not defending myself. I am simply explaining myself.
> I am not a bad programmer. I am a human with a work-in-progress laziness issue.

Pull requests (PRs) are great:

- As a contributor, you can implement a new feature or bug-fix and have your contribution merged upstream with visible accreditation.
- As a maintainer, it means some very intelligent, enthusiastic user has found an issue; invested time to debug and investigate your code; come up with a way to fix the issue; implemented said method; looked into your contributing guidelines, and followed said instructions to run tests, debug and fix their contribution, and (finally!) open a PR. That's a lot of effort.

But there's a hitch: maintainers are much more familiar with the codebase. They follow some project design conventions. No contributor should be expected to learn these -- they've already put in so much effort!

Maintainers want to fix such pragmatic discrepancies before merging (by rewriting or reimplementing large parts of a PR), seemingly ignoring or belittling the massive amount of effort contributors have put in.

Alternatively (thanks to many other articles and blog posts on this topic), maintainers are urged to merge imperfect PRs to avoid causing *offence*.

**THIS IS WRONG.**

This is not the most effective way of reducing potential for *offence*, and instead introduces additional problems.

If maintainers merge "imperfect" PRs, they will often follow-up later (post-merge) quietly fix the issues. This is bad because:

- the contributor may no longer be [given credit](https://github.com/casperdcl/git-fame) for their ideas (e.g. if all their surviving lines of code are changed), and
- the solo follow-up may not actually be required nor "correct", and may even introduce a bug, or
- alternatively, the follow-up issues may be forgotten and never addressed, adding to *technical debt*

Instead, if these "pedantic/polishing/finessing" changes were made in the original PR, the maintainer and contributor can review each other's code.[^follow-link]

[^follow-link]: Note that opening a follow-up ticket (issue or PR) clearly linking to the original PR (and mentioning/notifying the relevant contributor) is equivalent to doing everything in the original PR (regarding risking *offence*) but potentially better programming practice (regarding problem subdivision & agile development).

Worried about causing *offence*? The solution is: *communicate*.

Programmers are told they're not good at communication.

**THIS IS WRONG.**

Programmers are humans. All humans are better at communicating with other humans than with computers.

Personally, I've never knowingly merged an imperfect PR (without opening an immediate follow-up ticket).
However, I have -- on occasion -- failed to communicate appropriately.
I was being a lazy human. I was not being a bad programmer.

Risking accidentally causing occasional *offence* is preferable to build up of *technical debt*. It's easier to rectify. Saying "sorry" is much quicker and safer to do than refactoring. The wider user base will appreciate the resultant clean, consistent code. The contributor (who, by definition, has already demonstrated a high level of intelligence and enthusiasm) is far more likely to accept your apologies than morphing into a troll.

----

{{ site.comments }}
