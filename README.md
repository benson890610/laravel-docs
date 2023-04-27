# laravel-docs
Laravel documentation for learning
  
  
  
## Models 



### Model properties 

```

protected $table      = 'table_name' | posts
protected $primaryKey = 'primary_key_name' | id
protected $connection = 'connection_name' | mysql
protected $keyType    = 'string' | 'integer'

public $incrementing = true | false
public $timestamps   = true | false

```
  
  
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

// In controller

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

$posts = Post::orderBy('id', 'desc')->limit(5)->get() // Total 5 items or
$posts = Post::orderBy('id', 'desc')->take(5)->get()  // Total 5 items

```  


### Total count of items  

```

$total = Post::count();

```  


### Create new database record  

```  

use App\Post;

or 

use App\Models\Post;

$post = new Post;
$post->title = 'Some title';
$post->body  = 'Regular post body';
$post->save();

```  


### Update database record  

```

use App\Post;

// Single update
$post = Post::find($id)
$post->title = 'Updated new title';
$post->body  = 'Updated new post body';
$post->save();

// Mass updates
Post::where('status', 1)
    ->update([
      'name'  => 'User active',
      'gender => 'Male'
    ]);

```  


### Delete database record  

```

use App\Post;

// Single delete
$post = Post::find($id);
$post->delete();

// OR 

Post::destroy([1,2,3]);

// Mass delete
Post::where('status', 0)
    ->delete();

```

