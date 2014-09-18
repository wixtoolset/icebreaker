# ICE Breaker

ICEs -- [internal consistency evaluators](http://msdn.microsoft.com/en-us/library/aa369554%28v=vs.85%29.aspx) -- are Windows Installer tools that check your Windows Installer packages for consistency with requirements and recommendations. Unfortunately, ICEs are generally slow and because of how they're implemented, require privileges that prevent them from working on most continuous integration or hosted build servers.

The ICE Breaker project aims to replace the ICEs with the following benefits:

* Take advantage of the WiX compile/link/bind build cycle to provide better diagnostics. ICEs always run after the .msi package is completely built, including compression of files into cabs. ICE Breaker can run against a WiX output object before file compression takes place, which saves time when you get an error.
* Use modern C# rather than the eclectic mix of VBScript, JScript, and C++ the ICEs are built with.
* Be faster.
* Be more controllable. ICEs can be suppressed but not particular instances of them. That usually leads to developers suppressing the ICE entirely, potentially losing out on other useful diagnostics. WiX could offer more fine-grained control both in terms of discrete testing and in diagnostic reporting.

## Requirements

* Visual Studio 2013 (including Express 2013 for Windows Desktop)
* WiX v4.0

## Shipping plans

ICE Breaker is in its own repository to make it easier to work on independent from a WiX release. WiX v4.x will pick up ICE Breaker milestone releases. 

## Development plans [details tbd]

* Tests: Required but easy
* Output: WiX v4.x extension, command-line tool for v4 .wixpdbs, command-line tool for any .msi
* ICEs: Automated tests to ensure comparable output
