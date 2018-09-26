# AngularWithMVC
Use Angular with existing MVC projects, using Angular CLI.

## Getting Started
I wanted to use Angular in my existing MVC project. Most options around were to use Angular as its own and as SPA application. Following steps will let you set up an Angular app inside existing Asp core MVC project. Then you can use this app on any existing or new View.

### Prerequisites
* <a href='https://docs.npmjs.com/getting-started/installing-node'>NodeJS and npm.</a>
* Following example is in accordance with dotnetcore MVC Application created in Visual Studio 2017.

### Use this repository
This repository is created using Angular CLI.
Please follow <a href='https://angular.io/guide/quickstart'>Angular CLI</a> to create new application.
Othewise just clone this repository to a folder with project name e-g ```my-angular-app```, and follow next steps.

```
git clone https://github.com/AhsanRazaUK/AngularWithMVC my-angular-app
cd my-angular-app
```
### Set it up
* Open existing Solution or create new project in Visual Studio where you want to use Angular app
* Copy all files/folders of ```my-angular-app```
* Right Click on to your project in Visual Stuio and paste these files in project
* Click ```Show All Files``` from top of *Solution Explorer* to verify either ```node_modules``` folder has been created
* Open ```_Layout.cshtml```. And add following tags to call Angular script files in ```environment``` tag above ``` @RenderSection("Scripts", required: false) ``` in ```body``` section.
```
  <script src="~/dist/AngularApp/runtime.js"></script>
  <script src="~/dist/AngularApp/polyfills.js"></script>
  <script src="~/dist/AngularApp/styles.js"></script>
  <script src="~/dist/AngularApp/vendor.js"></script>
  <script src="~/dist/AngularApp/main.js"></script>
  
 ```

```body``` section must look like this now

```
 <div class="container body-content">
        @RenderBody()
        <hr />
        <footer>
            <p>&copy; 2018 - AngularMVCCore</p>
        </footer>
    </div>

    <environment include="Development">
        <script src="~/lib/jquery/dist/jquery.js"></script>
        <script src="~/lib/bootstrap/dist/js/bootstrap.js"></script>
        <script src="~/js/site.js" asp-append-version="true"></script>

        <script src="~/dist/AngularApp/runtime.js"></script>
        <script src="~/dist/AngularApp/polyfills.js"></script>
        <script src="~/dist/AngularApp/styles.js"></script>
        <script src="~/dist/AngularApp/vendor.js"></script>
        <script src="~/dist/AngularApp/main.js"></script>
    </environment>
```
* Open View ```.cshtml```file where you want to use Angular. e-g ```About.cshtml``` and replce code with ```<app-root></app-root>``` there.
```
@{
    ViewData["Title"] = "About";
}
  <h2>@ViewData["Title"]</h2>
  <h3>@ViewData["Message"]</h3>

  <app-root></app-root>

```
* Right Click on ```.csproj``` file, from context menu choose ``` Edit ....csproj```. In opened ```XML``` add following
```
  <PropertyGroup>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <TypeScriptToolsVersion>Latest</TypeScriptToolsVersion>
    <TypeScriptCompileBlocked>true</TypeScriptCompileBlocked>    
  </PropertyGroup>
```
* Right-Click on ```package.json``` file and ```Restore Packages```
* Open ```Command Prompt``` and go to folder where ```.csproj``` resides. And run ``` ng build ```
* If above runs successfully add ``` ng build ``` to ``` Build Events ``` of the project in ``` pre build event command line : ``` area
* Rebuild and Run the application and you must see Angular component loaded in your ```View``` ```(About)```.
* Press ```F12``` in browser and click ```console```, you may see this message.
```
Angular is running in the development mode. Call enableProdMode() to enable the production mode.
```
## Authors

* **Ahsan Raza** 

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* https://github.com/angular/quickstart

