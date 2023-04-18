# laravel-docs
Laravel documentation for learning  

## DB Library

### DB Commands  

DB methods are usually chained together
  
```

DB::table('customers')                       // Set the targeted table
->select('first_name', 'last_name', 'email') // Set the targeted selected columns
->get()                                      // Retreive results

```  
