# laravel-docs
Laravel documentation for learning
  
  
## Arisan CLI (Command Line Interface)  
  
<br>
  
### Serve project on default host  
  
```

php artisan serve              // http://127.0.0.1:8000
php artisan server --port=8080 // http://127.0.0.1:8080

```  

<br>
  
### Create controller  
  
```

php artisan make:controller HomeController
php artisan make:controller PostController --resource                         // Create controller with resource handler methods
php artisan make:controller AlbumController --model=Album --requests --api    // Create api controller with requests api handler methods

```  

<br>

### Create resource 
  
```

php artisan make:resource AlbumResource

```

<br>
  
### Create model  
  
```

php artisan make:model Phone
php artisan make:model Phone -m // create migration

```  

<br>

### Create migration  

```

php artisan make:migration create_post_table

```

<br>
  
### Create middleware  
  
```

php artisan make:middleware ageRestriction

```

<br>
  
### Show all available routes  
  
```

php artisan route:list

```  

<br>
  
### Generate new api key  
  
```

php artisan key:generate

```  
  
<br>

### Check project version  

```

php artisan --version

```  

<br>

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

<br>

### Maintance mode on/off  

```

php artisan down --message="Upgrading Database" // Set to maintance mode 
php artisan up                                  // Set to live mode

```  
  
<br>

### Route caching  

```

php artisan route:cache

```

<br>

### Create laravel symlink

```

php artisan storage:link

```
