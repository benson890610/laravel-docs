# laravel-docs
Laravel documentation for learning  
  
  
## Request service library  

Library: Illuminate\Http\Request


### Request collect params - $request->input($param)

```

$title = $request->input('title');
$title = $request->title;

```  
  
  
  
### Request route check - $request->is($path)

```

// layouts.blade.php 

@if ( request()->is('about')
    <div>Welcome to about page</div>
@endif

@if ( request()->is('/')
    <div>Welcome to home page</div>
@endif

```


### Request method - $request->method() and $request->isMethod($methodName)

```

$method = $request->method();      // eg. GET

if ( $request->isMethod('GET') ) {
    dd('It is GET request method');
}

```



### Request url and fullUrl - $request->url() and $request->fullUrl()  

```

// url() get full url without query string 
// fullUrl() get full url with query string

request()->url()      // http://my-site.com/page
request()->fullUrl()  // http://my-site.com/page?filter=true

```



### Request check required parameters - $request->has($string) or $request->has($array)  
  
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



### Upload file  

```

$file = $request->file('file');
$file->storeAs('storage/cover_images', $file->getClientOriginalName());

```
