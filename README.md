# ICE Breaker

ICEs -- [internal consistency evaluators][ices] -- are Windows Installer tools that 
check your Windows Installer packages for consistency with requirements and 
recommendations. Unfortunately, ICEs are generally slow and because of how they're 
implemented, require privileges that prevent them from working on most continuous 
integration or hosted build servers.

The ICE Breaker project aims to replace the ICEs with the following benefits:

* Take advantage of the WiX compile/link/bind build cycle to provide better 
diagnostics. ICEs always run after the .msi package is completely built, including 
compression of files into cabs. ICE Breaker can run against a WiX output object before 
file compression takes place, which saves time when you get an error.
* Use modern C# rather than the eclectic mix of VBScript, JScript, and C++ the ICEs are 
built with.
* Be faster.
* Be more controllable. ICEs can be suppressed but not particular instances of them. 
That usually leads to developers suppressing the ICE entirely -- or worse yet, 
suppressing ICE validation altogether -- potentially losing out on other useful 
diagnostics. WiX could offer more fine-grained control both in terms of discrete 
testing and in diagnostic reporting.
* Support running ICE Breaker tests on all WiX outputs:
  * .wixlib
  * .wixpdb
  * .msi
  * .exe (bundles)

## Requirements

* Visual Studio 2022
* WiX v4.0

## Shipping plans

ICE Breaker is in its own repository to make it easier to work on independent from a 
WiX release.

## Development plans [details tbd]

* Tests: Required but easy
* Output: WiX v4.x extension, including command for wix.exe dotnet tool.
* ICEs: Automated tests to ensure comparable output



[ices]: 
https://docs.microsoft.com/en-us/windows/win32/msi/internal-consistency-evaluators-ices
