leopard g5 is failing:

```
FAIL: aeadtest.sh
PASS: aes_wrap
...
PASS: rfc5280time_small.test 1
SKIP: rfc5280time_small.test 2 - rfc5280time_64-bit # SKIP this system is unable to represent times past 2038
PASS: rmdtest
...
PASS: ssl_versions
FAIL: ssltest.sh
PASS: testdsa.sh
...
PASS: tlsexttest
FAIL: tlstest.sh
PASS: tls_ext_alpn
...
PASS: x509name
============================================================================
Testsuite summary for libressl 3.2.0
============================================================================
# TOTAL: 79
# PASS:  75
# SKIP:  1
# XFAIL: 0
# FAIL:  3
# XPASS: 0
# ERROR: 0
============================================================================
See tests/test-suite.log
============================================================================
make[3]: *** [Makefile:1972: test-suite.log] Error 1
make[3]: Leaving directory '/Users/hocal/tmp/libressl-3.2.0/tests'
make[2]: *** [Makefile:2080: check-TESTS] Error 2
make[2]: Leaving directory '/Users/hocal/tmp/libressl-3.2.0/tests'
make[1]: *** [Makefile:2714: check-am] Error 2
make[1]: Leaving directory '/Users/hocal/tmp/libressl-3.2.0/tests'
make: *** [Makefile:455: check-recursive] Error 1
```

