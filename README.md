# laravel-docs
Laravel documentation for learning  

## Laravel authentication

<br>

### Theory
```

    Illuminate\Support\Facades\Auth is the main facade where authenticated or guest are manipulated.

    Retreiving authenticated user
    While handling an incoming request, you may access the authenticated user via the Auth facade's user method


    $user = Auth::user();
    $id   = Auth::id()
    $id   = Auth::user()->id


    Alternatively, once a user is authenticated, you may access the authenticated user via an Illuminate\Http\Request instance.
    Remember, type-hinted classes will automatically be injected into your controller methods.
    By type-hinting the Illuminate\Http\Request object, you may gain convenient access to the authenticated user from any
    controller method in your application via the request's user method


    public function update(Request $request) {
        // $request->user()
    }

    
    To determine if the user making the incoming HTTP request is authenticated,
    you may use the check method on the Auth facade. This method will return true if the user is authenticated


    Auth::check()


    Redirecting Unauthenticated Users
    -----------------------------------------------------------------------------------------------------
    When the auth middleware detects an unauthenticated user, it will redirect the user to the login named route.
    You may modify this behavior by updating the redirectTo function in your application's
    app/Http/Middleware/Authenticate.php file


    protected function redirectTo($request) {
        return route('login');
    }


    Remembering Users
    -----------------------------------------------------------------------------------------------------
    Many web applications provide a "remember me" checkbox on their login form.
    If you would like to provide "remember me" functionality in your application,
    you may pass a boolean value as the second argument to the attempt method.

    When this value is true, Laravel will keep the user authenticated indefinitely or until they
    manually logout. Your users table must include the string remember_token column, which will be
    used to store the "remember me" token.
    The users table migration included with new Laravel applications already includes this column:


    use Illuminate\Support\Facades\Auth;
 
    if (Auth::attempt(['email' => $email, 'password' => $password], $remember)) {
        // The user is being remembered...
    }


    If your application offers "remember me" functionality, you may use the viaRemember method
    to determine if the currently authenticated user was authenticated using the "remember me" cookie:


    use Illuminate\Support\Facades\Auth;
     
    if (Auth::viaRemember()) {
        // ...
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

### Change unauthenticated redirect route
```

    In App\Http\Middleware\Authenticate.php change route parameter to specific route

    protected function redirectTo($request) {
        if (! $request->expectsJson()) {
            return route('home.index');
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
