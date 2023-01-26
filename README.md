# laravel-docs
Laravel documentation for learning  

### env() helper  
  
```

// Return enviroment variable if exists, if not default second argument

$dbDriver = env('DB_CONNECTION', 'mysql');           // mysql default on creation project
$appName  = env('APP_NAME', 'Laravel Studio');       // Laravel default on creation project

```
