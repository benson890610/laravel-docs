# laravel-docs
Laravel documentation for learning
  
  
## Arisan CLI (Command Line Interface)  
  
  
  
  
### Serve project on default host  
  
```

php artisan serve // http://127.0.0.1:8000

```  
  
  
### Create basic controller  
  
```

php artisan make:controller HomeController
php artisan make:controller PostController --resource // create resource routes

```  
  
  
### Create model  
  
```

php artisan make:model Phone
php artisan make:model Phone -m // create migration

```
  
  
### Show all available routes  
  
```

php artisan route:list

```  
  
  
### Generate new api key  
  
```

php artisan key:generate

```
