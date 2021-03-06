# App Metrics Reporters <img src="http://app-metrics.io/logo.png" alt="App Metrics" width="50px"/> 
[![Official Site](https://img.shields.io/badge/site-appmetrics-blue.svg?style=flat-square)](http://app-metrics.io/getting-started/intro.html) [![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg?style=flat-square)](https://opensource.org/licenses/Apache-2.0)

## What is it?

The repo contains reporting extension packages to [App Metrics](https://github.com/alhardy/AppMetrics).

## Other Reporters for App Metrics

For metric reporting capabilities see:

- [InfluxDB Extensions](https://github.com/alhardy/AppMetrics.Extensions.InfluxDB)
- [Elasticsearch Extensions](https://github.com/alhardy/AppMetrics.Extensions.Elasticsearch)
- [Prometheus Extensions](https://github.com/alhardy/AppMetrics.Extensions.Prometheus)
- [Graphite Extensions](https://github.com/alhardy/AppMetrics.Extensions.Graphite) - *Work in Progress*

## Latest Builds, Packages & Repo Stats

|Branch|AppVeyor|Travis|Coverage|
|------|:--------:|:--------:|:--------:|
|dev|[![AppVeyor](https://img.shields.io/appveyor/ci/alhardy/appmetrics-reporters/dev.svg?style=flat-square&label=appveyor%20build)](https://ci.appveyor.com/project/alhardy/appmetrics-reporters/branch/dev)|[![Travis](https://img.shields.io/travis/alhardy/AppMetrics.Reporters/dev.svg?style=flat-square&label=travis%20build)](https://travis-ci.org/alhardy/AppMetrics.Reporters)|[![Coveralls](https://img.shields.io/coveralls/alhardy/AppMetrics.Reporters/dev.svg?style=flat-square)](https://coveralls.io/github/alhardy/AppMetrics.Reporters?branch=dev)
|master|[![AppVeyor](https://img.shields.io/appveyor/ci/alhardy/appmetrics-reporters/master.svg?style=flat-square&label=appveyor%20build)](https://ci.appveyor.com/project/alhardy/appmetrics-reporters/branch/master)| [![Travis](https://img.shields.io/travis/alhardy/AppMetrics.Reporters/master.svg?style=flat-square&label=travis%20build)](https://travis-ci.org/AppMetrics.Reporters)| [![Coveralls](https://img.shields.io/coveralls/alhardy/AppMetrics.Reporters/master.svg?style=flat-square)](https://coveralls.io/github/alhardy/AppMetrics.Reporters?branch=master)|

|Package|Dev Release|Pre-Release|Release|
|------|:--------:|:--------:|:--------:|
|App.Metrics.Extensions.Reporting.Console|[![MyGet Status](https://img.shields.io/myget/alhardy/v/App.Metrics.Extensions.Reporting.Console.svg?style=flat-square)](https://www.myget.org/feed/alhardy/package/nuget/App.Metrics.Extensions.Reporting.Console)|[![NuGet Status](https://img.shields.io/nuget/vpre/App.Metrics.Extensions.Reporting.Console.svg?style=flat-square)](https://www.nuget.org/packages/App.Metrics.Extensions.Reporting.Console/)|[![NuGet Status](https://img.shields.io/nuget/v/App.Metrics.Extensions.Reporting.Console.svg?style=flat-square)](https://www.nuget.org/packages/App.Metrics.Extensions.Reporting.Console/)
|App.Metrics.Extensions.Reporting.TextFile|[![MyGet Status](https://img.shields.io/myget/alhardy/v/App.Metrics.Extensions.Reporting.TextFile.svg?style=flat-square)](https://www.myget.org/feed/alhardy/package/nuget/App.Metrics.Extensions.Reporting.TextFile)|[![NuGet Status](https://img.shields.io/nuget/vpre/App.Metrics.Extensions.Reporting.TextFile.svg?style=flat-square)](https://www.nuget.org/packages/App.Metrics.Extensions.Reporting.TextFile/)|[![NuGet Status](https://img.shields.io/nuget/v/App.Metrics.Extensions.Reporting.TextFile.svg?style=flat-square)](https://www.nuget.org/packages/App.Metrics.Extensions.Reporting.TextFile/)|

## How to build

[AppVeyor](https://ci.appveyor.com/project/alhardy/appmetrics-reporters/branch/master) and [Travis CI](https://travis-ci.org/alhardy/AppMetrics.Reporters) builds are triggered on commits and PRs to `dev` and `master` branches.

See the following for build arguments and running locally.

|Configuration|Description|Default|Environment|Required|
|------|--------|:--------:|:--------:|:--------:|
|BuildConfiguration|The configuration to run the build, **Debug** or **Release** |*Release*|All|Optional|
|PreReleaseSuffix|The pre-release suffix for versioning nuget package artifacts e.g. `beta`|*ci*|All|Optional|
|CoverWith|**DotCover** or **OpenCover** to calculate and report code coverage, **None** to skip. When not **None**, a coverage file and html report will be generated at `./artifacts/coverage`|*OpenCover*|Windows Only|Optional|
|SkipCodeInspect|**false** to run ReSharper code inspect and report results, **true** to skip. When **true**, the code inspection html report and xml output will be generated at `./artifacts/resharper-reports`|*false*|Windows Only|Optional|
|BuildNumber|The build number to use for pre-release versions|*0*|All|Optional|


### Windows

Run `build.ps1` from the repositories root directory.

```
	.\build.ps1'
```

**With Arguments**

```
	.\build.ps1 --ScriptArgs '-BuildConfiguration=Release -PreReleaseSuffix=beta -CoverWith=OpenCover -SkipCodeInspect=false -BuildNumber=1'
```

### Linux & OSX

Run `build.sh` from the repositories root directory. Code Coverage reports are now supported on Linux and OSX, it will be skipped running in these environments.

```
	.\build.sh'
```

**With Arguments**

```
	.\build.sh --ScriptArgs '-BuildConfiguration=Release -PreReleaseSuffix=beta -BuildNumber=1'
```

> #### Nuget Packages
> Nuget packages won't be generated on non-windows environments by default.
> 
> Unfortunately there is [currently no way out-of-the-box to conditionally build & pack a project by framework](https://github.com/dotnet/roslyn-project-system/issues/1586#issuecomment-280978851). Because `App.Metrics` packages target `.NET 4.5.2` as well as `dotnet standard` there is a work around in the build script to force `dotnet standard` on build but no work around for packaging on non-windows environments. 

## Contributing

See the [contribution guidlines](https://github.com/alhardy/AppMetrics/blob/master/CONTRIBUTING.md) in the [main repo](https://github.com/alhardy/AppMetrics) for details.

## Acknowledgements

* [DocFX](https://dotnet.github.io/docfx/)
* [Fluent Assertions](http://www.fluentassertions.com/)
* [XUnit](https://xunit.github.io/)
* [StyleCopAnalyzers](https://github.com/DotNetAnalyzers/StyleCopAnalyzers)
* [Cake](https://github.com/cake-build/cake)
* [OpenCover](https://github.com/OpenCover/opencover)

***Thanks for providing free open source licensing***

* [Jetbrains](https://www.jetbrains.com/dotnet/) 
* [AppVeyor](https://www.appveyor.com/)
* [Travis CI](https://travis-ci.org/)
* [Coveralls](https://coveralls.io/)

## License

This library is release under Apache 2.0 License ( see LICENSE ) Copyright (c) 2016 Allan Hardy
