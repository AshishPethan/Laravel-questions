# Laravel-questions

Laravel Questions and answers...

Install
composer global require laravel/installer
Laravel new demoprojectname


What are Migrations?
-> Migrations are important because it allows you to share application by maintaining database consistency. Without migration, it is difficult to share any Laravel web applications.
-> Migrations are like version control for your database, allowing your team to easily modify and share the application's database schema.
-> Migrations in Laravel are a powerful feature that allows you to manage and version your database schema through code. They are like version control for your database.


What is Laravel?
-> Laravel is an open-source widely used PHP framework. That is used to develop complex web applications. It supports the Model-View-Controller
-> Laravel, models are a crucial part of the MVC (Model-View-Controller) architectural pattern. A model represents the data structure and the business logic of your applications to manage there views and logic of controllers.


difference between die and exit
In PHP, die() and exit() are aliases that serve the same purpose: to terminate script execution and optionally output a message. There's no functional difference between them.

What is Laravel lifecycle
The Laravel lifecycle is the process of how Laravel handles a request and returns a response. It involves several key stages:
Bootstrapping – Loads configurations, environment variables, and service providers.
Routing – Matches the request to a route and applies middleware.
Middleware Execution – Filters requests before reaching controllers.
Controller & Business Logic – Executes the application logic.
View Rendering – Generates the response, usually with Blade templates.
Response Sending – Sends the final response back to the client.

Explain what is composer in Laravel
-> In Laravel, the composer is a tool that works as a package manager for the framework. The composer helps to add fresh new packages and libraries from different sources directly into the application. One of the most common examples used for authentication purposes is a Passport. It generates a composer.json in the project directory to track all linked packages. Passport package can easily be easily installed with composer.

What is Eloquent EverLock in Laravel?


How can I get soft deleted records in Laravel ?
1. Retrieve Only Soft Deleted Records (onlyTrashed)
$deletedUsers = User::onlyTrashed()->get();

2. Retrieve All Records (Including Soft Deleted) (withTrashed)
$allUsers = User::withTrashed()->get();

3. Permanently Delete a Soft Deleted Record (forceDelete)
User::onlyTrashed()->forceDelete();



Laravel Passport
Laravel Passport is an official package for implementing OAuth2 authentication in Laravel applications. It provides a full OAuth2 server that allows API authentication using tokens instead of sessions or cookies.
Key Features of Passport
Full OAuth2 Implementation – Handles authentication using Access Tokens, Refresh Tokens, and Scopes.
Token-Based Authentication – Users receive API tokens for secure access.
Personal Access Tokens – Used for API authentication without OAuth flow.
Authorization Code Grants – Useful for third-party app authentication.
Client Credentials Grant – Machine-to-machine authentication without users.

composer require laravel/passport
php artisan migrate
php artisan passport:install
Configure Authentication in config/auth.php
Replace API driver with passport:
'guards' => [
    'api' => [
        'driver' => 'passport',
        'provider' => 'users',
    ],
],



Why Revoke a Token?
When a user logs out, their access token should no longer be valid.
If an API key is compromised, revoking prevents unauthorized access.
When a user changes their password, all old tokens should be revoked.
use Illuminate\Http\Request;
use Illuminate\Support\Facades\Auth;
public function logout(Request $request)
{
    $request->user()->token()->revoke();
    return response()->json(['message' => 'Logged out successfully']);
}
The user must re-authenticate to get a new token.
If a revoked token is used, the API will return a 401 Unauthorized response.





What is a Route in Laravel?
-> get, post, put, patch, delete, and options 

-> A route in Laravel refers to the mapping of a user-requested URL to a specific action, method, or callback function within the application. In other words, it defines the way an application responds to a client request through a specific URL pattern.
-> Routes play a crucial role in organizing the flow and handling of HTTP requests in a Laravel application. They can be defined in the route files stored within the routes directory of your project.
The primary route files include web.php, api.php, console.php, and channels.php.


