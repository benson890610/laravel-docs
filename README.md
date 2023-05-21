# laravel-docs
Laravel documentation for learning  

## Laravel relationships  


### Has many relationship

```

use App\Post;
use App\User;

class Post extends Model {
    protected $table      = 'posts';
    protected $primaryKey = 'id';
    
    public $incrementing  = true;
    
    public function user() {
        return $this->belongsTo('App\User'); // Laravel version 5.5.*
    }
    
}

class User extends Model {
    protected $table      = 'users';
    protected $primaryKey = 'id';
    
    public $incrementing  = true;
    
    public function posts() {
        return $this->hasMany('App\Post'); // Laravel version 5.5.*
    }
}

$users = User::all();
$john  = $users[0];

foreach ( $john->posts as $post ) {
    echo $post->id . ' ' . $post->title;
}

```


### Has one relationship  

```

use App\Phone;
use App\User;

class Phone extends Model {
    protected $table      = 'phones';
    protected $primaryKey = 'id';
    
    public $incrementing  = true;
    
    public function user() {
        // Inverse relationship
        // Second optional argument foreign_id
        // Third optiomal argument primary key from main table
        return $this->belongsTo('App\User', 'user_id', 'id');
    }
    
}

class User extends Model {
    protected $table      = 'users';
    protected $primaryKey = 'id';
    
    public $incrementing  = true;
    
    public function posts() {
        // One to one relationship
        // Second optional argument foreign key
        // Third optional argument primary key from main table
        return $this->hasOne('App\Phone', 'user_id', 'id');
    }
}

$users = User::all();
$john  = $users[0];

echo $john->phone->number . ' ' . $john->phone->country_code;

```
