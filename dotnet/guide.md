* coverage
dotnet test
dotnet tool install coverlet.console --tool-path ./tools || true
./tools/coverlet Tests/bin/Debug/netcoreapp2.0/Tests.dll --target "dotnet" --targetargs "test --no-build" --format cobertura
reportgenerator -reports:coverage.cobertura.xml -targetdir:report
start report/index.htm

https://medium.com/@goelhardik/collecting-single-code-coverage-report-for-multiple-dotnet-core-projects-e49c98b5a66e

* warn as error
<MSBuildTreatWarningsAsErrors>true</MSBuildTreatWarningsAsErrors>
<TreatWarningsAsErrors>true</TreatWarningsAsErrors>

* lint
** Microsoft.Analyzers.ManagedCodeAnalysis
   - https://docs.microsoft.com/en-us/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules?view=vs-2019
   - https://github.com/dotnet/roslyn-analyzers
   #+BEGIN_SRC xml
     <PropertyGroup>
       <CodeAnalysisRuleSet>..\Bamboo.ruleset</CodeAnalysisRuleSet>
     </PropertyGroup>
   #+END_SRC
   #+BEGIN_SRC xml
     <?xml version="1.0" encoding="utf-8"?>
     <RuleSet Name="helloworld" Description="desc" ToolsVersion="10.0">
       <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
       </Rules>
       <Rules AnalyzerId="Microsoft.CodeQuality.Analyzers" RuleNamespace="Microsoft.CodeQuality.Analyzers">
         <Rule Id="SA0000" Action="Error" />
       </Rules>
     </RuleSet>
   #+END_SRC
** Microsoft.DotNet.Analyzers.Compatibility
   - https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility
   - https://github.com/dotnet/platform-compat
   #+BEGIN_SRC xml
     <ItemGroup>
       <PackageReference
           Include="Microsoft.DotNet.Analyzers.Compatibility"
           Version="0.2.12-alpha">
         <PrivateAssets>all</PrivateAssets>
         <IncludeAssets>
           runtime; build; native; contentfiles; analyzers; buildtransitive
         </IncludeAssets>
       </PackageReference>
     </ItemGroup>
   #+END_SRC
** stylecop
   - https://www.nuget.org/packages/StyleCop/
#+BEGIN_SRC xml
    <ItemGroup>
      <PackageReference Include="StyleCop.Analyzers" Version="1.1.1-beta.61">
        <PrivateAssets>all</PrivateAssets>
        <IncludeAssets>
          runtime; build; native; contentfiles; analyzers
        </IncludeAssets>
      </PackageReference>
      <AdditionalFiles Include="..\stylecop.json" />
    </ItemGroup>
#+END_SRC
#+BEGIN_SRC json
  {
      "$schema": "https://raw.githubusercontent.com/DotNetAnalyzers/StyleCopAnalyzers/master/StyleCop.Analyzers/StyleCop.Analyzers/Settings/stylecop.schema.json",
      "settings": {
          "orderingRules": {
              "usingDirectivesPlacement": "outsideNamespace"
          }
      }
  }
#+END_SRC

** menees
   - https://www.nuget.org/packages/Menees.Analyzers/

#+BEGIN_SRC xml

  <ItemGroup>
    <AdditionalFiles Include="..\Menees.Analyzers.Settings.xml">
      <Link>Menees.Analyzers.Settings.xml</Link>
    </AdditionalFiles>
    <PackageReference Include="Menees.Analyzers.2017" Version="2.0.3">
      <PrivateAssets>all</PrivateAssets>
    </PackageReference>
  </ItemGroup>
#+END_SRC
#+BEGIN_SRC xml
  <?xml version="1.0" encoding="utf-8" ?>
  <Menees.Analyzers.Settings>
    <MaxLineColumns>100</MaxLineColumns>
    <MaxMethodLines>200</MaxMethodLines>
    <MaxFileLines>2250</MaxFileLines>
  </Menees.Analyzers.Settings>
#+END_SRC
** fxcop
#+BEGIN_SRC xml
      <ItemGroup>
        <PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers" Version="2.9.4" />
      </ItemGroup>
#+END_SRC
