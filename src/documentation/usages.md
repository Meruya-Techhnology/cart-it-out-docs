# Usages

## Adding new page
If there is any aditional requirement for adding new page, this is few step for adding new page.
1. Create page file `presentation/pages`
2. Add constant string `routeName` on the page file
3. Create provider file `presentation/providers`
4. Bind provider to the scaffold (page), for this step we can use default provider widget. Like [ChangeNotifierProvider](https://pub.dev/documentation/provider/latest/provider/ChangeNotifierProvider-class.html), or we can use `ChangeNotifierPage` from Utilities.
5. Register the page `routeName` on the `RouteUtil` class, inside the `Map<String, Widget Function(BuildContext)> get routes` values. For example
```dart
Map<String, Widget Function(BuildContext)> get routes => {
    NewPage.routeName: (context) => const NewPage(),
}
```

## Adding new datasource
Because Cart it out is backendless template, it will required to add some datasources. Follow these steps to add new datasources
1. Prepare request / response jsons
2. Convert jsons to model class inside `infrastructure/models`
3. Create / update an entity class inside `domain/entities`
4. Crate / update a mapper to map model into entity inside `infrastructure/mappers`
5. Create / update datasources abstract file for new datasource method, if needed we can use newly created model class to be an input / output of the datasource method. `infrastructure/datasources`
6. Create / update datasources implementation, create new method then do a external datasources communication such as HTTP Request, and use the model as output `infrastructure/datasources`
7. Then create / update repository abstract `domain/repositories`
8. Then create & implement the repository abstract, also use the newly created datasource class as the source. Inside the repository we execute the datasource method then convert the result into an entity using mapper. `data/repositories`
9. Is that all ? no, then we create use case for execute single or multiple repositories
10. Then finnaly add / update the facade class on the `facade` to bind and exectue the repositories
11. Finally use the facade class inside the provider class, then execute the desired repository method `presentation/provider`

## Updating data structure
If you already suitable with default data structure which located inside `assets/jsons`, and want to add more data on it you can just focus on the specific datasource for example. You want to add new field on json from `retrieve products` end point take this steps :
1. Locate impacted datasources implementation
2. Update the models `infrastructure/models` and add the desired field
3. Update the impacted entities `domain/entities` and add the desired field
4. Update the mappers `infrastructure/mappers` then map the added field both from models and entities


## Updating UI
Just like any other flutter template, we can just updating UI which suitable with our needs. But if the UI is depend on the data, we will also need the datasource, domain, provider to be updated.