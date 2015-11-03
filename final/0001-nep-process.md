---
NEP: 1
Author: Kyle Fuller
Status: Final
Created: 2015-11-03
Last Modified: 2015-11-03
---

# NEP 1: Nest Enhancement Proposals

## Table of Contents

- [What is a NEP](#what-is-a-nep)
- [NEP Submission Workflow](#rfc-submission-workflow)
    - [Pre-proposal](#pre-proposal)
    - [Submitting draft NEP](#submitting-draft-nep)
    - [Discussion, development, and updates](#discussion-development-and-updates)
    - [Review & Resolution](#review--resolution)
    - [Implementation](#implementation)

## What is a NEP?

NEP (or Nest Enhancement Proposal) are design documents providing
information for new features within Nest. NEPs provide concise technical
specifications of features along with rationales.

NEPs are intended to be the primary mechanism for proposing new features
to Nest allowing community input on any issues, and for documenting design
decisions that have gone into Nest.

## NEP Submission Workflow

The NEP process looks something like this:

1. [Pre-proposal](#pre-proposal)
2. [Submitting draft NEP](#submitting-draft-nep) for a change you would like
   to make to Nest.
3. [Discussion, development, and updates](#discussion-development-and-updates) -
   The NEP will be discussed, improved, and updated as feedback comes in.
4. [Review & Resolution](#review--resolution) - The NEP is considered by the
   Nest Core team and is either accepted or rejected.
5. [Implementation](#implementation) - The implementation of the proposed NEP
   is completed.

### Pre-proposal

The NEP process begins with a new idea or change in Nest. It is recommended
that you reach out to Nest community to determine if the proposal would make
sense, and to save the author time if the proposal would be outright rejected
for any reason.

Asking the Nest community first if an idea is original help prevent too
much time being spent on something that is guaranteed to be rejected based
on prior discussions (searching the Internet does not always do the trick).

It also helps to make sure the idea is applicable to the entire community and
not just the author.

### Submitting draft NEP

A draft NEP should be presented in the form of a pull request to the NEP repository.

1. Fork the NEP repository
2. Copy `template.md` to the `draft` directory and rename it to to reflect the
   title of the NEP.
3. Fill out the template NEP.
    - Number - Please leave the NEP number blank at this moment, once accepted,
      the NEP will be assigned a number.
    - Motivation - The most critical part of an NEP is to explain why this NEP is
      needed and why existing solutions are indadequate to address the problem that
      the NEP solves. NEP submissions without sufficient motiviation may be
      rejected.
    - Rationale - The rationale fleshes out the specification by describing
      what motivated the design and why particiular design decisions were made.
      It should describe alternate designs that were considered and related
      work.

      The rationale should provide evidence of consensus within the community
      and discuss important objections or concerns raised during discussion.
    - Backwards Compatibility - All NEPs that introduce backwards
      incompatibilities MUST include a section describing these
      incompatibilities and their severity.

### Discussion, development, and updates

At this point there will generally be more discussion, and of course updates
to the NEP.

Updates to a NEP can be submitted as pull requests; once again, a core
developer will merge those pull requests (typically they don't require much if
any review). In cases where the Author has commit access (fairly common), the
Author should just update the draft NEP directly.

### Review & Resolution

Once the author has completed the NEP, the API Blueprint team will review and
finally change the NEPs status to accepted, in which it is moved from the
`draft` directory into the `accepted` directory.

For a NEP to be accepted it must meet certain minimum criteria. It must be a
clear and complete description of the proposed change.

### Implementation

Finally, once an NEP has been accepted, the implementation must be completed.
When the implementation is complete and incorporated into the Nest
specification and any related tooling. The status will be changed to "Final"
and the NEP will be moved to the `final` directory.
