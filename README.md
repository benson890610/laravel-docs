# laravel-docs
Laravel documentation for learning  

## Laravel resources 

<br>

### Create resource  

```

php artisan make:resource V1\\AlbumResource

```

<br>


### Return resources needed parameters 

```

public function toArray($request) {
    return [
        'id' => $this->id,
 	'name' => $this->name,
	'created_at' => $this->created_at
	'updated_at' => $this->updated_at
    ]
}

```

<br>

### Return resources from controllers 

```

// AlbumController.php

use App\Http\Resources\AlbumResources;
use App\Models\Album;

public function index() {

    $albums = Album::all();

    return AlbumResources::collection($albums);
}

```
