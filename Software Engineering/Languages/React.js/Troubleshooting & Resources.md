# Troubleshooting

### Terminal

> 1. Check if Apache is on  `localhost``
> 2. ``localhost/api/info.php`
> 3. Change `memory_limit``
> 4. ``php -i`
> 5. Insert `error_report = E_ALL display_error = O` in XAMPP > Config> php.ini

### XAMPP

> XAMPP > Logs > error.log

### JS

> Use `debugger;`
>
> ````echo "adfad"; exit;`

> app/Http/Controllers/DataController.php > filter

### Browser

> 1. F12 and select `React` tab
> 2. Enable `Select a React element in the page to inspect it`
> 3. Hover the component 

### JSON

> In `server/proxy.js`
>
> ```react
> app.use('*/workload_stats', function (req, res, next) {
>         next(); return
>         sendMock(res, './workload_stats.json');
>     }
> );
> ```
>
> 
>
> In server, create a new file called XXX.json and click format
>
> ```react
> //Import JSON from F12 > Networks > Response
> ```
>
> 



# Resources

[Material-UI](http://www.material-ui.com/#/components/table)

[React tutorial by Facebook](https://facebook.github.io/react/tutorial/tutorial.html)

[Font Awesome](http://fontawesome.io)

[Swagger](https://swagger.io/)

[A Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)

[Material  Design](https://material.io/)