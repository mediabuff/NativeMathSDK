# NativeMathSDK
This is an attempt to follow MS's [Walkthrough: Creating an SDK using C++](https://docs.microsoft.com/en-us/visualstudio/extensibility/walkthrough-creating-an-sdk-using-cpp)

As per step 11 the `lib`, `DLL`s, `pri` and `winmd` files built from the `NativeMath` and `NativeMathWRT` projects have been copied and comitted in the `NativeMathVSIX` directory structure where appropriate.

T extention built by the `NativeMathVSIX` project, `NativeMathVSIX.vsix` was installed and a reference added to the project in the SDK sample solution.

However, the properties in `NativeMathSDK.props` are not being applied.

Also note that after multiple times adding and removing the reference, Visual Studio left multiple import elements in the project file.
You can see where I cleaned them up [here](https://github.com/phraemer/NativeMathSDK/commit/8044ebe35f8e1d85ff28a4e93c3836c37556692d).
The side effect of those extraneous imports is that the `NativeMathWRT` interface will not show up in the Object Browser. It just appears as empty. Once removed and the SDK reference was re-added the interface re-appeared.