What is reverse routing concept in Laravel?
- Route::get('users', [UserController::class, 'index'])->name('user.index');
- {{ route('user.index') }} use in blade of controller
- When we use route from the back side or when we call that route from it's name it is know as reverse routing. 


Define Hashing In Laravel ? 
-> It is the method of converting text into a key that shows the original text. Laravel uses the Hash facade to store the password securely in a hashed manner.



What is eloquent?
-> Laravel provides Eloquent, its own ORM system, which enables developers to handle database tables using object-oriented model classes.
-> Eloquent is an object-relational mapper (ORM) that comes standard with the Laravel framework. It provides simple Active record implementation working with the database. Eloquent ORM is a fast and flexible way to query databases using Laravel models. 




What Are Middleware In Laravel?
-> Middleware in Laravel is a crucial tool for handling HTTP requests entering the application. Middleware provides a convenient mechanism for filtering HTTP requests entering your application. For example, Laravel includes a middleware that verifies the user of your application is authenticated. The middleware redirects the user to the login screen if the user is not authenticated.
-> Middleware performs tasks before and after the request is handled by the application. They are used to define custom logic that needs to be executed on every request or response, such as checking if a user is banned. Laravel makes it easy to define this custom logic and apply it either globally, to a group of routes, or to a single route, enhancing the application's security and flexibility.




What Is Laravel Artisan?
-> Laravel Artisan is the command-line interface included in Laravel. Laravel Artisan provides numerous helpful commands for developing a Laravel application. Artisan commands automate repetitive tasks, making development more efficient and less error-prone. For example, Artisan can generate boilerplate code for new controllers, models, and migrations, speeding up the development process.
-> Artisan facilitates database management by allowing migrations and seedings in addition to code generation. This feature simplifies database operations and ensures consistency across development environments. Developers use Artisan to execute custom commands, which are defined to perform specific tasks tailored to the application's needs.





Explain Laravel's Routing With An Example.
-> Routes in Laravel are defined in the routes folder, typically in the web.php file for web routes. An example of a basic route in Laravel is given below.  

Route::get('/greeting', function () {
    return 'Hello, World';
});
Route::post('/userslist',[UserController::usersfunctionName])->name('users.list);

-> Laravel supports various types of routes, including GET, POST, PUT, DELETE, and PATCH, to handle different types of HTTP requests. It allows for parameterized routes, middleware integration, and group routing, enhancing flexibility and control over route handling. For instance, to define a route with a parameter. /{id}




Explain Eloquent Relationships In Laravel.
-> Eloquent relationships in Laravel define how different database models are connected. Laravel's Eloquent ORM provides a simple and fluent way to work with relationships. It supports several types of relationships including one-to-one, one-to-many, many-to-many, and polymorphic relationships. Each relationship type is represented by a method that returns a relationship instance.
-> A function is added to a model class to define a relationship. For example, in a one-to-one relationship, the hasOne and belongsTo methods are used. In a one-to-many relationship, hasMany and belongsTo methods are employed. For many-to-many relationships, the belongsToMany method is utilized. Polymorphic relationships are handled using morphTo and morphMany methods. Eloquent also allows eager loading of relationships, which optimizes queries by pre-loading the related data.


Difference between javascript and Jquery ?
1)  - JavaScript uses JIT[Just in Time Compiler] which is a combination of interpreter and Compile and is written in C. It’s a combination of ECMA script and DOM (Document Object Model).
    - JQuery Uses the resources that are provided by JavaScript to make things easier.It is a lightweight JavaScript library. It has only the DOM.

2)  - JavaScript uses long lines of code as an individual has to write the code own-self.
    - JQuery, one has to write fewer lines of code than JavaScript. We just need to import the library and use the only specific functions or methods of the library in our code.


Difference Between Polling and GET Request in API Communication
Polling
Repeatedly requests data from a server at regular intervals.	
Can be inefficient, as it makes continuous requests even if no new data is available.
Checking for new messages in a chat app every 5 seconds.
Uses a loop with a delay (e.g., setInterval in JavaScript).

