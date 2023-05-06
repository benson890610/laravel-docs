# laravel-docs
Laravel documentation for learning  

## Hash Library  



### Create hashed password  

```

use Illuminate\Support\Facades\Hash;

public function create(Request $request) {
    
    $password_hash = Hash::make($request->input('password'));
    
}

```
  
