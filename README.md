# laravel-docs
Laravel documentation for learning  
  
  
## Blade Templete Engine  
  
  
  
### Simple layout and page extends layout
  
```

// layouts/main.blade.php 

<!DOCTYPE html>
<html lang="en">
  <head>
      <title>@yield('title')</title>
  </head>
  <body>
    @yield('content')
  </body>
</html>


// home.blade.php  

@extends('layouts.main')

@section('title', 'Main Home Page')

@section('content')
    <h1>Main Home Page</h1>
@endsection


```
