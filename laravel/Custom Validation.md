# Custom Validation
* https://laracasts.com/discuss/channels/general-discussion/custom-validation-function-in-laravel-5

## STEP 1 of 3: Configure App Service Provider

```
<?php

namespace App\Providers;

use Illuminate\Support\ServiceProvider;
use Validator;

class AppServiceProvider extends ServiceProvider
{
    public function boot()
    {
        Validator::extend('strength', 'App\Http\CustomValidator@validateStrength');
    }

    public function register()
    {
        //
    }
}
```

## STEP 2 of 3: Create Custom Validator Class

```
<?php

namespace App\Http;

class CustomValidator {

    public function validateStrength($attribute, $value, $parameters, $validator)
    {
        if( preg_match('/(?=^.{8,}$)(?=.*\d)(?=.*[!@#$%^&*]+)(?![.\n])(?=.*[A-Z])(?=.*[a-z]).*$/', $value) )
            return true;

        return false;
    }

}
```

## STEP 3 of 3: Edit Language File

* resources/lang/en/validation.php

```
   /*
    |--------------------------------------------------------------------------
    | Custom Validation Language Lines
    |--------------------------------------------------------------------------
    |
    | Here you may specify custom validation messages for attributes using the
    | convention "attribute.rule" to name the lines. This makes it quick to
    | specify a specific custom language line for a given attribute rule.
    |
    */
    'strength' => 'The password :attribute is too weak and must contain one or more uppercase, lowercase, numeric, and special character (!@#$%^&*).',

    'custom' => [
        'attribute-name' => [
            'rule-name' => 'custom-message',
        ],
    ],
```

## Final Thoughts

```
'password'   => 'required|min:8|strength|confirmed',
```
