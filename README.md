# laravel-docs
Laravel documentation for learning  

### Route check if route has named 

```

@if ( Route::has('about') )
    // Named route 'about' founded
@endif 

```

<br>

### Prefix routes 

```

Route::prefix('v1')->group(function() {
    Route::get('/album', function() {  'All albums'; });          // v1/album
    Route::get('/album/1', function() { 'Album 1 single'; });     // v1/album/1
});

```
