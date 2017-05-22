# browserstack-alpine-bug

Demonstrates an issue with BrowserstackLocal on alpine linux container

## Run
```
> docker-compose up
```
Outputs the following, showing that the binary doesn't work properly on alpine:
```
...
test-alpine_1  | standard_init_linux.go:178: exec user process caused "no such file or directory"
browserstackalpinebug_test-alpine_1 exited with code 1
test-debian_1  | BrowserStack Local version 6.8
browserstackalpinebug_test-debian_1 exited with code 0
```
In addition, `ldd` on the `BrowserstackLocal` file indicates a lot of errors:
```
~/.browserstack # ldd BrowserstackLocal
        /lib64/ld-linux-x86-64.so.2 (0x5584955c9000)
        libdl.so.2 => /lib64/ld-linux-x86-64.so.2 (0x5584955c9000)
        librt.so.1 => /lib64/ld-linux-x86-64.so.2 (0x5584955c9000)
Error loading shared library libstdc++.so.6: No such file or directory (needed by BrowserstackLocal)
        libm.so.6 => /lib64/ld-linux-x86-64.so.2 (0x5584955c9000)
Error loading shared library libgcc_s.so.1: No such file or directory (needed by BrowserstackLocal)
        libpthread.so.0 => /lib64/ld-linux-x86-64.so.2 (0x5584955c9000)
        libc.so.6 => /lib64/ld-linux-x86-64.so.2 (0x5584955c9000)
Error relocating BrowserstackLocal: _Znam: symbol not found
Error relocating BrowserstackLocal: _ZNSo3putEc: symbol not found
Error relocating BrowserstackLocal: _ZNSt14basic_ofstreamIcSt11char_traitsIcEE4openEPKcSt13_Ios_Openmode: symbol not found
Error relocating BrowserstackLocal: _ZTv0_n24_NSoD1Ev: symbol not found
Error relocating BrowserstackLocal: _ZNSt14basic_ofstreamIcSt11char_traitsIcEED0Ev: symbol not found
Error relocating BrowserstackLocal: _ZSt29_Rb_tree_insert_and_rebalancebPSt18_Rb_tree_node_baseS0_RS_: symbol not found
Error relocating BrowserstackLocal: _ZNSs12_M_leak_hardEv: symbol not found
Error relocating BrowserstackLocal: _ZNSt15basic_streambufIcSt11char_traitsIcEE9pbackfailEi: symbol not found
Error relocating BrowserstackLocal: _ZNSt13basic_filebufIcSt11char_traitsIcEE5closeEv: symbol not found
Error relocating BrowserstackLocal: _ZNSs6insertEmPKcm: symbol not found
Error relocating BrowserstackLocal: _ZNSt8ios_baseC2Ev: symbol not found
Error relocating BrowserstackLocal: _ZNSt15basic_streambufIcSt11char_traitsIcEE5imbueERKSt6locale: symbol not found
Error relocating BrowserstackLocal: _ZNSt15basic_streambufIcSt11char_traitsIcEE5uflowEv: symbol not found
Error relocating BrowserstackLocal: _ZNSt8ios_baseD2Ev: symbol not found
Error relocating BrowserstackLocal: _ZSt17__throw_bad_allocv: symbol not found
Error relocating BrowserstackLocal: _ZNSo9_M_insertIxEERSoT_: symbol not found
Error relocating BrowserstackLocal: _ZNSoD0Ev: symbol not found
...
```
