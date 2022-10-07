# Model Authentication with Laravel Passport

## To preview: 

  * **Shift** + **Cmd** + **V**, _or_  
  * Right click on the editor tab, and select **Open Preview**, _or_  
  * Use the **Command Palette** (**Shift** + **Cmd** + **P**) to run the **Markdown: Open Preview to the Side**  

\
First install Laravel Passport: [Install](https://laravel.com/docs/9.x/passport#installation), and follow the examples.
\
Follow [article](https://www.toptal.com/laravel/passport-tutorial-auth-user-access) to use Laravel Passport for Authentication.  

<br></br>

## Create Custom Model to be Authenticated
***
<pre><code>php artisan make:model model_name</code></pre>



<br></br>
## Modify _config/auth.php_: 

***

  ### Add custom model provider  

  <pre><code>'providers' => [
        'users' => [
            'driver' => 'eloquent',
            'model' => App\Models\User::class,
        ],

        'consumers' => [
            'driver' => 'eloquent',
            'model' => App\Models\Consumer::class,
        ], 
      ],</code></pre>
 
  ### Add custom guard using the new model provider
  <pre><code>'guards' => [
        'web' => [
            'driver' => 'session',
            'provider' => 'users',
        ],
        'consumer' => [
            'driver' => 'passport',
            'provider' => 'consumers',
        ],
    ],</code></pre>