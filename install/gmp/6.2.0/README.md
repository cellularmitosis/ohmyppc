gmp is failing on leopard/g5/gcc-4.2 with:

```
m4  -DHAVE_CONFIG_H -D__GMP_WITHIN_GMP -DOPERATION_add_n -DPIC add_n.asm >tmp-add_n.s
 /usr/bin/gcc-4.2 -std=gnu99 -c -DHAVE_CONFIG_H -I. -I.. -D__GMP_WITHIN_GMP -I.. -DOPERATION_add_n -mmacosx-version-min=10.5 -mcpu=970 -Os tmp-add_n.s -fno-common -DPIC -o .libs/add_n.o
tmp-add_n.s:63:ld instruction is only for 64-bit implementations (not allowed without -force_cpusubtype_ALL option)
tmp-add_n.s:64:ld instruction is only for 64-bit implementations (not allowed without -force_cpusubtype_ALL option)
tmp-add_n.s:68:ld instruction is only for 64-bit implementations (not allowed without -force_cpusubtype_ALL option)
tmp-add_n.s:69:ld instruction is only for 64-bit implementations (not allowed without -force_cpusubtype_ALL option)
tmp-add_n.s:71:rldicl instruction is only for 64-bit implementations (not allowed without -force_cpusubtype_ALL option)
tmp-add_n.s:72:rldicl instruction is only for 64-bit implementations (not allowed without -force_cpusubtype_ALL option)
tmp-add_n.s:74:std instruction is only for 64-bit implementations (not allowed without -force_cpusubtype_ALL option)
tmp-add_n.s:76:ldu instruction is only for 64-bit implementations (not allowed without -force_cpusubtype_ALL option)
tmp-add_n.s:77:ldu instruction is only for 64-bit implementations (not allowed without -force_cpusubtype_ALL option)
tmp-add_n.s:79:rldicl instruction is only for 64-bit implementations (not allowed without -force_cpusubtype_ALL option)
tmp-add_n.s:80:rldicl instruction is only for 64-bit implementations (not allowed without -force_cpusubtype_ALL option)
tmp-add_n.s:82:stdu instruction is only for 64-bit implementations (not allowed without -force_cpusubtype_ALL option)
tmp-add_n.s:86:rldicl instruction is only for 64-bit implementations (not allowed without -force_cpusubtype_ALL option)
tmp-add_n.s:87:rldicl instruction is only for 64-bit implementations (not allowed without -force_cpusubtype_ALL option)
tmp-add_n.s:89:std instruction is only for 64-bit implementations (not allowed without -force_cpusubtype_ALL option)
tmp-add_n.s:94:rldicl instruction is only for 64-bit implementations (not allowed without -force_cpusubtype_ALL option)
tmp-add_n.s:95:rldicl instruction is only for 64-bit implementations (not allowed without -force_cpusubtype_ALL option)
tmp-add_n.s:97:std instruction is only for 64-bit implementations (not allowed without -force_cpusubtype_ALL option)
make[2]: *** [Makefile:768: add_n.lo] Error 1
make[2]: Leaving directory '/Users/hocal/tmp/gmp-6.2.0/mpn'
make[1]: *** [Makefile:995: all-recursive] Error 1
make[1]: Leaving directory '/Users/hocal/tmp/gmp-6.2.0'
make: *** [Makefile:785: all] Error 2
```


from https://code.google.com/archive/p/uhc/issues/10

Unfortunately, just setting -m32 does not seem to be enough. After further investigation, I believe gmp's ./configure needs CFLAGS to contain the two options "-m32 - force_cpusubtype_ALL". Below, are the final few lines of the gmp buildlog, using only -m32. I have checked that these errors are generated even with the latest version of gmp-4.3.1 downloaded from gmplib.org. However, with the extra (Darwin-only) option, -force-cpusubtype_ALL, compilation proceeds normally, but 'make check' of gmp shows some failures. So I'm not sure there is a good overall solution. The gmplib.org page does warn that "GMP is very often miscompiled ... the compilers that cause most problems are ... in particular Apple's gcc releases"


this is useful: https://gcc.gnu.org/onlinedocs/gcc/Darwin-Options.html

