# Introduction

**Cart It Out** is a scalable Flutter template for e-commerce application, which easy to use, and easy to adapt for small team to huge team operation. Cart It Out using Enhanced Clean Architecture, or so-called DDD (Domain Driven Design) Architecture. Cart It Out also using Newest **Material 3**, **Top Ranked Packages**, And **Dynamic approach** for more flexibility of future usecases. **Cart It Out** created with zero backend, but it's very possible to swap the datasource without breaking any logical & further changes (Depends on the usecase & Requirement).

Cart It Out also using composable package that makes any further customization is possible, also we are design Cart It Out to be a Startup Ready & Startup Friendly so our client does not have to refactor it later when they grow bigger. Because we understand that our client needs, Not only beautiful UI but also Robust and Scalable. Therefore for more simple application, it's very possible but we are recommend to read the primary guideline of [Clean Architecture](https://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html) first. 

- [Clean Architecture](https://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html) 
- [Dart Effective](https://dart.dev/guides/language/effective-dart)
- [Material 2](https://material.io/) 
- [Material 3](https://m3.material.io/) 

## Geting Started
After download and extract the project from Code Canyon run this code
```sh
flutter clean
```
Then run 
```sh
flutter pub get
```
Don't forget to add launch json for .vsCode configuration to run debug from Visual studio code.
```json
{
    // Use IntelliSense to learn about possible attributes.
    // Hover to view descriptions of existing attributes.
    // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        {
            "name": "cart-it-out [Development]",
            "request": "launch",
            "type": "dart", 
            "args": [
                "--dart-define",
                "PROFILE=development",
            ],
        },
        {
            "name": "cart-it-out [Staging](profile mode)",
            "request": "launch",
            "type": "dart",
            "flutterMode": "profile",
            "args": [
                "--dart-define",
                "PROFILE=staging",
            ],
        },
        {
            "name": "cart-it-out [Production](release mode)",
            "request": "launch",
            "type": "dart",
            "flutterMode": "release",
            "args": [
                "--dart-define",
                "PROFILE=production",
            ],
        }
    ]
}
```
However If you are using android studio you can add this args into launch configuration
`--dart-define PROFILE=development/staging/production`

## Project Structure

```
.
├─ .vscode
│  └─ launch.json
├─ assets
│  ├─ images
│  ├─ jsons
│  └─ markdowns
├─ android
├─ ios
├─ web
├─ test
└─ lib
   ├─ common
   │  ├─ consts
   │  ├─ core
   │  ├─ extensions
   │  ├─ styles
   │  └─ utils
   ├─ domain
   │  ├─ entities
   │  ├─ repositories
   │  ├─ usecases
   │  ├─ error_handler (Optional)
   │  └─ exceptions (Optional)
   ├─ facade
   ├─ infrastructure
   │  ├─ datasources
   │  ├─ models
   │  ├─ mappers
   │  └─ repositories
   └─ presentation
      ├─ providers
      ├─ pages
      ├─ params
      └─ widgets
```