# laravel-docs
Laravel documentation for learning  

## Laravel migrations


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
  
  $table->increments('id') // AUTO_INCREMENT INT 'id' column
  $table->string('title')  // VARCHAR(255) 'title' column
  $table->string('title')->nullable(false) // VARCHAR(255) NOT NULL 'title' column
  $table->mediumText('body') // MEDIUMTEXT 'body' column
  $table->mediumText('body')->nullable() // MEDIUMTEXT DEFAULT NULL 'body' column
  $table->timestamps() // Create created_at and updated_at columns

```
