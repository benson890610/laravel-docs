# Laravel-docs
Laravel documentation for learning  

## Laravel Santcum

<br>

### Useful Stuff

```

$tokens = $request->user()->tokens                         // Retreive all tokens

$token = $request->user()->createToken('token_name')       // Create new token

public function deleteToken(PersonalAccessToken $token) {  // Delete token

    $token->delete();

    return redirect('dashboard');

}

$tokenId   = $token->id                                  // Token id in 'personal_access_token' table
$tokenName = $token->name                                // Token name
$tokenRandChars = $token->last_used_at->diffForHumans()  // Token last used at eg. 2 hours ago

Route::middleware('auth:sanctum')->group(function() {      // Authenticate every route by token
    Route::prefix('v1')->group(function() {

        Route::apiResource('album', AlbumController::class);
    
        Route::group(['as' => 'image.'], function() {
            Route::get('image',         [ImageManipulationController::class, 'index'])->name('index');
            Route::get('image/by-album/{album}', [ImageManipulationController::class, 'byAlbum'])->name('byAlbum');
            Route::post('image/resize', [ImageManipulationController::class, 'resize'])->name('resize');
            Route::get('image/{image}', [ImageManipulationController::class, 'show'])->name('show');
            ROute::delete('image/{image}', [ImageManipulationController::class, 'destroy'])->name('destroy');
        });
        
    });
});

```
