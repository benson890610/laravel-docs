# laravel-docs
Laravel documentation for learning  

## Laravel validation 

Laravel validation is done with Illuminate\Http\Request library that is pased into controller method as dependecy.  
If one of the validation rules fail it will trigger redirection with proper status code.  
List of all rules:  
1. required - request data must be filled 
2. max:255  - request data must contain maximum 255 characters

```

// Inside controller use Illuminate\Http\Request as dependency library

public function store(Request $request) {
    $request->validate([
	'title' => ['required', 'max:255'] 
    ]);
}





```
