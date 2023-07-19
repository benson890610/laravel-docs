# laravel-docs
Laravel documentation for learning  

## Sessions 

Library: Illuminate\Support\Facades\Session

<br>

### Create session  

```

Session::flash('success', 'New user added');
session()->flash('success', 'New user added');

Session::put('name', 'value')

```

<br>

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

<br>

### Get session value  

```

$value = Session::get('success');
$value = session()->get('success);
$value = session('success');

```

<br>

### Remove session  

```

Session::forget('name');

$request->session()->forget('name');

session()->forget('name');

```
