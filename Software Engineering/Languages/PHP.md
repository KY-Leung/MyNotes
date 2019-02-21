### Debugging

```php
memory_limit

echo ini_get('memory_limit');
    
var_dump(debug_backtrace(DEBUG_BACKTRACE_IGNORE_ARGS, 10)); exit;
    
ini_set('memory_limit','7G');
    
error_log

```



### Declare Public

```php
public $datestr = "";

$this->datestr = $datestr;
```



### Function: Default parameters

```php
function getData($name, $limit = '50', $page = '1') {
    ...
}
```



### [Declare Object](https://www.webmaster-source.com/2009/08/20/php-stdclass-storing-data-object-instead-array/)

```php
$book = new stdClass;
$book->title = "Harry Potter and the Prisoner of Azkaban";
$book->author = "J. K. Rowling";
$book->publisher = "Arthur A. Levine Books";
$book->amazon_link = "http://www.amazon.com/dp/0439136369/";

$book->title
```

```php
$array = array(
"title" => "Harry Potter and the Prisoner of Azkaban",
"author" => "J. K. Rowling",
"publisher" => "Arthur A. Levine Books",
"amazon_link" => "http://www.amazon.com/dp/0439136369/"
);
$books = (object) $array;
```

Casting an object into an array: `$array = (array) $object`



### Declare array of object

```php
public $emptyWeekArray = array('Monday' => '0', 'Tuesday' => '0', 'Wednesday' => '0', 'Thursday' => '0', 'Friday' => '0', 'Saturday' => '0', 'Sunday' => '0');
```



### [Call function in function from another class PHP](https://stackoverflow.com/questions/8420431/call-function-in-function-from-another-class-php)

```php
$cls_a = new ClassA();
$cls_a->method1();

// or alternatively, you don't even need to instantiate ClassA
echo ClassA::method1();

//from PHP 5.4
(new ClassName)->method();
```



### `time()` 

> Returns the current time in the number of seconds since the Unix Epoch



### [Escaping](https://www.quora.com/What-is-escaping-to-PHP)

> Escaping a string means to reduce ambiguity in quotes (and other characters) used in that string

```php
//string with double quotes within it
"Hello "World.""

//escaping
"Hello \"World.\""

```



### [{{     }} VS {!!     !!}](https://laracasts.com/discuss/channels/general-discussion/blade-this-vs-that?page=0)

> To escape data use

```php
{{ $data }} 
```

> If you don't want the data to be escaped use :

```php
{!! $data !!}
```



### [Laravel Database Query Builder](https://laravel.com/docs/5.5/queries) 

```php
$systemInformation = SystemInformation::where('accountId', $accountId)->pluck('sysId');
```



### [Eloquent ORM](https://laravel.com/docs/4.2/eloquent)



### [Eloquent ORM VS Query Builder](https://stackoverflow.com/questions/38391710/laravel-eloquent-vs-query-builder-why-use-eloquent-to-decrease-performance)

> Eloquent is Laravel's implementation of Active Record pattern.
>
> #### Pros
>
> It is a good solution to use when you process a single entity in a CRUD manner: read from database or create a new entity and then save it or delete.
>
> * dirty checking (to send SQL UPDATE only for the fields which have been changed)
> * model events (e.g. to send administrative alert or update statistics counter when someone has created a new account)
> * traits (timestamps, soft deletes, custom traits) eager/lazy loading etc.
>
> ####Cons
>
> * comes with some performance price. When you process a single or just a few records, there is nothing to worry about. But for cases when you read lots of records (e.g. for datagrids, for reports, for batch processing etc.) the plain DB is better approach.
>
> ####Overall
>
> Use Laravel's Eloquent in web forms to process a single record
>
> Use DB (with SQL views) to retrieve data for grids, export etc.



###[Laravel HTTP Request](https://laravel.com/docs/5.5/requests)



```php
$sql = "select accessTokenExpireDate"
            . " from sessions where"
            . " userId = ? and accountId = $accountId";
$sessions = DB::select($sql, [$user->userId]);
```



###[Scope Resolution Operator `::`](http://php.net/manual/en/language.oop5.paamayim-nekudotayim.php#language.oop5.paamayim-nekudotayim)

| Files                               | Directory                  |
| ----------------------------------- | -------------------------- |
| routes.php                          | /api/app/Http/             |
| IncidentController.php              | /api/app/Http/Controllers/ |
| Incident.php                        | /api/app/                  |
| PGObject.php<br />(w/ parseFilters) | /api/app/                  |

LIKE: case-sensitive

ILIKE: case-insensitive

