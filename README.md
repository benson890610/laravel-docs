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
  
  
### Create middleware  
  
```

php artisan make:middleware ageRestriction

```
  
  
### Show all available routes  
  
```

php artisan route:list

```  
  
  
### Generate new api key  
  
```

php artisan key:generate

```  
  
  
### Check project version  

```

php artisan --version

```  


### Artisan Tinker  

```

php artisan tinker 

App\Post::count() // 2

$post = new App\Post;
$post->title = 'Post Four'
$post->body  = 'Text body message prepared'
$post->save()  // New post in database created

exit // This will exit from tinker terminal shell session


```  


### Maintance mode on/off  

```

php artisan down --message="Upgrading Database" // Set to maintance mode 
php artisan up                                  // Set to live mode

```  
  

### Route caching  

```

php artisan route:cache

```
