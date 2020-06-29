icu fails under leopard's gcc-4.2.  however, the error is misleading:

```
checking size of wchar_t... 0
configure: error: There is wchar.h but the size of wchar_t is 0
```

but the actual problem is that c11 is not implemented in gcc 4.2:

```
cc1: error: unrecognized command line option "-std=c11"
```

c11 requires at least gcc 4.7:

https://stackoverflow.com/a/16256596


