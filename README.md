# laravel-docs
Laravel documentation for learning  
  
  
## Controllers  
  
  
### Make basic controller and resource controller  
  
```

php artisan make:controller TasksController            // Simple controller 
php artisan make:controller TasksController --resource // Resources controller

```  
  
  
### Map resource controller into routes and add custom resource route and method 
  
```

// routes/web.php  

TasksController::get('tasks/export', 'TasksController@export')->name('tasks.export');
TasksController::resource('tasks',   'TasksController');

// Method names

public function index() {}                       // GET
public function show($id) {}                     // GET
public function edit($id) {}                     // GET
public function create() {}                      // GET
public function store(Request $request) {}       // POST
public function update(Request $request, $id) {} // PUT
public funtion destroy() {}                      // DELETE
public function export() {}                      // GET (custom user method)  

// Route names  

tasks.index
tasks.show
tasks.edit
tasks.create
tasks.store 
tasks.update 
tasks.destroy

```

