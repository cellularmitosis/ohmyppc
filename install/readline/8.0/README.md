tiger g4 is failing:

```
 /usr/libexec/gcc/powerpc-apple-darwin8/4.0.1/libtool -dynamic -compatibility_version 8.0 -current_version 8.0 -arch_only ppc -install_name /Users/hocal/opt/readline-8.0/lib/libreadline.8.dylib -noall_load -dynamic -undefined dynamic_lookup -weak_reference_mismatches non-weak -o libreadline.8.0.dylib -L/usr/lib/gcc/powerpc-apple-darwin8/4.0.1 -L/usr/lib/gcc/powerpc-apple-darwin8/4.0.1 -L/usr/lib/gcc/powerpc-apple-darwin8/4.0.1/../../.. readline.so vi_mode.so funmap.so keymaps.so parens.so search.so rltty.so complete.so bind.so isearch.so display.so signals.so util.so kill.so undo.so macro.so input.so callback.so terminal.so text.so nls.so misc.so history.so histexpand.so histfile.so histsearch.so shell.so mbutil.so tilde.so colors.so parse-colors.so xmalloc.so xfree.so compat.so -lncurses -lgcc -lSystemStubs -lSystem
ld: flag: -undefined dynamic_lookup can't be used with MACOSX_DEPLOYMENT_TARGET environment variable set to: 10.1
/usr/libexec/gcc/powerpc-apple-darwin8/4.0.1/libtool: internal link edit command failed
make[1]: *** [libreadline.8.0.dylib] Error 1
make: *** [shared] Error 2
```

see https://trac.macports.org/ticket/16286

"The default value for MACOSX_DEPLOYMENT_TARGET is 10.1 on Mac OS X 10.4 and earlier, and 10.5 on Mac OS X 10.5."

see also https://stackoverflow.com/questions/25352389/what-is-the-difference-between-macosx-deployment-target-and-mmacosx-version-min


