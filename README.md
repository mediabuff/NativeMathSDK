# NativeMathSDK

This is an attempt to follow MS [Walkthrough Creating an SDK using C++] in Visual Studio 2017(https://docs.microsoft.com/en-us/visualstudio/extensibility/walkthrough-creating-an-sdk-using-cpp)

As per step 11 the `lib`, `DLL`s, `pri` and `winmd` files built from the `NativeMath` and `NativeMathWRT` projects have been copied and comitted in the `NativeMathVSIX` directory structure where appropriate

However, I did add post build event that will replace them if you rebuild the `NativeMath` and/or `NativeMathWRT` projects.

## Mistakes in the walkthrough

* The `Prerequisites` element is missing from the `.vsixmanifest`
* Wrong pri file name. Should be `NativeMathWRT.pri` instead of `SimpleMath.pri`
* Incorrect path in the props file. Should be `DesignTime\Debug\x86` instead of `DesignTime\Retail\x86` (Or the example should work with a Release build)
* The `InstallationTarget` attributes in the `vsixmanifest` are incorrect (see note below)
* A minor issue, however, int step 11 the paths are formatted incorrectly without back slashes

### Wrong InstallationTarget

`<InstallationTarget Id="Microsoft.ExtensionSDK" TargetPlatformIdentifier="Windows" TargetPlatformVersion="v8.0"...` will install the extension at `C:\Program Files (x86)\Microsoft SDKs\Windows\v8.0\ExtensionSDKs\` and not `C:\Program Files (x86)\Microsoft SDKs\UAP\v0.8.0.0\ExtensionSDKs\` where a sample UWP app made with VS2017 expects them to be.
