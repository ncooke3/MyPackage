# MyPackage

This example Swift package demonstrates how Xcode does not pick up major
version 10+ tags as expected. There are two tagged releases for this package,
`9.0.0` and `10.0.0`. 

The issue is that when adding this package to a client project in Xcode, the
`9.0.0` tag is recommended as the latest tag instead if the `10.0.0` tag.

## Repro steps
1. In a client Xcode project, begin the `Add Package Dependency` flow.
1. Search for this package: `https://github.com/ncooke3/MyPackage.git`
1. On the package preview page, selecting the _Up to Next Major Version_
dependency rule will pin `9.0.0` as the current major version. **This is
unexpected as the latest version is `10.0.0`.**

This was reproduced with a clean SPM cache 
(`~/Library/Caches/org.swift.swiftpm/repositories`) in both Xcode 13.3.1 and
Xcode 14.2.
