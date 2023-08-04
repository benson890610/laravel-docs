# laravel-docs
Laravel documentation for learning  

## Hash Library  



### Hash Facade

```
Description
------------------------------------------------------------------------------------------------------
    The Laravel Hash facade provides secure Bcrypt and Argon2 hashing for storing user passwords.
    If you are using one of the Laravel application starter kits, Bcrypt will be used
    for registration and authentication by default.

    Bcrypt is a great choice for hashing passwords because its "work factor" is adjustable,
    which means that the time it takes to generate a hash can be increased as hardware power increases.
    When hashing passwords, slow is good. The longer an algorithm takes to hash a password, the longer
    it takes malicious users to generate "rainbow tables" of all possible string hash values
    that may be used in brute force attacks against applications.

    The default hashing driver for your application is configured in your application's
    config/hashing.php configuration file. There are currently several supported drivers: Bcrypt and Argon2

    use Illuminate\Support\Facades\Hash;


Example:
------------------------------------------------------------------------------------------------------
    public function create(Request $request) {
        $password_hash = Hash::make($request->input('password'));
    }

    or

    public function update(Request $request) {
        // Validate the new password length...
 
        $request->user()->fill([
            'password' => Hash::make($request->newPassword)
        ])->save();
    }


Verifying That A Password Matches A Hash

The check method provided by the Hash facade allows you to verify that a given
plain-text string corresponds to a given hash:


Example
------------------------------------------------------------------------------------------------------
    if (Hash::check('plain-text', $hashedPassword)) {
        // The passwords match...
    }


Determining If A Password Needs To Be Rehashed

The needsRehash method provided by the Hash facade allows you to determine if the work factor used by the
hasher has changed since the password was hashed. Some applications choose to perform this
check during the application's authentication process:


Example
------------------------------------------------------------------------------------------------------
    if (Hash::needsRehash($hashed)) {
        $hashed = Hash::make('plain-text');
    }

```
  
