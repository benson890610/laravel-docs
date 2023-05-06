# laravel-docs
Laravel documentation for learning  

## Laravel validation 

Laravel validation is done with Illuminate\Http\Request library that is pased into controller method as dependecy.  
If one of the validation rules fail it will trigger redirection with proper status code.  
List of all rules:  
1. required     - request data must be filled 
2. max:255      - request data must contain maximum 255 characters
3. confirmed    - request data password field must be the same as password confirm field
4. email        - request data email must be of correct type
5. min:6        - request data must contain minimum 6 characters
6. unique:users - request parameter must be unique in Users table e.g (email parameter)

```

// Inside controller use Illuminate\Http\Request as dependency library

public function store(Request $request) {
    $request->validate([
	'title' => ['required', 'max:255'],
	'email  => ['unique:users']
     ]);
}





```
