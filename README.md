# Require .NET Framework 4.7.2

This shows how you can author a NuGet package that will provide an error message
if the consumer is on .NET Framework 4.6.1 - 4.7.1.

Why? NuGet will allow .NET Standard 2.0 libraries to be referenced from .NET
Framework 4.6.1 and higher. Unfortunately, there are issues<sup>1</sup> with
that which is why we recommend that consumers should be on .NET Framework 4.7.2
or higher.

<sup>1</sup> See footnote 2 in the [.NET Standard support table][table].

[table]: https://docs.microsoft.com/en-us/dotnet/standard/net-standard#net-implementation-support

## General Approach

The NuGet package injects a custom MSBuild target that checks the .NET Framework
version and provides an error if it's in the problematic range.
