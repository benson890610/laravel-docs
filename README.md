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


### asset() helper  
  
```

// asset() helper automaticaly looks in public folder for other folders or files

<link rel="stylesheet" href="{{ asset('css/app.css') }}">

```  
  

### config() helper  

```

# Works with config directory accessing files and files written options 

config('app.name');
config('database.connections);

```
