# laravel-docs
Laravel documentation for learning  

### Install laravel globaly  
  
```

composer global require "laravel/installer"

```  
  
  
### Namespace classes  
  
```
    \Illuminate\Support\Facades\DB         // DB facade
    \Illuminate\Support\Facades\Auth       // Auth facade
    \Illuminate\Support\Facades\Hash       // Hash facade
    \Illuminate\Support\Facades\View       // View facade
    \Illuminate\Support\Facades\Session    // Session facade
    \Illuminate\Support\Facades\File       // File facade
    \Illuminate\Support\Facades\Schema     // Schema facade used as helper with creating migration tables
    
    \Illuminate\Database\Eloquent\Model    // Parent model class extended by other child models
    \Illuminate\Database\Schema\Blueprint  // Blueprint class used in conjuction with Schema Facade for creating table columns
    
    \Illuminate\Http\Request                // Incoming request
    \Illuminate\Http\JsonResponse           // Return response in JSON format
    
    \App\Http\Controllers\MyController;     // Controller namespace path
    
    \App\Post or \App\Models\Post           // Model namespace path

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
  
  
### Create laravel app in virtual host enviroment  

```

# In apache/conf/extra/httpd-vhosts.conf 

<VirtualHost *:80>
DocumentRoot "C:\xampp\htdocs\laravel\lsapp\public"
DirectoryIndex index.php
ServerName lsapp.test
	<Directory "C:\xampp\htdocs\laravel\lsapp\public">
	Options Indexes FollowSymLinks MultiViews
	AllowOverride all
	Order Deny,Allow
	Allow from all
	Require all granted
	</Directory>
</VirtualHost>


# In C:\Windows\System32\drivers\etc\hosts

127.0.0.1 lsapp.test

```  


### CKEditor JS  

```

<script src="https://cdn.ckeditor.com/4.21.0/standard/ckeditor.js"></script>
<script>
    CKEDITOR.replace( 'body' );
</script>

```
