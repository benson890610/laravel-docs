# laravel-docs
Laravel documentation for learning  
  
  
## Blade Templete Engine  
  
<br>
  
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

<br>
  
### Show dynamic variable from controller  
  
```

<h1>This is {{ $title }}</h1>
<p>This is {{ $paragraph }}</p>

```  

<br>
  
### Include other file  
  
```

  @include('inc.navbar')

```  

<br>

### Blade parse html elements from code  

```

<div class="bg-white w-full py-4 px-6">{!! $body !!}</div>

```

<br>
  
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

<br>
  
### Method field  
  
```

// Request method as PUT
<form action="#" method="post">
    {{ method_field('PUT') }}
    <input type="hidden" name="_method" value="PUT">
</form>

```  
  
<br>

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

<br>

### Blade validation errors  

```

@if ( $errors->any() )
    @foreach ( $errors->all as $error )
        {{ $error }}
    @endforeach
@endif 

```  

<br>

### Blade @auth and @guest

```
// EXAMPLE 1.

@if ( auth()->user() ) 
    // Show authenticate user content
@else 
    // Show guest user content
@endif


@if ( auth()->guest() ) 
    // Show guest user content
@else 
    // Show authenticate user content
@endif

// EXAMPLE 2.

@auth
  // Show auth user content
@else
  // Show guest user content
@endauth


@guest 
  // Show guest user content
@else
  // Show auth user content
@endguest

```  

<br>

### Blade @switch control statement  

```

@switch ( $role ) 
  
  @case ( 'admin' )
      <div>Load admin panel</div>
      @break
  @case ( 'manager' )
  
      <div>Load manager panel</div>
      @break
      
  @default
      <div>Load operator panel</div>
  
@endswitch

```  

<br>

### Blade @isset and @empty conditions  

```

@isset ( $users )
    // Loop through users collection 
@endisset


@empty ( $message )
    // Message is empty = ''
@endempty

```  

<br>

### Blade loops  

```


// Example 1. regular foreach

@foreach ( $users as $user )
    {{ $user->name }} {{ $user->email }}
@endforeach


// Example 2. foreach with loop variable (first, last and index, parent, count) properties
// $loop->count return total number of elements
// $loop->parent used in nested loop will contain parent loop values 
// $loop->first return the first iteration
// $loop->last return the last iteration
// $loop->index return current index

@foreach ( $users as $user )
  @if ( $loop->first) 
    // First iteration
  @endif
  
  {{ $loop->index }} {{ $user->name }} {{ $user->email }}
  
  @if ( $loop->last ) 
    // Last iteration
  @endif
@endforeach  


// Example 3. foreach with @continue and @break

@foreach ( $users as $user )
    @if ( $user->is_active === 0 ) @continue
    
    @if ( $user->is_blacklisted ) @break
@endforeach


// Example 4. forelse

@forelse ( $users as $user ) 
    <div>{{ $user->name }} {{ $user->email }}</div>
@empty
    <div>No users found</div>
@endforelse  


// Example 5. while 

@while ( true )
  <div>I am looping forever</div>
@endwhile

```
