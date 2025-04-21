# browserstack-sdk-dotnet-9

Demo showing that the BrowserStack SDK has a compatibility issue with .NET 9
This is a default xUnit test project, with the only change being adding `BrowserStack.TestAdapter` as a package reference.

[Per this page](https://www.browserstack.com/docs/automate/selenium/getting-started/c-sharp/nunit/integrate-your-tests) “BrowserStack does not support .NET version 9 and above.”

## Repro Steps

1. Install the .NET 9.0 SDK
2. Run `dotnet restore`
3. Run `dotnet build`

## Result

```plaintext
...browserstack-sdk-dotnet-9/TestProject1/TestProject1.csproj : error : 
      MonoMod.Core does not support the net9.0 runtime. Please visit https://github.com/MonoMod/MonoMod/ to participate in discussion or contribute.
                       If you REALLY know what you're doing, set MonoMod_CheckTargetRuntime to false to skip this check.
```

Note that adding `<MonoMod_CheckTargetRuntime>false</MonoMod_CheckTargetRuntime>` to the csproj does not change the error.

## Expected Result

The project builds successfully with no errors.
