# Laravel-docs
Laravel documentation for learning  

## Laravel Responses

<br>

```
Example (Return response with view)
--------------------------------------------------------------------------

public function someMethod() {
    return response(view('user.login'), 200);
}


Example (Return response with view and cookie)
--------------------------------------------------------------------------

public function someMethod() {
    return response(view('user.login'), 200)->withCookie('cookieName', 'cookieValue', $minutes);
}
```