GET Request
A single request to fetch data from the server.
Used to retrieve data once, like fetching a user profile.
More efficient, as it only fetches data when needed.
Fetching a user’s profile data when they visit their profile page.
Uses a direct HTTP request like axios.get().

1. setTimeout() (Basic Delay-Based Animation)
            setTimeout(move, 50); // Moves every 50ms
2. setInterval() (Continuous Loop Animation)
3. requestAnimationFrame() (Smooth Frame-Based Animation)
            requestAnimationFrame(animate);
4. CSS Animations with JavaScript
document.getElementById("box").style.transition = "all 0.5s ease-in-out";
document.getElementById("box").style.transform = "translateX(200px)";



How can i do Array to string
In PHP, if you want to convert an array to a string, you can use methods like implode(), json_encode()


Give 5 array function
 - array_chunk() - function splits an array into chunks of new arrays
 - array_diff() - function compares the values of two (or more) arrays, and returns the differences.
 - array_flip() - function flips/exchanges all keys with their associated values in an array.
 - array_pop()	- Deletes the last element of an array
 - array_push()	- Inserts one or more elements to the end of an array
 - array_search() - function search an array for a value and returns the key
 - array_values() - Returns all the values of an array
 - in_array() -	Checks if a specified value exists in an array
 - count() - function returns the number of elements in an array.

Give 5 String function
 - explode() - Breaks a string into an array
 - echo() - Outputs one or more strings
 - strlen() - function returns the length of a string
 - strrev() - function reverses a string.
 - strtolower() - function converts a string to lowercase.
 - strtoupper() - function converts a string to uppercase.
 - trim() - function removes whitespace and other predefined characters from both sides of a string
 - ltrim() - Removes whitespace or other predefined characters from the left side of a string
 - rtrim() - Removes whitespace or other predefined characters from the right side of a string


Access modifire in php
 - There are three access modifiers:
	public - the property or method can be accessed from everywhere. This is default
	protected - the property or method can be accessed within the class and by classes derived from that class
	private - the property or method can ONLY be accessed within the class


Accessor get value and Mutator set value.

What is the Laravel Service Container, and how does it work?
The Service Container is a powerful dependency injection tool that allows class binding and resolution. Example:
app()->bind('MyService', function () {
    return new \App\Services\MyService();
});

What is a Service Provider, and why is it used?
It is used to register services and bindings in Laravel. The main bootstrapping location is app/Providers/.

What’s the difference between Laravel Sanctum and Passport?
Sanctum: For SPA & mobile authentication (lightweight).

Passport: OAuth2-based full authentication (used for third-party API authentication).

How do you handle API rate limiting in Laravel?
Use the throttle middleware in api.php
Route::middleware(['throttle:60,1'])->group(function () {
    Route::get('/user', 'UserController@index');
});

How do you version APIs in Laravel?
By defining different API routes:
Route::prefix('v1')->group(function () {
    Route::get('/users', 'V1\UserController@index');
});





*****Database logical questions****

What is foreign key?
A foreign key is a column in a database table that creates a relationship between two tables by referencing the primary key of another table. 


How many type of procedure in MYsql
four types of procedures based on their parameter modes:
1. IN Procedure (Accepts input but doesn’t return a value)
2. OUT Procedure (Returns a value as output)
3. INOUT Procedure (Accepts input and modifies it)
4. No Parameter Procedure (Executes logic without parameters)


triggers for automated actions (logging, enforcing constraints).

What is different between Trigger and Procedure ?
Trigger
Executes automatically when an event (INSERT, UPDATE, DELETE) occurs on a table.
Runs based on table events (BEFORE/AFTER INSERT, UPDATE, DELETE).
Cannot return values.
Cannot be called directly; fires automatically.

Procedure
Executes manually using the CALL statement.
Runs when explicitly called by a user or application.
Can return values using OUT or INOUT parameters.
Used for complex operations like batch processing or calculations.
Can be called multiple times explicitly (CALL procedure_name).
More optimized since they execute only when needed.


