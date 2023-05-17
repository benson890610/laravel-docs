# laravel-docs
Laravel documentation for learning  
  
  
## Request service library  

Library: Illuminate\Http\Request


### Get value from request  

```

$title = $request->input('title');
$title = $request->title;

```


### Check and Get specific query string  
  
```

public function service(Request $request) {

    // Check if request parameter present
    if ( $request->has('state') ) {
        echo $request->get('state');
    }
    
    // Check if multiple request parameters are present
    if ( $request->has(['name', 'email']) ) {
        // Continue with request parameter
    }
    
}

```  
  
  
### Check if request coming from route  
  
```

public function handle(Request $request) {

    if ( $request->routeIs('users.*') ) {
        // Continue with request
    } else {
        // Show error message
    }

}

```  


### Get http request path  

```

public function handle(Request $request) {
    // If request url was: http://localhost:8000/foo/bar
    
    $request->path(); // foo/bar
}

```  


### Get request referer header  

```

public function handle(Request $request) {
    $request->server('HTTP_REFERER');
    $request->headers->get('referer');
}

```  

### Get request file  

```

$fileObj  = $request->file('filename');
$name     = $fileObj->getClientOriginalName();
$type     = $fileObj->getClientMimeType();
$ext      = $fileObj->getClientExtension();
$size     = $fileObj->getClientSize();

```
