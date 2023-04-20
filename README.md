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
  
  
### Show dynamic variable from controller  
  
```

<h1>This is {{ $title }}</h1>
<p>This is {{ $paragraph }}</p>

```  
  
  
### Include other file  
  
```

  @include('inc.navbar')

```  
  
  
### CSRF Token  
  
```

<form action="#" method="post">
    {{ csrf_field() }}
    // Create <input type="hidden" name="_token" value="WQEQWasd1212dasdCZSXAADGGG002">
</form>

<form action="#" method="post">
    <input type="hidden" name="_token" value="{{ csrf_token() }}">
</form>

<form action="#" method="post">
    @csrf
    // Create <input type="hidden" name="_token" value="WQEQWasd1212dasdCZSXAADGGG002">
</form>

```  
  
  
### Method field  
  
```

// Request method as PUT
<form action="#" method="post">
    {{ method_field('PUT') }}
    <input type="hidden" name="_method" value="PUT">
</form>

```  
  
  
### Ajax CSRF token  
  
```

In <head> add: 
<meta name="csrf-token" content="{{ csrf_token() }}">

in <script>

$.ajax({
    headers: {
      'X-CSRF-TOKEN': $('meta[name="csrf_token"]').attr('content')
    }
});

```  


### Blade validation errors  

```

@if ( $errors->any() )
    @foreach ( $errors->all as $error )
        {{ $error }}
    @endforeach
@endif 

```
