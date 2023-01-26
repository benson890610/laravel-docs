# laravel-docs
Laravel documentation for learning  
  
  
## Laravel routing  
  
  
  

### Create routes options  
  
```

Route::get('/', function(){ return 'Home Page' });     // Basic GET route
Route::get('/', 'HomeController@index')                // 5.5 version controller routes
Route::get('/', [HomeController::class, 'index']);     // Newer version controller routes

Route::get('/about', [HomeController::class, 'about'])->name('home.about') // Naming routes 

```
