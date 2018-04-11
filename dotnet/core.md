.NET Core
=========

https://blogs.msdn.microsoft.com/dotnet/2016/11/16/announcing-net-core-tools-msbuild-alpha/




https://blog.rendle.io/my-essential-visual-studio-extensions/


ETC : https://docs.microsoft.com/en-us/dotnet/articles/csharp/expression-trees-translating





[.NET Core Roadmap](https://github.com/dotnet/core/blob/master/roadmap.md)

# [PCL](http://blog.jakeymvc.com/dotnet-tomorrow)
PCL 이 제공하는 기능은 닷넷 생태계의 교집합적인 기능이므로 Full .NET 프레임워크에 비해서는 제한적일 수 밖에 없는 단점이 존재한다. 또한, PCL이 각각 다른 플랫폼에서 어떻게 동작하는지가 명료하지 않아서 참조한 기능이 의도하지 않게 플랫폼에 따라 다르게 동작할 수 있는 위험도 있다.
닷넷의 미래

다행이도 Microsoft는 이 문제를 인식하고 명확한 비전을 수립했다. PCL 방식을 버리고 플랫폼간에 공통 API를 지원하는 계약(CONTRACT) 방식으로 전환한다는 전략이다. 교집합 성격의 PCL이 합집합 성격의 계약으로 바뀌고 이 계약을 지키는 플랫폼과 그렇지 못한 플랫폼을 개발자에게 알려 준다.

이 새로운 계약기반 API를 .NET Standard Library라고 한다. NET Standard Library 는 구현 차원에서 두 가지 성격이 공존하는데 크로스 플랫폼적인 Full Implementation과 플랫폼 종속적인 Reference Implementation(기존의 PCL 방식)의 조합이다.


# [.NET Standard](https://docs.microsoft.com/en-us/dotnet/articles/standard/library)


# [Framework](https://docs.microsoft.com/en-us/dotnet/articles/standard/frameworks)
Framework version alias TFM(Target Framework Moniker) TFM(Compact Target Framework Moniker .NET Standard Meta package
Framework	Latest Version	Target Framework Moniker (TFM)	Compact Target Framework Moniker (TFM)	.NET Standard Version	Metapackage
.NET Standard	1.6	.NETStandard,Version=1.6	netstandard1.6	N/A	NETStandard.Library
.NET Core Application	1.0.1	.NETCoreApp,Version=1.0	netcoreapp1.0	1.6	Microsoft.NETCore.App
.NET Framework	4.6.2	.NETFramework,Version=4.6.2	net462	1.5	N/A


~~~
SHARED - .NET Standard Library.
.NET Framework : WPF, Windows.Forms, ASP.NET
.NET Core : UWP, ASP.NET Core
Xamarin: iOs, macOs, Android
~~~


# .NET Core와 .NET Framework 차이점.
https://docs.microsoft.com/en-us/dotnet/articles/core/index


* App-models -- .NET Core does not support all the .NET Framework app-models, in part because many of them are built on Windows technologies, such as WPF (built on top of DirectX). The console and ASP.NET Core app-models are supported by both .NET Core and .NET Framework.
* APIs -- .NET Core contains many of the same, but fewer, APIs as the .NET Framework, and with a different factoring (assembly names are different; type shape differs in key cases). These differences currently typically require changes to port source to .NET Core. .NET Core implements the .NET Standard Library API, which will grow to include more of the .NET Framework BCL API over time.
* Subsystems -- .NET Core implements a subset of the subsystems in the .NET Framework, with the goal of a simpler implementation and programming model. For example, Code Access Security (CAS) is not supported, while reflection is supported.
* Platforms -- The .NET Framework supports Windows and Windows Server while .NET Core also supports macOS and Linux.
* Open Source -- .NET Core is open source, while a read-only subset of the .NET Framework is open source.

# .NET Core와 Mono
Mono is the original cross-platform and open source .NET implementation, first shipping in 2004. It can be thought of as a community clone of the .NET Framework. The Mono project team relied on the open .NET standards (notably ECMA 335) published by Microsoft in order to provide a compatible implementation.
The major differences between .NET Core and Mono:
* App-models -- Mono supports a subset of the .NET Framework app-models (for example, Windows Forms) and some additional ones (for example, Xamarin.iOS) through the Xamarin product. .NET Core doesn't support these.
* APIs -- Mono supports a large subset of the .NET Framework APIs, using the same assembly names and factoring.
* Platforms -- Mono supports many platforms and CPUs.
* Open Source -- Mono and .NET Core both use the MIT license and are .NET Foundation projects.
* Focus -- The primary focus of Mono in recent years is mobile platforms, while .NET Core is focused on cloud workloads.


# [CLI](https://github.com/dotnet/cli)

[install script](https://docs.microsoft.com/en-us/dotnet/articles/core/tools/dotnet-install-script)
[document-cli](https://docs.microsoft.com/en-us/dotnet/articles/core/tools/index)
[CI - integration](https://docs.microsoft.com/en-us/dotnet/articles/core/tools/using-ci-with-cli)

# DNX
In short, the DNX tools have been replaced with the .NET Core CLI tools.
DNX, a Dot Net eXecution environment, contains all of the code that is required to bootstrap and run an application. It includes the compilation system, SDK tools and the native CLR host, with NuGet packages being used to access assemblies that are referenced by the application

[~]$ brew install Caskroom/cask/dotnet
brew install openssl
brew link --force openssl

mkdir temp && cd temp
dotnet new
dotnet restore
dotnet run

## new
project.json
Program.cs

## restore
analyze `project.json`
download dependencies
write `project.lock.json` for `dotnet build` or `dotnet run`

## run - [deployment](https://docs.microsoft.com/en-us/dotnet/articles/core/deploying/index)
call `dotnet build`
`dotnet <assembly.dll` to run the target application


### FDD : Framework-Dependent Deployment
### SCD : Self-Contained Deployment


### [RID](Runtime IDentifier)
https://docs.microsoft.com/en-us/dotnet/articles/core/rid-catalog

[runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json)
`[os].[version]-[arch]`


## [publish](https://docs.microsoft.com/en-us/dotnet/articles/core/tools/dotnet-publish)
compiles the application, reads through its dependencies specified in the `project.json` file and publishes the resulting set of files to a directory.


## clean - [.NET Core CLI extensibility model](https://docs.microsoft.com/en-us/dotnet/articles/core/tools/extensibility)
ln -s dotnet-clean /usr/local/bin/



# [Visual Studio Tools for Docker](https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4)


.Net 4.5 C# using ExceptionDispatchInfo.Capture to rethrow exceptions
