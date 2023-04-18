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


### Get single or fail
  
```

$post = Post::findOrFail($id);  // This will fetch post or redirect to fail destination

```  
  
  
### Get all by pagination  
  
```

$posts = Post::orderBy('id', 'desc')->paginate(2);

// In blade.php  

@foreach($posts as $post) 
    // Show each post
@endforeach

// Show pagination links
{{ $posts->links() }}

```  
  
  
### Limit enough items  

```

$posts = Post::orderBy('id', 'desc')->limit(5)->get() // Total 5 items

```
