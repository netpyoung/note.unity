* docfx
There are Tools for building and publishing API documentation for .NET projects - [dotnet/docfx](https://github.com/dotnet/docfx) .

- [msdn:documentation-comments](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/language-specification/documentation-comments)

- dotnet team have issue about comment style [xml vs markdown](https://github.com/dotnet/csharplang/issues/891) but this issue doesn't resolve yet.

#+BEGIN_SRC yaml
  version: '3'
  services:
    dotnet:
      # https://hub.docker.com/r/codedevote/dotnet-mono/
      image: codedevote/dotnet-mono
      volumes:
        - ${PWD}:/prj:rw
      command:
        - /bin/sh
        - -c
        - |
          ls
          pwd
          dotnet --version
          cd /prj
          dotnet build
          cd /prj/docfx_project
          mkdir -p /usr/local/share/dotnet/sdk/NuGetFallbackFolder
          nuget install docfx.console -version 2.44.0
          find / -name docfx.exe 2> /dev/null
          mono ./docfx.console.2.44.0/tools/docfx.exe
#+END_SRC
#+BEGIN_SRC json
  "metadata": [
      {
        "src": [
          {
            "files": [
              "blabla.csproj"
            ],
            "exclude": ["**/bin/**", "**/obj/**"],
            "src": "../"
          }
        ],
        "dest": "api",
        "disableGitFeatures": false,
        "disableDefaultFilter": false
      }
    ],
      "template": ["statictoc"],

#+END_SRC

* naturldocs
  - https://www.naturaldocs.org/
    #+BEGIN_QUOTE
    naturaldocs ndconfig
    naturaldocs -i Source -p ndconfig -o HTML <destination>
    #+END_QUOTE
    #+BEGIN_SRC yaml
      version: '3'
      services:
        dotnet:
          # https://hub.docker.com/r/s417lama/naturaldocs/dockerfile
          image: s417lama/naturaldocs
          volumes:
            - ${PWD}:/prj:rw
            command:
              - /bin/sh
              - -c
              - |
                cd /prj
                mkdir -p public
                naturaldocs ndconfig
    #+END_SRC