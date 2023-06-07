# laravel-docs
Laravel documentation for learning  

## DB Query Builder Library

### DB Commands  

DB methods are usually chained together
  
```

DB::table('customers')                       // Set the targeted table
->select('first_name', 'last_name', 'email') // Set the targeted selected columns
->get()                                      // Retreive results

```  
  
  
  
### DB named or positional bindings 

```

$id = 1002;

DB::table('customer')
->where('id', '=', ':id')
->setBindings([ ':id' => $id ])
->update([ 'status' => 1 ]);

// OR 

DB::table('customer')
->where('id', '=', '?')
->setBindings([ $id ])
->update([ 'status' => 1 ]);

```
