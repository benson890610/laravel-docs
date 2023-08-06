# laravel-docs
Laravel documentation for learning  

<br>
  
## Middleware  
  
<br>

### Theory
```

Middleware provide a convenient mechanism for inspecting and filtering HTTP requests entering your application.
For example, Laravel includes a middleware that verifies the user of your application is authenticated.
If the user is not authenticated, the middleware will redirect the user to your application's login screen.
However, if the user is authenticated, the middleware will allow the request to proceed further into the application.

Global Middleware.
If you want a middleware to run during every HTTP request to your application,
list the middleware class in the $middleware property of your app/Http/Kernel.php class.

```

<br>

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

<br>

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

<br>

### Middleware inside constructor with except option  
```

use Illuminate\Http\Request;

class PostsController extends Controller {
    public function __construct() {
        // Require authenticate user access
        // but not for index method
        
        $this->middleware('auth', ['except' => ['index'] ])
    }
    
    public function index() {
        // Index page
    }
    
    public function create() {
        // Create page
    }
    
    public function edit(Request $request, $id) {
        // Edit page
    }
    
}

```
