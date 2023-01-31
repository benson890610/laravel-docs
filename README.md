# laravel-docs
Laravel documentation for learning
  
  
  
## Models  
  
  
### Create model and with migration  
  
```

php artisan make:model Post     // Model created
php artisan make:model Post -m  // Model with migration created

```  
  
  
### Get all  
  
```

$posts = Post::all();
$posts = Post::orderBy('id', 'desc')->get();

```  
  
  
### Get single  
  
```

$post = Post::find($id);

```
