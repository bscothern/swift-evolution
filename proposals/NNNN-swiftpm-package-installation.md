# Package Manager Package Installation

* Proposal: [SE-NNNN](NNNN-filename.md)
* Authors: [Braden Scothern](https://github.com/bscothern)
* Review Manager: TBD
* Status: **Awaiting implementation**

*During the review process, add the following fields as needed:*

* Implementation: [apple/swift-package-manager#NNNNN](https://github.com/apple/swift-package-manager/pull/NNNNN)
* Decision Notes: [Rationale](https://forums.swift.org/), [Additional Commentary](https://forums.swift.org/)
* Bugs: [SR-NNNN](https://bugs.swift.org/browse/SR-NNNN), [SR-MMMM](https://bugs.swift.org/browse/SR-MMMM)
* Previous Revision: [1](https://github.com/apple/swift-evolution/blob/...commit-ID.../proposals/NNNN-filename.md)
* Previous Proposal: [SE-XXXX](XXXX-filename.md)

## Introduction

This is a proposal for adding support for the installation of executables and libraries compiled by the Swift Package Manager.

Swift-evolution thread: [Discussion thread topic for that
proposal](https://forums.swift.org/)

## Motivation

Describe the problems that this proposal seeks to address. If the problem is that some functionality is currently hard to use, show how it is currently used and describe its drawbacks. If it's completely new functionality that cannot be emulated, motivate why this new functionality would help Swift developers create better Swift packages.

## Proposed solution

We propose adding the new command `swift install`.



Describe your solution to the problem. Provide examples and describe how they work. Show how your solution is better than current workarounds: is it cleaner, easier, or more efficient?

## Detailed design

### Installation Paths

We propose that the `/usr/local` hierarchy be used as the default installation location for packages. The Linux Foundation's [File Hierarchy Standards](http://refspecs.linuxfoundation.org/FHS_2.3/fhs-2.3.html) states the following as the purpose of this heiarchy:

> The `/usr/local` hierarchy is for use by the system administrator when installing software locally. It needs to be safe from being overwritten when the system software is updated. It may be used for programs and data that are shareable amongst a group of hosts, but not found in `/usr`.
> 
> Locally installed software must be placed within `/usr/local` rather than `/usr` unless it is being installed to replace or upgrade software in `/usr`.

The last statement in their standard is why it is proposed that executables be placed in `/usr/local/bin` and libraries placed in `/usr/local/lib` rather than `/usr/bin` and `/usr/lib`. This makes installed packages compatible with the exepcted file hierarchy for both macOS and Linux. This will also work in conjunction with other package managers which install to either `/usr/local` or `/usr`.



Describe the design of the solution in detail. If it involves adding or modifying functionality in the package manager, explain how the package manager behaves in different scenarios and with existing features. If it's a new API in the `Package.swift` manifest, show the full API and its documentation comments detailing what it does.  The detail in this section should be sufficient for someone who is *not* one of the author of the proposal to be able to reasonably implement the feature.


### Subcommands
`swift install --url github.com/Foo/Bar.git` Installs the package Bar from the Foo user on github.

## Security

Does this change have any impact on security, safety, or privacy?

## Impact on exisiting packages

Explain if and how this proposal will affect the behavior of existing packages. If there will be impact, is it possible to gate the changes on the tools version of the package manifest?

## Alternatives considered

Describe alternative approaches to addressing the same problem, and
why you chose this approach instead.
