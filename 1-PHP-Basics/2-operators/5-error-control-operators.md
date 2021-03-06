###Error Control Operators 
<p>PHP supports one error control operator: the at sign (@). When prepended to an expression in PHP, any error messages that might be generated by that expression will be ignored.</p>
<p>If you have set a custom error handler function with set_error_handler() then it will still get called, but this custom error handler can (and should) call error_reporting() which will return 0 when the call that triggered the error was preceded by an @.</p>
<p>If the track_errors feature is enabled, any error message generated by the expression will be saved in the variable $php_errormsg. This variable will be overwritten on each error, so check early if you want to use it.</p>

```PHP
<?php
/* Intentional file error */
$my_file = @file ('non_existent_file') or
    die ("Failed opening file: error was '$php_errormsg'");

// this works for any expression, not just functions:
$value = @$cache[$key];
// will not issue a notice if the index $key doesn't exist.

?>
```

###### Links
 - http://php.net/manual/en/language.operators.errorcontrol.php