# laravel-docs
Laravel documentation for learning 

## File handling

<br>

### File facade  

```

Illuminate\Support\Facades\File

```  

<br>
  
### Check if file exists 

```

public function handle() {
    if ( File::exists($fullPathName) ) {
    	dd('File found');
    } else {
    	dd('File NOT found');
    }
}

```

<br>

### Delete file or files  

```

public function handle() {
    // Delete one file 
    File::delete($fullPathFile);
    
    // Delete multiple files
    File::delete([$file1, $file2, $file3, $file4]);
    File::delete($file1, $file2, $file3);
}

```

<br>

### Create directory 

```

$dir = public_path() . 'images/' . Str::random();

File::makeDirectory($dir);

```

<br>

### Validate file  

```

public function handle(Request $request) {
    $request->validate([
    	'file' => ['image', 'mimes:jpg,png,jpeg', 'max:2048']
    ]);
}

```  

<br>

### Upload file  

```

public function handle(Request $request) {
    $file = $request->file('file')    // UploadFile instance
    
    $filename = pathinfo($file->getClientOriginalName(), PATHINFO_FILENAME);
    $ext      = $file->getClientOriginalExtension();
    $formated = $filename . '_' . time() . '.' . $ext;     // Create unique file
    
    $file->storeAs('public/location/', $formated);
}

```
