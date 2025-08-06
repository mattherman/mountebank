# Update: August 2025

Myself and a few others are working to transfer the original project to an [organization](https://github.com/mountebank-testing) for continued maintenance. This fork is no longer relevant.

# Project Status

This repository is a fork of [bbyars/mountebank](https://github.com/bbyars/mountebank).

In May 2024 the project maintainer announced that development was ending with the following message:

> Unfortunately, there are no easy exit ramps for hobbyist open source. I've greatly enjoyed building and maintaining mountebank, but after a decade, I find myself no longer having the energy or passion to continue to do so on nights, weekends, and holidays. Handing someone else that responsibility for a 10-year-old code base that they did not write is... challenging.
>
> Please fork at will, and thank you for being part of the community.

I'm incredibly grateful to Brandon Byars for his work on Mountebank over the years. I take no credit for any of the work he did maintaining this project up until this point. My hope with this fork is to at least keep up with patching dependencies and releasing new versions to npm. While the docs are bundled with the tool itself, I'm hoping to get a Github Pages site set up to host the documentation somewhere.

I can't guarantee any development of new features. While I've been a user of Mountebank for years (and even maintain a client library, [MbDotNet](https://github.com/mattherman/MbDotNet)), I've never contributed to the actual codebase or maintained any other npm packages. If I get to a point where I understand things well enough to actually start building and publishing new packages, I may be open to pull requests for bug fixes or small feature additions.

# Welcome, friend

mountebank is the only open source service virtualization tool that competes with the commercial offerings
in terms of protocol diversity, capability, and performance. Here's what
[Capital One wrote](https://medium.com/capital-one-tech/moving-one-of-capital-ones-largest-customer-facing-apps-to-aws-668d797af6fc)
about their mobile cloud migration (emphasis theirs):

>In fact, halfway through we discovered our corporate mocking software couldn’t handle the
>sheer amount of performance testing we were running as part of this effort (_we completely crushed
>some pretty industrial enterprise software in the process_). As a result, we made the call to move
>the entire program over to a Mountebank OSS-based solution with a custom provision to give us the ability
>to expand/shrink our mocking needs on demand.

At the moment, the following protocols are implemented, either directly in the tool or as a community extension:
* http
* https
* tcp (text and binary)
* smtp
* ldap
* grpc
* websockets
* graphql
* snmp
* telnet
* ssh
* netconf

mountebank supports mock verification, stubbing with advanced predicates, JavaScript injection,
and record-playback through proxying.

![how it works](https://github.com/mattherman/mountebank/blob/master/src/public/images/overview.gif?raw=true)

## Install and Run

Install:

    npm install -g mountebank

Run:

    mb

There are a number of command line options if you need
to customize mountebank.

All pre-release versions of mountebank are available with the `beta` [npm tag](https://www.npmjs.com/package/mountebank).
No `beta` version is published unless it has passed all tests.

## Learn More

After installing and running, view the docs in your browser at <http://localhost:2525>.

You can always learn more by buying Brandon's book:

[![Testing Microservices with Mountebank](https://github.com/mattherman/mountebank/blob/master/src/public/images/book.jpg)](https://www.manning.com/books/testing-microservices-with-mountebank?a_aid=mb&a_bid=ee3288f4)

## Building

There are two packages: mountebank itself, and a test package called mbTest (which houses all
out-of-process tests against mountebank). First ensure all dependencies are installed for both packages:

    npm install

Then, run all tests:

    npm test

Several other test configurations exist. You can see the CI pipeline in .circleci/config.yml.

There are some tests that require network access.
A few of these tests verify the correct behavior under DNS failures.  If your ISP
is kind enough to hijack the NXDOMAIN DNS response in an attempt to allow you to conveniently peruse their
advertising page, those tests will fail.  I suggest that, under such circumstances, you talk to your ISP
and let them know that their policies are causing mountebank tests to fail. You can also set
the environment variable `MB_AIRPLANE_MODE=true`, which will avoid tests requiring your DNS resolver.

## Contributing

See "Project Status" section for details.
