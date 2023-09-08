# laravel-docs
Laravel documentation for learning  

## Laravel validation 

Laravel validation is done with Illuminate\Http\Request library that is pased into controller method as dependecy.  
If one of the validation rules fail it will trigger redirection with proper status code.  
List of all rules:  
1. required           - request data must be filled 
2. max:255            - request data must contain maximum 255 characters
3. email              - request data email must be of correct type
4. min:6              - request data must contain minimum 6 characters
5. unique:users       - request parameter must be unique in Users table e.g (email parameter)
6. unique:users,email - request parameter must be unique in Users table on email column
7. confirmed          - request parameter used in password validation, must contain password_confirmation field
8. image              - request parameter file must be an image
9. 'images.*' => 'image|mimes:jpeg,png,jpg,gif|max:2048' - request parameter are multiple images validate all images
10. mimes:png,jpg      - request file image must be png or jpg
11. max:2048          - request when used on image, then image must be 2048 Kb
12. exists:App\Models\Album, id - check if passed value exists as id in Album model
13. url               - request parameter must be of type URL
14. numeric           - request parameter must be integer or decimal number

```

// Inside controller use Illuminate\Http\Request as dependency library

public function store(Request $request) {
    $request->validate([
	'title'    => ['required', 'max:255'],
	'email     => ['unique:users'],
	'password' => ['confirmed'],
	'file'     => ['image', 'mimes:jpg,png', 'max:2048']
     ]);
}





```
