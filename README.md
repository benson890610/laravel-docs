# laravel-docs
Laravel documentation for learning
  
  
  
## Models  
  
  
### Create model and with migration  
  
```

php artisan make:model Post     // Model created
php artisan make:model Post -m  // Model with migration created

```  
  
  
### Get all with order by and limit  
  
```

$posts = Post::all();
$posts = Post::orderBy('id', 'desc')->get();
$posts = Post::orderBy('id', 'desc')->take(3)->get();

```  
  
  
### Get single  
  
```

$post = Post::find($id);
$post = Post::where('id', $id)->first() // To retreive as Post Model
$post = Post::where('id', $id)->get()   // To retreive as Collection

```
