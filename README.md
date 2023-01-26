# laravel-docs
Laravel documentation for learning  
  
  
## Request service library  



### Check and Get specific query string  
  
```

public function service(Request $request) {
    if($request->has('state')) {
        echo $request->get('state');
    }
}

```
