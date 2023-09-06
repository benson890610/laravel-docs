# laravel-docs
Laravel documentation for learning  

<br>

### Install laravel globaly  
  
```

composer global require "laravel/installer"

```  

<br>
  
### Namespace classes  
  
```
    \Illuminate\Support\Str                // Str facade
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
    \Illuminate\Http\UploadedFile           // Uploaded file instance used for uploaded files
    
    \App\Http\Controllers\MyController;     // Controller namespace path
    
    \App\Post or \App\Models\Post           // Model namespace path

```

<br>
  
### Create latest version or with specific version project   
  
```
composer create-project laravel/laravel app_name
composer create-project laravel/laravel "5.5.*" app_name --prefer-dist
composer create-project laravel/laravel myproject --prefer-dist v5.5.*

```

<br>
  
### Laravel commands  
  
```

laravel new app_name // Create new application  
laravel -v           // Check laravel installer version

```  

<br>

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

<br>
  
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

<br>

### Install laravel breeze login and registration

```

- For laravel v.8.* run this composer require laravel/breeze:1.9.4
- For laravel higher than v.8 composer require laravel/breeze --dev

php artisan breeze:install
npm install
npm run dev

```

<br>

### CKEditor JS  

```

<script src="https://cdn.ckeditor.com/4.21.0/standard/ckeditor.js"></script>
<script>
    CKEDITOR.replace( 'body' );
</script>

```
