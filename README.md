# laravel-docs
Laravel documentation for learning  

### env() helper  
  
```

// Return enviroment variable if exists, if not default second argument

$dbDriver = env('DB_CONNECTION', 'mysql');           // mysql default on creation project
$appName  = env('APP_NAME', 'Laravel Studio');       // Laravel default on creation project

```  
  
  
### resposne() helper in combination with json()  
  
```

return response('<h1>Main Page Title</h1>', 200, $headers);
return response()->json([
    'status' => [
        'text' => 'OK',
        'code' => 200
    ],
    'message' => 'Json response handled'
], 200, $headers);

```  


### method_field() helper  
  
```

// Used in forms as PUT or DELETE or PATCH

{{ method_field('PUT') }}
or 
{{ method_field('DELETE') }}

```  


### csrf_field() and csrf_token() helper  

```

// Used in forms for cross site protection together with POST, PUT, PATCH and DELETE requests

csrf_field()

or 

<input type="hidden" name="_token" value="{{ csrf_token() }}">

```
  

### config() helper  

```

# Works with config directory accessing files and files written options 

config('app.name');
config('database.connections);

```  
  
  
### route() helper with parameter - this helper is connected with named routes 

```

// blade template 

<a href="{{ route('posts.show', ['post' => $post->id]) }}">{{ $post->title }}</a>

```  


### base_path() helper  - this helper will return root path of project

```  

echo base_path() // C:\xampp\htdocs\laravel\lsap

```  


### asset() - this helper will look for files in public directory 

``` 

echo asset('css/app.css') // http://lsapp.test/css/app.css
echo asset('js/app.js')   // http://lsapp.test/js/app.js

```
