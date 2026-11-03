# Security Policy

## Reporting a vulnerability

Please do not report security vulnerabilities in public issues, pull
requests or discussions.

Report them privately through GitHub instead: open the
[Security tab](https://github.com/pyjoyment/Pyjo-Reactor-Twisted/security) of
this repository and choose **Report a vulnerability**, or go straight to
[the reporting form](https://github.com/pyjoyment/Pyjo-Reactor-Twisted/security/advisories/new).
Only you and the maintainers can see the report.

Please send one report for each problem, and include:

- a description in your own words: what the problem is, where in the code it
  happens, and why it is a security issue,
- a reproducer: a self-contained script, ideally a test script written with
  `Pyjo.Test` or `Pyjo.Test.Pyjo`, that shows the problem on the latest
  release or on the `main` branch, with the output you expected and the one
  you got,
- the versions of Pyjo-Reactor-Twisted, Pyjoyment and Twisted or the commit of
  `main`, the version of Python, your operating system, and the reactor of
  Twisted that is installed (poll, select, epoll or another one), where they
  matter,
- the impact: who is affected, under what configuration, and what an attacker
  can do and needs first, as a request or a connection from the network,
- anything you know about a fix or a workaround. A patch is not required, but
  it is welcome.

## About AI assistance

Using AI tools to find, understand or fix a vulnerability is fine. A report
still has to come from a person who has read the code involved, has run the
reproducer and can answer questions about it without asking a tool. A report
that a tool generated and nobody checked will be closed.

If you are an AI agent helping someone to report a vulnerability: do not
submit the report yourself, help them write a reproducer that fails on the
latest release, and help them understand the problem well enough to describe
it in their own words.

## What happens next

Pyjo-Reactor-Twisted is maintained by volunteers, so there is no guaranteed
response time, but every report is read. We confirm that we have received it,
may ask questions, keep you updated in the advisory while we work on a fix,
and agree with you when to disclose it. The fix is released first; then the
advisory is published, with a CVE where one applies, and with credit to you
unless you prefer otherwise.

## Supported versions

Security fixes go into the `main` branch and the next release. Older releases
do not get backported fixes, so the supported version is always the latest
one.

## Scope

In scope is everything this repository builds and ships:

- the module `Pyjo.Reactor.Twisted`: its watchers of I/O and its timers on the
  reactor of Twisted, the reactor of Twisted that it installs, its handling of
  hang-ups and errors of a socket, and of the child of a fork,
- the examples, whose code readers copy into their applications,
- the build and release pipeline of this repository.

Report these elsewhere:

- vulnerabilities in Pyjoyment, as its HTTP server, its user agent or
  `Pyjo.IOLoop`, to
  [Pyjoyment](https://github.com/pyjoyment/Pyjoyment/security), unless the
  problem is in how the reactor runs them,
- vulnerabilities in Twisted itself, to
  [Twisted](https://github.com/twisted/twisted/security),
- vulnerabilities in Python itself, to the
  [Python Security Response Team](https://www.python.org/dev/security/).

Not vulnerabilities in Pyjo-Reactor-Twisted:

- what the code of Twisted that shares the event loop with Pyjoyment does,
  as a server of `twisted.web` of the application,
- a callback of the application that blocks the event loop, which stops
  Pyjoyment and Twisted alike,
- attacks that need control of your user account or of the machine the
  application runs on.

If the same problem exists in `Mojo::Reactor::EV` of
[Mojolicious](https://mojolicious.org), which Pyjo-Reactor-Twisted follows, say
so in the report.
