# Kickstart your SPA with this angular / .net core template

When it's time to start a new project you're faced with the same decisions time and time again: What stack should I use, what libraries will I be utilizing, how will I structure the application? Like us, you may start digging through old projects and code to find how you set up some initial boilerplate (DB Connections, Authentication, Localization, etc…). This is a great solution if you're a single developer or on a small team, but what if you no longer have access to the code? Or maybe you're on a larger team and are not the only one responsible for setting up the project. This is where code consistency starts to fall apart.

That's why we decided to create a starter template. With it, we are set up with the tools and boilerplate to get things rolling as quickly as possible. Not only does this save us time but it also helps to keep the team moving in the same direction. We spend less time doing the same things again and again, which runs the risk of deviating from our common practices, and more time building awesome applications.

# Features

Our template is not meant to impose strict rules and dampen creativity. It is built with clean and detailed instructions to quickly add the features you need while ignoring the ones you don't. Some of the features and guidelines we have added (so far) include:

- Folder Structure and Files split by feature
- State Management with RxJs Observables
- Theming
- Localization
- Data Transfer Models and autogenerated TypeScript Models
- x Authentication and Authorization
- x Data Access
- Azure Pipelines Continuous Integration & Delivery

Experimentation is still an invaluable part of software development for us. So as we continue to try and test new ideas and then reflect those ideas into the template.

# Organizing Files and Folders (Split by Feature)

Navigating the code of an application gets increasingly more complex as it grows, features are added and code is reworked. That's why it's important to have a clean, organized foundation. We have structured the template in a way that makes it easier and more familiar to find your way around.

The basis of the folder structure starts from the built in `dotnet new angular` template.

![image-20191104225401262](..\img\angular-template\image-20191104225401262.png)

In the project directory there are only 4 areas where you will spend the most time:

- **API**: Contains all API **controllers** and **models** (DTOs).
- **ClientApp**: The angular project folder, all angular and SPA related code goes here.
- **Data**: The Data Access layer which will contain all **Database Models** and **Data Access** (i.e. Entity Framework, ADO.Net).
- **Root**: The root directory contains all top level application code including `Startup.cs` and `appsettings.json`.

## The API folder structure

We split our API Controllers by feature or specific areas with each new feature following the same pattern. The DTO's or Models are always in the same area as the controller it's related to. This keeps the items organized by area rather than a single folder with all controllers and a single folder with all models.

<img src="..\img\angular-template\1572802621684.png" alt="1572802621684" style="zoom:50%;" />

As you can see above our folder structure follows the format:

```
/API/[Feature]/
/API/[Feature]/[Feature]Controller.cs
/API/[Feature]/Models/
/API/[Feature]/Models/[Feature]Model.cs
/API/[Feature]/Models/[Feature2]Model.cs
```

## Angular Client Application

The **ClientApp** folder is going to contain the bulk of your application code, which makes it important to keep it as clean as possible. We have setup a structure that covers splitting by feature but also common shared functionality.

<img src="..\img\angular-template\1572804449388.png" alt="1572804449388" style="zoom:50%;" />

Starting from the top, we have the **app** folder which contains all application code, **assets** which contain styles, images and all other static resources, **environments** for configuration specific settings, and **theme** for overriding the default bootstrap styles.

### The app folder

**Components** and **Sub Components** are located directly in the **app** folder. It is important to group related components and features together. For example, if your application requires the ability to manage user accounts. You may need a screen to search and a screen to create and edit. The edit screen may have a details section and a roles and permissions section. So your component hierarchy may look something like:

```
/app/users/{user.component}
/app/users/search/{search.component}
/app/users/user/{user.component}
/app/users/user/details/{details.component}
/app/users/user/permissions/{permission.component}
```

In some cases a **component** is not directly related to an overall page or feature and is re-used in multiple areas of the application. For this we have a **shared** folder.

![image-20191104225319566](..\img\angular-template\image-20191104225319566.png)

The **shared** folder contains a single **module\*\*** which is used to declare common **components**, **directives**, and **pipes**. Each module in the application can then import the **shared module**. If a component is expected to be used outside of it's current module for any reason, it should be declared inside the **shared module** instead.

**Services**, **Endpoints** and **Models**

![image-20191104230106155](..\img\angular-template\image-20191104230106155.png)

## Running the application

- Run , see how it works

### Angular

### Api

## State Management with RxJs Observables

## TypeGen

## Services / Endpoints

## Setup

- Clone repo
- Dotnet restore
- npm i
- Secrets extension

## Recommended Extensions for VS Code

-