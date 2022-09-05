# APCu

APCu is the successor of the "Alternative PHP Cache" short APC. APC was a PHP extension which covered two tasks. Firstly as a PHP accelerator that stored bytecode in memory. Through this bytecode cache, the PHP interpreter does not have to interpret the entire bytecode with every call. Instead, the already computed code can be executed. This functionality has been replaced by OPcache.

On the other hand, APC has a data cache in which a PHP application itself could store data. This function is now taken over by "APC User Cache" in short APCu. Thanks to APCu, database queries, for example, can be placed in the cache and thus save time.



## Increase the apc.shm_size value

If APCu is not allocated enough memory, errors like this may occur:

```PHP Warning: apc_store(): Unable to allocate memory for pool.```

To fix this error you can allocate more memory to APCu.

To set the value correctly you have to know how much memory APCu has at the moment. The easiest way is to check the apc.shm\_sie settings in the command line.

```$ php -i | grep aapc.shm_size```

```Apc.shm_size => 8M => 8M```

To increase the value to, for example, 16M, changes must be made in the ``php.ini`` file.

```Apc.shm_size = 16M```

Afterwards php-fpm must be restarted.

```$ sudo service php7.0-fpm restart```

```[ok] Restarting PHP 7.0 FastCGI Process Manager: php-fpm7.0```

## APCu monitoring

To monitor APCu the apc.php script can be used.

The script gives important information like:

### APCu memory usage

The script calculates free and used memory and gives a clear overview of cache hits and misses. As in any caching system, the more hits the better.

![image](https://user-images.githubusercontent.com/47870802/187645357-8caf875b-ba36-4d71-9265-2b6518232c47.png)

### APCu cache fragmentation

The cache fragmentation is a bit more complicated. You should simply remember the following: The less fragmentation the better.

![image](https://user-images.githubusercontent.com/47870802/187645421-782b129f-b23d-47bc-85df-7747d7077669.png)

### Host stats

- General Cache Information (APCu version, uptime)
- Cache information (cached variables, hit rate)
- Runtime settings (APCu settings, eg. ``apc.shm_size``)

### User Cache Entries

To access the user cache entries, the default password string must be edited in the apc.php script.

```defaults('ADMIN_USERNAME','apc'); //Admin Username``

```defaults('ADMIN_PASSWORD','password'); //Admin Password - CHANGE THIS TO ENABLE!!!```

It is worth the effort to change the settings because you get access to granular data in each cache entry.

- Number of hits
- Size
- Last modified, created on and timeout (if set)
- Path to the file (double click on an entry)

You also have the option to clear all cache entries for the APCu cache.
