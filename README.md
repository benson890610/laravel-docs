# laravel-docs
Laravel documentation for learning  

## Laravel authentication
  

### Check if user is logged  

```

use Illuminate\Support\Facades\Auth;

public function doSomething() {
    if ( Auth::check() ) {
    	// OK continue
    } else {
    	// Abort redirect
    }
} 

```  


### Attempt to logg in  

```

use Illuminate\Support\Facades\Auth;

public function login() {
    
    $email    = $request->input('email');
    $password = $request->input('password');
    
    if ( Auth::attempt(['email' => $email, 'password' => $password ]) ) {
    	// Redirect with success
    } else {
    	// Redirect with fail
    }

}

```
