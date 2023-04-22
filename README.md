# laravel-docs
Laravel documentation for learning  

## Sessions 

Library: Illuminate\Support\Facades\Session

### Create session  

```

Session::flash('success', 'New user added');
session()->flash('success', 'New user added');

```


### Check for session  

```

if ( Session::has('success') ) {
    // Code here
} else {
    // Code here
}

if ( session()->has('success') ) {
    // Code here
} else {
    // Code here
}

```  


### Get session value  

```

$value = Session::get('success');
$value = session()->get('success);
$value = session('success');

```
 
