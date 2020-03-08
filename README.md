
### Clean Architecture
According to the ASP.Net Core [documentation](https://docs.microsoft.com/en-us/dotnet/architecture/modern-web-apps-azure/common-web-application-architectures#clean-architecture), our source code can be structured as separate projects or layers with proper dependency flow from outwards towards our application core layer. The dependency flow is as represented below: 

![Imgur](https://i.imgur.com/culkU5x.png)
<figcaption>Clean Architecture Dependency</figcaption>

__Application Core Types__ includes Interfaces, Services, DTO (Data Transfer Objects) and Entities (Business Models).<br/>
__Infrastructure Types__ includes EF Core types (DbContext, Migration), Data access implementation types (Repositories), Infrastructure-specific services (for example, FileLogger or SmtpNotifier).<br/>
__User Interface Types__ includes Controllers, Filters, Views, ViewModels, Startup<br/>
__Tests Types__ includes Unit Tests, Integration Tests

To create our template, we first have to create a blank solution in visual studio or using the command line

```
dotnet new sln -o CleanArchitecture
```

This creates a *CleanArchitecture.sln* file inside CleanArchitecture folder.
Next we move into the folder by running the following command

```
cd CleanArchitecture
```

Inside the folder, we will create the relevant projects or layers of our application.

```
dotnet new classlib -o CleanArchitecture.Core

dotnet new classlib -o CleanArchitecture.Infrastructure

dotnet new mvc -o CleanArchitecture.Presentation

dotnet new xunit -o CleanArchitecture.Tests
```

If you noticed, I changed the names a bit, yes, you can absolutely customize the structure to fit your needs. 
Next, we will add these projects to the solution *CleanArchitecture.sln*.

```

dotnet sln CleanArchitecture.sln add .\CleanArchitecture.Core\CleanArchitecture.Core.csproj .\CleanArchitecture.Infrastructure\CleanArchitecture.Infrastructure.csproj .\CleanArchitecture.Presentation\CleanArchitecture.Presentation.csproj .\CleanArchitecture.Tests\CleanArchitecture.Tests.csproj

```

We're done! 👍

All we need do now is to create the relevant folders inside the individual project folders. For instance, for *CleanArchitecture.Core* project we will create the _Interface_, _Service_, _Entities_ and _DTO_ folders and do the same for the other projects according to our needs and requirements.

Happy coding!!!