# laravel-docs
Laravel documentation for learning  

## Laravel migrations



### Create migration  

```

  php artisan make:migration create_post_table

```


### Migrate to database
  
```

php artisan migrate

```  


### Revert migration back  

```

php artisan migrate:rollback

```


### Blueprint $table dependency commands

```  

  // Version 5.5.*
  
  $table->increments('id')                 // AUTO_INCREMENT INT 'id' column
  $table->string('title')                  // VARCHAR(255) 'title' column
  $table->string('title')->nullable(false) // VARCHAR(255) NOT NULL 'title' column
  $table->mediumText('body')               // MEDIUMTEXT 'body' column
  $table->mediumText('body')->nullable()   // MEDIUMTEXT DEFAULT NULL 'body' column
  $table->timestamps()                     // Create created_at and updated_at columns
  $table->rememberToken()                  // Create remember_token column VARCHAR(255) DEFAULT NULL
 
```


### Drop column on migrate rollback  

```

    public function down() {
        Schema::table('posts', function(Blueprint $table) {
            $table->dropColumn('user_id');
        });
    }

```