How can i get second largest salary person in users table ?
-> Using LIMIT and OFFSET
LIMIT 1 OFFSET 1 skips the highest salary and fetches the second highest.

SELECT DISTINCT salary 
FROM users 
ORDER BY salary DESC 
LIMIT 1 OFFSET 1;


DISTINCT provide unique salary record only


You have a users table with 1 million records. When fetching users, the query is very slow. How can you optimize this query?
1. Use Indexing on columns frequently used in WHERE, ORDER BY, or JOIN
2. Use Select Specific Columns instead of SELECT *.
3. Use Pagination instead of fetching all records.



You have a posts table and a comments table (one-to-many). The following query causes the N+1 problem, how do you fix it?
$posts = Post::all();
foreach ($posts as $post) {
    echo $post->comments; // Causes multiple queries
}

-> Use Eager Loading (with()) to reduce the number of queries:
$posts = Post::with('comments')->get(); // Loads comments in one query



You want to restrict access so only admins can access certain pages. How do you implement this in Laravel?
1. Create Middleware   php artisan make:middleware AdminMiddleware
2. Modify Middleware (app/Http/Middleware/AdminMiddleware.php) 
public function handle($request, Closure $next)
{
    if (auth()->user()->role !== 'admin') {
        abort(403, 'Unauthorized action.');
    }
    return $next($request);
}
3. Register Middleware (app/Http/Kernel.php)
protected $routeMiddleware = [
    'admin' => \App\Http\Middleware\AdminMiddleware::class,
];
4. Apply Middleware in Routes (web.php)
Route::middleware(['auth', 'admin'])->group(function () {
    Route::get('/admin/dashboard', [AdminController::class, 'index']);
});




How can you prevent SQL injection attacks in Laravel?
-> DB::select("SELECT * FROM users WHERE email = ?", [$email]); // Uses bindings 


**** For Practical ****

Create signup and signin system in Laravel with two roles (Admin & User)

Step 1: Install Laravel and Set Up Authentication
composer create-project --prefer-dist laravel/laravel AuthProject

Now, install Laravel Breeze for authentication
composer require laravel/breeze --dev
php artisan breeze:install
php artisan migrate
npm install && npm run dev


Step 2: Add Role Column in Users Table
php artisan migrate


Step 3: Update User Model
Step 4: Update Registration Form to Include Role
Step 5: Modify Registration Logic
Step 6: Create Middleware for Role-Based Access
php artisan make:middleware RoleMiddleware

Edit app/Http/Middleware/RoleMiddleware.php:
use Closure;
use Illuminate\Http\Request;
class RoleMiddleware
{
    public function handle(Request $request, Closure $next, $role)
    {
        if (!auth()->check() || auth()->user()->role !== $role) {
            abort(403, 'Unauthorized action.');
        }
        return $next($request);
    }
}

Register middleware in app/Http/Kernel.php:
protected $routeMiddleware = [
    'role' => \App\Http\Middleware\RoleMiddleware::class,
];

Step 7: Create Admin and User Dashboards
Step 8: Create Routes for Role-Based Dashboards
use App\Http\Controllers\AdminController;
use App\Http\Controllers\UserController;

Route::middleware(['auth', 'role:admin'])->group(function () {
    Route::get('/admin/dashboard', [AdminController::class, 'index'])->name('admin.dashboard');
});

Route::middleware(['auth', 'role:user'])->group(function () {
    Route::get('/user/dashboard', [UserController::class, 'index'])->name('user.dashboard');
});

Step 9: Modify Login Redirection Based on Role
Edit app/Providers/RouteServiceProvider.php:
use Illuminate\Support\Facades\Route;

public const HOME = '/dashboard';

public function boot()
{
    parent::boot();

    Route::get('/dashboard', function () {
        if (auth()->user()->role == 'admin') {
            return redirect()->route('admin.dashboard');
        } else {
            return redirect()->route('user.dashboard');
        }
    })->middleware(['auth'])->name('dashboard');
}

Step 10: Create Blade Files for Dashboards
Step 11: Test the Application






