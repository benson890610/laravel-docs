# laravel-docs
Laravel documentation for learning  
  
  
## Middleware  
  
  

### Create middleware  
  
```

php artisan make:middleware CheckAge

// app/Http/Middleware/CheckAge.php 
public function handle($request, Closure $next) {

    $age = $request->age;
    
    if ( $age < 18 ) {
        return redirect()->route('home');
    }

}

// app/Http/Kernel.php
protected $routeMiddleware = [
    'auth' => \Illuminate\Auth\Middleware\Authenticate::class,
    'auth.basic' => \Illuminate\Auth\Middleware\AuthenticateWithBasicAuth::class,
    'bindings' => \Illuminate\Routing\Middleware\SubstituteBindings::class,
    'can' => \Illuminate\Auth\Middleware\Authorize::class,
    'guest' => \App\Http\Middleware\RedirectIfAuthenticated::class,
    'throttle' => \Illuminate\Routing\Middleware\ThrottleRequests::class,
    'checkAge' => \App\Http\Middleware\CheckAge::class
];

// routes/web.php 

Route::get('adult', function() { 'Adult page'; })->middleware('checkAge');

```  


### Middleware inside constructor  

```

class PostsController extends Controller {
    public function __construct() {
        // Require authenticate user access
        
        $this->middleware('auth')
    }
    
    public function index() {
        // Index page
    }
    
    public function create() {
        // Create page
    }
}


```
