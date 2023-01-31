# laravel-docs
Laravel documentation for learning  

### Install laravel globaly  
  
```

composer global require "laravel/installer"

```
  
  
### Create latest version or with specific version project   
  
```
composer create-project laravel/laravel app_name
composer create-project laravel/laravel "5.5.*" app_name --prefer-dist
composer create-project laravel/laravel myproject --prefer-dist v5.5.*

```
  
  
### Laravel commands  
  
```

laravel new app_name // Create new application  
laravel -v           // Check laravel installer version

```  
  
  
### RouteServiceProvider.php  
  
```

// v5.5 if this property is presented then we dont need to specify in routes/ full controller namespace path 
protected $namespace = 'App\Http\Controllers';

public function boot() {
  
  // Only execute if {id} is numeric
  Route::pattern('id', '[0-9]+');
  
  // Bind eloquent model class to route parameter
  Route::model('user', App\User::class);
  
  parent::boot();

}

```
