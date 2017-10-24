# NativeMathSDK

This is an attempt to follow MS [Walkthrough Creating an SDK using C++](https://docs.microsoft.com/en-us/visualstudio/extensibility/walkthrough-creating-an-sdk-using-cpp)

As per step 11 the `lib`, `DLL`s, `pri` and `winmd` files built from the `NativeMath` and `NativeMathWRT` projects have been copied and comitted in the *NativeMathVSIX* directory structure where appropriate


## Mistakes in the walkthrough

* The `Prerequisites` element is missing from the `.vsixmanifest`
* Wrong pri file name. Should be `NativeMathWRT.pri` instead of `SimpleMath.pri`
* Incorrect path in the props file. Should be `DesignTime\Debug\x86` instead of `DesignTime\Retail\x86` (Or the example should work with a Release build)
* The `InstallationTarget` attributes in the `vsixmanifest` are incorrect (see note below)
* A minor issue, however, int step 11 the paths are formatted incorrectly without back slashes

### Wrong InstallationTarget

`<InstallationTarget Id="Microsoft.ExtensionSDK" TargetPlatformIdentifier="Windows" TargetPlatformVersion="v8.0"...` will install the extension at `C:\Program Files (x86)\Microsoft SDKs\Windows\v8.0\ExtensionSDKs\` and not `C:\Program Files (x86)\Microsoft SDKs\UAP\v0.8.0.0\ExtensionSDKs\` where a sample UWP app made with VS2017 expects them to be.

## Remaining problem

The extention installer built by the `NativeMathVSIX` project fine.
`NativeMathVSIX.vsix` was installed and a reference added to the project in the SDK sample solution.

However, the properties in `NativeMathSDK.props` are not being applied.

Also note that after multiple times adding and removing the reference, Visual Studio left multiple import elements in the project file.
You can see where I cleaned them up [here](https://github.com/phraemer/NativeMathSDK/commit/8044ebe35f8e1d85ff28a4e93c3836c37556692d).
The side effect of those extraneous imports is that the `NativeMathWRT` interface will not show up in the Object Browser. It just appears as empty. Once removed and the SDK reference was re-added the interface re-appeared.
