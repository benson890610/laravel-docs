# laravel-docs
Laravel documentation for learning  
  
  
## Request service library  



### Check and Get specific query string  
  
```

public function service(Request $request) {

    // Check if request parameter presented
    if($request->has('state')) {
        echo $request->get('state');
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
