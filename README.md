# laravel-docs
Laravel documentation for learning  

## Laravel authentication

<br>

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

<br>

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

<br>

### Change authenticated redirect route  
```

    Open the RedirectIfAuthenticated middleware located at app/Http/Middleware/RedirectIfAuthenticated.php.
    Look for the handle method, which contains the logic for redirecting authenticated users.
    By default, it looks like this:

    public function handle($request, Closure $next, $guard = null) {
        if ( Auth::guard($guard)->check() ) {
            return redirect('/home');
        }
    
        return $next($request);
    }

    Change the redirect URL from /home to your desired route.
    For example, if you want to redirect authenticated users to the /dashboard route, modify the method as follows:

    public function handle($request, Closure $next, $guard = null) {
        if ( Auth::guard($guard)->check() ) {
            return redirect('/dashboard');
        }
    
        return $next($request);
    }

```

<br>

### Redirect unauthenticated users to specific route
```

    In Laravel 8, you can easily redirect unauthenticated users to a specific route using middleware.
    By default, Laravel provides a guest middleware that handles this redirection.
    However, you can create a custom middleware to customize the behavior and redirect
    unauthenticated users to your desired route.

    Create a new middleware using the following Artisan command:

    php artisan make:middleware RedirectUnauthenticated

    Open the newly created middleware file located at app/Http/Middleware/RedirectUnauthenticated.php.
    In the handle method, add the logic to redirect unauthenticated users to your specific route.
    For example, if you want to redirect unauthenticated users to the /login route, modify the method as follows:

    use Illuminate\Support\Facades\Auth;

    public function handle($request, Closure $next) {
        if ( ! Auth::check() ) {
            return redirect('/login');
        }
    
        return $next($request);
    }

    Register the middleware in the $routeMiddleware array in the app/Http/Kernel.php file.
    Add the following line to the array:

    protected $routeMiddleware = [
        // ...
        'redirect.unauthenticated' => \App\Http\Middleware\RedirectUnauthenticated::class,
    ];

    Now, you can apply the middleware to the routes that you want to protect from unauthenticated access.
    Open the web.php routes file (located at routes/web.php) and add the middleware
    to the desired route group or individual routes:

    use App\Http\Middleware\RedirectUnauthenticated;

    Route::middleware([RedirectUnauthenticated::class])->group(function () {
        // Routes that unauthenticated users will be redirected to /login
    });

    Alternatively, you can apply the middleware directly to specific routes:

    use App\Http\Middleware\RedirectUnauthenticated;

    Route::get('/protected-route', function () {
        // ...
    })->middleware(RedirectUnauthenticated::class);

    With this setup, any unauthenticated user trying to access the routes that use the RedirectUnauthenticated middleware
    will be redirected to the specified route (e.g., /login).
    Remember to replace /login with the actual route you want to use for unauthenticated users.

```
