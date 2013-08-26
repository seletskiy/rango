rango
====

```
Ring buffer tool.

Read stdout and write in specified <filename> in circular manner, so result
file size is not exceed specified size.

Usage:
    rango [-s <size>] <filename>
    rango -r <filename>

Options:
    -s <size>  Max file size in bytes [default: 1024].
    -r         Output contents of circular buffer.
```

Example usage
-------------

`%` marks no new line at eof.

```
$ echo -n '' | ./rango -s8 asd && ./rango -r asd 
$ echo -n '1' | ./rango -s8 asd && ./rango -r asd
1%
$ echo -n '1' | ./rango -s4 asd && ./rango -r asd 
1%
$ echo -n '12' | ./rango -s4 asd && ./rango -r asd 
12%
$ echo -n '123' | ./rango -s4 asd && ./rango -r asd 
123%
$ echo -n '1234' | ./rango -s4 asd && ./rango -r asd 
1234%
$ echo -n '12345' | ./rango -s4 asd && ./rango -r asd 
2345%
$ echo -n '123456' | ./rango -s4 asd && ./rango -r asd 
3456%
```
